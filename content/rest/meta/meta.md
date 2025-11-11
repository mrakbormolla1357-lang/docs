// Octokit.js
// https://github.com/octokit/core.js#readme
const octokit = new Octokit()

await octokit.request('GET /versions', {
  headers: {
    'X-GitHub-Api-Version': '2022-11-28'
  }
})"Responsive is better than fast
