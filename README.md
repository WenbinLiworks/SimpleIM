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
### Macro Variables
```
#define _GNU_SOURCE
#define PEE(ERR_MSG) \
perror(ERR_MSG); \
exit(EXIT_FAILURE)
#define MSG_H
#define CONTENT_SIZE 70
#define FILE_NAME_MAX 100
#define BUF_SIZE sizeof(Message) / sizeof(char)
```
### Global Variables
```
Message message;
MYSQL mysql;
MYSQL_RES* result;
MYSQL_ROW row;
struct epoll_event ev, events[MAX_EVENTS];
int listen_sock, conn_sock, nfds, epollfd;
```
#### Interface function between modules
echo:
<br>Receive messages and deliver to next department
<br>for socket identifier
<br>return type: void
