---
description: 'Daha fazla bilgi edinin: Koordinattorrecoverylogentrybozulmuş'
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3a848c634a226b34023a24898f9827162b4dafc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771346"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="f06c8-103">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="f06c8-103">CoordinatorRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="f06c8-104">Kimlik: 139</span><span class="sxs-lookup"><span data-stu-id="f06c8-104">Id: 139</span></span>  
  
 <span data-ttu-id="f06c8-105">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="f06c8-105">Severity: Error</span></span>  
  
 <span data-ttu-id="f06c8-106">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="f06c8-106">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="f06c8-107">Description</span><span class="sxs-lookup"><span data-stu-id="f06c8-107">Description</span></span>  

 <span data-ttu-id="f06c8-108">Bu olay, bir düzenleyici kurtarma günlüğü girişinin bozuk olduğunu ve seri durumdan çıkarılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f06c8-108">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="f06c8-109">Veri kaybı bu hatadan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="f06c8-109">Data loss may result from this error.</span></span> <span data-ttu-id="f06c8-110">Olayda Işlem KIMLIĞI, kurtarma verileri (Base64 kodlamalı), özel durum, işlem adı ve işlem KIMLIĞI listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f06c8-110">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06c8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f06c8-111">See also</span></span>

- [<span data-ttu-id="f06c8-112">Etkinlikleri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="f06c8-112">Event Logging</span></span>](index.md)
- [<span data-ttu-id="f06c8-113">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f06c8-113">Events General Reference</span></span>](events-general-reference.md)
