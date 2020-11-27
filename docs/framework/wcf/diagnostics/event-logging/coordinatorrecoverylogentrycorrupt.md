---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: c3174e70d42385923674a3db5f696a0f64eda29f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295372"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="1d15a-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="1d15a-102">CoordinatorRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="1d15a-103">Kimlik: 139</span><span class="sxs-lookup"><span data-stu-id="1d15a-103">Id: 139</span></span>  
  
 <span data-ttu-id="1d15a-104">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="1d15a-104">Severity: Error</span></span>  
  
 <span data-ttu-id="1d15a-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="1d15a-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="1d15a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d15a-106">Description</span></span>  

 <span data-ttu-id="1d15a-107">Bu olay, bir düzenleyici kurtarma günlüğü girişinin bozuk olduğunu ve seri durumdan çıkarılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d15a-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="1d15a-108">Veri kaybı bu hatadan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="1d15a-108">Data loss may result from this error.</span></span> <span data-ttu-id="1d15a-109">Olayda Işlem KIMLIĞI, kurtarma verileri (Base64 kodlamalı), özel durum, işlem adı ve işlem KIMLIĞI listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d15a-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d15a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d15a-110">See also</span></span>

- [<span data-ttu-id="1d15a-111">Etkinlikleri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="1d15a-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="1d15a-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1d15a-112">Events General Reference</span></span>](events-general-reference.md)
