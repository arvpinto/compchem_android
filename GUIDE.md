<p align="justify"><b>CompChemKit is a set of small apps for everyday work in computational chemistry and molecular modelling, organised in five suites and tied together by a control center. This guide gives a short tour of each part. </b></p>

<p align="justify"> The suites are a lab notebook, a literature hub, an HPC workbench, a structure studio with a QM/MM region builder, and a paper kit. They run as an Android app or in any browser, work offline apart from the online lookups (Crossref, OpenAlex, RCSB PDB, UniProt, AlphaFold DB and PubChem), and keep all data on your own device, with no account and no tracking. The screenshots use made-up example data for a fictional researcher: the papers in the library are real publications, while the people, calculations, radar results, citation profile and journal figures are invented or illustrative. </p>

<div align="center">
    <img src="screenshots/desk-control-center.png" alt="The control center on a computer">
</div>

---

<br>
<h2> <p align="center"> <b>I - Installation</b> </p></h2>

<br/>

<p align="justify"><b>Android (8.0 or newer).</b> Download the compchemkit-X.Y.Z.apk file from the <i>Releases</i> page of the repository, open it and allow the install when Android asks. The launcher gets six icons, CompChemKit (the control center) and one per suite, all sharing the same data. The app is signed by its author rather than distributed through the Play Store, so Android shows a warning; you install it at your own risk. To update, install the newer APK over the old one and your data stays. You can check the download against the .sha256 file published next to it: </p>

<pre style="color: white; background-color: black;">
# Linux
sha256sum compchemkit-1.0.0.apk

# macOS
shasum -a 256 compchemkit-1.0.0.apk

# Windows (PowerShell)
Get-FileHash compchemkit-1.0.0.apk -Algorithm SHA256
</pre>

<br/>

<p align="justify"><b>Computer.</b> Put the files in a folder and start the small server that comes with them (Python 3.8 or newer, no extra packages), then open http://127.0.0.1:8765/control-center.html in the browser. Keep using the same address and port, because the browser keeps the data of each address separately. The pages also work from a static host such as GitHub Pages, but without automatic backups. </p>

<pre style="color: white; background-color: black;">
# Serve the suites on http://127.0.0.1:8765/
python serve_apps.py

# Choose the port and keep 60 daily backups per app.
python serve_apps.py --port 8765 --keep 60

# All options.
python serve_apps.py --help
</pre>

<br/>

<p align="justify"> In every suite the apps sit in a bar at the bottom of the screen (a rail on the left on wide screens), next to a <b>Backup</b> button. Most apps have a ⋮ menu with exports and <i>Export backup</i> / <i>Import backup</i>, and a + button to add something new. </p>

<br>
<h2> <p align="center"> <b>II - Control center</b> </p></h2>

<br/>

<p align="justify"> The place to start the day. <b>Today</b> shows what needs attention (passed deadlines, overdue action items, failed jobs, allocations running out early), an agenda for the next 14 days, running and queued calculations, and new papers and structures. <b>Projects</b> gathers everything linked to one project across all apps, <b>Search</b> looks through every app at once, <b>Apps</b> opens any suite at the right app, and <b>Backup</b> backs everything up or restores it. </p>

<p align="justify"> The + button adds a log entry, idea, deadline, calculation, command or paper without opening the suite. Papers are looked up in Crossref by DOI or title words, and you pick the right one from the list of matches. Settings (the palette icon) holds the colour scheme, your name for <i>My actions</i>, and your OpenAlex key. </p>

<br/>

<div align="center">
    <img src="screenshots/cc-today.png" width="260" alt="Today view">
    <img src="screenshots/cc-projects.png" width="260" alt="Projects view">
    <img src="screenshots/cc-capture-paper.png" width="260" alt="Adding a paper from Crossref">
</div>

<br>
<h2> <p align="center"> <b>III - Lab notebook</b> </p></h2>

<br/>

<p align="justify"><b>Research log:</b> dated entries (notes, results, problems, fixes, decisions) sorted by project, with #tags, pins and filters, plus meeting notes with people, decisions and action items. The Actions tab collects the open actions from every meeting, grouped by due date, and a follow-up meeting brings along whatever is still open. </p>

<p align="justify"><b>Ideas:</b> a board with four stages (sparks, exploring, doing, done), categories, tags and favourites. </p>

<p align="justify"><b>Script plans:</b> plan a Python or Bash script (inputs and outputs, command-line options, functions, steps and checks) and get a skeleton with a complete argument parser to start from. </p>

<p align="justify"><b>Deadlines:</b> grant calls, abstracts, reports and teaching, with countdowns, yearly repeats and export to a calendar file. </p>

<br/>

<div align="center">
    <img src="screenshots/ln-meetings.png" width="260" alt="Meeting notes with action items">
    <img src="screenshots/ln-ideas.png" width="260" alt="Ideas board">
    <img src="screenshots/ln-plans-code.png" width="260" alt="Script skeleton generated from a plan">
</div>

<br>
<h2> <p align="center"> <b>IV - Literature hub</b> </p></h2>

<br/>

<p align="justify"><b>Papers:</b> your library, with collections and stars. Add papers by DOI or by searching Crossref, copy DOIs and citations, and export BibTeX, RIS or CSV. </p>

<p align="justify"><b>Radar:</b> follows topics such as <code>PETase OR cutinase</code> in OpenAlex and marks new papers until you have seen them, with filters for dates, paper types, open access and citations. One tap saves a paper to the library. </p>

<p align="justify"><b>Citations:</b> your OpenAlex author profile, with citations, h-index, i10-index, yearly charts and the citations each work gained since the last check. </p>

<br/>

