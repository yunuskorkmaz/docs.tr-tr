---
description: 'Daha fazla bilgi edinin: System. ServiceModel. TxCompletionStatusCompletedForAsyncAbort'
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 892a867607d1c6d34c06a59947cc336db067fb19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735692"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="65a61-103">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="65a61-103">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>

<span data-ttu-id="65a61-104">Belirtilen işlem için belirtilen işlem zaman uyumsuz iptal nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="65a61-104">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="65a61-105">Description</span><span class="sxs-lookup"><span data-stu-id="65a61-105">Description</span></span>  

 <span data-ttu-id="65a61-106">Geçerli işlem, başka bir katılımcının Iptali, zaman aşımları veya bir işlemin katılımcısı içinde başka bir hata nedeniyle sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="65a61-106">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="65a61-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="65a61-107">Troubleshooting</span></span>  

 <span data-ttu-id="65a61-108">Bu iptal beklenmiyorsa, İptalin gerçek nedenini öğrenmek için tüm sistem günlüklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="65a61-108">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a61-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65a61-109">See also</span></span>

- [<span data-ttu-id="65a61-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="65a61-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="65a61-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="65a61-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="65a61-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="65a61-112">Administration and Diagnostics</span></span>](../index.md)
