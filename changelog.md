# Change Log

## Version 1.0 Initial Application Requirements

* User form captures data and submits it to MySQL Database
* View filter will be by department or by employee
* Department view will display all submissions by department
* Employee view will display all submissions by employee
* Create a view for individual form
* User selects a category
* User is allowed to add tasks to selected category
* User must complete a “clear the path” field for thyself or other 

## Version 1.0 Initial Application Design

* Survey page will query for the goals/tasks submitted and paths/actions submitted for that week
* Query will select all goal/task&paths/actions ids associated with a user’s last submission
* Last submission looked up by “last_submission_id” field in the employees take, once it is found we will inner join tasks and submissions to find all goals for the employee’s submission.
* When a user hits submit, the submission row’s “completed” field is updated to 1, to indicate it’s been submitted. A new submission is then created, ready for a user to attach more goals.
* Page will also display the users name and the goal for the week. Both fields can be pulled from the DB
* When user hits submit, a submission ID is stored

## Version 1.0 Initial Application Action Flow

* User accesses application home page
* If user does not have an active “last submission”, we create one and display all goals associated with the submission. (which is zero until user adds goals)
* If user has a last submission, we will display all goals associated with that last submission.
* Once a user submits their goals, we will set the submission “complete” field to complete/1, and generate a new submission. Their last submission id will be updated in their row.     

## Database Schema (Initial Draft)

```
Employees
* employee_id            / int (primary key)
* employee_name          / string
* employee_dep           / int
* creation_date          / date
* last_submission_id     / int
* last_submission_status / int

Tasks
* task_id                / int (primary key)
* task_type              / int
* task_content           / string
* creation_date          / date
* employee_id            / int
* submission_id          / int

Actions
* action_id           / int (primary key)
* action_path_type    / int
* action_path_content / string
* action_completed    / int
* creation_date       / date
* employee_id         / int

Submissions – Goals reference table
* submission_id           / int (primary key)
* submission_completed    / int
* creation_date           / date
* employee_id             / int
```


## Version 1.1 Requested Changes by Nyreen

* List goals for year on “add goal/path” page
* Label the goals and paths table for users distinction
* Add edit functionality so users can change their goals before submission.
* Add status functionality so users can update status of previously submitted goals

## Version 1.2 Suggested Changes by Nyreen, Dawn and Swetha

* Update WIG status options to include “Not Started”, “In-Progress” or “Complete”.
* Not Started will appear red or white, in-progress will appear yellow, complete will appear green
* Add a logging feature to track all edits/changes made to goals
* Add a way for users to select which employee they want to “Clear The Path” for.

## Version 1.3 Suggested Changes by Team

* Add a way for users to select which employee they want to “Clear The Path” for.
* Add a way for users to select an employee or “resource” they need to “clear the path” for them.
* A mailing feature will also be implemented to send mail to users who have been selected for a “clear the path”
* Create a feature to allow a user to select a department in the case they don’t know which employee to select (Greg’s suggestion)
* Score card display to track task completion for employees and departments
* Allow users to add notes to the status of a task (closing task notes or incomplete task notes for additional information)
* Create a feature to allow users the ability to download a physical copy
* Functionality exists, only need to create the HTML view.
* Create users to select a theme for the application (new look or old look)
* This is for users who prefer the old form look. Users will be able to customize their portal’s theme to accommodate their preference.

## Version 1.4 Revising Changes requested by Team per version 1.3 
**(In-Progress)**
- [x] New Icons – Notification Bell, Text Sizer, PDF File, Expand and Shrink
- [x] Add Dark Mode, Light Dark Mode – User will be allowed to select their preferred color scheme.
- [x] Classic View button will be moved to an icon instead of a button
- [x] Add Expand Mode – This will allow user to expand table out into a full screen view
- [x] Add Text Sizing – This will allow users to increase or decrease the size of text
- [x] Add Notifications – User will receive a notification when selected for a “clear the path” task.
- [x] Clicking the notification bell will switch the table view to a the “clear the path” requests
- [x] Arrow Navigator – This will allow users to navigate their submissions via Arrow keys. Left goes backwards, right goes forward.
- [x] Add Date Picker – This will allow users to pick the date on a GUI calender instead of typing in numbers
- [x] User Feedback - Send user feedback when action occurs (adding a goal/path)
- [x] Tool Tip - Add a tool tip description for all icons and buttons
- [x] Dark Mode Icon Change - Change shading of icon to indicate whether light or dark mode is toggled
- [x] Look into removing the goal ID section for more table space
- [x] Notifcations - Remove bell icon if no notifications exist
- [x] Expand Mode - Allow tables to fit to content
- [ ] Provide description when user hovers over table fields
- [ ] Alt parameters - Give each button, image and icon an alt parameter for ADA compliance
- [ ] Email notification will be sent out to the selected user (must be implemented in prod due to test server limitations)

### Bug Fixes per version 1.3 and 1.4
- [x] Fix table sizing issues
- [x] Fix window sizing issues on laptop displays
- [x] Fix issue on line 30 of download-template.php (undefined var $main) 
- [x] Fix issue on line 2 of hamburgermenu.php (undefined var $colorSheet) 
- [x] Fix issue with "Add Goal" becoming "Add Path" when user closes form
- [x] Fix issue submission table overlapping format :(
- [x] Fix response live search field for Paths form
- [x] Fix bell icon click action for submission page. Generating multiple javascript errors.
- [x] Fix issue with text failing to size on for requester table
- [x] Remove bell icon when no notifications exist
- [x] Fix issue with color mode toggling twice (probably eventlistener bug of some kind)
- [ ] Few more small adjustments should be made for laptop displays (hamburger menu overlapping with table, week of disappears when zoomed)
- [ ] Last employee submission for loadcontent.php needs to be fixed for submissions page
- [ ] Prev/Next feature must be changed for submission.php page
