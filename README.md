# SimpleIM
simple Instant Messaging tool implementation 

### Struct definition is listed as below
```
typedef struct _Message {
/*Fields based on chatting type*/
char content[CONTENT_SIZE]; 

 /*define message Type*/
 int8_t msgType;
 
 /*define Operation Type*/
 int8_t msgRet;
 
char sendName[20]; /* sender Name*/
char recvName[20]; /*Receiver Name*/

/*Time of delivering message*/
char msgTime[20]; 

/*define File name*/
char fileName[FILE_NAME_MAX];
} Message;

enum MessageType {

 /*Requiring register*/
 REGISTER = 1,
 
 /*Requiring logging*/
 LOGIN=0,
 
/*Requiring help*/
HELP, 

/*Requiring exit*/
EXIT,

/*online user list*/
VIEW_USER_LIST, 
 
 /*
 define list of chatting
 */

/*Requiring group chatting*/
 GROUP_CHAT,
PERSONAL_CHAT, /*Requiring private chatting*/
VIEW_RECORDS, /*Requiring chatting records*/

/*
type of message
*/
RESULT, 
UNKONWN, /*unknown type*/
REPLY, // reply from server
FL, //reminding of receiving
FL_CONTENT, //file contents
ADD_FRIEND, //add chatting friend
DELETE_FRIEND, //delete
MOVE_FRIEND //move group identification of user
};

/*define operation results */
enum StateRet {
EXCEED, //Exceed server limits
SUCCESS, //success
FAILED, //fail
DUPLICATEID, //duplicate users
INVALID, //illegal 
ID_NOT_EXIST, //
WRONGPWD, //password wrong
ALREADY_ONLINE, //already online
ID_NOT_ONLINE, //not online
ALL_NOT_ONLINE, //none online
MESSAGE_SELF //not allow to send messages to self
};

```
