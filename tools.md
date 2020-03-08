# Tools

Tools useful across all fields.

## VCS

[git](https://git-scm.com/) is an excellent VCS. It provides fast feature branching, etc. 

[GitHub](https://github.com/) is an excellent platform for software development. It has great features like documentation pages, CI/CD integrations, bug reporting, security checks, etc.

## Gradle

[Gradle](https://gradle.org/) is a build management system for languages such as Swift, Scala, JavaScript, etc. It correctly generates dependency trees so that you don't have to worry about having the incorrect build tool version, transient dependency versions, global script problems, etc. Unlike copmeting build tools like [Bazel](https://bazel.build/) and [Buck](https://buck.build/), Gralde has a plugin system which allows you to reuse tools (e.g., GitHub releases) in any language.

## GitLab CI/CD

GitHub Actions doesn't support features such as static pages properly. [GitLab CI](https://docs.gitlab.com/ee/ci/) integrates with GitHub repositories in just a few clicks. Even making an account is just a click or two away since they have social sign in options with services such as GitHub and Google. What's more is that they use Docker images, which allow you to easily use any version of any language, platform, etc., even without knowing what Docker is. So unlike other CI/CD services which only work for certain versions of certain technologies at certain times, GitLab CI gives you unlimited support for anything.

## TDD

Automated testing is easier to set up because you don't need to manually navigate to a certain call site when manually running your program to verify that a particular function works as expected. Automated tests give you confidence that your code actually works, allowing you to deploy faster because you no longer need to do an unnecessary number of sanity tests. Changes in one part of the codebase can easily cause another part to break because of previously unthought of edge cases, or unseen coupling. Writing automated tests ensure that your code is easily testable, and hence is modular and maintainable. Using automated tests, you'll no longer forget which edge cases to test, and it'll take a negligible amount of time to test your entire app while you're building it because all you have to do now is run a command instead of manually repeating the same tasks over and over again. Writing tests is extremely simple. With tools such as hamcrest matchers, all you have to do is write something like `add(3, 4) shouldBe 7`, or `getData() shouldContainAll listOf(1, 2, 3)`.

Test driven development (TDD) allows you to code quicker and easier. Similar to how writing the documentation comment on a function before beginning to implement it helps you to get a much clearer idea of how to write it, TDD helps you better understand what you're going to code. It prevents you from forgetting to write tests for that piece of code.