---
title: WF etkinlikleri hata işleme
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 51431e367f0ec8874588a52cb4dbd76d714768fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512391"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="0ea6a-102">WF etkinlikleri hata işleme</span><span class="sxs-lookup"><span data-stu-id="0ea6a-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="0ea6a-103"> hata işleme ve kurtarma uygulamak için birkaç sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ea6a-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="0ea6a-104">Daha fazla bilgi için bkz: [özel durumları](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="0ea6a-104">For more information, see [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="0ea6a-105">Hata işleme etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="0ea6a-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="0ea6a-106">İçinden son durum bloğunu bir `TryCatch` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="0ea6a-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="0ea6a-107">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ea6a-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="0ea6a-108">Özel durum işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="0ea6a-108">Implements exception handling.</span></span>|
