# github-ci-presentation

This repository serves as a demonstration for showcasing the usage of GitHub Actions and its capabilities during PyCon PL 2023. It provides practical examples and workflows to illustrate the power and versatility of GitHub Actions in the Python development ecosystem.

# Requirements
- __Poetry >= 1.3.0__: The project requires Poetry version 1.3.0 or higher for dependency management and packaging. You can refer to the official installation guide for instructions on installing Poetry.

- __Python >= 3.7__: The project is compatible with Python version 3.7 and higher. Please ensure that you have Python installed on your system.

- __git__: Git is required for cloning the repository and version control operations. Make sure you have Git installed and configured on your machine.

- __GitHub account__: You will need a GitHub account to clone the github-ci-presentation repository and interact with the GitHub platform.

- __PyPI account (optional)__: Having a PyPI account is optional. It is only necessary if you want to publish and distribute your project on the Python Package Index (PyPI).

# Setup

To get started, clone the github-ci-presentation repository by running the following command in your terminal:

``` bash
git clone git@github.com:uoboda-splunk/github-ci-presentation.git
```

Next, navigate into the cloned repository directory and install the project dependencies using Poetry:

``` bash
cd github-ci-presentation
poetry install
```

Once the installation is complete, you can activate the Poetry shell environment to work within it:

``` bash
poetry shell
```

By spawning the Poetry shell, you will have access to the project's virtual environment, allowing you to execute commands and interact with the project more efficiently.

# Project description
The jobsim library is designed to function as a straightforward workplace manager. Its current features include the ability to register new employees and schedule introduction trainings for them. You can define various departments in the jobsim/departments directory and different locations in the jobsim/locations directory. Once an employee has been assigned to their respective department and location, trainings can be scheduled accordingly.

The example.py file in the jobsim repository provides an illustrative demonstration of how the library can be utilized. It showcases the practical implementation of various functions and features within the jobsim library. By examining the example.py file, you can gain a better understanding of how to effectively employ the jobsim library for managing employees, departments, locations, and training schedules

``` python
from jobsim.employee import Employee
from jobsim.location import Location
from jobsim.department import Department
from jobsim.trainings_scheduler import schedule_trainings

IT = "it"
FINANCE = "finance"
SF = "San_francisco"
KRK = "Krakow"
SYD = "Sydney"

employee_1 = Employee("Jackie", "1", Department(IT), Location(SF))
employee_2 = Employee("Molly", "2", Department(FINANCE), Location(SF))
employee_3 = Employee("Mark", "3", Department(IT), Location(KRK))
employee_4 = Employee("John", "4", Department(IT), Location(SYD))
employee_5 = Employee("Bob", "5", Department(FINANCE), Location(SYD))
employee_6 = Employee("Andrew", "6", Department(FINANCE), Location(KRK))
employee_7 = Employee("Tom", "7", Department(FINANCE), Location(SYD))
employee_8 = Employee("Gary", "8", Department(IT), Location(SF))
employee_9 = Employee("Martin", "9", Department(IT), Location(SF))

schedule_trainings(
    [
        employee_1,
        employee_2,
        employee_3,
        employee_4,
        employee_5,
        employee_6,
        employee_7,
        employee_8,
        employee_9,
    ]
)
```

To run example:

``` bash
python example.py
```

Output:
```
Jackie is a new employee in San_francisco 🇺🇸
Jackie is joining IT department 💻
Molly is a new employee in San_francisco 🇺🇸
Molly is joining FINANCE department 💵
Mark is a new employee in Krakow 🇵🇱
Mark is joining IT department 💻
John is a new employee in Sydney 🇦🇺
John is joining IT department 💻
Bob is a new employee in Sydney 🇦🇺
Bob is joining FINANCE department 💵
Andrew is a new employee in Krakow 🇵🇱
Andrew is joining FINANCE department 💵
Tom is a new employee in Sydney 🇦🇺
Tom is joining FINANCE department 💵
Gary is a new employee in San_francisco 🇺🇸
Gary is joining IT department 💻
Martin is a new employee in San_francisco 🇺🇸
Martin is joining IT department 💻

----------------- Required trainings -----------------

Required trainings for Jackie: security_team, hr_intro, health_training,
Required trainings for Molly: law_team, hr_intro, health_training,
Required trainings for Mark: security_team, hr_intro, health_training,
Required trainings for John: security_team, hr_intro, health_training,
Required trainings for Bob: law_team, hr_intro, health_training,
Required trainings for Andrew: law_team, hr_intro, health_training,
Required trainings for Tom: law_team, hr_intro, health_training,
Required trainings for Gary: security_team, hr_intro, health_training,
Required trainings for Martin: security_team, hr_intro, health_training,

----------------- Scheduled trainings -----------------

Trainings for Jackie: security_team miami Tue 9-17, hr_intro las_vegas Fri 8-10, health_training chicago Fri 9-14,
Trainings for Molly: law_team boston Wed 7-12, hr_intro las_vegas Fri 8-10, health_training chicago Fri 9-14,
Trainings for Mark: security_team warsaw Mon 9-17, hr_intro rzeszow Mon 8-10, health_training warsaw Fri 8-13,
Trainings for John: security_team melbourne Wed 9-17, hr_intro melbourne Mon 9-11, health_training perth Mon 10-15,
Trainings for Bob: law_team perth Fri 11-16, hr_intro melbourne Mon 9-11, health_training perth Mon 10-15,
Trainings for Andrew: hr_intro rzeszow Mon 8-10, health_training warsaw Fri 8-13,
Trainings for Tom: law_team perth Fri 11-16, hr_intro melbourne Mon 9-11, health_training perth Mon 10-15,
Trainings for Gary: security_team miami Tue 9-17, hr_intro las_vegas Fri 8-10, health_training chicago Fri 9-14,
Trainings for Martin: security_team miami Tue 9-17, hr_intro las_vegas Fri 8-10, health_training chicago Fri 9-14,
```

