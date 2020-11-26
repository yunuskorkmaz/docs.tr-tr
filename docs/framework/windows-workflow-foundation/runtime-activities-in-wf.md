---
title: WF 'de çalışma zamanı etkinlikleri
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: b0472c669d69d9397843a004bee1bb2c15e139c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245714"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="e963d-102">WF 'de çalışma zamanı etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="e963d-102">Runtime Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="e963d-103">, kalıcılık ve sonlandırma gibi iş akışı çalışma zamanının özelliklerine erişmek için sistem tarafından sağlanan çeşitli etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e963d-103">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="e963d-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e963d-104">Activity</span></span>|<span data-ttu-id="e963d-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e963d-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="e963d-106">İş akışının durumunu kalıcı olarak sürdürmediğini açıkça ister.</span><span class="sxs-lookup"><span data-stu-id="e963d-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="e963d-107">Çalışan iş akışı örneğini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e963d-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="e963d-108">Alt etkinliklerin kalıcı olmasını önleyen bir kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="e963d-108">A container activity that prevents child activities from persisting.</span></span>|
