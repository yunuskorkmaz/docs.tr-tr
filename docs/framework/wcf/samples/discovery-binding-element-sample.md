---
title: "Keşif Bağlama Öğesi Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 821f629a7f39869975af19c793fe26188a40d7d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="7d03d-102">Keşif Bağlama Öğesi Örneği</span><span class="sxs-lookup"><span data-stu-id="7d03d-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="7d03d-103">Bu örnek, bir hizmet bulmak için bulma istemci bağlama öğesi kullanılacak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="7d03d-104">Bu özellik, bir keşif istemcisi kanalını programlama modeli çok sezgisel hale getirme, mevcut istemci kanal yığınına eklemek için geliştiricilere sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d03d-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="7d03d-105">İlişkili kanalı açıldığında hizmetinin adresini bulma kullanılarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="7d03d-106">Bu örnek aşağıdaki projeleri oluşur:</span><span class="sxs-lookup"><span data-stu-id="7d03d-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="7d03d-107">**CalculatorService**: bir bulunabilirlik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="7d03d-107">**CalculatorService**: A discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
-   <span data-ttu-id="7d03d-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aramak ve CalculatorService çağırmak için keşif istemcisi kanalını kullanan istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="7d03d-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="7d03d-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aramak ve CalculatorService çağırmak için dinamik bir uç noktası kullanan istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="7d03d-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d03d-110">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7d03d-111">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7d03d-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7d03d-112">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7d03d-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d03d-113">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7d03d-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="7d03d-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="7d03d-114">CalculatorService</span></span>  
 <span data-ttu-id="7d03d-115">Bu proje uygulayan bir basit hesap makinesi hizmetinin içeriyor `ICalculatorService` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="7d03d-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="7d03d-116">Aşağıdaki App.config dosyası eklemek için kullanılan bir `<serviceDiscovery>` hizmet davranışları ve bunun yanı sıra bulma uç noktası davranışı.</span><span class="sxs-lookup"><span data-stu-id="7d03d-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="7d03d-117">Bu, hizmet ve bitiş noktaları bulunabilirlik kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7d03d-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="7d03d-118">CalculatorService NetTcpBinding bağlama kullanarak bir uç nokta ekler kendini barındıran bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="7d03d-119">Ayrıca ekler bir `EndpointDiscoveryBehavior` uç noktasına ve aşağıdaki kodda gösterildiği gibi bir kapsam belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="7d03d-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="7d03d-120">CalculatorClient</span></span>  
 <span data-ttu-id="7d03d-121">Bu proje için CalculatorService iletileri gönderen bir istemci uygulaması içerir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="7d03d-122">Bu programın kullandığı `CreateCustomBindingWithDiscoveryElement()` yöntemi bir özel, bağlama oluşturmak için keşif istemcisi kanalını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7d03d-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 <span data-ttu-id="7d03d-123">Sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> olan örneği, geliştirici için bir hizmet ararken kullanılacak ölçütleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="7d03d-124">Bu durumda, bulma bulma ölçüttür `ICalculatorService` türü.</span><span class="sxs-lookup"><span data-stu-id="7d03d-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="7d03d-125">Ayrıca, geliştirici belirten bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> döndüren bir <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> nerede Hizmetleri araması belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="7d03d-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Yeni döndürür <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneği.</span><span class="sxs-lookup"><span data-stu-id="7d03d-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7d03d-127">[Keşif istemci kanalıyla özel bağlama kullanma](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="7d03d-127"> [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 <span data-ttu-id="7d03d-128">Bu durumda, istemci UDP kullanan Hizmetleri yerel alt ağda aramak için keşif protokolü tarafından tanımlanan çok noktaya yayın mekanizması.</span><span class="sxs-lookup"><span data-stu-id="7d03d-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="7d03d-129">Yöntem kalanı özel bağlama oluşturur ve yığının en üstte keşif bağlama öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="7d03d-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d03d-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Bağlama yığının üst kısmında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d03d-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="7d03d-131">Tüm <xref:System.ServiceModel.Channels.BindingElement> üstünde <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> kanal fabrikası veya oluşturduğu kanal kullanmayan emin olmanız gerekir `EndpointAddress` veya `Via` özellikler, gerçek adresini yalnızca keşif istemcisi kanalını bulunamadığı için.</span><span class="sxs-lookup"><span data-stu-id="7d03d-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="7d03d-132">Ardından, `CalculatorClient` bir uç nokta adresi yanı sıra, bu özel bağlama geçirerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="7d03d-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="7d03d-133">Keşif istemcisi kanalını kullanırken, belirtilen sabit uç noktası adresi daha önce geçirilen.</span><span class="sxs-lookup"><span data-stu-id="7d03d-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="7d03d-134">Artık çalışma zamanında keşif istemcisi kanalını bulma ölçütleri tarafından belirtilen hizmetini bulur ve kendisine bağlar.</span><span class="sxs-lookup"><span data-stu-id="7d03d-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="7d03d-135">Hizmet ve bağlantı kurmak için istemci için de aynı temel bağlama yığınına olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d03d-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7d03d-136">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7d03d-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="7d03d-137">Çözümde açmak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d03d-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="7d03d-138">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d03d-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="7d03d-139">Hizmet uygulaması ve her bir istemci uygulamaları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d03d-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="7d03d-140">İstemci hizmet adresini bilmeden bulamıyor gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="7d03d-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d03d-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d03d-141">See Also</span></span>
