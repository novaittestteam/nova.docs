{%
   include-markdown ".\links.md"
   start="<!--tasklink-start-->"
   end="<!--tasklink-end-->"
   rewrite-relative-urls=false
%}

#Nova.BotConnector
##Product Notices
***
##2022R3
###2022R3-6 :briefcase: Epic
####New Features
####Bug Fixes

##2022R1
###2022R1-4 :briefcase: Epic
####New Features
- none

####Bug Fixes
- *Facebook Wall Posts*: fixed problem with registration of pooling service causing assertion errors [:clipboard: NOV-346] [NOV-346]
- *Facebook Wall Posts*: changed short term token for non-expiring one [:clipboard: NOV-346] [NOV-346]
***

##2021R4
###2021R4-5 :briefcase: Epic
####New Features
- none

####Bug Fixes
- *Facebook*: cleaned leftover logging [:clipboard: NOV-287] [NOV-287]
- *Twitter*: cleaned leftover logging [:clipboard: NOV-287] [NOV-287]

	> If error ESOCKETTIMEDOUT occurs after sending media content (for ex. with big size), it is possible to increase timeout in config via variable setTimeoutForMedia.

	> Path: server.setTimeoutForMedia.

***

###2021R4-4 :briefcase: Epic
####New Features
- *WhatsApp (Nexmo)*: migration from API v0.1 to API v1 [:clipboard: NOV-304] [NOV-304]

	- New version of API require usage of JWT authentification

	- headers: {  Authorization: Bearer <JWT> }

	> • for generation of JWT, fields **application_id** and **private_key** are needed and must be generated in Nexmo dashboard

####Bug Fixes
- *WhatsApp (Infobip)*: fixed bug when downloading file created a hollow file [:clipboard: NOV-305] [NOV-305]
***

###2021R4-2 :briefcase: Epic
####New Features
- *Vkontakte Wall Posts*: added support of VK comments on posts [:clipboard: NOV-265] [NOV-265]
	
	- comment creates new conversation with possibility of one reply from agent

	- comment doesn't create conversation if it doesn't contain mention (**@groupname**) if it is not direct reply to group's post

	- variable in payload for comments **CanReply** has value **false**

	- payload has client's avatar url

####Bug Fixes
- none
***

###2021R4-1 :briefcase: Epic
####New Features
- *Facebook Wall Posts*: pooling service [:clipboard: NOV-271] [NOV-271]
- *Facebook Wall Posts*: added support of channel [:clipboard: NOV-36] [NOV-36]

	- Posts and comments are sent to agent's workplace as a separate conversations 

	- Only direct comments to owner are sent to workplace 

	- Comments between users (no owner mention) are not sent to workplace

	- If agents aren't available at the moment, then conversation will "wait" for first available agent

- *All channels*: added channel variable *Avatar* and config variable *CanReply* [:clipboard: NOV-36] [NOV-36]

	- CanReply has defult value *true* and is used only in Wallposts channels
	
	- With CanReply *false*, agent can reply to comment\post only once

- *Twitter Wall Posts*: added support of channel [:clipboard: NOV-42] [NOV-42]

	- Posts and comments are sent to agent's workplace as a separate conversations 

	- Only direct comments to owner are sent to workplace 

	- Comments between users (no owner mention) are not sent to workplace

	- If agents aren't available at the moment, then conversation will "wait" for first available agent

- *All channels*: added **Avatar** parameter to template [:clipboard: NOV-260] [NOV-260]

	> {avatar} - link on user's picture; stored locally.

####Bug Fixes
- none
***

##2021R3
####New Features
- *Telegram*: Implemented *Typing Indicator* (agent writes a message idicator for clients to see) [:clipboard: NOV-107] [NOV-107]

	> The status is set for 5 seconds or less (when a message arrives from your bot, Telegram clients clear its typing status)

- *Facebook*: Implemented *Typing Indicator* (agent writes a message idicator for clients to see) [:clipboard: NOV-107] [NOV-107]

	> Typing indicators are automatically turned off after 20 seconds, or when the bot sends a message.

- *Viber*: Implemented *Typing Indicator* (agent writes a message idicator for clients to see) [:clipboard: NOV-107] [NOV-107]

	> Typing indicators are not supported for bots

- Optimized deployment of new component versions with daemon process manager [:clipboard: NOV-253] [NOV-253]