To run small tests:
``` bash
poetry run pytest -v tests/small
```

To run large tests:
``` bash
poetry run pytest -v tests/large
```

# Tasks

## 1. Prepare your copy of workshop repository

During the workshop, we will utilize this repository as a hands-on demonstration of the powerful functionality provided by GitHub Actions. To get started, please fork this repository by following these steps:

1. Click on the `Fork` button in the top-right corner of the page.
2. Select your own GitHub account or to create a fork of the repository.

Once you have successfully forked the repository, you may notice that the Actions history is currently unavailable. To enable access to the Actions history and start utilizing workflows, please perform the following steps:

1. Open the forked repository in your GitHub account.
2. Navigate to the `Actions` tab located near the top of the repository's page.
3. Click on the `I understand my workflows, go ahead and enable them` button
This will enable Actions for the repository, allowing you to view and execute workflows.

In order to initiate the first workflow run, an additional trigger needs to be added to the main workflow. This trigger, called `workflow_dispatch`, enables manual runs of the workflow. To add this trigger, please follow these instructions:

1. Open the main workflow file in the repository (main.yml file)
2. Locate the existing event trigger workflow configuration (section starting with `on`)
3. Add the `workflow_dispatch` trigger to the workflow configuration without any input parameters.

Once you have made the required modifications to the workflow file, it is essential to push the changes to the main branch. By doing so, you will activate the `workflow_dispatch` trigger and make manual runs of the workflow possible.

To initiate a manual workflow run, follow these steps:

1. Go to the `Actions` tab of the repository
2. Select the `main` workflow
3. Click on the `Run workflow` button
4. Trigger the workflow run
5. Check workflow execution

## 2. Make main workflow green
You might have noticed that the `report_workflow` job is currently failing after forking the repository. This issue arises due to the absence of necessary actions secrets, which are crucial for the successful execution of the job. Please follow the steps below to set up the required secrets:

1. Navigate to the "Settings" tab located near the top-right corner of the GitHub repository page
2. In the left sidebar, click on the `Secrets and variables` option and `Actions` next
3. Click on the `New repository secret`
4. Create the first secret by specifying the name as `SPLUNK_HOST` and provide the appropriate value. This secret is used to configure the host for the Splunk integration.
5. Next, create the second secret with the name `SPLUNK_TOKEN` and input the corresponding value. This secret is required for authenticating and authorizing access to the Splunk service.
6. Through the `Actions` tab of the repository navigate to main workflow with unsuccessful `report_workflow` run and trigger rerun manually. This time job should pass

Values for these secrets will be provided during the workshop.

Take a look at the logs in the GitHub Actions console. You can utilize the search box to find specific information within the logs.
Additionally, there are options available to rerun specific jobs if needed.

> **_NOTE:_**
> Please remember to always execute the `report_workflow` job as the last one to ensure accurate tracking of progress. Keep this in mind when adding new jobs to the workflow.

## 3. Create job running large tests
Please create an additional job in the main workflow named `large-tests` that executes large tests. Currently, it should run in parallel with the
`small-tests` job. Ensure that the results obtained from the GitHub Actions run are identical to the results obtained from running the large tests locally.

Modify needs parameter for `report_workflow`, as this job must be ran as the last one in the workflow.

GitHub documentation: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idneeds

In the context of the `needs` parameter, let's consider the different job hierarchy in our project. We can add `needs` to the `pre-commit`, `small-tests`, and `large-tests` jobs. What would be the best job dependency tree?

## 4. Adding artifacts
To enhance your test jobs, you can modify them to create JUnit logs and store those logs as artifacts. In order to generate JUnit logs using pytest, you can add the `--junitxml` option to the pytest command (for both test types):
``` bash
python -m pytest -v --junitxml=small_tests_results.xml tests/small
```
To upload artifacts, please make use of the official action provided at https://github.com/actions/upload-artifact

