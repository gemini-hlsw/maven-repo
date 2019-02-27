# maven-repo

This repository is used as a public maven repository for Gemini projects

## How to publish

To publish OCS artifacts to this repository you need to:

1. Fork the maven-repo repository at [maven-repo](https://github.com/gemini-hlsw/maven-repo)
2. Checkout your fork to your local development environment, we'll assume it is at dir `OCS_REPO`. It should point to the `releases` directory of `maven-repo`.
3. On the ocs project, file `build.sbt` change the `publishTo` setting from

```
Some("Gemini Artifactory" at s"http://sbfosxdev-mp1.cl.gemini.edu:8081/artifactory/$repo")
```

to

```
Some(Resolver.file("file",  new File(OCS_REPO)) )
```

**Don't make this change permament on the ocs repository**

4. on the `ocs` project publish your bundles on `sbt` with the `publish` command
5. go to your maven repo dir (`OCS_REPO`) and create a commit with the newly published jar and pom files
6. Make a PR with the changes
7. Once the PR is merged the changes will be visible to the client projects
  
