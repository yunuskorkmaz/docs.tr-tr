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
ms.openlocfilehash: 4d57f0e7528c8df6ebf98aa712fe3efd728b421d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="1c394-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="1c394-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="1c394-103">Kimliği: 139</span><span class="sxs-lookup"><span data-stu-id="1c394-103">Id: 139</span></span>  
  
 <span data-ttu-id="1c394-104">Önem derecesi: hata</span><span class="sxs-lookup"><span data-stu-id="1c394-104">Severity: Error</span></span>  
  
 <span data-ttu-id="1c394-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="1c394-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="1c394-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c394-106">Description</span></span>  
 <span data-ttu-id="1c394-107">Bu olay, bir düzenleyici kurtarma günlük girişi bozuktu ve seri durumdan çıkarılmış açılamadı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c394-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="1c394-108">Bu hatadan veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c394-108">Data loss may result from this error.</span></span> <span data-ttu-id="1c394-109">Olay listeleri işlem kimliği, kurtarma verileri (Base64 ile kodlanmış), özel durum, işlem adı ve işlem kimliği</span><span class="sxs-lookup"><span data-stu-id="1c394-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c394-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c394-110">See Also</span></span>  
 [<span data-ttu-id="1c394-111">Olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="1c394-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="1c394-112">Etkinlik genel başvurusu</span><span class="sxs-lookup"><span data-stu-id="1c394-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
