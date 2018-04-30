---
title: Keşif İstemcisi Kanalını Kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7828b3037318e4fb63820fe8d235a92e64fb0b07
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="using-the-discovery-client-channel"></a><span data-ttu-id="7bfaf-102">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7bfaf-102">Using the Discovery Client Channel</span></span>
<span data-ttu-id="7bfaf-103">Bir WCF istemcisi uygulama yazarken, aradığınız hizmet uç noktası adresi bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-103">When writing a WCF client application you need to know the endpoint address of the service you are calling.</span></span> <span data-ttu-id="7bfaf-104">Çoğu durumda, bir hizmetin uç noktası adresi önceden bilinmiyor veya zamanla hizmetinin adresini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-104">In many situations the endpoint address of a service is not known in advance or the address of the service changes over time.</span></span> <span data-ttu-id="7bfaf-105">Keşif istemcisi kanalını aramak istediğiniz hizmetini tanımlayan ve istemci kanal otomatik olarak bir yoklama isteği gönderir bir WCF istemci uygulaması yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-105">The Discovery Client Channel allows you to write a WCF client application, describe the service you want to call, and the client channel automatically sends a probe request.</span></span> <span data-ttu-id="7bfaf-106">Bir hizmet yanıtladığında keşif istemcisi kanalını hizmeti için uç nokta adresi araştırma yanıtı alır ve hizmeti çağırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-106">When a service responds, the discovery client channel retrieves the endpoint address for the service from the probe response and uses it to call the service.</span></span>  
  
## <a name="using-the-discovery-client-channel"></a><span data-ttu-id="7bfaf-107">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7bfaf-107">Using the Discovery Client Channel</span></span>  
 <span data-ttu-id="7bfaf-108">Keşif istemcisi kanalını kullanmak için bir örnek ekler <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> istemci kanal yığınına.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-108">To use the Discovery Client Channel, add an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your client channel stack.</span></span> <span data-ttu-id="7bfaf-109">Alternatif olarak kullanabileceğiniz <xref:System.ServiceModel.Discovery.DynamicEndpoint> ve <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> zaten yüklü değilse, bağlama otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-109">Alternatively you can use the <xref:System.ServiceModel.Discovery.DynamicEndpoint> and a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is automatically added to your binding if not already present.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="7bfaf-110">Önerilir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , istemci kanal yığında en üstteki öğesidir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-110">It is recommended that the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is the top-most element on your client channel stack.</span></span> <span data-ttu-id="7bfaf-111">Üstünde eklenen herhangi bir bağlama öğesi <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> emin olmanız gerekir <xref:System.ServiceModel.ChannelFactory> veya kanal oluşturur, uç nokta adresi kullanmaz veya `Via` adresi (geçirilen `CreateChannel` yöntemi) çünkü bunlar doğru içeremez adresi.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-111">Any binding element that is added on top of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the <xref:System.ServiceModel.ChannelFactory> or channel it creates does not use the endpoint address or `Via` address (passed to the `CreateChannel` method) because they may not contain the correct address.</span></span>  
  
 <span data-ttu-id="7bfaf-112"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Sınıfı iki genel özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7bfaf-112">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> class contains two public properties:</span></span>  
  
1.  <span data-ttu-id="7bfaf-113"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, istediğiniz çağırmak için hizmeti açıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-113"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, which is used to describe the service you want to call.</span></span>  
  
