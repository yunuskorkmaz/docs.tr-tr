---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: de9d27e74088b1bac9c8a401c5af2b119fc8e90e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797979"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="28fa8-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="28fa8-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="28fa8-103">Numarasını 139</span><span class="sxs-lookup"><span data-stu-id="28fa8-103">Id: 139</span></span>  
  
 <span data-ttu-id="28fa8-104">İnin Hata</span><span class="sxs-lookup"><span data-stu-id="28fa8-104">Severity: Error</span></span>  
  
 <span data-ttu-id="28fa8-105">Alan Işlem Köprüsü</span><span class="sxs-lookup"><span data-stu-id="28fa8-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="28fa8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28fa8-106">Description</span></span>  
 <span data-ttu-id="28fa8-107">Bu olay, bir düzenleyici kurtarma günlüğü girişinin bozuk olduğunu ve seri durumdan çıkarılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28fa8-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="28fa8-108">Veri kaybı bu hatadan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="28fa8-108">Data loss may result from this error.</span></span> <span data-ttu-id="28fa8-109">Olayda Işlem KIMLIĞI, kurtarma verileri (Base64 kodlamalı), özel durum, işlem adı ve işlem KIMLIĞI listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="28fa8-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28fa8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28fa8-110">See also</span></span>

- [<span data-ttu-id="28fa8-111">Günlüğe Olay Kaydetme</span><span class="sxs-lookup"><span data-stu-id="28fa8-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="28fa8-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="28fa8-112">Events General Reference</span></span>](events-general-reference.md)
