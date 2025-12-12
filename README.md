## REQUIREMENTS
Help the team set up a continuous integration pipeline using a GitHub Actions starter workflow.

1. Start by creating a new repo and adding the exercise files for this challenge.

    - [requirements.txt](./requirements.txt)
    - [test_pandas_version.py](./test_pandas_version.py)

1. Use the GitHub Actions web interface to create a starter workflow.
1. Run the workflow and observe the problems the team is referring to.
1. Fix any errors in the code so that the tests pass successfully.
1. Update the workflow to add a summary of the tests being run. 
    1. Update the workflow so that it has permissions to create checks in the Actions interface.  
    1. Update the call to `pytest` so that it creates a JUnit report named `junit.xml`.
        
            python -m pytest --verbose --junit-xml=junit.xml
            
    1. Add a new step that uses the [JUnit Report Action](https://github.com/marketplace/actions/junit-report-action) from the GitHub Marketplace:

            - name: Publish Test Report
            uses: mikepenz/action-junit-report@v3
            if: success() || failure() # always run even if the previous step fails
            with:
                report_paths: '**/junit.xml'
                detailed_summary: true
                include_passed: true


