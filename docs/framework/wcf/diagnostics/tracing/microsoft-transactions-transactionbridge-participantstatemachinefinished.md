---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: bd6c9124e6346437e2bb35df620e00bad13b60f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258952"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="b2d3b-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="b2d3b-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>

<span data-ttu-id="b2d3b-103">Katılımcı listesi için durum makinesi tamamlandı durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="b2d3b-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b2d3b-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2d3b-104">Description</span></span>  

 <span data-ttu-id="b2d3b-105">Bir alt katılımcı kaydı 2PC işlemesini tamamladığında izleniyor.</span><span class="sxs-lookup"><span data-stu-id="b2d3b-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="b2d3b-106">Kayıt için sonuç kaydedilmiş veya durdurulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2d3b-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="b2d3b-107">Ayrıca, hazırlama sırasında herhangi bir katılımcının salt okunur olarak oylaması halinde de izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b2d3b-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d3b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2d3b-108">See also</span></span>

- [<span data-ttu-id="b2d3b-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="b2d3b-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="b2d3b-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="b2d3b-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b2d3b-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="b2d3b-111">Administration and Diagnostics</span></span>](../index.md)
