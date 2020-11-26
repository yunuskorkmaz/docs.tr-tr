---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: e4c8040d2350e3824b5d68dc6f32376007792a7f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235122"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="11ea3-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="11ea3-102">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="11ea3-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="11ea3-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="11ea3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11ea3-104">Description</span></span>  

 <span data-ttu-id="11ea3-105">Bir ileti işlenirken iş parçacıkları değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="11ea3-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="11ea3-106">İleti işleme aşağıdaki nedenlerden dolayı duraklatılabilir:</span><span class="sxs-lookup"><span data-stu-id="11ea3-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="11ea3-107">ConcurrencyMode tek veya yer aldığı ve hizmet başka bir iletiyi işliyor.</span><span class="sxs-lookup"><span data-stu-id="11ea3-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="11ea3-108">İşlem etkin ve hizmet başka bir işlem işliyor.</span><span class="sxs-lookup"><span data-stu-id="11ea3-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="11ea3-109">Eşitleme bağlamı güncel değil.</span><span class="sxs-lookup"><span data-stu-id="11ea3-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ea3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11ea3-110">See also</span></span>

- [<span data-ttu-id="11ea3-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="11ea3-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="11ea3-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="11ea3-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="11ea3-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="11ea3-113">Administration and Diagnostics</span></span>](../index.md)
