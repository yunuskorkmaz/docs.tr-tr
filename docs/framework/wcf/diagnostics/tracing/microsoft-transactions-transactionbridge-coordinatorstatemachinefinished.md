---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 2d874cebe96b9caa99032e2881e19ec9cd34d047
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259017"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="5d547-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="5d547-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>

<span data-ttu-id="5d547-103">Bir düzenleyici kaydı için durum makinesi tamamlandı durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="5d547-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5d547-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d547-104">Description</span></span>  

 <span data-ttu-id="5d547-105">Yerel Işlem yöneticisi bir üstün düzenleyici kaydı olduğunu düşündüğü zaman, 2PC işlemini tamamladı.</span><span class="sxs-lookup"><span data-stu-id="5d547-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="5d547-106">Kayıt için sonuç kaydedilmiş veya durdurulmuş ya da unutulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d547-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="5d547-107">Ayrıca, yerel Işlem yöneticisinin hazırlama sırasında salt okunur olarak oylaması halinde de izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5d547-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d547-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d547-108">See also</span></span>

- [<span data-ttu-id="5d547-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="5d547-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="5d547-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="5d547-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5d547-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="5d547-111">Administration and Diagnostics</span></span>](../index.md)