####Bug Fixes
- *WeChat*: changed processing of media data [:clipboard: NOV-39] [NOV-39]
- *Facebook*: fixed receiving of additional user information from new users [:clipboard: NOV-215] [NOV-215]
***

##2021R2
####New Features
- *All channels*: added sending of REF value from uri to Omilia context at the start of conversation [:clipboard: NOV-172] [NOV-172]

	- Facebook messenger:
	
	> https://m.me/<NAME>?ref=<REF>

	- Viber:
	
	> viber://pa?chatURI=<NAME>&context=<REF>

	- Telegram:

	> https://t.me/<NAME>?start=<REF>

	- Variables:

		• NAME - name of bot, page, or account in curresponding messengers
	
		• REF - any value
	
- *Facebook*: added receiving of additional user information (*firstname*, *lastname*, *username*) [:clipboard: NOV-181] [NOV-181]
- *WebChat*: added receiving of additional user infogrmation (*firstname*, *lastname*) [:clipboard: NOV-199] [NOV-199]
- *All channels*: deletion of user privacy related data from DB [:clipboard: NOV-203] [NOV-203]
- *All channels*: added outbound messaging [:clipboard: NOV-238] [NOV-238]

	> Three working algorithms:

	> • without specific reply redirect on agent or workgroup\skillgroup (simple outbound message)

	>	- sending of message to client, that has had a previous conversation, without awaiting for reply

	> • with reservation of routing on agent or workgroup\skillgroup after outbound message and reply redirect on reserverd agent or workgroup\skillgroup (outbound message with agent or workgroup\skillgroup reservation for routing)

	>	- sending of message to client, that has had a previous conversation, without awaiting for reply

	>	- reservation of reply receiver (agent or workgroup\skillgroup)

	> 	(reservation cleanup: field "Expiration Timeout" in config, value in minutes)

	> 	- routing on agent or workgroup\skillgroup after reply
	
	>	(outbound message is sent as a first incoming message from agent)

	> • with reservation of agent or workgroup\skillgroup after client's reply and specific answer redirect on agent or workgroup\skillgroup (outbound message with instant routing on agent or workgroup\skillgroup)

	> 	- sending of message to client, that has had a previous conversation, without awaiting for reply

	> 	- routing on agent or workgroup\skillgroup
	
	>	(outbound message is sent as a first incoming message from agent)

####Bug Fixes
- *Slack*: fixed **oAuthUrl** field on channel registration in connector
- *Twitter*: fixed webhook setup due to API change [:clipboard: NOV-111] [NOV-111]
***

##2021R1
####New Features
- *Viber*: added support of "**Request Contact**" button type [:clipboard: NOV-140] [NOV-140]
- *Facebook*: added support of "**Request Contact**" button type [:clipboard: NOV-141] [NOV-141]
- *WhatsApp (Nexmo)*: added support of Omilia **Quick Replies** rich media [:clipboard: NOV-154] [NOV-154]
- Implemented mechanism to delete old conversations (bson cleanup) [:clipboard: NOV-65] [NOV-65]

	> Parameters in config file:
	
	> 	• cleanOlder: X, // X - number of days; messages older than this number of days will be cleaned up

	> 	• cleanUpSessions: Y, // Y - true or false

	> (Deletes records in database: connectors.conversations)

<details><summary>Cleaning Service</summary>
<p>
```
[Unit]
Description=cURL Test request
After=network.target

[Service]
Type=oneshot
User=root
Group=root
ExecStart=/usr/bin/curl -X DELETE "http://localhost:8080/connectors/{{Connector_Id}}/clean"

[Install]
WantedBy=multi-user.target
```
</p>
</details>

<details><summary>Timer Service</summary>
<p>
```
[Unit]
Description=Test

[Timer]
OnUnitInactiveSec=120
#OnUnitInactiveSec - for this timer to work, cleaning service must be launched at least once

#OnCalendar=--* ::00
#OnCalendar - works periodically, the above example is for every minute launch

[Install]
WantedBy=timers.target
```
</p>
</details>


####Bug Fixes
- *Telegram*: any text that goes with **/start** command is inputed as a first message to Omilia [:clipboard: NOV-147] [NOV-147]
- *All channels*: Carousel type error fix
***

##2020R4
####New Features
- *Telegram*: added sending of **/start** command following text as REF parameter [:clipboard: NOV-112] [NOV-112]

	> • https://telegram.me/<BotName>?start=<**parameters**>

####Bug Fixes
- *Skype*: fixed *Text* sending both ways [:clipboard: NOV-109] [NOV-109]

	> • Media data is not supported

