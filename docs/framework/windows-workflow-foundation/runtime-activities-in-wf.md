---
description: "Daha fazla bilgi edinin: WF 'de çalışma zamanı etkinlikleri"
title: WF 'de çalışma zamanı etkinlikleri
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 5ff164539b9efd7b2b8a4e7cffd5239eae6145fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792641"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="039f3-103">WF 'de çalışma zamanı etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="039f3-103">Runtime Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="039f3-104">, kalıcılık ve sonlandırma gibi iş akışı çalışma zamanının özelliklerine erişmek için sistem tarafından sağlanan çeşitli etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="039f3-104">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="039f3-105">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="039f3-105">Activity</span></span>|<span data-ttu-id="039f3-106">Description</span><span class="sxs-lookup"><span data-stu-id="039f3-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="039f3-107">İş akışının durumunu kalıcı olarak sürdürmediğini açıkça ister.</span><span class="sxs-lookup"><span data-stu-id="039f3-107">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="039f3-108">Çalışan iş akışı örneğini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="039f3-108">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="039f3-109">Alt etkinliklerin kalıcı olmasını önleyen bir kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="039f3-109">A container activity that prevents child activities from persisting.</span></span>|
