---
title: "API Reference for UML Modeling Extensibility | Microsoft Docs"
ms.custom: ""
ms.date: "2018-06-30"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UML - extending"
  - "UML API"
  - "UML model, API"
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: "alexhomer1"
ms.author: gewarren
manager: "douge"
---
# API Reference for UML Modeling Extensibility
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

The latest version of this topic can be found at [API Reference for UML Modeling Extensibility](https://docs.microsoft.com/visualstudio/modeling/api-reference-for-uml-modeling-extensibility).  
  
You can write program code to read and modify the models that you create with Visual Studio. The API reference provides information about the specific classes to help you with this. For more task-oriented information, see the topics under [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md). To see which versions of Visual Studio support UML models, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## Assemblies  
  
|Assembly|What this allows you to do|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|-   Read and change model elements such as IUseCase, IAssociation, and so on.<br />-   Navigate relationships between elements.<br /><br /> The namespaces and types correspond to those that are defined in the UML Specification.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-   Create new instances of model elements<br />-   Access and modify shapes and diagrams.|  
  
## See Also  
 [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md)   
 [API Reference for Modeling SDK for Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)



