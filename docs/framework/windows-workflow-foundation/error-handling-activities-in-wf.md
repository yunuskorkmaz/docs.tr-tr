---
description: "Daha fazla bilgi edinin: WF 'de hata Işleme etkinlikleri"
title: WF 'de etkinlikler Işlenirken hata oluştu
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: ef26c47d8d99f2d2186ef02820f9bebe691c2ff8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742460"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="ae1dc-103">WF 'de etkinlikler Işlenirken hata oluştu</span><span class="sxs-lookup"><span data-stu-id="ae1dc-103">Error Handling Activities in WF</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="ae1dc-104">, hata işleme ve kurtarmayı uygulamak için sistem tarafından sağlanan çeşitli etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae1dc-104">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="ae1dc-105">Daha fazla bilgi için bkz. [özel durumlar](exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="ae1dc-105">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="ae1dc-106">Etkinlikler işlenirken hata oluştu</span><span class="sxs-lookup"><span data-stu-id="ae1dc-106">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="ae1dc-107">Etkinliğin içinden atılan son özel durumu yeniden oluşturur `TryCatch` .</span><span class="sxs-lookup"><span data-stu-id="ae1dc-107">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="ae1dc-108">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ae1dc-108">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="ae1dc-109">Özel durum işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="ae1dc-109">Implements exception handling.</span></span>|