- *Telegram*: fixed errors caused by special symbols in text sent in Rich Media structures [:clipboard: NOV-122] [NOV-122]
***

##2020R3
####New Features
- *Viber*: added sending of *userid* in template [:clipboard: NOV-91] [NOV-91]
- Added Proxy Server support [:clipboard: NOV-94] [NOV-94]

	- 2 environmental variables: 

	• *GLOBAL_AGENT_HTTP_PROXY* and *GLOBAL_AGENT_NO_PROXY*

	> • *GLOBAL_AGENT_HTTP_PROXY* - proxy server address

	> • *GLOBAL_AGENT_NO_PROXY* - ulr of chatproxy or other url's that we don't want proxying

####Bug Fixes
- none
***

##2020R3
####New Features
- *Odnoklassniki*: added support of channel [:clipboard: NOV-73] [NOV-73]

####Bug Fixes
- *Facebook*: fixed saving of *verifyToken* in MongoDB at channel creation [:clipboard: NOV-85] [NOV-85]
- *WhatsApp (Nexmo)*: fixed saving of *accountType* in MongoDB at channel creation [:clipboard: NOV-86] [NOV-86]
***

##2020R3
####New Features
- *Vkontakte*: added support of channel [:clipboard: NOV-72] [NOV-72]

####Bug Fixes
- none
***

##2020R2
####New Features
- *WeChat*: sending of *first name* and *parential* (*ancestral*) *name* to PureEngage chatproxy [:clipboard: NOV-71] [NOV-71]

	> • WeChat doesn't sent *first name* and *parential* (*ancestral*) *name* of the client, therefore, there is need to send second request to API

####Bug Fixes
- none
***

##2020R1
####New Features
- *Line*: added support of channel [:clipboard: NOV-50] [NOV-50]

####Bug Fixes
- none
***

##2019R3
####New Features
- Integration with high-availability cluster *Mongodb* (on *mongoose* driver level) [:clipboard: NOV-21] [NOV-21]
- *Facebook*: added support of channel [:clipboard: NOV-27] [NOV-27]
- *WhatsApp (Nexmo)*: added support of channel [:clipboard: NOV-28] [NOV-28]
- *Smooch*: added integration to channel [:clipboard: NOV-32] [NOV-32]

####Bug Fixes
- none
***

##2019R2
####New Features
- *WhatsApp (Infobip)*: added support of channel [:clipboard: NOV-17] [NOV-17]

####Bug Fixes
- none
***

##2019R1
####New Features
- none

####Bug Fixes
- *Viber*: fixed sending message types of [:clipboard: NOV-14] [NOV-14]:
	* text
	* picture\photo
	* video
	* quick replies
	* carousel

***

##2018R4
####New Features
- Created RPM package for installation [:clipboard: NOV-4] [NOV-4]
	* dependencies on MongoDB and NodeJS packages
	* systemd script to auto reload on crash
	* root for modules: /opt/nova.botconnector

- *WhatsApp (Twillio)*: developed integration to channel [:clipboard: NOV-3] [NOV-3]
- *All channels*: DELETE method for deletion of messages in database  [:clipboard: NOV-6] [NOV-6]

	> Remove all conversations from the connector:

	> curl -X DELETE "http://localhost:8080/connectors/${CONNECTOR_ID}/clean"

	> Remove a single conversation from the connector:

	> curl -X DELETE "http://localhost:8080/connectors/${CONNECTOR_ID}/conversations/${CONVERSATION_ID}"

- Implemented logging [:clipboard: NOV-7] [NOV-7]

####Bug Fixes
- none
***

##2018R3
####New Features
- *WeChat*: developed integration to channel [:clipboard: NOV-1] [NOV-1]:
	* session token autoupdate mechanism
	* sending of text
	* sending of pictures
	* sending of video
	* sending of audio

- Developed a webchat integration to connector (based on RECAST AI webchat):
	* functionality check [:clipboard: NOV-8] [NOV-8]
	* backend development [:clipboard: NOV-9] [NOV-9]

	> • server connector for chat (NodeJS) with ability to load previous conversation content from MongoDB

	* frontend development [:clipboard: NOV-10] [NOV-10]

	> • deleted/changed all excess code for seamless integration with BotConnector
	
	> • configuration can now be loaded from static json file

####Bug Fixes
- *Microsoft*: changed the JSON format for conformity with actual connector version [:clipboard: NOV-5] [NOV-5]