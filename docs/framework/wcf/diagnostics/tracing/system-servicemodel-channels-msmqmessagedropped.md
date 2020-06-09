---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601926"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="d2add-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="d2add-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="d2add-103">MSMQ iletiyi bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d2add-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d2add-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2add-104">Description</span></span>  
 <span data-ttu-id="d2add-105">İzleme, bir MSMQ iletisinin bırakıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2add-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="d2add-106">MSMQ iletileri Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile kullanılan) tarafından işlenemiyor olduğunda bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2add-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="d2add-107">Bu tür iletiler, zarar iletileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d2add-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="d2add-108">`ReceiveErrorHandling`NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında bir zehirli ileti bırakılır `Drop` .</span><span class="sxs-lookup"><span data-stu-id="d2add-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="d2add-109">Bırakılan bir ileti kuyruktan kaldırılır ve artık kurtarılamaz.</span><span class="sxs-lookup"><span data-stu-id="d2add-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="d2add-110">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="d2add-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2add-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2add-111">See also</span></span>

- [<span data-ttu-id="d2add-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="d2add-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="d2add-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2add-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d2add-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="d2add-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="d2add-115">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="d2add-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
