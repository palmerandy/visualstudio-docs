---
title: "IDiaEnumDebugStreamData::get_Count | Microsoft Docs"
ms.custom: ""
ms.date: "2018-06-30"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreamData::get_Count method"
ms.assetid: 74ff3a85-3cc2-4aa8-ad9a-7f335b795ed1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::get_Count
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

The latest version of this topic can be found at [IDiaEnumDebugStreamData::get_Count](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumdebugstreamdata-get-count).  
  
Retrieves the number records in the debug data stream.  
  
## Syntax  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### Parameters  
 pRetVal  
 [out, retval] Returns the number of records.  
  
## Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## See Also  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)



