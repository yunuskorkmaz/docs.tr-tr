---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 0dc74b784d8a9ed3ab27bb4b8d3de34143f6ce07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639490"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="4fa8e-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="4fa8e-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="4fa8e-103">Kimliği: 139</span><span class="sxs-lookup"><span data-stu-id="4fa8e-103">Id: 139</span></span>  
  
 <span data-ttu-id="4fa8e-104">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="4fa8e-104">Severity: Error</span></span>  
  
 <span data-ttu-id="4fa8e-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="4fa8e-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="4fa8e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fa8e-106">Description</span></span>  
 <span data-ttu-id="4fa8e-107">Bu olay bir düzenleyici kurtarma günlük girdisi bozuk ve seri durumdan çıkarılmış hale getirilemedi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fa8e-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="4fa8e-108">Bu hatadan veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa8e-108">Data loss may result from this error.</span></span> <span data-ttu-id="4fa8e-109">Olay listeleri işlem kimliği, kurtarma verileri (şifreli Base64), özel durum, işlem adı ve işlem kimliği</span><span class="sxs-lookup"><span data-stu-id="4fa8e-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa8e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa8e-110">See also</span></span>
- [<span data-ttu-id="4fa8e-111">Günlüğe Olay Kaydetme</span><span class="sxs-lookup"><span data-stu-id="4fa8e-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="4fa8e-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4fa8e-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