<div align="center">
    <img src="screenshots/lh-papers-search.png" width="260" alt="Searching Crossref for a paper">
    <img src="screenshots/lh-radar.png" width="260" alt="New papers in the radar">
    <img src="screenshots/lh-citations.png" width="260" alt="Citation dashboard">
</div>

<br>
<h2> <p align="center"> <b>V - HPC workbench</b> </p></h2>

<br/>

<p align="justify"><b>Tracker:</b> every calculation with its cluster, resources, walltime and progress. It estimates progress and finishing time from the rate, warns when a walltime runs out and counts core-hours. Allocations get a projection of how fast you are using them. </p>

<p align="justify"><b>Job scripts:</b> SLURM or PBS scripts for Gaussian, ORCA, CP2K, GROMACS, AMBER or any command, with presets for your clusters and warnings about common mistakes. </p>

<p align="justify"><b>Benchmarks:</b> ns/day for each setup, the cost per ns, the fastest and cheapest options, and the wall time and cost of the run you are planning. </p>

<p align="justify"><b>Commands:</b> the commands you keep looking up, with blanks such as <code>{tpr}</code> that you fill in before copying; the last values are remembered. </p>

<br/>

<div align="center">
    <img src="screenshots/hpc-tracker.png" width="260" alt="Calculation tracker">
    <img src="screenshots/hpc-scripts.png" width="260" alt="Job script generator">
    <img src="screenshots/hpc-bench.png" width="260" alt="Benchmarks">
</div>

<br>
<h2> <p align="center"> <b>VI - Structure studio</b> </p></h2>

<br/>

<p align="justify"><b>Viewer:</b> a 3D viewer (3Dmol.js) for PDB, mmCIF, GRO, XYZ, SDF, MOL2 and PQR files. It opens PDB entries, AlphaFold models and PubChem compounds by ID, or searches all three by keyword. It has the usual styles and colourings, surfaces, ligand pockets, residue selections, distances and angles, trajectory frames and PNG snapshots. </p>

<p align="justify"><b>QM/MM:</b> pick the QM region on a protonated structure by tapping or typing residues, choose where each residue is cut, and follow a running count of QM atoms, link atoms, charge, electrons and multiplicity, with every boundary checked. It writes Gaussian ONIOM input, a CP2K QM/MM section, Amber, VMD and GROMACS selections, and an XYZ file of the QM region. </p>

<p align="justify"><b>Watcher:</b> saved searches (words, EC numbers, UniProt accessions or a sequence) that flag new structures in the PDB and new sequences in UniProt, ready to open in the viewer. </p>

<br/>

<div align="center">
    <img src="screenshots/ss-viewer-pocket.png" width="260" alt="Ligand pocket in the viewer">
    <img src="screenshots/ss-qmmm.png" width="260" alt="QM/MM region builder">
    <img src="screenshots/ss-watcher.png" width="260" alt="Structure watcher">
</div>

<p align="center"><i>The viewer shows HIV-1 protease with its inhibitor (PDB 1HVR); the QM/MM example is the zinc site of a zinc finger (PDB 5A7U, with hydrogens added).</i></p>

<br>
<h2> <p align="center"> <b>VII - Paper kit</b> </p></h2>

<br/>

<p align="justify"><b>Plot guide:</b> 31 chart types, each with a tested Python script that draws it from example data and saves a 600 dpi PNG. </p>

<p align="justify"><b>Schemes:</b> an editor for reaction mechanisms with bonds, lone pairs, charges, curved arrows, reaction arrows and transition-state brackets, exported as SVG or 600 dpi PNG. </p>

<p align="justify"><b>Journals:</b> 37 journals to filter by scope, citation impact (OpenAlex 2-year mean citedness, close to but not the same as the Impact Factor), open access cost and speed. You can edit the values and add your own journals. </p>

<br/>

<div align="center">
    <img src="screenshots/pk-plots-code.png" width="260" alt="Plot guide script">
    <img src="screenshots/pk-schemes.png" width="260" alt="Mechanism scheme editor">
    <img src="screenshots/pk-journals.png" width="260" alt="Journal selector">
</div>

<br>
<h2> <p align="center"> <b>VIII - Backups, colours and privacy</b> </p></h2>

<br/>

<p align="justify"> Your data lives only on your device, so keep copies. The Android app backs up each app automatically to dated files and copies them to Download/CompChemKit/backups/, where they survive an uninstall; on a computer, serve_apps.py writes the same files once you switch automatic backups on. The <b>Backup</b> button in each suite shows the latest file for each app and restores any earlier one, and <b>Download everything as one file</b>, in the control center's Backup view, saves all apps in a single file that restores on any device. Use it to move to a new phone or computer, and regularly when you use a hosted copy. In a browser the data belongs to that browser and address, and browsers can clear it; Safari does so after about a week without a visit unless the suites are installed to the home screen. </p>

<p align="justify"> Settings offers dark, light or match device, in five palettes (Orchid, Ocean, Forest, Ember and Graphite), and the choice applies at once to every suite and app. </p>

<br/>

<div align="center">
    <img src="screenshots/cc-settings.png" width="260" alt="Colour scheme settings">
    <img src="screenshots/theme-light-today.png" width="260" alt="Light Ocean scheme">
</div>

<br/>

<p align="justify"> Nothing leaves your device unless you use a lookup, and then the service receives only what the request needs. Papers come from Crossref; the radar, citations and journal figures from OpenAlex; structures from RCSB PDB, UniProt, AlphaFold DB and PubChem. OpenAlex needs a free API key: sign in at <a href="https://openalex.org/settings/api" target="_blank">openalex.org/settings/api</a>, copy the key and paste it in the control center's Settings. It stays on your device and is never written into backup files. </p>

<br/>

For installation details, building the Android app and the scientific notes on the QM/MM builder and job scripts, see the [README](../README.md).
