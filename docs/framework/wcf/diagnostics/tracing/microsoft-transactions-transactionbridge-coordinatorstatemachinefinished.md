---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. Koordinattorstatemachinefinished'
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 83cbc6fe80d0fc611c88e8074805cae870261305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759399"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="2ea1b-103">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="2ea1b-103">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>

<span data-ttu-id="2ea1b-104">Bir düzenleyici kaydı için durum makinesi tamamlandı durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="2ea1b-104">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2ea1b-105">Description</span><span class="sxs-lookup"><span data-stu-id="2ea1b-105">Description</span></span>  

 <span data-ttu-id="2ea1b-106">Yerel Işlem yöneticisi bir üstün düzenleyici kaydı olduğunu düşündüğü zaman, 2PC işlemini tamamladı.</span><span class="sxs-lookup"><span data-stu-id="2ea1b-106">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="2ea1b-107">Kayıt için sonuç kaydedilmiş veya durdurulmuş ya da unutulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ea1b-107">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="2ea1b-108">Ayrıca, yerel Işlem yöneticisinin hazırlama sırasında salt okunur olarak oylaması halinde de izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="2ea1b-108">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea1b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea1b-109">See also</span></span>

- [<span data-ttu-id="2ea1b-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="2ea1b-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="2ea1b-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="2ea1b-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2ea1b-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="2ea1b-112">Administration and Diagnostics</span></span>](../index.md)
