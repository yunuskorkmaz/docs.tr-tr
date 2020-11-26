---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: bfa279887339f025e4cb7c9c455fd25098684073
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236617"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="3b78e-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="3b78e-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>

<span data-ttu-id="3b78e-103">WS-AT protokol hizmeti, hazırlama Işlemine yanıt vermeyen dayanıklı bir katılımcıdan bir yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="3b78e-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="3b78e-104">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3b78e-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3b78e-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b78e-105">Description</span></span>  

 <span data-ttu-id="3b78e-106">Dayanıklı bir katılımcı hazırlanırken bir yeniden yürütme iletisi alındığında izleniyor.</span><span class="sxs-lookup"><span data-stu-id="3b78e-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="3b78e-107">Bu durum için geçersiz bir ileti ve işlem durdurulacak.</span><span class="sxs-lookup"><span data-stu-id="3b78e-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3b78e-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="3b78e-108">Troubleshooting</span></span>

<span data-ttu-id="3b78e-109">Bu hatanın alınması, dayanıklı bir katılımcının (alt Işlem yöneticileri dahil) hatadan kurtarıldığını gösterebilir; Ancak, işlem sonucu emin değildir ve durumunu ister.</span><span class="sxs-lookup"><span data-stu-id="3b78e-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b78e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b78e-110">See also</span></span>

- [<span data-ttu-id="3b78e-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="3b78e-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="3b78e-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="3b78e-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3b78e-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="3b78e-113">Administration and Diagnostics</span></span>](../index.md)
