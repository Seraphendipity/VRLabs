---
title: VRLabs | Project Proposal
author: Elijah T. Rose, elirose
date: 2020-11-04
header-left: \includegraphics[height=0.6cm]{Resources/Logos/UABLogo-Horiz.png}
header-right: 
- Department of ECE
- EE485 | Intro to Embedded Systems
footer-left: \includegraphics[height=0.3cm]{Resources/Logos/Logo-Seraph.png} 
bibliography: [references.bib]
---

# VRLabs | Project Proposal
A Virtual Reality [@Wiki-VR] attempt to integrate hardware learning with the cost-effectiveness and ease of logistics of software modelling.

For the purposes of this proposal and most likely the initial project design, the idea of a Circuit-SPICE integration will be used.

## Existing Solutions
Experimental learning has and continues to be an extremely valuable resource to students across grade levels. It is one thing to look at theory or work word problems yet another entirely to see it in practice and work with it by hand. Many people are visual learners and all but require such demonstration to grasp the concepts at hand, and for those who study better by the book it is still useful to handle the real-world analogues in order to make connections between their learning relationships. 

However, real-world demonstrations also pose many problems:

* **Cost**: No matter how trivial, near any demo will require some amount of resource costs. Some labs are cheap, some are disposable; however, many may require expensive machinery or not easily-acquirable components. With education systems near always being strained for resources, justifying a $500 or $5000 lesson versus a simple board or paperwork instruction can be daunting, especially in lower-income school systems. Such costs can put poorer students at further disadvantages compared to more well-off students and school systems.
* **Safety**: many experiments are relatively harmless assuming basic precautions. But in some chemical, physics, and electrical experiments there is a risk to both the components (refer back to cost) as well as the individuals involved unless there is a strict adherence to protocol. To some extent, this risk can be seen as beneficial due to being able to encounter it in a laboratory setting with plentiful safety devices and people nearby. However, for labs that can prove dangerous such that instant irreversible damage can take place to unwary students, there is a lack of a safety net that assumes a lot of risk to participants, leading to either the rejection of the experiment outright as a learning tool or a delay in when students are able to learn it due to age restrictions.
* **Logistics**: due to the need at time for specialized components or adherence to safety protocols, experiments typically need to be carried out in special (and often expensive) labs. This reduces their effectiveness somewhat or at least their accessibility. The Covid-19 situation has exacerbated this issue, requiring the distribution of lab tools and a reworking of the labs to accommodate household environments, limiting the tools to be taught and experiments that can be carried out. Additionally, those who cannot acquire the kits -- such as those overseas -- rely entirely on the experimental data acquired by others and thus miss any hands-on experience.

And thus the tools of simulation come in, allowing the setting up of virtual representation of real world components. Not only are these vital tools for education [@RemoteLabs], but additionally important to learn in themselves due to their use as tools in the workplace. These simulations, however, do have a disconnect between their visual display and the real-world models they represent and as such may not be the end-all be-all of teaching experimentally [^1]. 

## Potential Solution
To help address the tradeoff between 2D simulation and 3D real-world experiences, VRLabs seeks to create an API integration between simulator engines such as SPICE and 3D model interactions.

![A rough sketch of the user viewpoint. They'll be able to view both the 3D model of the circuit as well as the 2D representation, they being dynamically linked in real-time. Note 3D model not accurate to 2D model as I couldn't model the other components quickly; hand model provided by awesomenessman [@HandModel].][ViewSketch]

### Hardware
Most of this is not part of our design -- the solution is near entirely software with integration of hardware components.

The hardware is rather simplistic: a Virtual-Reality headset, internet connection, and potentially just that. There are numerous models on the market, however perhaps the most applicable currently is the recently-released Oculus Rift 2 [@OculusRift]. With a relatively very cheap price point ($300), ability to work with and without external computer connections [^2], and well-developed marketplace it provides a reasonably competitive alternative to providing laboratory equipment on a large-scale distribution.

![Oculus Rift 2 [@OculusRift]][Rift2]

Additional hardware will ideally be allowed integration, such as feedback gloves. Whether having the physical touch of the fingers significantly helps in education of the tools (as opposed to buttons or simpler grasp controls) remains to be seen. HaptX [@HaptX] believes that there could be significant potential in running simulations with such devices; other companies are exploring simpler alternatives to similar effect [@HapticFeedback] [@SensX].

![HaptX Gloves [@HaptX]][HaptX]

Digital touchscreen phones (which have now become near ubiquitous, even amongst younglings) are increasingly capable of handling multi-tasking and 3D tasks. As such, it is not out of the question to use phones as viewports for 3D worlds, either through cheap viewers [@GoogleCardboard] or simply swaying them left and right.

While not well thought-out, one idea is to also potentially keep a physical element -- dummy "toy" models of what is represented. Could be as simple as expandable boxes/3D printed toys or as complex as modifiable models with dials and such. These dummy models could be sensed by the headsets (near all of which use outside-in tracking via camera on the headset, allowing both camera and infrared detection) to give the tactile feedback to students.

### Software
The job of VRLabs is to combine several existing components alongside potentially new libraries, 3D object-interaction recognition, and 3D models to allow an easy and intuitive lab experience. Notably, even with relatively simpler software such as Zoom, many users can struggle even when it is widely adopted -- as such, in order to best serve the primary audience of students and instructors, creating a seamless integration and cohesive system is of the utmost importance. This facet is important as to address the ruling of a simple wrapper or 3D engine API alone.

