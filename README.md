# Playground

Launch on-demand isolated environments for your Apps and APIs (Playground environments).

### How to define the components you want to start
- Edit or create an environment file in the `environments` directory (f.i: `environments/play01.json`).
- Specify the projects you want to start with the branch you want to use. For example:

```
{
  "projects": [
    { "name": "app", "branch": "main" },
    { "name": "api1", "branch": "main" },
    { "name": "api2", "branch": "main" },
    { "name": "api3", "branch": "main" }
  ]
}
```

### How to launch an environment
- Go to `Actions`
- Select workflow `Launch environment`
- Press `Run workflow` and select the environment you want to launch (f.i. `play01`)
- Click on `Run workflow`.

This will trigger the launch in parallel of the selected projects to the specified environment.

### Considerations
- Each project repo contains a Github workflow named `playground-deployment.yml` to deploy itself to a specified playground environment.
- The projects belong to the same Github Organization or Github User (in my case, `jcasanovas`). You will need to modify the [owner](https://github.com/jcasanovas/playground/blob/main/.github/workflows/launch.yml#L42) in `.github/workflows/launch.yml` file with your Github Organization or User.
- Create a Github Personal Access Token (PAT) with *repo access* and store it as a secret in Github Secrets as GH_PAT. It will be used  as [github_token](https://github.com/jcasanovas/playground/blob/main/.github/workflows/launch.yml#L43) in `.github/workflows/launch.yml`.

Feel free to clone this repository and adapt it to your needs :)
