---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 8371dba79573f480b264ed6185b8cf0098e3cb2a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576583"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="1bf20-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="1bf20-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="1bf20-103">Belirtilen işlem için belirtilen işlem zaman uyumsuz iptal nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1bf20-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1bf20-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bf20-104">Description</span></span>  
 <span data-ttu-id="1bf20-105">Geçerli işlem, başka bir katılımcının Iptali, zaman aşımları veya bir işlemin katılımcısı içinde başka bir hata nedeniyle sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="1bf20-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1bf20-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1bf20-106">Troubleshooting</span></span>  
 <span data-ttu-id="1bf20-107">Bu iptal beklenmiyorsa, İptalin gerçek nedenini öğrenmek için tüm sistem günlüklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1bf20-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf20-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf20-108">See also</span></span>

- [<span data-ttu-id="1bf20-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="1bf20-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="1bf20-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1bf20-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1bf20-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="1bf20-111">Administration and Diagnostics</span></span>](../index.md)
