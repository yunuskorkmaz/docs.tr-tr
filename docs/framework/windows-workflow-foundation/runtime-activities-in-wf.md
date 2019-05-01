---
title: Çalışma zamanı WF etkinlikleri
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938105"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="fdcac-102">Çalışma zamanı WF etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="fdcac-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="fdcac-103">kalıcılığı ve sonlandırma gibi iş akışı çalışma zamanı özellikleri erişmek için çeşitli sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdcac-103">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="fdcac-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="fdcac-104">Activity</span></span>|<span data-ttu-id="fdcac-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdcac-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="fdcac-106">İş akışı durumuna kalıcı açıkça ister.</span><span class="sxs-lookup"><span data-stu-id="fdcac-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="fdcac-107">Çalışan iş akışı örneği sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="fdcac-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="fdcac-108">Çocuk etkinliklerinin kalıcı engelleyen bir kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="fdcac-108">A container activity that prevents child activities from persisting.</span></span>|
