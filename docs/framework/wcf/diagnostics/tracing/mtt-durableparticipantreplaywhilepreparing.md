---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589138"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="952be-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="952be-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="952be-103">WS-AT protokol hizmeti, hazırlama Işlemine yanıt vermeyen dayanıklı bir katılımcıdan bir yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="952be-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="952be-104">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="952be-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="952be-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="952be-105">Description</span></span>  
 <span data-ttu-id="952be-106">Dayanıklı bir katılımcı hazırlanırken bir yeniden yürütme iletisi alındığında izleniyor.</span><span class="sxs-lookup"><span data-stu-id="952be-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="952be-107">Bu durum için geçersiz bir ileti ve işlem durdurulacak.</span><span class="sxs-lookup"><span data-stu-id="952be-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="952be-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="952be-108">Troubleshooting</span></span>

<span data-ttu-id="952be-109">Bu hatanın alınması, dayanıklı bir katılımcının (alt Işlem yöneticileri dahil) hatadan kurtarıldığını gösterebilir; Ancak, işlem sonucu emin değildir ve durumunu ister.</span><span class="sxs-lookup"><span data-stu-id="952be-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952be-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="952be-110">See also</span></span>

- [<span data-ttu-id="952be-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="952be-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="952be-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="952be-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="952be-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="952be-113">Administration and Diagnostics</span></span>](../index.md)
