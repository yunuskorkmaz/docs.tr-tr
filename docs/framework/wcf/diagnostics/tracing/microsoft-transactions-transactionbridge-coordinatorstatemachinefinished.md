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
ms.openlocfilehash: 2f99670d61df45edfef5350da080f12e892a0f74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="9b811-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="9b811-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="9b811-103">Bir düzenleyici listelemesi için durum makinesinin tamamlanmış duruma geçti.</span><span class="sxs-lookup"><span data-stu-id="9b811-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9b811-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b811-104">Description</span></span>  
 <span data-ttu-id="9b811-105">Yerel işlem yöneticisi üstün düzenleyici listelemesi 2pc işleme tamamlandı düşündüğü, izlenen.</span><span class="sxs-lookup"><span data-stu-id="9b811-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="9b811-106">Kaydı için sonuç, kabul edilen veya iptal edildi veya Forgotten olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b811-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="9b811-107">Yerel işlem yöneticisi salt okunur hazırlama sırasında oylarının, ayrıca izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="9b811-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b811-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b811-108">See Also</span></span>  
 [<span data-ttu-id="9b811-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="9b811-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9b811-110">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="9b811-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9b811-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="9b811-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
