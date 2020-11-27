---
title: WF 'de etkinlikler Işlenirken hata oluştu
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 332e16b4c399341151761a4bce2d47198779ad64
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280318"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="11e24-102">WF 'de etkinlikler Işlenirken hata oluştu</span><span class="sxs-lookup"><span data-stu-id="11e24-102">Error Handling Activities in WF</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="11e24-103">, hata işleme ve kurtarmayı uygulamak için sistem tarafından sağlanan çeşitli etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="11e24-103">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="11e24-104">Daha fazla bilgi için bkz. [özel durumlar](exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="11e24-104">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="11e24-105">Etkinlikler işlenirken hata oluştu</span><span class="sxs-lookup"><span data-stu-id="11e24-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="11e24-106">Etkinliğin içinden atılan son özel durumu yeniden oluşturur `TryCatch` .</span><span class="sxs-lookup"><span data-stu-id="11e24-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="11e24-107">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11e24-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="11e24-108">Özel durum işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="11e24-108">Implements exception handling.</span></span>|
