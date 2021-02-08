---
description: 'Daha fazla bilgi edinin: Istemci Channel-Level programlama'
title: İstemci Kanal Düzeyi Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 7e4e977231339fbbede7111e38a67054eb24eed9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803002"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="7068b-103">İstemci Kanal Düzeyi Programlama</span><span class="sxs-lookup"><span data-stu-id="7068b-103">Client Channel-Level Programming</span></span>

<span data-ttu-id="7068b-104">Bu konuda, <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> sınıfı ve ilişkili nesne modeli kullanılmadan Windows Communication Foundation (WCF) istemci uygulamasının nasıl yazılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7068b-104">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="7068b-105">Ileti gönderme</span><span class="sxs-lookup"><span data-stu-id="7068b-105">Sending Messages</span></span>  

 <span data-ttu-id="7068b-106">İletileri göndermeye ve yanıtları almaya ve işlemeye hazırlamak için aşağıdaki adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="7068b-106">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="7068b-107">Bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7068b-107">Create a binding.</span></span>  
  
2. <span data-ttu-id="7068b-108">Bir kanal fabrikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7068b-108">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="7068b-109">Kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7068b-109">Create a channel.</span></span>  
  
4. <span data-ttu-id="7068b-110">İstek gönderin ve yanıtı okuyun.</span><span class="sxs-lookup"><span data-stu-id="7068b-110">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="7068b-111">Tüm kanal nesnelerini kapatın.</span><span class="sxs-lookup"><span data-stu-id="7068b-111">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="7068b-112">Bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="7068b-112">Creating a Binding</span></span>  

 <span data-ttu-id="7068b-113">Alıcı çalışmasına benzer şekilde (bkz. [Service Channel-Level programlama](service-channel-level-programming.md)), gönderme iletileri bir bağlama oluşturarak başlar.</span><span class="sxs-lookup"><span data-stu-id="7068b-113">Similar to the receiving case (see [Service Channel-Level Programming](service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="7068b-114">Bu örnek, yeni bir oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> öğesi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="7068b-114">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="7068b-115">ChannelFactory oluşturma</span><span class="sxs-lookup"><span data-stu-id="7068b-115">Building a ChannelFactory</span></span>  

 <span data-ttu-id="7068b-116">Oluşturma yerine <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType> , bu kez, <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> tür parametresinin bulunduğu bağlamayı çağırarak oluşturuyoruz <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7068b-116">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7068b-117">Kanal dinleyicileri gelen iletiler için bekleyen bir tarafında kullanıldığında, kanal fabrikaları bir kanal oluşturma iletişimini Başlatan tarafında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7068b-117">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="7068b-118">Yalnızca Kanal dinleyicileri gibi, kanal fabrikaları kullanılmadan önce açılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7068b-118">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="7068b-119">Kanal oluşturma</span><span class="sxs-lookup"><span data-stu-id="7068b-119">Creating a Channel</span></span>  

 <span data-ttu-id="7068b-120">Daha sonra <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> bir oluşturmak için öğesini çağırıyoruz <xref:System.ServiceModel.Channels.IRequestChannel> .</span><span class="sxs-lookup"><span data-stu-id="7068b-120">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="7068b-121">Bu çağrı, oluşturulmakta olan yeni kanalı kullanarak iletişim kurmak istediğimiz bitiş noktasının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="7068b-121">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="7068b-122">Kanalımız olduktan sonra, iletişim için hazırlamak üzere açık duruma getirmek için üzerinde aç çağrısı yaptık.</span><span class="sxs-lookup"><span data-stu-id="7068b-122">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="7068b-123">Taşımanın yapısına bağlı olarak, bu açmaya yapılan çağrı hedef uç noktayla bir bağlantı başlatabilir veya ağda hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="7068b-123">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="7068b-124">Istek gönderme ve yanıtı okuma</span><span class="sxs-lookup"><span data-stu-id="7068b-124">Sending a Request and Reading the Reply</span></span>  

 <span data-ttu-id="7068b-125">Açık bir kanaldan karşılaştığımız bir ileti oluşturabilir ve kanalın Istek yöntemini kullanarak isteği gönderebilir ve yanıtın geri gelmesini bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7068b-125">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="7068b-126">Bu yöntem döndürüldüğünde, bitiş noktasının yanıtının ne olduğunu öğrenmek için okuyabilmemiz gereken bir yanıt iletisi vardır.</span><span class="sxs-lookup"><span data-stu-id="7068b-126">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="7068b-127">Nesneleri kapatma</span><span class="sxs-lookup"><span data-stu-id="7068b-127">Closing Objects</span></span>  

 <span data-ttu-id="7068b-128">Sızan kaynakların sızmasını önlemek için, iletişimlerdeki nesneleri artık gerekli olmadıklarında kapattık.</span><span class="sxs-lookup"><span data-stu-id="7068b-128">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="7068b-129">Aşağıdaki kod örneği, bir ileti göndermek ve yanıtı okumak için kanal fabrikası kullanan temel bir istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7068b-129">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
