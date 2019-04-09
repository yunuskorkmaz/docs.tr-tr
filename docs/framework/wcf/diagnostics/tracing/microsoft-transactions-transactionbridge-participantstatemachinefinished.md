---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 7f37cb5d9ee3d2d9d56519f785388f278b3333b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170735"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="5ad4b-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="5ad4b-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="5ad4b-103">Katılımcı bir listesi için durum makinesinin tamamlandı durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="5ad4b-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5ad4b-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ad4b-104">Description</span></span>  
 <span data-ttu-id="5ad4b-105">Bağımlı bir katılımcı listesi 2pc işlemeyi tamamlandığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="5ad4b-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="5ad4b-106">Liste için sonuç, kabul edilen veya iptal edildi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ad4b-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="5ad4b-107">Herhangi bir katılımcı salt okunur hazırlama sırasında oyları, ayrıca izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="5ad4b-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad4b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ad4b-108">See also</span></span>

- [<span data-ttu-id="5ad4b-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="5ad4b-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="5ad4b-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ad4b-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5ad4b-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="5ad4b-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
