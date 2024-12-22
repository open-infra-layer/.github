# About:

The Open Infra Layer (OIL) project is a project and software suite intended to be a competitor with OpenStack with a few different goals in mind:

## Goals of Open Infra Layer:

1. Thin Cloud Layer
  - Instead of introducing new software, OIL is intended to be a thin interface layer on top of common existing IT infrastructure tools
    - The layer consists of 4 components:
      - Core layer:
        - A core API layer for interop with other software
      - Public layers:
        - A declarative API layer to support Infrastructure-as-Code standards
        - A command line API layer to support shell-based administration
        - A web UI layer to support remote administration
    - No layer, except the core layer, may offer more features than the other 3.
      - The core layer may offer experimental or new features for testing
      - This way you get control of every control feature regardless of preffered interaction method
  - We find that re-inventing the wheel is unnecessary and comes with certain downsides:
    - Infrequent software patches. Due to OpenStack's complexity, software updates are infrequent targeted at only occurring twice a year.
    - OS incompatibilities. Due to OpenStack's wide responisibility range, it is hard to have their features tested on every platform and have their components coordinated.
      - OpenStack only targets specific versions of specific platforms and doesn't always target them consistently across their components
      - Additionally, OpenStack's narrow window of supported platforms limits your ability to run system patches
2. Multi-Domain & Mult-Tenant Centric
  - To offer a fully competent cloud, the cloud must be containerizable up to and including containerization of the administration layer
3. Journaled and Atomic High + Migratable Availability
  - Synchronizing settings must be done atomically
  - Syncs must be treated like transactions
  - An effort must be made to make migration-ware for infrastructure tools of the same type
4. Up-to-date Documentation
  - Documentation is to be updated every time a feature is introduced into the public layers

## How we plan to implement these goals.

We mostly plan to adopt concepts from other tools

The main problem with a thin layer cloudware, is that the underlying cloud tools use inconsistent config methods and don't always integrate well with others. We need a simple way to interact with the config APIs of those tools.
To do this we plan to adopt nginx-ui's method of interacting with underlying cloud software. They offer a thin layer, but also offer a UI to interact directly with nginx's config files directly from the browser.
The UI we plan to adopt will be more robust than nginx-ui's and more comparable to vscode.dev

Another problem is atomic high availability. One issue with syncing settings and resources is that these syncs often need to be atomic (i.e. all settings applied at once). To do this we plan to adopt atomic settings changes from OpenWRT's UCI/LUCI (commit system).
We also plan to adopt journaled.

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
