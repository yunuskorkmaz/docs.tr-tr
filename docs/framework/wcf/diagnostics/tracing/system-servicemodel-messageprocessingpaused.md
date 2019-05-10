---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 7dcdb9fdd6a283f692897cbbb49cd1f2d1dd661e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586786"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="405a6-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="405a6-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="405a6-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="405a6-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="405a6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="405a6-104">Description</span></span>  
 <span data-ttu-id="405a6-105">İş parçacığı, bir ileti işlenirken anahtarlı.</span><span class="sxs-lookup"><span data-stu-id="405a6-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="405a6-106">İleti işleme, aşağıdaki nedenlerden duraklatılabilir:</span><span class="sxs-lookup"><span data-stu-id="405a6-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="405a6-107">ConcurrencyMode tek ya da desteklemeyeceğini ve başka bir ileti işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="405a6-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="405a6-108">İşlem etkindir ve başka bir işlem işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="405a6-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="405a6-109">Eşitleme bağlamı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="405a6-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="405a6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="405a6-110">See also</span></span>

- [<span data-ttu-id="405a6-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="405a6-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="405a6-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="405a6-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="405a6-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="405a6-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