![The major components of the VRLabs project: handling engine 3D integration, allowing saving and sharing of lab scenarios, and connecting classrooms. [^3]][SoftwareSketch]

While tools such as Unity and Unreal exist to allow great and relatively easy-to-use flexibility in designing 3D distributable scenes and have made great effort in offering tutorials and lessening their learning curves, they still present a rather large obstacle in practically implementing custom experiments. To address such an issue...

1. **Lab/Experiment Distribution Marketplace**: scenes, alongside relevant papers and other material, to be downloaded easily by instructors and students.
2. **Simplified Experiment Scene Creator Toolkit for Instructors**: a simplified drag-and-drop editor for creating quick, custom scenes. Potentially a text-based system. Due to the potential complexity of such a custom editor, likely an optional deliverable.

Additionally, it should be noted that another huge benefit of the software are the associated models with various engines -- assuming ownership, users can use them quickly in their own scenes. If paired with the custom editor, could be a tool not only for VRLabs, but setting up quick 3D scenarios and simulations for general-use purposes such as presentations.

1. **Upfront Integration**: potentially may require such logic such as fluid mechanics and connection recognition from the upfront program.
2. **Engine-Dependent Libraries**: SPICE has its own additional libraries of 3D model connection recognition, ASL has associated advanced physics equations imported, etc.
3. **Separate Libraries Classes**: depends on the engine/lab, have various importable libraries that integrates some advanced functionality into the 3D space. For instance, a "Fluid Mechanics" library that handles all sorts of fluids would be required by both DWSIM as well as various ASL models.

Additionally, in order to show the 2D models there would be the need of either creating our own 2D viewers or using an existing viewer software, adding potentially another block between the Engines and VRLabs.

## Need

### Target Audience
* Education
  * Students: "hands-on" learning and more experiments with concepts in action
  * Instructors: seeking novel ways to instruct and give demonstrations
  * Admins: potentially cheaper in logistics and over-time costs for lab upkeep, consumable replacement, and accident prevention.
  * Online Course Students
  * DIY Learners: for those who are learning topics outside of typical degree programs or topics without degrees.
  * SIM Learners: for those with a strong background in the physical components who are now learning the 2D simulation analogues, and vice versa.
* Professional Simulation(?)
  * I somewhat doubt that, even if potentially more intuitive and designed around workflows, a 3D simulation could outmatch the traditional 2D simulation workflow for trained professionals. That said, in such fields as art there is some value in a realized 3rd dimension -- possibly architects and engineers in that field could find some practical use for it?

### Why Now?
* Evolving Immersive Technologies
  * VR Walks
  * HaptX
* VR is Cheaper than Ever
* New Features: Link
  * No Reliance on PCs
  * Ability to Mod and Extend past First-Party Marketplace
  * Somewhat exclusive to Oculus, but other parties likely to follow suit.
* VR Software Tools
  * Kinks ironed out:  people have solved many hiccups and problems, what works and doesnt, etc. 
  * Library integrations for various 3D engines
* Internet Infrastructure: increasing over past decades, but Covid-19 helped push it further
* 3D Engines in Phones
  * In cases where VR headsets cannot be provided to everyone, cheaper phone-dependent headsets or use of phones could be provided
  * Phones now have more and more streamlined 3D processing and AR applications that allow integration with 3D viewports and the like.

---

\newpage
## References

::: {#refs}
:::

[^1]: This is somewhat an assumption. One comparative study [@SimVsIrl] found no significant difference between simulation and real-world experimental learning. However, even as a fan of simulator experiences, I'd cast my doubt on if all students can learn the same from a 2D swinging ball or circuit model as they can by plugging things in themselves -- at least in my own experience, I found doing the labs by hand allowed me to better connect the theory and real-world experience even after performing SPICE simulations. Arguably, if current simulations prove to be sufficiency, this project would be somewhat obsolete, however could still be useful as perhaps it could allow even more effective means of communication of ideas.
[^2]: This is arguably its most important feature. Beforehand, there were few options:

      1. **PC Connected VR**: relies on the PC for computation. At cheapest, looking at around ~$800 PC on top of the VR headset, thus a $1000-$2000 option. Needs additional wires and power outlet.
      2. **Standalone System**: relies entirely on itself. However, suffers in quality of display (less computational power) and less ability to modify and extend -- stuck to a single, official marketplace.

    With the addition of the ability to use it standalone as well as connect to a PC for further modification and computational power, it allows users to overcome the previous problems with both systems in a significantly cheaper fashion.
[^3]: Regarding the "Additional Processing" block, I am unsure of it currently, but it may be necessary to import custom 3D libraries for logic regarding components. This may be attached to the Translator Models as a library package, or perhaps be a separate component that can be pulled from regarding the models. As far as I can see, one of three scenarios can play out:

[ViewSketch]: Resources/Images/VRLabs-Demo.png
[SoftwareSketch]: Resources/Diagrams/VRLabs-SoftwareDiagram-V1-Color.png
[Rift2]: Resources/Images/OculusRift2.png {height=7.5cm}
[HaptX]: Resources/Images/HaptX.jpg