---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3f51d1269f5ca89f4f02257c8accef3423aa7eb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472689"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="28a48-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="28a48-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="28a48-103">Kimliği: 139</span><span class="sxs-lookup"><span data-stu-id="28a48-103">Id: 139</span></span>  
  
 <span data-ttu-id="28a48-104">Önem derecesi: hata</span><span class="sxs-lookup"><span data-stu-id="28a48-104">Severity: Error</span></span>  
  
 <span data-ttu-id="28a48-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="28a48-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="28a48-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28a48-106">Description</span></span>  
 <span data-ttu-id="28a48-107">Bu olay, bir düzenleyici kurtarma günlük girişi bozuktu ve seri durumdan çıkarılmış açılamadı gösterir.</span><span class="sxs-lookup"><span data-stu-id="28a48-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="28a48-108">Bu hatadan veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="28a48-108">Data loss may result from this error.</span></span> <span data-ttu-id="28a48-109">Olay listeleri işlem kimliği, kurtarma verileri (Base64 ile kodlanmış), özel durum, işlem adı ve işlem kimliği</span><span class="sxs-lookup"><span data-stu-id="28a48-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a48-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28a48-110">See Also</span></span>  
 [<span data-ttu-id="28a48-111">Günlüğe Olay Kaydetme</span><span class="sxs-lookup"><span data-stu-id="28a48-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="28a48-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="28a48-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
