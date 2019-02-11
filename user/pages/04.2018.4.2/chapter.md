---
title: GitPrime Enterprise 2018.4.2
taxonomy:
    category: docs
child_type: docs
---


### Latest Release: 2018.4.2

>>> <i class="fa fa-exclamation"></i> Important: This release introduces several data changes that are important for providing you with improved performance.  Please read this section before upgrading.

Upgrading to GitPrime Enterprise 2018.4.2 introduces several data changes that are important.  This can mean that the release will take some time, depending on the size of your data.  Please be patient with the upgrade.

Before starting the upgrade, you should:

- Backup your database.  This can be done by following the instructions found in the "Backups" section of this wiki.
- Be sure that you have a valid database backup that can be restored.
- Read the section "Updating GitPrime Enterprise" section thoroughly before starting the update.
- Make sure you have installed Docker version 17.12.1 or greater. See Installing Docker for more information.
- Make sure you have installed Replicated version 2.28.0 or greater. See Installing Replicated for more information.

>>>>>> Features:

- Review Collaboration Submitter and Reviewer detail drill downs now lazy load on scroll rather than paginating data
- PR time series charts (Review Workflow, Review Collaboration detail view, and PR Resolution) UI update to PR's closed and merged without review
- Repos Imported and Available tabs now persist mutual filters when navigating between pages
- Added a sortable Status column and filter for imported repos to easily find and manage blocked repos
- Repo Group names are now visible and filterable on the Imported Repos page
- Added the repo URL to imported repos for all self-hosted integrations to the Repo Details page
- Significant performance improvement via Database partitioning

>>>> Bugs:

- Fixed issue in Review Collaboration causing Sort by  selections to not appropriately persist
- Fixed issue with some Merged and Closed PR's not having a closed_at date
- Fixed issue with Unicode characters causing an SSH import to fail
- Fixed issue with Repos Imported and Repos Available page not sorting correctly due to pagination
- Fixed issue with failing O-Auth connection warnings appearing on the wrong active window
- Fixed issue causing Fundamental tiles to be cut off on small window sizes
- Fixed issue where the Settings side nav would be hidden when drilled into an individual author in the Worklog
- Fixed issue causing the Targets page to not handle saving null values in some cases
- Fixed issue causing repo names to be vertically offset in FireFox
- Fixed an issue causing authors that were assigned to a team to appear in the "Unassigned Contributors" team if they had specific view rights

>>>>> Miscellaneous Updates and Fixes:

- Updated language on Review Collaboration reports to better convey when selected periods have "No data" rather than simply displaying zeros
- Personal Info and Email Preferences screens have been moved to a single Personal Preferences screen
- SSO screen is now in react
- PR Metrics re-processor now reruns after authors are hidden/unhidden or merged together
- Added PR Resolution target labels
- Updated the author color randomizer for tooltips to better prevent like colors 
- Added week separation lines to Worklog when weekends are turned off
- Removed the Current Period from the fundamentals trendline for more accurate Trend calculations
- Replaced the 4-week trailing avg from Fundamentals tiles with the average for the selected time period
- Removed ability to delete individual Ticket and PR Projects as they would be re-imported the next time discovery was run
- Added a minimum size to commit bubbles on Worklog