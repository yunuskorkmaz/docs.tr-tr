---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: e36126dcdfcc87a410d200cdf23aac670dc2b5e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596520"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="22387-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="22387-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="22387-103">Belirtilen işlem için belirtilen işlem yürütme işlenmeyen bir özel durum nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="22387-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="22387-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22387-104">Description</span></span>  
 <span data-ttu-id="22387-105">Geçerli işlemi tamamlamak için girişimi sırasında bir hata oluştuğunda izlenen.</span><span class="sxs-lookup"><span data-stu-id="22387-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="22387-106">Bir yanıt önce böyle veya hata çağırana gönderilir.</span><span class="sxs-lookup"><span data-stu-id="22387-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="22387-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="22387-107">Troubleshooting</span></span>  
 <span data-ttu-id="22387-108">Özel durum iletisi ve herhangi bir eyleme dönüştürülebilir öğe için izlenen iletisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="22387-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22387-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22387-109">See also</span></span>
- [<span data-ttu-id="22387-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="22387-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="22387-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="22387-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="22387-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="22387-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
