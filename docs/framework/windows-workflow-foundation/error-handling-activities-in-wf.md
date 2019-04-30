---
title: WF etkinliklerini hata işleme
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774029"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="a3f39-102">WF etkinliklerini hata işleme</span><span class="sxs-lookup"><span data-stu-id="a3f39-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a3f39-103">hata işleme ve kurtarma uygulamak için birkaç sistem tarafından sağlanan etkinliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3f39-103">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="a3f39-104">Daha fazla bilgi için [özel durumları](exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="a3f39-104">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="a3f39-105">Hata işleme etkinlik</span><span class="sxs-lookup"><span data-stu-id="a3f39-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="a3f39-106">İçinden oluşturulan son özel durumu yeniden oluşturur bir `TryCatch` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a3f39-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="a3f39-107">Özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3f39-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="a3f39-108">Özel durum işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="a3f39-108">Implements exception handling.</span></span>|
