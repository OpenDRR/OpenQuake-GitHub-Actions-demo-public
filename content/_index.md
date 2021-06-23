+++
title = "Running OpenQuake on GitHub-hosted runners"
outputs = ["Reveal"]
[reveal_hugo]
theme = "beige"
+++

# Running OpenQuake on GitHub-hosted Runners

Anthony Fok &lt;anthony.fok@canada.ca&gt;

Geological Survey of Canada

23 June 2021

---

## Automation with GitHub Actions (Workflows)

* Free computing resources for CI/CD
* Easier and cheaper than Amazon EC2 if the job can be completed within 6 hours on GitHub-hosted virtual environment.

---

## Yes, GEM already knows GitHub Actions :wink:

* https://github.com/gem/oq-engine/actions
* https://github.com/gem/oq-engine/tree/master/.github/workflows
    * [demos.yml](https://github.com/gem/oq-engine/blob/master/.github/workflows/demos.yml)
    * [linux_install.yml](https://github.com/gem/oq-engine/blob/master/.github/workflows/linux_install.yml)
    * ...

---

## A Tale of Two Repos

{{% fragment %}}### 1. OpenQuake-GitHub-Actions-demo (private) [→](https://github.com/OpenDRR/OpenQuake-GitHub-Actions-demo){{% /fragment %}}

{{% fragment %}}to protect raw site data at the building address level that may cause harm if made public
  
{{% /fragment %}}

{{% fragment %}}### 2. OpenQuake-GitHub-Actions-demo-public [→](https://github.com/OpenDRR/OpenQuake-GitHub-Actions-demo){{% /fragment %}} 

{{% fragment %}}for running GitHub Actions without using up 2,000 or 3,000 minutes/month quota with private repos{{% /fragment %}}

---

## Three demos

`runs-on`:

1. `ubuntu-20.04`
    https://raw.githubusercontent.com/gem/oq-engine/master/install.py
2. `macos-latest`
    https://raw.githubusercontent.com/gem/oq-engine/master/install.py
3. GitHub container using openquake/engine:nightly Docker image

(Oops, I forgot Windows... &lt;grin, duck, run...&gt;)

---

{{< highlight yaml >}}
    container:
      # openquake/engine:3.11 has ~/.local but not /usr/src/oq-engine
      # openquake/engine:nightly has /usr/src/oq-engine but not ~/.local
      image: openquake/engine:nightly
{{< /highlight >}}

`openquake/engine:nightly` is chosen for its inclusion of `sudo` for fixing permissions of the `/__w/OpenQuake-GitHub-Actions-demo-public/OpenQuake-GitHub-Actions-demo-public` (`$GITHUB_WORKSPACE`) directory.

---

# Demo

---

## Future explorations

* Tutorials
* A new "openquake" GitHub Action

---

## Thanks and Acknowledgements

* {{% fragment %}}Murray Journeay{{% /fragment %}}
* {{% fragment %}}Tiegan Hobbs{{% /fragment %}}
* {{% fragment %}}Michal Kolaj{{% /fragment %}}
* {{% fragment %}}Joost van Ulden{{% /fragment %}}
* {{% fragment %}}GitHub, Inc.{{% /fragment %}}
* {{% fragment %}}Global Earthquake Model Foundation (GEM){{% /fragment %}}

---

# Thank You!

---

# Questions?
