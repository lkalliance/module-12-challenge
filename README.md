# Employee Manager [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Description

<img src='./assets/images/EM-screenshot-1.png' width='300' style='float: right; margin-left: 15px;' />

The Employee Manager CLI application allows a user to enter information about a company's organization and to display it in an organized fashion based on an information tree of Department > Role > Employee.

I like keeping track of the staff of my local MLB franchise, I don't think they get enough attention. It occurred to me that actual business owners might make good use of such a tool as well! So I made this.

You can view a video walkthrough of the application [here](https://drive.google.com/file/d/1ciPhbsTWx50Fex4kUeDg7YmctreaJ2YR/view?usp=sharing).


## Table of Contents


* [Installation Instructions](#installation-instructions)
* [Usage Information](#usage-information)
* [Application Features](#application-features)
* [Design Notes](#design-notes)
* [Credits](#credits)
* [Software License](#software-license)
* [Contact the Developer](#contact-the-developer)

## Installation Instructions

This is a Node.js application that utilizes a MySQL database. Make sure you have MySQL installed on the host computer. 

There are several several dependency modules, all either available via npm or custom built and included. The custom modules are in the /modules directory, and the dependencies can be installed with "npm i" in the presence of this app's "package.json" file. In its abssence, download these npm modules:
* inquirer (no later than version 8.2.4)
* mysql2
* press-any-key
* console.table

Once all the modules are in place, run the provided schema sql file (/db/schema.sql) at your mysql prompt to create the database. You can also pre-seed the database with some test data by running the seeds file (/db/seeds.sql).


## Usage Information

To launch the Employee Manger, in your terminal from inside the diretory where you've installed the application run "npm start", or in the absence of npm run "node index".

You will be offered a series of available actions:
* View Employees, Roles or Departments
* Add Employee, Role or Department
* Update an employee's Role or Manager

<img src='./assets/images/EM-screenshot-2.png' />

The definitions of each kind of entity are cascading: Roles are children of Departments, so to enter a Role you must have at least one Department; Employees must have a Role, so to enter an Employee you must have at least one Role.

To enter a Department, Role or Employee, simply follow the prompts after selecting the action. An employee's Role and Manager can be updated later. You do have the option of listing Employee with no Manager, but not with no Role. To update an employee's Role or Manager, select the action and follow the prompts.

<img src='./assets/images/EM-screenshot-4.png' />

In all, the data associated with each entity are:
* Departments have an (auto-entered) id, and a name.
* Roles have an (auto-entered) id, a title, a salary, and belong to a Department.
* Employees hava an (auto-entered) id, a first and last name, inhabit a Role, and report to a Manager. Via their assigned Role, they have a related Department and salary.

Viewing any of the lists is simple: select the appropriate option. Departments are sorted by id, Roles are sorted by Department and then by salary, and Employees are sorted by last name.

<img src='./assets/images/EM-screenshot-3.png' />

## Application Features

* Simple, directed entry interface
* Relational assignment of Departments and salaries to Employees
* Guardrails to prevent illogical associations
* A snazzy splash screen!

## Design Notes

* Early in the design of the Employee Manager, I decided that when showing Employees in a selectable list, to include parenthetically their current titles, to make manager selection decisions easier.
* There are two different arrays of Employees for use in inquirer prompts. One includes a "No one" option for choosing a manager when creating a new Employee, and the other doesn't for when you are updating the manager. I wasn't originally going to give the option to not list a manager, but it became clear to me that unless you entered your Employees in a reasonably planned order, that any given Employee's manager might not yet exist at the point of entry. Rather than demand a user choose a "placeholder" manager, I left it an option to have none, at least on creation.
* After some thought, I've opted to clear the screen before each readout. It felt like there was more attention devoted to the information rather than the visual clutter that preceded it.
* There are some features that I would put in next: the ability to edit Roles and Departments and Employee names; the ability to delete Employees and Roles or otherwise mark them as no longer part of the company; the ability to sort the Employees list on a variety of columns; the ability to ask for a list of Roles or Employees for a specific Department; and the ability to ask for a subset of Employees that report to a chosen manager.


## Credits

The original code for the Employee Manager is written by Lee Klusky. Per usual, I have received guidance and the contribution of much wisdom from the instructional and tutorial staff of the University of Minnesota Full Stack Coding Boot Camp. I've also received much wisdom from developers and commenters from around the Web, most notably at [Stack Overflow](https://www.stackoverflow.com), the [Mozilla Developer Network](https://developer.mozilla.org), and [W3 Schools](https://www.w3schools.com).


## Software License

©2023, Lee Klusky

This software is covered by a [MIT License](https://opensource.org/licenses/MIT).

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Questions?

Contact me at <a href="mailto:lkbootcamp@yahoo.com">lkbootcamp@yahoo.com</a>, or visit my [GitHub profile](https://www.github.com/lkalliance).
