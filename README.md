PubNub's Enahnced Stack'O'Bot Game with In-Game Chat, Online Presence, and More!
====================================
Welcome to PubNub's Stack'O'Bot Game Enahnced with our Unreal SDK!

This is an Unreal Engine game built using the [Stack'O'Bot](https://www.unrealengine.com/marketplace/en-US/product/stack-o-bot?sessionInvalidated=true) game, a thirdperson sandbox project built by Epic Games to showcase UE 5 features.

PubNub has enhanced this functionality by integrating real-time features utilizing our new [Unreal SDK](https://www.pubnub.com/docs/sdks/unreal), such as:

* In-Game Messaging: Send and receive messages in the lobby and main menu.
* Channels: Communicate with different players through whisper (private), group, and all (public) chat.
* Presence: Detect when users are online/offline
* Blueprint Compatible: The Unreal SDK is Blueprint compatable, and the entire chat example was built using Blueprints.

While this README is focused on the PubNub functionality added to the game, please review the [learning path](https://dev.epicgames.com/community/learning/paths/yG/stack-o-bot) from Epic Games to understand the base game itself.

Note: 
* This game is meant to serve as a simple sample of how easy it is to power real-time features using PubNub.
* The game is actively in development and more features are planned to be incorporated in the near future.

## Prerequisites
You'll need to perform the following before getting started. Make sure you follow the [Unreal SDK](https://www.pubnub.com/docs/sdks/unreal) for specific details or updated changes to installation instructions.

### Set up Project Enviornment
1. Download Unreal Engine 5.0 and higher. This project was built wiht 5.4.3.
2. Clone the content of the [Unreal SDK repository](https://github.com/pubnub/unreal-engine) into the Plugins folder. Change the sdk folder name to Pubnub.
3. Generate C++ project files (as we need to add the SDK to the build file) by rick clicking on your `.uproject` file.
4. The private module dependency has already been added for you in `Source/_{YourProject}_/_{YourProject}_.Build.cs`.
5. Compile the code.
6. Open the project in UE.
7. Click Edit > Plugins, and ensure the PubNub SDK is enabled.
8. Click Edit > Project Settings and scroll down to the PLugins section and click Pubnub SDK.
9. Add your publish and subscribes keys obtained in the next step and save.

### Get Your PubNub Keys
1. Sign in to your [PubNub Dashboard](https://admin.pubnub.com/). You are now in the Admin Portal.
2. Click on the generated app and keyset or create your own App and Keyset by giving them a name.
3. Enable Presence by clicking on the slider to turn it on. A pop-up will require that you enter in “ENABLE”. Enter “ENABLE” in all caps and then press the “Enable” button. Enable the "Generate Leave on TCP FIN or RST checkbox", which generates leave events when clients close their connection (used to track occupancy and remove non-connected clients in app). You can leave the rest of the default settings.
4. Enable Stream Controller.
7. Click on save changes.
8. Save the Pub/Sub Keys.

You are now ready to start playing the game!

## Playing the Game
To begin playing the game, start the game in the editor. 
* The number of currently logged in platers will be displayed at the top of the screen (Presence).
* You can open the chat with the `Enter` key on the keyboard. This focuses the chat and darkens the chat elements.
* Type a message and press the `Enter` key again to send the message. This display the message to you and everyone else (all = public channel)
* There are different commands you can trigger in the chat. Enter /help in the chat to pull up these various commands
* Type /whisper <userId> to establish a private message channel with another player. The text will become green and opens a private messaging channel between you and that associated player - no one else can see these messages.
* Type /join <groupName> to join a group. The text will become orange and opens a group channel between you and that group after you start to type messages.
* Type /leave <groupName> to leave the specified group.
* You can cycle between channels with the `Left CNTRL` key on the keyboard. Keep in mind you need to have at least one other channel you are associated with before cycling channels.
* Both the open chat and channel cycling key can be changed to another key or button the gamepad via the Input Mapping Context located in Content > StackOBot > Input > IMC_ThirdPerson. This will also change the text displayed on the screen for what key to press to open or cycle channels.

## Files Adjusted

The following files are of focus to review for this game and pertain to PubNub Functionality. All functionality has been built using Blueprints, so please take a look at the Graph view of each Blueprint to examine functionality. Everything is located in the Content > Chat folder. Specific functionality:
- AC_Chat_PC: Contains initial configuration and some event handling to listen for keyboard input
- WB_ChatUI: Contains the UI elements, the chat and presence count.
- WB_ChatBox: Contains the chatbox and most of the logic of the app, including PubNub setup, channel cycling, etc.
- WB_PresenceCount: Displays the occupancy count

## Links
- PubNub Unreal SDK: https://www.pubnub.com/docs/sdks/unreal
- Not used in this tutorial, but a quick way to add robust chat features to your game. PubNub Unreal Chat SDK: https://www.pubnub.com/docs/chat/unreal-chat-sdk/overview
- Admin Portal (to obtain Pub/Sub API Keys): https://admin.pubnub.com/

## License
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