2.  <span data-ttu-id="7bfaf-114"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> bulma ileti göndermek için bulma uç noktası belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-114"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> which specifies the discovery endpoint to send discovery messages to.</span></span>  
  
 <span data-ttu-id="7bfaf-115"><xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Özellik aradığınız hizmet sözleşmesini belirtmenize olanak tanır, gerekli tüm kapsam URI'ler ve kanalını açmayı denemek için saat sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-115">The <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> property allows you to specify the service contract you are searching for, any required scope URIs, and the maximum number of time to attempt to open the channel.</span></span> <span data-ttu-id="7bfaf-116">Oluşturucu çağırarak belirtilen sözleşme türü <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-116">The contract type is specified by calling the constructor  <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span> <span data-ttu-id="7bfaf-117">Kapsam URI'ler eklenebilir <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-117">Scope URIs can be added to the <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> property.</span></span> <span data-ttu-id="7bfaf-118"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Özelliği için istemci çalıştığı bağlanmak sonuçları sayısını belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-118">The <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> property allows you to specify the maximum number of results to which the client tries to connect to.</span></span> <span data-ttu-id="7bfaf-119">Bir araştırma yanıtı aldığında istemci yoklama yanıtı uç nokta adresinden kullanarak kanalını açmayı dener.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-119">When a probe response is received the client attempts to open the channel using the endpoint address from the probe response.</span></span> <span data-ttu-id="7bfaf-120">Bir özel durum oluşursa, istemcinin sonraki yoklama yanıtı gerekiyorsa alınabilmesi daha fazla yanıt bekleniyor geçer.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-120">If an exception occurs the client moves on to the next probe response, waiting for more responses to be received if necessary.</span></span> <span data-ttu-id="7bfaf-121">Kanal başarıyla açıldı veya sonuçları sayısı üst sınırına kadar bunun devam eder.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-121">It continues to do this until the channel is successfully opened or the maximum number of results is reached.</span></span> <span data-ttu-id="7bfaf-122">Bu ayarlar hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-122">For more information about these settings, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>  
  
 <span data-ttu-id="7bfaf-123"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Özelliğini kullanmak için bulma uç noktası belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-123">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> property allows you to specify the discovery endpoint to use.</span></span> <span data-ttu-id="7bfaf-124">Normalde bu olan bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ancak herhangi bir geçerli uç nokta olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-124">Normally this is a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, but it can be any valid endpoint.</span></span>  
  
 <span data-ttu-id="7bfaf-125">Hizmet ile iletişim kurmak için kullanılacak bağlama oluştururken, hizmet olarak tam aynı bağlama kullanılacağını dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-125">When you are creating the binding to use to communicate with the service, you must be careful to use the exact same binding as the service.</span></span> <span data-ttu-id="7bfaf-126">Tek fark bağlama istemcisinin yüklü olduğu bir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> yığının üst kısmında.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-126">The only difference is the client binding has a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> on the top of the stack.</span></span> <span data-ttu-id="7bfaf-127">Hizmet sistem tarafından sağlanan bağlamalar birini kullanıyorsanız, yeni bir oluşturma <xref:System.ServiceModel.Channels.CustomBinding> ve sistem tarafından sağlanan bir bağlamayı için geçirin <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-127">If service is using one of the system-provided bindings, create a new <xref:System.ServiceModel.Channels.CustomBinding> and pass in the system-provided binding to the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor.</span></span> <span data-ttu-id="7bfaf-128">Ekleyebileceğiniz sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> çağırarak `Insert` üzerinde <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-128">Then you can add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> by calling `Insert` on the <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> property.</span></span>  
  
 <span data-ttu-id="7bfaf-129">Bunu ekledikten sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , bağlama için ve, yapılandırılmış WCF istemci sınıfının bir örneğini oluşturur, bunu açın ve yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-129">Once you have added the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your binding and configured it, you can create an instance of the WCF client class, open it, and call its methods.</span></span> <span data-ttu-id="7bfaf-130">Aşağıdaki örnek, uygulayan bir WCF hizmeti bulmak için keşif istemcisi kanalını kullanır `ICalculator` sınıfı (başlatıldı WCF alma öğreticide kullanılan) ve çağrıları kendi `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-130">The following example uses the Discovery Client Channel to discover a WCF service that implements the `ICalculator` class (used in the Getting Started WCF tutorial) and calls its `Add` method.</span></span>  
  
```  
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the   
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a><span data-ttu-id="7bfaf-131">Güvenlik ve keşif istemcisi kanalını</span><span class="sxs-lookup"><span data-stu-id="7bfaf-131">Security and the Discovery Client Channel</span></span>  
 <span data-ttu-id="7bfaf-132">Keşif istemcisi kanalını kullanırken, iki uç nokta belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-132">When using the discovery client channel, two endpoints are being specified.</span></span> <span data-ttu-id="7bfaf-133">Bir kullanılan bulma iletileri için genellikle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ve diğer uygulama uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-133">One is used for discovery messages, usually <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, and the other is the application endpoint.</span></span> <span data-ttu-id="7bfaf-134">Güvenli bir hizmet uygularken, her iki uç noktalarını güvenli hale getirmek için dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bfaf-134">When implementing a secure service, care must be taken to secure both endpoints.</span></span> <span data-ttu-id="7bfaf-135">Güvenlik hakkında daha fazla bilgi için bkz: [güvenli hale getirme hizmetler ve istemcileri](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7bfaf-135">For more information about security, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span>
