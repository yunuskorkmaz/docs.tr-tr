---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674794"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="0f283-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="0f283-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="0f283-103">MSMQ iletiyi bıraktı.</span><span class="sxs-lookup"><span data-stu-id="0f283-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f283-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f283-104">Description</span></span>  
 <span data-ttu-id="0f283-105">İzleme, bir MSMQ iletisinin bırakıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f283-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="0f283-106">MsMQ iletileri, Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile birlikte kullanılır) bunları işleyemediğinde bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f283-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="0f283-107">Bu tür iletilere zehirli iletiler denir.</span><span class="sxs-lookup"><span data-stu-id="0f283-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="0f283-108">NetMsmqBinding veya `ReceiveErrorHandling` MsmqIntegrationBinding üzerindeki özellik ayarlandığında bir zehir `Drop`iletisi bırakılır.</span><span class="sxs-lookup"><span data-stu-id="0f283-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="0f283-109">Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılamaz.</span><span class="sxs-lookup"><span data-stu-id="0f283-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="0f283-110">İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın.</span><span class="sxs-lookup"><span data-stu-id="0f283-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f283-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f283-111">See also</span></span>

- [<span data-ttu-id="0f283-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="0f283-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0f283-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0f283-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0f283-114">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="0f283-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="0f283-115">Zehir-Mesaj Taşıma</span><span class="sxs-lookup"><span data-stu-id="0f283-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
