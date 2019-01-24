---
title: Temel Örnek
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 7a9a6134313ed75fd0f9b9f929a3a3715a0af133
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706832"
---
# <a name="basic-sample"></a><span data-ttu-id="e6b0b-102">Temel Örnek</span><span class="sxs-lookup"><span data-stu-id="e6b0b-102">Basic Sample</span></span>
<span data-ttu-id="e6b0b-103">Bu örnek, bir hizmet bulunabilir hale getirme ve arayın ve kayıtlı bir bulunabilir hizmet çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="e6b0b-104">Bu örnek iki projeden oluşan: hizmet ve istemci.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
>  <span data-ttu-id="e6b0b-105">Bu örnek, kod içinde bulma uygular.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="e6b0b-106">Yapılandırmada bulma uygulayan bir örnek için bkz. [yapılandırma](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e6b0b-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>  
  
## <a name="service"></a><span data-ttu-id="e6b0b-107">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e6b0b-107">Service</span></span>  
 <span data-ttu-id="e6b0b-108">Bu bir basit hesap makinesi hizmet uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="e6b0b-109">Kod içinde bulunabilir bulma ilgili `Main` burada bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına eklenir ve <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki kodda gösterildiği gibi eklenir.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="e6b0b-110">İstemci</span><span class="sxs-lookup"><span data-stu-id="e6b0b-110">Client</span></span>  
 <span data-ttu-id="e6b0b-111">İstemcinin kullandığı bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmetini bulamadı.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="e6b0b-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>, Bir standart uç nokta, istemci açıldığında hizmetinin uç noktası giderir.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="e6b0b-113">Bu durumda, <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmet sözleşmesine dayalı hizmet arar.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="e6b0b-114"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Üzerinden arama yapar bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="e6b0b-115">Hizmet uç noktası bulduktan sonra istemci bu hizmet için belirtilen bağlama üzerinden bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 <span data-ttu-id="e6b0b-116">İstemci adı verilen bir yöntem tanımlar `InvokeCalculatorService` kullanan <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri aramak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="e6b0b-117"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Devraldığı <xref:System.ServiceModel.Description.ServiceEndpoint>, bu nedenle, geçirilebilir `InvokeCalculatorService` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="e6b0b-118">Ardından örnekte <xref:System.ServiceModel.Discovery.DynamicEndpoint> bir örneğini oluşturmak için `CalculatorServiceClient` ve çeşitli işlemler hesaplayıcı hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Subtract service operation.  
   result = client.Subtract(value1, value2);  
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Multiply service operation.  
   result = client.Multiply(value1, value2);  
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Divide service operation.  
   result = client.Divide(value1, value2);  
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
   Console.WriteLine();  
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e6b0b-119">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e6b0b-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="e6b0b-120">Bu örnek HTTP uç noktaları kullanır ve bu örneği çalıştırmak için doğru URL ACL eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="e6b0b-121">Daha fazla bilgi için [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="e6b0b-121">For more information, see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="e6b0b-122">Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="e6b0b-123">Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler yerine etki alanı ve kullanıcı adı isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="e6b0b-124">Visual Studio 2012 kullanarak Basic.sln açın ve örnek oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>  
  
3.  <span data-ttu-id="e6b0b-125">Service.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-125">Run the service.exe application.</span></span>  
  
4.  <span data-ttu-id="e6b0b-126">Hizmet başlatıldıktan sonra client.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-126">After the service has started, run the client.exe.</span></span>  
  
5.  <span data-ttu-id="e6b0b-127">İstemci hizmet adresini bilmeden bulamadı gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-127">Observe that the client was able to find the service without knowing its address.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6b0b-128">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6b0b-129">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e6b0b-130">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6b0b-131">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="e6b0b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b0b-132">See also</span></span>
