---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: faf4a07badb71588c601cd9390e4d8e3f187e629
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121634"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="c83c1-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="c83c1-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="c83c1-103">Kimliği: 139</span><span class="sxs-lookup"><span data-stu-id="c83c1-103">Id: 139</span></span>  
  
 <span data-ttu-id="c83c1-104">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="c83c1-104">Severity: Error</span></span>  
  
 <span data-ttu-id="c83c1-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="c83c1-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="c83c1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c83c1-106">Description</span></span>  
 <span data-ttu-id="c83c1-107">Bu olay bir düzenleyici kurtarma günlük girdisi bozuk ve seri durumdan çıkarılmış hale getirilemedi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c83c1-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="c83c1-108">Bu hatadan veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c83c1-108">Data loss may result from this error.</span></span> <span data-ttu-id="c83c1-109">Olay listeleri işlem kimliği, kurtarma verileri (şifreli Base64), özel durum, işlem adı ve işlem kimliği</span><span class="sxs-lookup"><span data-stu-id="c83c1-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83c1-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c83c1-110">See also</span></span>

- [<span data-ttu-id="c83c1-111">Etkinlikleri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="c83c1-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="c83c1-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c83c1-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
