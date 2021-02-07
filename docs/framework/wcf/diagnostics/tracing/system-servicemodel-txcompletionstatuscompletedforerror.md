---
description: 'Şu konuda daha fazla bilgi edinin: System. ServiceModel. TxCompletionStatusCompletedForError'
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 83cd5c258b3a60f69cc94426aed7ccc1d27f6013
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735614"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="88482-103">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="88482-103">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>

<span data-ttu-id="88482-104">Belirtilen işlem için belirtilen işlem, işlenmemiş bir yürütme özel durumu nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="88482-104">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="88482-105">Description</span><span class="sxs-lookup"><span data-stu-id="88482-105">Description</span></span>  

 <span data-ttu-id="88482-106">Geçerli işlemi tamamlamaya çalışırken bir hata oluştuğunda izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="88482-106">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="88482-107">Bu, çağrıyı yapana bir yanıt veya hata gönderilmeden önce oluşur.</span><span class="sxs-lookup"><span data-stu-id="88482-107">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="88482-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="88482-108">Troubleshooting</span></span>  

 <span data-ttu-id="88482-109">Özel durum iletisi ve herhangi bir işlem yapılabilir öğe için izlenen iletiyi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="88482-109">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88482-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88482-110">See also</span></span>

- [<span data-ttu-id="88482-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="88482-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="88482-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="88482-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="88482-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="88482-113">Administration and Diagnostics</span></span>](../index.md)
