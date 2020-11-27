---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 6e8b134f61d2dc9bd5daf541db4ec81604166baa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260389"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="ea38c-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="ea38c-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>

<span data-ttu-id="ea38c-103">MSMQ iletiyi bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ea38c-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ea38c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea38c-104">Description</span></span>  

 <span data-ttu-id="ea38c-105">İzleme, bir MSMQ iletisinin bırakıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea38c-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="ea38c-106">MSMQ iletileri Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile kullanılan) tarafından işlenemiyor olduğunda bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea38c-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="ea38c-107">Bu tür iletiler, zarar iletileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ea38c-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="ea38c-108">`ReceiveErrorHandling`NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında bir zehirli ileti bırakılır `Drop` .</span><span class="sxs-lookup"><span data-stu-id="ea38c-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="ea38c-109">Bırakılan bir ileti kuyruktan kaldırılır ve artık kurtarılamaz.</span><span class="sxs-lookup"><span data-stu-id="ea38c-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="ea38c-110">İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="ea38c-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea38c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea38c-111">See also</span></span>

- [<span data-ttu-id="ea38c-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="ea38c-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="ea38c-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ea38c-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ea38c-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="ea38c-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="ea38c-115">Zehirli Ileti Işleme</span><span class="sxs-lookup"><span data-stu-id="ea38c-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
