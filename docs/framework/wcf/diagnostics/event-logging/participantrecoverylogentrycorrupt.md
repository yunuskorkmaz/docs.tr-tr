---
title: ParticipantRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
ms.openlocfilehash: 8fe65199425196ab8910d9ffc9f70d7224137825
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278576"
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="9296f-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="9296f-102">ParticipantRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="9296f-103">Kimlik: 138</span><span class="sxs-lookup"><span data-stu-id="9296f-103">Id: 138</span></span>  
  
 <span data-ttu-id="9296f-104">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="9296f-104">Severity: Error</span></span>  
  
 <span data-ttu-id="9296f-105">Kategori: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="9296f-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="9296f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9296f-106">Description</span></span>  

 <span data-ttu-id="9296f-107">Bu olay katılımcı kurtarma günlüğü girişinin bozuk olduğunu ve seri durumdan çıkarılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9296f-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="9296f-108">Veri kaybı bu hatadan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="9296f-108">Data loss may result from this error.</span></span> <span data-ttu-id="9296f-109">Olayda Işlem KIMLIĞI, kurtarma verileri (Base64 kodlamalı), özel durum, işlem adı ve işlem KIMLIĞI listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="9296f-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9296f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9296f-110">See also</span></span>

- [<span data-ttu-id="9296f-111">Etkinlikleri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="9296f-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="9296f-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9296f-112">Events General Reference</span></span>](events-general-reference.md)
