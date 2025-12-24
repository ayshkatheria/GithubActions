# GithubActions

1) Get the run ID of the latest run:
```yaml
  run_id=$(curl -s -H "Authorization: token YOUR_TOKEN" -H "Accept: application/vnd.github.v3+json" "https://api.github.com/repos/{owner}/lab2/actions/runs?per_page=1" | jq '.workflow_runs[0].id')
```
2) Get the job ID of the 'job2':

   job_id=$(curl -s -H "Authorization: token YOUR_TOKEN" -H "Accept: application/vnd.github.v3+json" "https://api.github.com/repos/{owner}/lab2/actions/runs/${run_id}/jobs" | jq '.jobs[] | select(.name == "job2") | .id')

3) Retrieve the logs:

   curl -L -H "Accept: application/vnd.github+json" -H "Authorization: Bearer YOUR_TOKEN" -H "X-GitHub-Api-Version: 2022-11-28" https://api.github.com/repos/{owner}/lab2/actions/jobs/${job_id}/logs
