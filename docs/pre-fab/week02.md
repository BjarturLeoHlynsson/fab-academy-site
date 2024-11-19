# Electronics Design and Production

## Assignment

- Use KiCad to design a development board to interact and communicate with an embedded microcontroller.
- Make and test the development board you designed.

More information can be found on the [🇮🇸 Fab Isa Site](https://www.fabisa.is/N%C3%A1msefni/Pre-Fab/2-rafrasasmidi/).

### Installing KiCad

To get started, I downloaded the following tools:

- [KiCad](https://www.kicad.org/)
- [Fab Electronics Library](https://gitlab.fabcloud.org/pub/libraries/electronics/kicad)
- [Inkscape](https://inkscape.org/)

!!! Tip "Installing Fab Electronics Library in KiCad"
	On the GitLab repo, there are installation instructions:

	- Clone or download the Fab Electronics Library and rename it to fab.
	- Store it in a safe place such as ~/kicad/libraries or C:/kicad/libraries.
	- Run KiCad or open a KiCad .pro file.
	- Go to "Preferences / Manage Symbol Libraries" and add fab.kicad_sym as a symbol library.
	- Go to "Preferences / Manage Footprint Libraries" and add fab.pretty as a footprint library.

We were instructed to watch a YouTube series from Fab Lab Reykjavík, which is linked [here 🇮🇸](https://www.youtube.com/playlist?list=PLs4ifnZzVJmqaSM1lsg68vPVtJxVNhVwV).

After installing these tools, I started by creating a project folder. Then, I opened KiCad, made a project, and opened the Schematic Editor.

### The Schematic Editor

![KiCad Schematic Editor](../images/KiCad/SchEditor.png)

I began by adding the following components:

- **ATtiny 412**
- **Switch_Tactile_Omron**
- **C_1206**
- **L_1206**
- **Conn_PinHeader_1x03**

After adding the components, I connected all of them together and labeled everything. Then, I changed the paper to A5 and labeled it. Finally, I had something that looked like this:

![KiCad Schematic Editor](../images/KiCad/SchDonepng.png)

### The PCB Editor

Next, I opened the PCB Editor and synced my schematic to the editor by pressing this button:

![]()

Then, I arranged the components and started connecting them together following the labels I had made in the Schematic Editor. So I had this:

![]()

To finish, I placed a square outline to tell the computer how large the board was supposed to be. Then, I had this which I could use to make the board.

![]()

Lastly, as a secondary task, I opened the 3D viewer and assigned all the components 3D models so I could use that as a reference to model a case or something similar in FreeCad

![]()

### Exporting and Inkscape

Next, I had to export my KiCad board so I could mill it using the circuit mill. I went into export and selected F_CU and (B) and then exported it as an SVG. Then i did it again but now i only selected Edge_cuts. Now i had two svg files that looked like this:

![F_CU](/docs/images/KiCad/Project1-F_Cu.svg)

![Edge_Cuts](/docs/images/KiCad/Project1-Edge_Cuts.svg)