---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: e4466df2ce96760db4790b6545484704c22f0842
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254304"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="c124f-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="c124f-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>

<span data-ttu-id="c124f-103">Belirtilen işlem için belirtilen işlem, işlenmemiş bir yürütme özel durumu nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c124f-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c124f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c124f-104">Description</span></span>  

 <span data-ttu-id="c124f-105">Geçerli işlemi tamamlamaya çalışırken bir hata oluştuğunda izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c124f-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="c124f-106">Bu, çağrıyı yapana bir yanıt veya hata gönderilmeden önce oluşur.</span><span class="sxs-lookup"><span data-stu-id="c124f-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c124f-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="c124f-107">Troubleshooting</span></span>  

 <span data-ttu-id="c124f-108">Özel durum iletisi ve herhangi bir işlem yapılabilir öğe için izlenen iletiyi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="c124f-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c124f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c124f-109">See also</span></span>

- [<span data-ttu-id="c124f-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="c124f-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="c124f-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="c124f-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c124f-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="c124f-112">Administration and Diagnostics</span></span>](../index.md)
