# Fisothemes' Standard Library for TwinCAT

Welcome to the Fisothemes's Standard Library for TwinCAT! This library aims to consolidate, clean up, and improve the existing TwinCAT library on my GitHub profile. The goal is to provide TwinCAT developers with a clean, simple, and consistent library that enhances their development experience and helps them build projects more efficiently.

## Features

- **Modularity**: The library is organized into different modules, each focusing on a specific area such as core functionality, error handling, strings, numerics, collections, I/O, hashing, streams, sockets, and callbacks.
- 🚧 **Reusability**: The modules will be designed to be reusable components that can be easily integrated into your TwinCAT projects.
- 🚧 **Documentation**: The repository will include comprehensive documentation that guides you on how to use the library effectively and efficiently.
- 🚧 **Examples**: A collection of examples will be provided to showcase the usage of different modules and help you get started quickly.
- 🚧 **Contributions**: Contributions from the TwinCAT community are welcome! Please refer to the [Contribution Guidelines](./Documentation/ContributionGuidelines/README.md) for more information.
---
## Getting Started

Please note that the Fisothemes's Standard Library for TwinCAT is currently under development. While it is not yet ready for full usage, I would like to provide you with a glimpse of what is planned. Here are some code snippets to give you a taste of what I have in mind:

### Base Class
 
```
FsFB_Object IMPLEMENTS FsI_Object
├── Methods
│   ├── Equals(fbObject : REFERENCE TO FsFB_Object) -> BOOL
│   └── ToString() -> FsT_Str
└── Properties
    ├── Name : FsT_Str
    ├── TypeName : FsT_Str
    ├── Path : FsT_Str
    ├── Address : FsT_Ptr
    ├── Size : FsT_Size
    └── MemoryArea : FsT_MemArea
```

### Error Interface
 
```
FsI_Error
└── Properties
    ├── Message : FsT_Str
    ├── Source : FsT_Str
    └── Code : FsT_ErrCode
```

### Immutable String Example
**Declarations:** 
```ST
VAR
    sValue : STRING;
    fbImmutStr : FsFB_ImmutableString('I love cats!');
    DogPosition : FsT_Pos;
    ipErr : FsI_Error;
    ErrorMsg : FsT_Str;
    ErrorSrc : FsT_Str;
END_VAR
```

**Implementation:**
```ST
sValue := fbImmutStr
    .Search('Dogs', 0, Position => DogPositon, e => ipErr)
    .ToString();
IF ipErr <> 0 THEN
    ErrorMsg := ipErr.Message; // OUTPUT: 'Value not found.'
    ErrorSrc := ipErr.Source; // OUTPUT: 'MAIN.fbImmutStr'
ELSE
    ...
    END_IF
```


### TCP Client Example
**Declarations:** 
```ST
VAR
    SendBuffer, RecvBuffer : FsT_Str;
    fbTcpClient : FsFB_TcpClient;
    ipErr : FsI_Error;
    ErrorCode : FsT_ErrCode;
END_VAR
```

**Implementation:**
```ST
IF bConnect THEN
    // The Connect method returns TRUE when done irrespective of error.
	bConnect := NOT fbTcpClient.Connect('127.0.0.1', 8008, e => ipErr);
    IF ipErr <> 0 THEN
        ErrorCode := ipErr.Code;
	END_IF
    END_IF
	
IF bDisconnect THEN
	bDisconnect := NOT fbTcpClient.Disconnect(e => ipErr);
	END_IF
	
IF bSend THEN
	bSend := NOT fbTcpClient.Send(SendBuffer, e => ipErr);
	END_IF

IF bReceive THEN
	bReceive := NOT fbTcpClient.Receive(RecvBuffer, nBytes => nRBytes, e => ipErr);
	END_IF
```
---
## License

This project is licensed under the [MIT License](./LICENSE).

---
## Contact

If you have any questions or suggestions regarding the Fisothemes's Standard Library for TwinCAT, you can reach out to me via [fisothemes@gmail.com](mailto:fisothemes@gmail.com).
