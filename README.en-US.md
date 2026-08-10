

# auto-green

[![Build Status](https://github.com/justjavac/auto-green/workflows/ci/badge.svg?branch=master)](https://github.com/justjavac/auto-green/actions)

Automatically keep your GitHub contribution graph green.

> a commit a day keeps your girlfriend away.

## How it works

Uses GitHub Actions' scheduled task feature to automatically run `git commit` at regular intervals with the commit message "a commit a day keeps your girlfriend away". Inspired by an anonymous user's answer to the Zhihu question [What is it like to keep your GitHub contribution graph fully green for 365 days?](https://www.zhihu.com/question/34043434/answer/57826281):

> I kept it fully green for over 200 days, but neglected my girlfriend, and it has been green ever since.

## Usage

- Click the **Fork** button in the top right corner to fork this GitHub repository
- In your forked project, go to the **Actions** tab at the top, and click the green button “**I understand my workflows, go ahead and enable them**” to enable the auto-commit functionality
- Update [lines 19 and 20 of ci.yml](https://github.com/justjavac/auto-green/blob/master/.github/workflows/ci.yml#L19) with your own GitHub username and nickname
- (Optional) You can adjust the frequency by modifying [line 8 of ci.yml](https://github.com/justjavac/auto-green/blob/master/.github/workflows/ci.yml#L8)

The cron syntax consists of 5 fields separated by spaces, where each field represents a time unit.

```plain
┌───────────── 分钟 (0 - 59)
│ ┌───────────── 小时 (0 - 23)
│ │ ┌───────────── 日 (1 - 31)
│ │ │ ┌───────────── 月 (1 - 12 或 JAN-DEC)
│ │ │ │ ┌───────────── 星期 (0 - 6 或 SUN-SAT)
│ │ │ │ │
│ │ │ │ │
│ │ │ │ │
* * * * *
```

Meaning of each time field:

| Symbol | Description     | Example                                       |
| ------ | --------------- | --------------------------------------------- |
| `*`    | Any value       | `* * * * *` Every minute of every hour        |
| `,`    | Value separator | `1,3,4,7 * * * *` Minutes 1, 3, 4, and 7 of every hour |
| `-`    | Range           | `1-6 * * * *` Minutes 1 to 6 of every hour    |
| `/`    | Step            | `*/15 * * * *` Every 15 minutes               |

**Note:** Due to GitHub Actions limitations, if set to `* * * * *`, the actual execution frequency will be every 5 minutes.

## License

[auto-green](https://github.com/justjavac/auto-green) is released under the MIT License. See the bundled [LICENSE](./LICENSE) file for details.
