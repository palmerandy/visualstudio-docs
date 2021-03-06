---
title: "StopTrackingAndCleanup | Microsoft Docs"
ms.custom: ""
ms.date: "2018-06-30"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
api_name: 
  - "StopTrackingAndCleanup"
api_location: 
  - "filetracker.dll"
api_type: 
  - "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: "ghogen"
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

The latest version of this topic can be found at [StopTrackingAndCleanup](https://docs.microsoft.com/visualstudio/msbuild/stoptrackingandcleanup).  
  
  
Stops all tracking and frees any memory used by the tracking session.  
  
## Syntax  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## Return Value  
 Returns an [HRESULT](<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) with the [SUCCEEDED](<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) bit set if tracking was stopped.  
  
## Requirements  
 **Header:** FileTracker.h  
  
## See Also  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)



