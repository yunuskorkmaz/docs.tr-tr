---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 591e1a1dcb6746d79ff5eceba7e74e890f327354
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112664"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="16c5c-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="16c5c-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="16c5c-103">Belirtilen işlem için belirtilen işlem yürütme işlenmeyen bir özel durum nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="16c5c-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="16c5c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16c5c-104">Description</span></span>  
 <span data-ttu-id="16c5c-105">Geçerli işlemi tamamlamak için girişimi sırasında bir hata oluştuğunda izlenen.</span><span class="sxs-lookup"><span data-stu-id="16c5c-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="16c5c-106">Bir yanıt önce böyle veya hata çağırana gönderilir.</span><span class="sxs-lookup"><span data-stu-id="16c5c-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="16c5c-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="16c5c-107">Troubleshooting</span></span>  
 <span data-ttu-id="16c5c-108">Özel durum iletisi ve herhangi bir eyleme dönüştürülebilir öğe için izlenen iletisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="16c5c-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c5c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16c5c-109">See also</span></span>

- [<span data-ttu-id="16c5c-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="16c5c-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="16c5c-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="16c5c-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="16c5c-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="16c5c-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
