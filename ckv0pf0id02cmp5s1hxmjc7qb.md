## What is Semantic Versioning (aka semver)?

Have you ever came across version number 4.3.2? Yes, that’s semantic versioning.


> What exactly this is?


Well, it’s an approach/technique to differentiate between the previous version and a new version of any software.

Version number 4.3.2 can be splits into Major(4).Minor(3).Patch(2), increment in


- Major - changes in major functionality like API
- Minor - changes in functionality

And

- Patch - some bug fixes.

Here is a live example

```
v0.0.0 // New project
v0.1.0 // Add some functionality
v0.2.0 // Add other new functionality
v0.2.1 // Fix bug
v0.3.0 // Add some functionality
v0.3.1 // Fix bug
v0.3.2 // Fix bug
v0.3.3 // Fix bug
v0.3.4 // Fix bug
v0.4.0 // Add some functionality
v0.4.1 // Fix bug
v0.4.2 // Fix bug
v1.0.0 // Code is being used in production
v1.1.0 // Add some functionality
v1.2.0 // Add other new functionality
v1.2.1 // Fix bug
v2.0.0 // Implement changes that causes
``` 

Semantic Versioning is mostly useful in API development when you need to add **breaking changes to release notes.**

When you add a new version of api and you have breaking changes and you need to develop release notes you can prepare that version 4.8.9 bug fix will remove this breaking change and this will solve your problems, you can even prepare release notes based on version numberings.

I came to know about semantic versioning when I started in the  [GitHub community](https://github.com)  they have semantic versioning for much time. The approach is to manually adding the version number and update ReadMe.md every time they add/fix any feature or bug.

<hr>

So when you are developing something useful next time don’t forget to add semver to your project 😉.


%%[promo]