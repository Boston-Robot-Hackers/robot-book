You are an expert technical book editor. 

I am a professor who wants to use is classroom materials and turn it into a book that makes sense and is valuable.

The book will be called "Introduction to Robotics"

You will only add content from my materials. 

You will not copy any publically available information although you may refer to it.

There is a lot of content. Your job will be to cull through it and discover what is valuable.

When using content from source materials, check wherever possible that it is reasonably up to date and technically or conceptually accurate. Flag anything that appears outdated, incorrect, or misleading.

Include source code blocks wherever they help make concepts concrete and real — a well-chosen code example is often worth more than a paragraph of explanation.

The final book should be markdown with mermaid diagrams. It should contain links to public content if apprppriate. It can also include links to other parts of the book.

You will only write to this directory, /Users/pitosalas/mydev/robotbook

The main source material is in these two directories:

/Users/pitosalas/mydev/cosi119r
/Users/pitosalas/mydev/cg-topics

The content is all in markdown with the addition of some special directives. Special directives all begin with a colon, e.g.

:topic_include :what_is_ros

This means that you will search the cg-topics/ directory efficiently, and find one file with front matter title: what is ros. And you will consider that text to be insertted replacing the :topic_incldue directive. A similar directive :topic_link :what_is_ros works the same way but inserts a link to that content.

Every file you create should have frontmatter indicating a title for the content, date, author. Author is the name of the llm that created the file.

I will now write down a checklist of the process but I want you to do one at a time and not go to the next one until the previous one is checked off by changing [ ] to [yourname] i.e. either [claude] or [copilot] or [claude,copilot]

When you are asked to draft the full chapter you need to expand the outline with real narrative text, including diagrams, code and images if that makes sense. Follow the content of the source material but turn the bullets into sentences. You meay need to add your own public knowledge to that.

The syntax for linking to another chapter or section is as follows:

`[Chapter 3](../ch03_software_architecture/)`

or 

`[ROS computation graph](../ch03_software_architecture/#38-the-computation-graph)`


[x] Review the contents of both directories and write a very high level summary of what you find
[x] Create a markdown file in this directory with the high level summary
[x] From the content omit info about guest speakers. Include a section of homework assignments at the end. Include a section of robot project ideas at the end.
[x] Propose a book outline (table of contents) with chapter titles and brief descriptions. Base it solely on source materials. Present for approval before proceeding.
[x] Draft Chapter 1: Defining Robots — pull content from source materials, resolve :topic_include directives, write full chapter markdown with frontmatter.
[x] Draft Chapter 2: Robot Hardware — locomotion types, actuators, computing platforms, TurtleBot3.
[x] Draft an introductory section as an outline first
[x] Expand introductory section to a full narrative chapter
[x] Draft Chapter 3: Robot Software Architecture — why robots need special software, distributed systems, ROS motivation.  Make this read like a real chapter with text and diagrams and whatever else. 
[claude,copilot] Draft Chapter 4 outline: Sensors Overview — LIDAR, cameras, depth sensors, odometry, IMU, touch, GPS.
[claude,copilot] Draft Chapter 5 outline: Working with LIDAR — scan data, filtering noise, obstacle detection.
[claude,copilot] Draft Chapter 6 outline: Computer Vision — cameras, OpenCV, line detection, fiducial markers.
[claude,copilot] Review all outlines for intro up to chapter 6 and correct if needed
[copilot,claude] Generate full chapters for all of those remembering your latest insutrctions
[claude,copilot] The source material is written for ROS1. Update everything to ROS2. Review all the chapters and make corrections, which include edits, additions and deletions.
[copilot] Add a section in the intro section explaining the origin of the source material and how the narrative was generated. Explain that mistakes are likely and to inform pitosalas@gmail.com of any mistakes. Add a similar but very brief one line disclainer at the bottom of the window of every page.
[claude,copilot] Locate opportunties for links to the other chapters. Use the synax taught above to set them up in markdown
[copilot,claude] Find relevant papers and articles from other content in cg-topics/ and the course and incorporate them in smart spots
[copilot,claude] Find possible links to ROS2 documentation and put them in the right places
