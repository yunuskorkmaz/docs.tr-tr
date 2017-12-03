---
title: "WF etkinlikleri çalışma zamanı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 022f12448d697ba179fb3705f18962e6b0c44239
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="31a7b-102">WF etkinlikleri çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="31a7b-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="31a7b-103">kalıcılığı ve sonlandırma gibi iş akışı çalışma zamanı özelliklerine erişmek için birkaç sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31a7b-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="31a7b-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="31a7b-104">Activity</span></span>|<span data-ttu-id="31a7b-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31a7b-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="31a7b-106">İş akışı durumu kalıcı açıkça istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="31a7b-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="31a7b-107">Çalışan iş akışı örneği sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="31a7b-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="31a7b-108">Kalıcı gelen alt etkinlikler engeller kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="31a7b-108">A container activity that prevents child activities from persisting.</span></span>|
