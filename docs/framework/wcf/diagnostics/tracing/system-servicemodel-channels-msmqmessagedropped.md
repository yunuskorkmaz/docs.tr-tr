---
description: ': System. ServiceModel. Channels. Msmqmessagebırakıldı hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 41b9c6d5399f0f6b458404ee4b64624e5863c777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780966"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="0258c-103">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="0258c-103">System.ServiceModel.Channels.MsmqMessageDropped</span></span>

<span data-ttu-id="0258c-104">MSMQ iletiyi bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0258c-104">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0258c-105">Description</span><span class="sxs-lookup"><span data-stu-id="0258c-105">Description</span></span>  

 <span data-ttu-id="0258c-106">İzleme, bir MSMQ iletisinin bırakıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0258c-106">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="0258c-107">MSMQ iletileri Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile kullanılan) tarafından işlenemiyor olduğunda bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="0258c-107">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="0258c-108">Bu tür iletiler, zarar iletileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0258c-108">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="0258c-109">`ReceiveErrorHandling`NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında bir zehirli ileti bırakılır `Drop` .</span><span class="sxs-lookup"><span data-stu-id="0258c-109">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="0258c-110">Bırakılan bir ileti kuyruktan kaldırılır ve artık kurtarılamaz.</span><span class="sxs-lookup"><span data-stu-id="0258c-110">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="0258c-111">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="0258c-111">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0258c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0258c-112">See also</span></span>

- [<span data-ttu-id="0258c-113">İzleme</span><span class="sxs-lookup"><span data-stu-id="0258c-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="0258c-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0258c-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0258c-115">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="0258c-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="0258c-116">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="0258c-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
