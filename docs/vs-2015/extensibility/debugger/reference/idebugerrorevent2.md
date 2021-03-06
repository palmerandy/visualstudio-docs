---
title: "IDebugErrorEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "2018-06-30"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2"
helpviewer_keywords: 
  - "IDebugErrorEvent2 interface"
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugErrorEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

The latest version of this topic can be found at [IDebugErrorEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugerrorevent2).  
  
This interface specifies an error message to be reported to the user.  
  
## Syntax  
  
```  
IDebugErrorEvent2 : IUnknown  
```  
  
## Notes for Implementers  
 The debug engine (DE) implements this interface to report errors as human-readable messages. The [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface must be implemented on the same object as this interface. The SDM  uses [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) to access the `IDebugEvent2` interface.  
  
## Notes for Callers  
 The DE creates and sends this event object to report an error. The event is sent by using the [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback function that is supplied by the SDM when it attached to the program being debugged.  
  
## Methods in Vtable order  
 This interface implements the following method:  
  
|Method|Description|  
|------------|-----------------|  
|`GetErrorMessage`|Returns an error as a human-readable string.|  
  
## Remarks  
 If the debug engine encounters an error, it can use this interface to report the message through Visual Studio to the user.  
  
## Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## See Also  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

