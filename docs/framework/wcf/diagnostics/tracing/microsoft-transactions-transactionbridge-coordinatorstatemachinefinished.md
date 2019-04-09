---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: bffaed4976d82202eaea9ce50f6d389548fdabfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144839"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="ea10d-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="ea10d-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="ea10d-103">Bir düzenleyici kaydı için durum makinesinin tamamlandı durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="ea10d-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ea10d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea10d-104">Description</span></span>  
 <span data-ttu-id="ea10d-105">Üstün düzenleyici listelemesi 2pc işlemeyi tamamladığı yerel hareket yöneticisi inanmaktadır yaparken izlenen.</span><span class="sxs-lookup"><span data-stu-id="ea10d-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="ea10d-106">Liste için sonuç, kabul edilen veya iptal edildi veya unutulan olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea10d-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="ea10d-107">Yerel hareket yöneticisi hazırlama sırasında salt okunur oyları, ayrıca izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="ea10d-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea10d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea10d-108">See also</span></span>

- [<span data-ttu-id="ea10d-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="ea10d-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ea10d-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ea10d-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ea10d-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="ea10d-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
