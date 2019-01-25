---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 8cc32e7b38bfd1bdafd2377ad759f98b248d722e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710462"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="32a6e-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="32a6e-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="32a6e-103">Bir düzenleyici kaydı için durum makinesinin tamamlandı durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="32a6e-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="32a6e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32a6e-104">Description</span></span>  
 <span data-ttu-id="32a6e-105">Üstün düzenleyici listelemesi 2pc işlemeyi tamamladığı yerel hareket yöneticisi inanmaktadır yaparken izlenen.</span><span class="sxs-lookup"><span data-stu-id="32a6e-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="32a6e-106">Liste için sonuç, kabul edilen veya iptal edildi veya unutulan olabilir.</span><span class="sxs-lookup"><span data-stu-id="32a6e-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="32a6e-107">Yerel hareket yöneticisi hazırlama sırasında salt okunur oyları, ayrıca izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="32a6e-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a6e-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32a6e-108">See also</span></span>
- [<span data-ttu-id="32a6e-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="32a6e-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="32a6e-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="32a6e-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="32a6e-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="32a6e-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
