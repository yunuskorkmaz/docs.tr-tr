---
title: WF etkinlikleri çalışma zamanı
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513041"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="279c8-102">WF etkinlikleri çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="279c8-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="279c8-103"> kalıcılığı ve sonlandırma gibi iş akışı çalışma zamanı özelliklerine erişmek için birkaç sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="279c8-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="279c8-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="279c8-104">Activity</span></span>|<span data-ttu-id="279c8-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="279c8-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="279c8-106">İş akışı durumu kalıcı açıkça istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="279c8-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="279c8-107">Çalışan iş akışı örneği sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="279c8-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="279c8-108">Kalıcı gelen alt etkinlikler engeller kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="279c8-108">A container activity that prevents child activities from persisting.</span></span>|
