## Objective: Create a Jenkins Job that will monitor a repository if a code has been committed in the last 5 minutes. Ensure that we maintain only the last 10 executions. By default, this job should count the number of words in the README.md file. If a person manually invokes the Job it should ask for a file name and the file name being asked job should show the number of words in that file

### Steps followed:
1. Create a freestyle job
2. Check the `Discard old builds` under the general section and set the `max # builds to keep` 10. This will only keep the last 10 executions.
3. Add the github url in the github project section.
4. Check `This project is parameterized`. Say the name of the parameter is `fileName` and add a default value as `README.md` because we want to operate on this one by default as mentioned in the objective.
5. Add the repo url in the source code management section.
6. Set the build trigger as `Poll SCM` as we want to execute this every 5 minutes only if code has been committed. Set the schedule as `*/5 * * * *`
7. In the build steps, select execute shell and run `wc -w ${filename}`. This returns the word count for the `fileName`. Note that this is the same name that we gave to our parameter which we accessed over here.
8. Hit save and you're good to go.

The logs for the job triggered by the poll are present in log.md
