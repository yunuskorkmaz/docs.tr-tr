---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. DurableParticipantReplayWhilePreparing'
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fcaa50dd4faa548cad8ff085f1c66f94c63bd010
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635668"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="03542-103">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="03542-103">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>

<span data-ttu-id="03542-104">WS-AT protokol hizmeti, hazırlama Işlemine yanıt vermeyen dayanıklı bir katılımcıdan bir yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="03542-104">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="03542-105">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="03542-105">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="03542-106">Description</span><span class="sxs-lookup"><span data-stu-id="03542-106">Description</span></span>  

 <span data-ttu-id="03542-107">Dayanıklı bir katılımcı hazırlanırken bir yeniden yürütme iletisi alındığında izleniyor.</span><span class="sxs-lookup"><span data-stu-id="03542-107">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="03542-108">Bu durum için geçersiz bir ileti ve işlem durdurulacak.</span><span class="sxs-lookup"><span data-stu-id="03542-108">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="03542-109">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="03542-109">Troubleshooting</span></span>

<span data-ttu-id="03542-110">Bu hatanın alınması, dayanıklı bir katılımcının (alt Işlem yöneticileri dahil) hatadan kurtarıldığını gösterebilir; Ancak, işlem sonucu emin değildir ve durumunu ister.</span><span class="sxs-lookup"><span data-stu-id="03542-110">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03542-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03542-111">See also</span></span>

- [<span data-ttu-id="03542-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="03542-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="03542-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="03542-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="03542-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="03542-114">Administration and Diagnostics</span></span>](../index.md)
