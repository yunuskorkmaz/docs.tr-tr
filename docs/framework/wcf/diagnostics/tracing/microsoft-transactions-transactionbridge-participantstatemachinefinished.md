---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 0652b3b76c155431b68c5ee0dc8f83977f9845a5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594367"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="a9ded-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="a9ded-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="a9ded-103">Katılımcı listesi için durum makinesi tamamlandı durumuna girdi.</span><span class="sxs-lookup"><span data-stu-id="a9ded-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a9ded-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9ded-104">Description</span></span>  
 <span data-ttu-id="a9ded-105">Bir alt katılımcı kaydı 2PC işlemesini tamamladığında izleniyor.</span><span class="sxs-lookup"><span data-stu-id="a9ded-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="a9ded-106">Kayıt için sonuç kaydedilmiş veya durdurulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9ded-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="a9ded-107">Ayrıca, hazırlama sırasında herhangi bir katılımcının salt okunur olarak oylaması halinde de izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a9ded-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ded-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9ded-108">See also</span></span>

- [<span data-ttu-id="a9ded-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="a9ded-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="a9ded-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9ded-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a9ded-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="a9ded-111">Administration and Diagnostics</span></span>](../index.md)
