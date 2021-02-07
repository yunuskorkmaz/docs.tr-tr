---
description: ': System. ServiceModel. Messageprocessingduraklatıldığı hakkında daha fazla bilgi'
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 77e4742bc5617904136b2ddd9cb90fe886d38b10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716191"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="1e150-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="1e150-103">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="1e150-104">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="1e150-104">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="1e150-105">Description</span><span class="sxs-lookup"><span data-stu-id="1e150-105">Description</span></span>  

 <span data-ttu-id="1e150-106">Bir ileti işlenirken iş parçacıkları değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="1e150-106">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="1e150-107">İleti işleme aşağıdaki nedenlerden dolayı duraklatılabilir:</span><span class="sxs-lookup"><span data-stu-id="1e150-107">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="1e150-108">ConcurrencyMode tek veya yer aldığı ve hizmet başka bir iletiyi işliyor.</span><span class="sxs-lookup"><span data-stu-id="1e150-108">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="1e150-109">İşlem etkin ve hizmet başka bir işlem işliyor.</span><span class="sxs-lookup"><span data-stu-id="1e150-109">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="1e150-110">Eşitleme bağlamı güncel değil.</span><span class="sxs-lookup"><span data-stu-id="1e150-110">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e150-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e150-111">See also</span></span>

- [<span data-ttu-id="1e150-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="1e150-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="1e150-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1e150-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1e150-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="1e150-114">Administration and Diagnostics</span></span>](../index.md)
