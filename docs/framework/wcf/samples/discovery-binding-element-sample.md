---
title: Keşif Bağlama Öğesi Örneği
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: d906d9a389c50095f2af5d52e3874c3e43199e68
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687614"
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="a1b71-102">Keşif Bağlama Öğesi Örneği</span><span class="sxs-lookup"><span data-stu-id="a1b71-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="a1b71-103">Bu örnek, bir hizmet bulmak için bulma istemci bağlama öğesi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="a1b71-104">Bu özellik, geliştiricilerin çok sezgisel programlama modeli yaparak kendi mevcut istemci kanal yığınına bir keşif istemcisi kanalını eklemelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1b71-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="a1b71-105">İlişkili kanalı açıldığında hizmetinin adresini bulma kullanılarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="a1b71-106">Bu örnek aşağıdaki projeleri oluşur:</span><span class="sxs-lookup"><span data-stu-id="a1b71-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="a1b71-107">**CalculatorService**: WCF kayıtlı bir bulunabilir hizmet.</span><span class="sxs-lookup"><span data-stu-id="a1b71-107">**CalculatorService**: A discoverable WCF service.</span></span>  
  
-   <span data-ttu-id="a1b71-108">**CalculatorClient**: bir WCF istemcisi için arama yapın ve CalculatorService çağırmak için keşif istemcisi kanalını kullanan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a1b71-108">**CalculatorClient**: A WCF client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="a1b71-109">**DynamicCalculatorClient**: bir WCF istemcisi için arama yapın ve CalculatorService çağırmak için dinamik bir uç nokta kullanan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a1b71-109">**DynamicCalculatorClient**: A WCF client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a1b71-110">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="a1b71-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1b71-111">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a1b71-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a1b71-112">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a1b71-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1b71-113">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a1b71-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="a1b71-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="a1b71-114">CalculatorService</span></span>  
 <span data-ttu-id="a1b71-115">Bu proje uygulayan basit hesap makinesi hizmette içeren `ICalculatorService` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="a1b71-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="a1b71-116">Aşağıdaki App.config dosyasına eklemek için kullanılan bir `<serviceDiscovery>` hizmet davranışları ve bunun yanı sıra bulma uç noktası davranışı.</span><span class="sxs-lookup"><span data-stu-id="a1b71-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
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
  
 <span data-ttu-id="a1b71-117">Bu, hizmet ve kendi uç bulunabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1b71-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="a1b71-118">CalculatorService ekleyen bir uç nokta NetTcpBinding bağlama kullanılarak şirket içinde barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="a1b71-119">Ayrıca ekler bir `EndpointDiscoveryBehavior` uç noktasına ve aşağıdaki kodda gösterildiği gibi bir kapsam belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="a1b71-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="a1b71-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="a1b71-120">CalculatorClient</span></span>  
 <span data-ttu-id="a1b71-121">Bu proje için CalculatorService iletiler gönderen bir istemci uygulaması içerir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="a1b71-122">Bu programın kullandığı `CreateCustomBindingWithDiscoveryElement()` keşif istemcisi kanalını özel bağlamayı oluşturmak için gereken yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1b71-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
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
  
 <span data-ttu-id="a1b71-123">Sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> olan örneği, geliştirici hizmeti için aramak için kullanılan ölçütü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="a1b71-124">Bu durumda, bulma bulma ölçüttür `ICalculatorService` türü.</span><span class="sxs-lookup"><span data-stu-id="a1b71-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="a1b71-125">Ayrıca, geliştirici belirtir bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> döndüren bir <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Hizmetleri aranacağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="a1b71-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Yeni döndürür <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneği.</span><span class="sxs-lookup"><span data-stu-id="a1b71-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> <span data-ttu-id="a1b71-127">Daha fazla bilgi için [keşif istemci kanalıyla özel bağlama kullanma](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="a1b71-127">For more information, see [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
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
  
 <span data-ttu-id="a1b71-128">Bu durumda, istemci UDP kullanan yerel alt ağdaki hizmetleri Bulma Protokolü tarafından tanımlanan çok noktaya yayın mekanizması.</span><span class="sxs-lookup"><span data-stu-id="a1b71-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="a1b71-129">Yöntemin geri kalanı, özel bir bağlama oluşturur ve yığın üstüne bulma bağlama öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="a1b71-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1b71-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Bağlama yığınının üzerinde yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="a1b71-131">Tüm <xref:System.ServiceModel.Channels.BindingElement> üst kısmındaki <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> kanalı oluşturur ve kanal fabrikası kullanmaz emin olmanız gerekir `EndpointAddress` veya `Via` özellikleri, gerçek adresi yalnızca keşif istemcisi kanalını bulunamadığından.</span><span class="sxs-lookup"><span data-stu-id="a1b71-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="a1b71-132">Ardından, `CalculatorClient` bir uç nokta adresi yanı sıra, bu özel bağlama geçirerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a1b71-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="a1b71-133">Keşif istemcisi kanalını kullanırken, belirtilen sabit bir uç nokta adresini daha önce geçirilen.</span><span class="sxs-lookup"><span data-stu-id="a1b71-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="a1b71-134">Artık çalışma zamanında, Keşif istemcisi kanalını bulma ölçütleri tarafından belirtilen hizmetini bulur ve kendisine bağlar.</span><span class="sxs-lookup"><span data-stu-id="a1b71-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="a1b71-135">Hizmet ve istemci bağlantı kurmak için Ayrıca aynı temel alınan bağlama yığına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1b71-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a1b71-136">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a1b71-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="a1b71-137">Bir çözüm açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a1b71-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="a1b71-138">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a1b71-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="a1b71-139">Hizmet uygulaması ve her bir istemci uygulamaları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1b71-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="a1b71-140">İstemci hizmet adresini bilmeden bulamadı gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="a1b71-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b71-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1b71-141">See Also</span></span>