GitHub documentation: https://docs.github.com/en/actions/using-workflows/storing-workflow-data-as-artifacts

Notice that the `large-tests` are currently failing, and you need to add some logic to handle this situation. By default, when a step fails in a job, the execution of the job is halted.

GitHub documentation: https://docs.github.com/en/actions/learn-github-actions/expressions#about-expressions

## 5. Matrix strategy
In our workflow, we are currently utilizing the `actions/setup-python` action to set up Python 3.9 for the test jobs.
However, we would like to ensure that our library functions seamlessly with Python versions 3.10 and 3.11 as well.
To accomplish this, we should modify the workflow to execute the tests with these additional versions.

GitHub documentation: https://docs.github.com/en/actions/using-jobs/using-a-matrix-for-your-jobs

Please keep in mind that we require JUnit logs from every execution with Python versions 3.9, 3.10, and 3.11. To achieve this,
we may need to add some more parameterization to our workflow.

Additionally, combine small and large tests into a single job definition using parametrization. Furthermore, we want to have a unified job definition
where the small tests are executed with all Python versions, while the large tests are exclusively run with Python versions 3.9 and 3.10.

## 6. Semantic Release
Please take a moment to familiarize yourself with the `.releaserc` file, as it plays a crucial role in the release process. To incorporate the release process into your pipeline, you can use the action available at https://github.com/splunk/semantic-release-action.

Using this action, you can leverage conventional commits syntax to create a few releases. This syntax follows a standardized format for commit messages, allowing for automated release versioning based on the commit history.

By configuring the `.releaserc` file and incorporating the semantic-release-action into your pipeline, you can automate the release process and ensure consistent versioning based on the conventional commits.

Please refer to the documentation of the semantic-release-action for detailed instructions on how to set it up and utilize conventional commits syntax for creating releases.

Conventional Commits: https://www.conventionalcommits.org/en/v1.0.0/

> **_BONUS TASK:_**
>Please attempt to utilize the haya14busa/action-update-semver action to update shorter tags like v1 and v1.1. You can find the action at https://github.com/haya14busa/action-update-semver
> The desired outcome of using this action is that, after releasing version v1.2.0, both the v1 and v1.2 tags should refer to the same commit as v1.2.0.

## 7. PyPI release

This task is optional. We will demonstrate how to make a PyPI release. If you have a PyPI account, you have the option to perform
the release using your account. However, it is not a requirement for the subsequent tasks.

You will face a problem with uploading a package with the same name as ours, it is generally not possible to upload a package with the same name as an existing package on PyPI.
Each package on PyPI must have a unique name to avoid conflicts and ensure proper identification. If a package with the same name already exists, you will need to choose a different name for your package to avoid naming conflicts.

## 8. Reusable workflow

GitHub provides the capability to create workflows that can be reused across multiple repositories. We have prepared a workflow that lists pull requests (PRs) and issues for a repository, which you can find at https://github.com/kkania-splunk/gh-monitor-workflow.

To incorporate this workflow into your repository, you can follow these steps:

1. Navigate to your repository on GitHub.
2. Go to the "Actions" tab.
3. Click on the "New workflow" button.
4. Choose the option to "Set up a workflow yourself" to create a new workflow file.
5. Paste below content to your workflow file:
```yaml
name: repo-monitor

on:
  push:
    branches:
      - "**"

permissions:
  contents: read
  pull-requests: read
  issues: write

jobs:
  call-workflow:
    uses: kkania-splunk/gh-monitor-workflow/.github/workflows/monitor.yml@main
    secrets:
      GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
6. Commit and push the changes to trigger the workflow.

Once the workflow runs, you can examine the logs from the GitHub runs by navigating to the "Actions" tab in your repository. From there, you can view the workflow runs, inspect the logs, and review the output generated by the workflow.

By utilizing this reusable workflow, you can benefit from the functionality it provides for listing PRs and issues, making it easier to monitor and manage them within your repository.

GitHub documentation: https://docs.github.com/en/actions/using-workflows/reusing-workflows

Create a fork of the reusable workflow and proceed to modify the action within it. Update the workflow logic so that it fails
if there are any open issues. To make this behavior configurable, add an input parameter to the workflow. This input parameter will determine whether the
workflow should fail if there are open issues or if it should proceed regardless. By introducing this configuration option, you can adapt the behavior of the workflow to meet your specific needs.

## 9. Creating your own action
Create a composite GitHub Action that replaces the previous implementation of `small-tests` and `large-tests`
You can follow these steps to create action:

1. Set up a new GitHub repository.
2. Include an `action.yml` file in your repository.
3. Define the required input parameters in the `action.yml` file.
4. Add the necessary steps to your action, considering the logic and functionality required.
5. In the project repository where you want to use the composite action, add a uses section that references your action's implementation

GitHub documentation: https://docs.github.com/en/actions/creating-actions/creating-a-composite-action
