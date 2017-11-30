---
title: CoordinatorRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1db6f8dc4136623f35767c122dbea46fd4706b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="75912-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="75912-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="75912-103">Kimliği: 139</span><span class="sxs-lookup"><span data-stu-id="75912-103">Id: 139</span></span>  
  
 <span data-ttu-id="75912-104">Önem derecesi: hata</span><span class="sxs-lookup"><span data-stu-id="75912-104">Severity: Error</span></span>  
  
 <span data-ttu-id="75912-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="75912-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="75912-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75912-106">Description</span></span>  
 <span data-ttu-id="75912-107">Bu olay, bir düzenleyici kurtarma günlük girişi bozuktu ve seri durumdan çıkarılmış açılamadı gösterir.</span><span class="sxs-lookup"><span data-stu-id="75912-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="75912-108">Bu hatadan veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="75912-108">Data loss may result from this error.</span></span> <span data-ttu-id="75912-109">Olay listeleri işlem kimliği, kurtarma verileri (Base64 ile kodlanmış), özel durum, işlem adı ve işlem kimliği</span><span class="sxs-lookup"><span data-stu-id="75912-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75912-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75912-110">See Also</span></span>  
 [<span data-ttu-id="75912-111">Olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="75912-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="75912-112">Etkinlik genel başvurusu</span><span class="sxs-lookup"><span data-stu-id="75912-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
