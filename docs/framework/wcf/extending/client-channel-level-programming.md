---
title: İstemci Kanal Düzeyi Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923272"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="1f3e7-102">İstemci Kanal Düzeyi Programlama</span><span class="sxs-lookup"><span data-stu-id="1f3e7-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="1f3e7-103">Bu konu, kullanmadan bir Windows Communication Foundation (WCF) istemci uygulaması yazma açıklar <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> sınıf ve onun ilişkili nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="1f3e7-104">İleti gönderme</span><span class="sxs-lookup"><span data-stu-id="1f3e7-104">Sending Messages</span></span>  
 <span data-ttu-id="1f3e7-105">İleti göndermek ve almak ve yanıtları işlemek hazır olması için aşağıdaki adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="1f3e7-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="1f3e7-106">Bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-106">Create a binding.</span></span>  
  
2. <span data-ttu-id="1f3e7-107">Kanal fabrikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-107">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="1f3e7-108">Bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-108">Create a channel.</span></span>  
  
4. <span data-ttu-id="1f3e7-109">Bir istek gönderir ve yanıtı okuyun.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-109">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="1f3e7-110">Tüm kanal nesneleri kapatın.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="1f3e7-111">Bir bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f3e7-111">Creating a Binding</span></span>  
 <span data-ttu-id="1f3e7-112">Alıcı çalışmasına benzer (bkz [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), bir bağlama oluşturarak iletileri başlatır gönderme.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="1f3e7-113">Bu örnekte yeni bir oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve ekler bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> alt öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="1f3e7-114">Bir ChannelFactory oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f3e7-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="1f3e7-115">Oluşturmak yerine bir <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, bu kez, oluşturduğumuz bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> tür parametresi olduğu bağlama üzerinde <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f3e7-116">Kanal dinleyicileri gelen iletileri beklediği yan yana kullanılırken, kanal fabrikaları bir kanal oluşturmak için iletişim başlatır yan yana kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="1f3e7-117">Kanal dinleyicileri olduğu gibi kanal fabrikaları ilk kullanılabilmesi için önce açılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="1f3e7-118">Bir kanal oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f3e7-118">Creating a Channel</span></span>  
 <span data-ttu-id="1f3e7-119">Ardından diyoruz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> oluşturmak için bir <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="1f3e7-120">Bu çağrı ile oluşturulan yeni kanal kullanarak iletişim kurmak istiyoruz uç nokta adresini alır.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="1f3e7-121">Biz bir kanal oluşturduktan sonra açık bir durumuna iletişimi için hazır hale getirmek için üzerindeki diyoruz.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="1f3e7-122">Taşıma yapısı, bağlı olarak bu çağrıyı açık bağlantı hedef uç nokta ile başlatabilir veya ağ üzerinde hiç bir şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="1f3e7-123">Bir isteği gönderme ve yanıt okuma</span><span class="sxs-lookup"><span data-stu-id="1f3e7-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="1f3e7-124">Biz açılan bir kanal oluşturduktan sonra size bir ileti oluşturup isteği gönderme ve geri dönmeniz yanıt için beklemek için kanal istek yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="1f3e7-125">Bu yöntem döndürüldüğünde, uç noktanın yanıt neydi kullanıma bulmak için okuyabilecekleri bir yanıt iletisi sahibiz.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="1f3e7-126">Nesnelerini kapatma</span><span class="sxs-lookup"><span data-stu-id="1f3e7-126">Closing Objects</span></span>  
 <span data-ttu-id="1f3e7-127">Kaynakları sızdırılmasını önlemek için şu nesneler artık gerekli olmayan iletişimde kullanılan kapatın.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="1f3e7-128">Aşağıdaki kod örneği, bir ileti gönderin ve yanıt okumak için kanal fabrikası kullanarak temel bir istemci gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f3e7-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
