---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 960166c7c1d91bcab8420a55e633b461bf37c626
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="65e98-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="65e98-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="65e98-103">Bir düzenleyici listelemesi için durum makinesinin tamamlanmış duruma geçti.</span><span class="sxs-lookup"><span data-stu-id="65e98-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="65e98-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65e98-104">Description</span></span>  
 <span data-ttu-id="65e98-105">Yerel işlem yöneticisi üstün düzenleyici listelemesi 2pc işleme tamamlandı düşündüğü, izlenen.</span><span class="sxs-lookup"><span data-stu-id="65e98-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="65e98-106">Kaydı için sonuç, kabul edilen veya iptal edildi veya Forgotten olabilir.</span><span class="sxs-lookup"><span data-stu-id="65e98-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="65e98-107">Yerel işlem yöneticisi salt okunur hazırlama sırasında oylarının, ayrıca izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="65e98-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e98-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65e98-108">See Also</span></span>  
 [<span data-ttu-id="65e98-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="65e98-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="65e98-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="65e98-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="65e98-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="65e98-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
