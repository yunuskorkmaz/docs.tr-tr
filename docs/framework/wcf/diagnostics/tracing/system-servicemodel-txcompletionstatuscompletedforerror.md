---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 2bc71d18480fa19be66cbfa1687a7b63eb548309
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601458"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="0dcf6-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="0dcf6-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="0dcf6-103">Belirtilen işlem için belirtilen işlem, işlenmemiş bir yürütme özel durumu nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0dcf6-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0dcf6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dcf6-104">Description</span></span>  
 <span data-ttu-id="0dcf6-105">Geçerli işlemi tamamlamaya çalışırken bir hata oluştuğunda izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0dcf6-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="0dcf6-106">Bu, çağrıyı yapana bir yanıt veya hata gönderilmeden önce oluşur.</span><span class="sxs-lookup"><span data-stu-id="0dcf6-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0dcf6-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0dcf6-107">Troubleshooting</span></span>  
 <span data-ttu-id="0dcf6-108">Özel durum iletisi ve herhangi bir işlem yapılabilir öğe için izlenen iletiyi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="0dcf6-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dcf6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dcf6-109">See also</span></span>

- [<span data-ttu-id="0dcf6-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="0dcf6-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="0dcf6-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0dcf6-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0dcf6-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="0dcf6-112">Administration and Diagnostics</span></span>](../index.md)
