---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ba067303d861bbd7d88c67f6fd868bd808e07dfd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528686"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="0081e-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="0081e-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="0081e-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="0081e-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="0081e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0081e-104">Description</span></span>  
 <span data-ttu-id="0081e-105">İş parçacığı, bir ileti işlenirken anahtarlı.</span><span class="sxs-lookup"><span data-stu-id="0081e-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="0081e-106">İleti işleme, aşağıdaki nedenlerden duraklatılabilir:</span><span class="sxs-lookup"><span data-stu-id="0081e-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="0081e-107">ConcurrencyMode tek ya da desteklemeyeceğini ve başka bir ileti işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="0081e-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="0081e-108">İşlem etkindir ve başka bir işlem işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="0081e-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="0081e-109">Eşitleme bağlamı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0081e-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0081e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0081e-110">See also</span></span>
- [<span data-ttu-id="0081e-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="0081e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0081e-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0081e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0081e-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="0081e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
