# MATRIX-dashboards
An inventory of dashboard development for One Health disease surveillance. Produced within Work Package 6 of the [One Health EJP](https://onehealthejp.eu/) project [MATRIX](https://onehealthejp.eu/jip-matrix/).

## Structure
This repository is divided into two main sections: A dashboard information hub (kept in the **docs** folder), and working dashboard examples to complement the information (kept in the **code** folder).

### Information Centre
This is the starting point of the inventory. The idea is that someone who wants to develop a One Health surveillance dashboard can go to this information centre (publicly accessible as a webpage at [https://sva-se.github.io/MATRIX-dashboards](https://sva-se.github.io/MATRIX-dashboards)) and use it as a resource.

The information centre is divided into sections:

- Data and Workflows
- Dashboard Design and Technology
- Dashboard Examples
- Glossary
- Resources

The pages can be edited using the **markdown** (MD) language (see the [Markdown Guide](https://www.markdownguide.org/) for a good tutorial). Each page of the centre will be its own MD file in the **docs** directory of this repository (except for the main page which is index.md in the repository root). These files can be edited directly in the browser here at GitHub, but you can also sync the repository to your PC using git, work locally and then push the changes when ready. For a tutorial on git, see the [Git handbook](https://guides.github.com/introduction/git-handbook/).

### Dashboard Examples
Each country/institute developing a dashboard as part of MATRIX (or has/will work on a similar project that is suitable to share in the inventory) should describe their work in the "Dashboard Examples" section (docs/examples.md). An example could possibly be accompanied by a link to a working online dashboard, or by functioning code to generate the dashboard (or a dummy version as a showcase) which then should live inside its own subfolder in the **code** directory. If no dashboard or code is available to show, it should be described why such is the case (e.g. data confidentiality or restricted access).
