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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae2b8a8bb536d914edd6c7154136867caee553b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="32b28-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="32b28-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="32b28-103">Kimliği: 139</span><span class="sxs-lookup"><span data-stu-id="32b28-103">Id: 139</span></span>  
  
 <span data-ttu-id="32b28-104">Önem derecesi: hata</span><span class="sxs-lookup"><span data-stu-id="32b28-104">Severity: Error</span></span>  
  
 <span data-ttu-id="32b28-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="32b28-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="32b28-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b28-106">Description</span></span>  
 <span data-ttu-id="32b28-107">Bu olay, bir düzenleyici kurtarma günlük girişi bozuktu ve seri durumdan çıkarılmış açılamadı gösterir.</span><span class="sxs-lookup"><span data-stu-id="32b28-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="32b28-108">Bu hatadan veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="32b28-108">Data loss may result from this error.</span></span> <span data-ttu-id="32b28-109">Olay listeleri işlem kimliği, kurtarma verileri (Base64 ile kodlanmış), özel durum, işlem adı ve işlem kimliği</span><span class="sxs-lookup"><span data-stu-id="32b28-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b28-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32b28-110">See Also</span></span>  
 [<span data-ttu-id="32b28-111">Günlüğe Olay Kaydetme</span><span class="sxs-lookup"><span data-stu-id="32b28-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="32b28-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="32b28-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
