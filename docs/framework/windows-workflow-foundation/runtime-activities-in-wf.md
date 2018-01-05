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
ms.workload: dotnet
ms.openlocfilehash: 3386138f01d4865b02ca821a30da68e5d73b64e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="596dc-102">WF etkinlikleri çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="596dc-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="596dc-103">kalıcılığı ve sonlandırma gibi iş akışı çalışma zamanı özelliklerine erişmek için birkaç sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="596dc-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="596dc-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="596dc-104">Activity</span></span>|<span data-ttu-id="596dc-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="596dc-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="596dc-106">İş akışı durumu kalıcı açıkça istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="596dc-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="596dc-107">Çalışan iş akışı örneği sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="596dc-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="596dc-108">Kalıcı gelen alt etkinlikler engeller kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="596dc-108">A container activity that prevents child activities from persisting.</span></span>|
