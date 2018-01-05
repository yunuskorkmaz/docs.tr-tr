---
title: "Önemli İzlemeler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6641fe633585caf6cbf068a804430f9171e5ece0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="significant-traces"></a><span data-ttu-id="1ad31-102">Önemli İzlemeler</span><span class="sxs-lookup"><span data-stu-id="1ad31-102">Significant Traces</span></span>
<span data-ttu-id="1ad31-103">Bu konu tarafından gösterilen önemli izlemeler bazıları listeler [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ad31-103">This topic lists some of the major traces emitted by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="significant-traces"></a><span data-ttu-id="1ad31-104">Önemli İzlemeler</span><span class="sxs-lookup"><span data-stu-id="1ad31-104">Significant Traces</span></span>  
  
|<span data-ttu-id="1ad31-105">İzleme</span><span class="sxs-lookup"><span data-stu-id="1ad31-105">Trace</span></span>|<span data-ttu-id="1ad31-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ad31-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ad31-107">İleti günlüğü izleme</span><span class="sxs-lookup"><span data-stu-id="1ad31-107">Message log trace</span></span>|<span data-ttu-id="1ad31-108">İzleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ileti ileti günlüğü tarafından günlüğe özelliği `System.ServiceModel.MessageLogging` izleme kaynağını etkindir.</span><span class="sxs-lookup"><span data-stu-id="1ad31-108">The trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is logged by the message logging feature when the `System.ServiceModel.MessageLogging` trace source is enabled.</span></span> <span data-ttu-id="1ad31-109">Bu izleme tıklatarak iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1ad31-109">Clicking this trace displays the message.</span></span> <span data-ttu-id="1ad31-110">Bir ileti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, ileti günlüğü izleme iletisi kaynak öznitelikte belirttiği.</span><span class="sxs-lookup"><span data-stu-id="1ad31-110">There are four configurable logging points for a message: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, also indicated by the Message Source attribute in the message log trace.</span></span>|  
|<span data-ttu-id="1ad31-111">Alınan ileti izleme</span><span class="sxs-lookup"><span data-stu-id="1ad31-111">Message received trace</span></span>|<span data-ttu-id="1ad31-112">Bu izleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] varsa iletisi aldı `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1ad31-112">This trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is received if the `System.ServiceModel` trace source is enabled at information or verbose level.</span></span> <span data-ttu-id="1ad31-113">Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ad31-113">This trace is necessary to see the message correlation arrow in the activity graph view.</span></span>|  
|<span data-ttu-id="1ad31-114">Gönderilen ileti izleme</span><span class="sxs-lookup"><span data-stu-id="1ad31-114">Message sent trace</span></span>|<span data-ttu-id="1ad31-115">Bu izleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , iletinin gönderildiği `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1ad31-115">This trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is sent if the `System.ServiceModel` trace source is enabled at information or verbose level.</span></span> <span data-ttu-id="1ad31-116">Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ad31-116">This trace is necessary to see the message correlation arrow in the activity graph view.</span></span>|  
|<span data-ttu-id="1ad31-117">ChannelEndpointElement öğesini Al</span><span class="sxs-lookup"><span data-stu-id="1ad31-117">Get ChannelEndpointElement</span></span>|<span data-ttu-id="1ad31-118">Bu izleme bilgileri düzeyinde yapı kanal fabrikası yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1ad31-118">This trace is emitted in Construct channel factory, at information level.</span></span> <span data-ttu-id="1ad31-119">Bu, istemci uç nokta açıklamasını Konuşmayı (uzak adres, bağlama, sözleşme adı) sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ad31-119">It provides a description of the endpoint the client is talking to (remote address, binding, contract name).</span></span>|  
|<span data-ttu-id="1ad31-120">ServiceElement öğesini Al</span><span class="sxs-lookup"><span data-stu-id="1ad31-120">Get ServiceElement</span></span>|<span data-ttu-id="1ad31-121">Bu izleme, bilgi düzeyinde yapı hizmeti ana bilgisayarı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1ad31-121">This trace is emitted in Construct service host, at Information level.</span></span> <span data-ttu-id="1ad31-122">Bağlama ve hizmet sözleşmesini açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ad31-122">It provides a description of the service contract and binding.</span></span>|  
|<span data-ttu-id="1ad31-123">SocketConnection oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ad31-123">SocketConnection create</span></span>|<span data-ttu-id="1ad31-124">Bu izleme, istemci tarafından gerçekleştirilen ilk işlem eylem ve hizmet alma bayt faaliyete yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1ad31-124">This trace is emitted in the first Process action performed by the client and in the Receive bytes activity on the service.</span></span> <span data-ttu-id="1ad31-125">Yerel ve uzak IP adresleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ad31-125">It provides the local and remote IP addresses.</span></span> <span data-ttu-id="1ad31-126">Bilgi düzeyinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1ad31-126">It is emitted at Information level.</span></span>|
