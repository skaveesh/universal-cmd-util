# Universal Command Line Utility

## Description
This innovation idea is to implement an application utility that is designed to improve the Command Line Interface (CLI) experience. This utility offers a range of features to help users navigate through the CLI more efficiently.

A main feature that was implemented to allow users to search and filter through commands, eliminating the need to memorize every command or search for them manually, thus improving the overall efficiency of using CLI. Other features include users to record their command history for a specific application or service, making it easier to access and repeat previously executed commands. Additionally, it provides suggestions for commands related to the current application or service, potentially utilizing artificial intelligence for better user experience.

## Problem Statement
Users may have a bad user experience with most of the Command Line Utilities due to various reasons. Some of the most common reasons are:

- Universal: Command Line Interface (CLI) tools are mostly limited to a single Operating System (OS) where users have to switch to different CLI tools if they switch OSs.
- Lack of familiarity: CLIs require a certain level of technical proficiency, which may not be familiar to all users. Users who are new to CLI may find it difficult to navigate and execute commands.
- Complexity: CLIs can be complex and have a steep learning curve, especially for more advanced tasks. Users may find it challenging to understand and remember the syntax and parameters of different commands.
- Limited feedback: CLIs typically provide minimal feedback, making it difficult for users to know whether they have executed a command correctly or not. This can lead to frustration and errors.
- Lack of discoverability: CLIs often lack discoverability, making it hard for users to discover new or alternative commands. This can lead to users getting stuck or not utilizing the full potential of the tool.
- Limited context: CLIs typically provide limited context about the environment in which they are operating, which can make it challenging for users to know what commands are available or how to use them correctly.

Overall, these factors can contribute to a bad user experience with Command Line Utilities, but the utility we have developed can help to overcome some of these challenges and improve the overall experience for users.


![Typical cmd interface](https://i.imgur.com/sfMm6JA.png "Basic look of a CLI where no suggestions are provided while user types.")


### Objective
The objective of creating a CLI with the features mentioned above is to provide a more user-friendly and efficient command line interface.

Create a universal CLI tool to use on multi platforms.
Create a more user-friendly and efficient Command Line Interface (CLI).
Overcome challenges faced by users with traditional CLIs, such as the steep learning curve, limited feedback, and lack of discoverability.
Make the CLI easier to use, more intuitive, and provide better context to users.
Enable users to execute commands more efficiently and with greater confidence.
Improve the overall user experience when using the command line, making it more accessible and productive for a wider range of users.

## Solution
To create a Command Line Interface (CLI) that is universally accessible, our solution was to use multi-platform programming languages and Graphical User Interface (GUI) libraries. However, in order to achieve this objective, we had to thoroughly explore the programming languages, GUI frameworks, and their respective functionalities. By doing so, we were able to select the most appropriate tools to create a CLI that is user-friendly, efficient, and accessible across a range of platforms. This approach enabled us to develop a CLI that can be used by a wide variety of users, regardless of their technical expertise or preferred operating system. Overall, our solution aimed to provide a universal tool that improves the user experience and increases productivity when using the command line.

## Technologies
### Technologies and Frameworks Considered
For a universal tool we have considered below technologies and frameworks:

#### Backend technologies:
- Java
- Node.js
- Rust

#### Frontend technologies:
- Qt
- Tauri
- gtk4-rs

### Technologies Used

#### Below technologies made to the final list due to the reasons mentioned against it:
- Rust - Mainly it's cross-platform, has high-performance command execution and useful for system-level programming tasks
- Tauri - It can be implemented using Vanilla JavaScript and has a huge community support

#### Below technologies disregarded due to the below reasons:
- Java - Cannot achieve fine-grained control over system resources
- Node.js - Not optimized for low-level command execution
- Qt - Too much features to select, makes it cumbersome to implement lightweight GUI
- gtk4-rs - Due to its less community support

## Design
### Architecture
Tauri is a toolkit that helps developers make applications for the major desktop platforms - using virtually any frontend framework in existence. The core is built with Rust, and the CLI leverages JavaScript making Tauri a genuinely polyglot approach to creating and maintaining apps with Rust backend.

![Architecture diagram](https://i.imgur.com/aLgzPQc.png "Architecture diagram")

### Implementation
Frontend is basically an HTML web-based application with JavaScript and CSS.

Rust backend is bound to the frontend:
```rust
fn main() {
    tauri::Builder::default()
        .invoke_handler(tauri::generate_handler![print_cmd_output, get_suggestions])
        .run(tauri::generate_context!())
        .expect("error while running tauri application");
}
```

Moreover, JS code calls the Rust backend with async tasks to pass the user input to the system OS and return the results:
```javascript
async function getSuggestions() {
    await invoke("get_suggestions", { name: commandInputEl.value })
        .then((commands) => {
    
         // omitted for brevity
    
    });
}
```

Suggestion providing floating list was getting the pre-defined set of suggestions from a data source file.


## Current Progress
![Current progress UI](https://i.imgur.com/rA7bIal.png "Current progress UI")

The basic functionality was implemented to execute commands, despite having minor hiccups. Furthermore, useful command suggestion feature is also implemented.



Execution Steps
1. Installed Rust and Tauri.
2. Built a Tauri sample app from the terminal.
3. From terminal prompt of Tauri, selected the frontend configurations.
4. Meanwhile, installed required apps from Microsoft to configure the system.
5. Implemented a basic suggestion feature from file in Rust application.
6. Implemented the command execution logic.
7. Created frontend using HTML, CSS and JavaScript.
8. Combined backend and frontend.
9. Resolved conflicts.
10. Build and run.


## Learning Outcomes & Accomplishments
- Able to explore high performance programming language like Rust.
- Was able to get a hands-on experience on multi-platform GUI library like Tauri.
- Get to know about the other multi-platform GUI libraries.
- Was able to get hands-on experience on system-level programming tasks.
- Was able to work with Rust libraries like "word-dictionary" and implemented new features on top of that.
- Was able to create interactive GUI with JavaScript.


## Demo

![Demo GIF](https://i.imgur.com/8kXR5BV.gif "Demo GIF")


## Follow-Ups
- Implement a middle layer to distinguish different operating systems and provide curated suggestions for each.
- Implement feature to track most used commands using caching mechanism.
- Maintain a history and implement a way to easily navigate through it.
- There are certain commands that need fixing in order to pass-down to the operating system.
- Enhance the user experience on the frontend.
- Implement AI suggestion feature to provide better results.