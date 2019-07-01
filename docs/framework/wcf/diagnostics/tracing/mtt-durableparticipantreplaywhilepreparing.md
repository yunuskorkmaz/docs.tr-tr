---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486763"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="6603d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="6603d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="6603d-103">WS-AT protokolü hizmetini hazırlama için yanıt vermedi dayanıklı bir katılımcı yeniden yürütme iletisi aldı.</span><span class="sxs-lookup"><span data-stu-id="6603d-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="6603d-104">Sonuç olarak, işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6603d-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6603d-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6603d-105">Description</span></span>  
 <span data-ttu-id="6603d-106">Dayanıklı bir katılımcı hala hazırlama sırasında yeniden yürütme iletisi aldıysanız izlenen.</span><span class="sxs-lookup"><span data-stu-id="6603d-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="6603d-107">Bu durum için geçersiz bir ileti budur ve işlem iptal edecek.</span><span class="sxs-lookup"><span data-stu-id="6603d-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6603d-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="6603d-108">Troubleshooting</span></span>

<span data-ttu-id="6603d-109">Bu hatanın belirtebilirsiniz (alt TransactionManagers dahil) dayanıklı bir katılımcı; hatasından kurtarıldı Ancak, hareketin sonucu kullanacağınızdan ve durumunu ister.</span><span class="sxs-lookup"><span data-stu-id="6603d-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6603d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6603d-110">See also</span></span>

- [<span data-ttu-id="6603d-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="6603d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="6603d-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="6603d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6603d-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="6603d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
