---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
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
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::ReadAt method"
  - "ReadAt method"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

The latest version of this topic can be found at [IDebugMemoryBytes2::ReadAt](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorybytes2-readat).  
  
Reads a sequence of bytes, starting at a given location.  
  
## Syntax  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### Parameters  
 `pStartContext`  
 [in] The [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) object that specifies where to start reading bytes.  
  
 `dwCount`  
 [in] The number of bytes to read. Also specifies the length of the `rgbMemory` array.  
  
 `rgbMemory`  
 [in, out] Array filled in with the bytes actually read.  
  
 `pdwRead`  
 [out] Returns the number of contiguous bytes actually read.  
  
 `pdwUnreadable`  
 [in, out] Returns the number of unreadable bytes. May be a null value if the client is uninterested in the number of unreadable bytes.  
  
## Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## Remarks  
 If 100 bytes are requested and the first 50 are readable, the next 20 are unreadable, and the remaining 30 are readable, this method returns:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 In this case, because `*pdwRead + *pdwUnreadable < dwCount`, the caller must make an additional call to read the remaining 30 bytes of the original 100 requested and the [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) object passed in the `pStartContext` parameter must be advanced by 70.  
  
## See Also  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

