---
title: "İstemci Kanal Düzeyi Programlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c3d9bc1819045c8261f003cbab52dd71c4da408
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="78d7e-102">İstemci Kanal Düzeyi Programlama</span><span class="sxs-lookup"><span data-stu-id="78d7e-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="78d7e-103">Bu konuda nasıl yazılacağını açıklar bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanmadan istemci uygulaması <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> sınıfı ve onun ilişkili nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="78d7e-103">This topic describes how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="78d7e-104">İleti gönderme</span><span class="sxs-lookup"><span data-stu-id="78d7e-104">Sending Messages</span></span>  
 <span data-ttu-id="78d7e-105">İletileri göndermek ve almak ve yanıtları işlemek hazır olması için aşağıdaki adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="78d7e-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1.  <span data-ttu-id="78d7e-106">Bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78d7e-106">Create a binding.</span></span>  
  
2.  <span data-ttu-id="78d7e-107">Kanal fabrikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78d7e-107">Build a channel factory.</span></span>  
  
3.  <span data-ttu-id="78d7e-108">Bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78d7e-108">Create a channel.</span></span>  
  
4.  <span data-ttu-id="78d7e-109">Bir istek gönderin ve yanıt okuyun.</span><span class="sxs-lookup"><span data-stu-id="78d7e-109">Send a request and read the reply.</span></span>  
  
5.  <span data-ttu-id="78d7e-110">Tüm kanal nesneleri kapatın.</span><span class="sxs-lookup"><span data-stu-id="78d7e-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="78d7e-111">Bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="78d7e-111">Creating a Binding</span></span>  
 <span data-ttu-id="78d7e-112">Alıcı çalışmasına benzer (bkz [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), bir bağlama oluşturarak iletileri başlatır gönderme.</span><span class="sxs-lookup"><span data-stu-id="78d7e-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="78d7e-113">Bu örnekte yeni bir oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve ekleyen bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> , öğeler koleksiyonuna.</span><span class="sxs-lookup"><span data-stu-id="78d7e-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="78d7e-114">Bir ChannelFactory oluşturma</span><span class="sxs-lookup"><span data-stu-id="78d7e-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="78d7e-115">Oluşturmak yerine bir <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, biz bu oluşturduğunuzda bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> tür parametresi olduğu bağlama üzerinde <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78d7e-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78d7e-116">Kanal dinleyicileri gelen iletiler için bekleyeceği yan yana kullanılırken, kanal fabrikaları bir kanal oluşturmak için iletişim başlatır yan yana kullanılır.</span><span class="sxs-lookup"><span data-stu-id="78d7e-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="78d7e-117">Kanal dinleyicileri olduğu gibi kullanılabilmesi için önce kanal fabrikaları öncelikle açılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78d7e-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="78d7e-118">Bir kanal oluşturma</span><span class="sxs-lookup"><span data-stu-id="78d7e-118">Creating a Channel</span></span>  
 <span data-ttu-id="78d7e-119">Ardından diyoruz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> oluşturmak için bir <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="78d7e-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="78d7e-120">Bu çağrı ile oluşturulan yeni kanal kullanarak iletişim kurmak istiyoruz uç noktası adresi alır.</span><span class="sxs-lookup"><span data-stu-id="78d7e-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="78d7e-121">Bir kanal sahibiz sonra açık bir durumda iletişimi için hazır put dayanarak diyoruz.</span><span class="sxs-lookup"><span data-stu-id="78d7e-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="78d7e-122">Taşıma yapısı, bağlı olarak bu çağrıyı açık hedef uç noktası ile bir bağlantı başlatmak veya ağ üzerinde hiç bir şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d7e-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="78d7e-123">Bir istek göndermek ve yanıt okuma</span><span class="sxs-lookup"><span data-stu-id="78d7e-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="78d7e-124">Biz açılmış bir kanal olduktan sonra size bir ileti oluşturup isteği göndermek ve geri dönmeniz yanıt için beklemek için kanalın istek yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d7e-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="78d7e-125">Bu yöntem döndürüldüğünde, biz uç noktanın yanıt neydi çıkışı bulmak için okuyabilecekleri bir yanıt iletisi sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="78d7e-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="78d7e-126">Nesneleri kapatma</span><span class="sxs-lookup"><span data-stu-id="78d7e-126">Closing Objects</span></span>  
 <span data-ttu-id="78d7e-127">Kaynakları sızmasını önlemek için biz artık gerekli olduklarında iletişimde kullanılan nesneleri kapatın.</span><span class="sxs-lookup"><span data-stu-id="78d7e-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="78d7e-128">Aşağıdaki kod örneği, ileti gönderme ve yanıt okumak için kanal fabrikası kullanarak temel bir istemci gösterir.</span><span class="sxs-lookup"><span data-stu-id="78d7e-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
