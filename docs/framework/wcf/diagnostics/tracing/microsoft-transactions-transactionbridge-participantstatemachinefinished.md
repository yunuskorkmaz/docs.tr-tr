---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53ac142c8c7d8004020210ffb3c0dcb2355a5b61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="4d532-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="4d532-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="4d532-103">Katılımcı kaydı Durum makinesi tamamlanmış durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="4d532-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4d532-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d532-104">Description</span></span>  
 <span data-ttu-id="4d532-105">Bağımlı bir katılımcı listesi 2pc işlemeyi tamamlandığında izlenen.</span><span class="sxs-lookup"><span data-stu-id="4d532-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="4d532-106">Kaydı için sonuç, kabul edilen veya iptal edildi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d532-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="4d532-107">Herhangi bir katılımcı ReadOnly hazırlama sırasında oylarının, ayrıca izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="4d532-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d532-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d532-108">See Also</span></span>  
 [<span data-ttu-id="4d532-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="4d532-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4d532-110">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="4d532-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4d532-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="4d532-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
