---
title: Temel Örnek
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 07015c61ccab303d0fe38e65077d984ff40ce357
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045716"
---
# <a name="basic-sample"></a><span data-ttu-id="967a1-102">Temel Örnek</span><span class="sxs-lookup"><span data-stu-id="967a1-102">Basic Sample</span></span>

<span data-ttu-id="967a1-103">Bu örnek, bir hizmetin bulunabilir hale getirme ve keşfedilebilir bir hizmeti nasıl arayılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="967a1-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="967a1-104">Bu örnek iki projeden oluşur: hizmet ve istemci.</span><span class="sxs-lookup"><span data-stu-id="967a1-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="967a1-105">Bu örnek kodda bulma işlemini uygular.</span><span class="sxs-lookup"><span data-stu-id="967a1-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="967a1-106">Yapılandırmada bulmayı uygulayan bir örnek için bkz. [yapılandırma](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="967a1-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>

## <a name="service"></a><span data-ttu-id="967a1-107">Hizmet</span><span class="sxs-lookup"><span data-stu-id="967a1-107">Service</span></span>

<span data-ttu-id="967a1-108">Bu, basit bir Hesaplayıcı hizmet uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="967a1-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="967a1-109">Bulma ile ilgili kod, hizmet ana bilgisayarına `Main` eklenen ve <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki kodda gösterildiği gibi eklenen yerlerde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="967a1-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>

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

## <a name="client"></a><span data-ttu-id="967a1-110">İstemci</span><span class="sxs-lookup"><span data-stu-id="967a1-110">Client</span></span>

<span data-ttu-id="967a1-111">İstemci, hizmetini bulmak <xref:System.ServiceModel.Discovery.DynamicEndpoint> için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="967a1-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="967a1-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>Standart bir uç nokta, istemci açıldığında hizmetin uç noktasını çözer.</span><span class="sxs-lookup"><span data-stu-id="967a1-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="967a1-113">Bu durumda <xref:System.ServiceModel.Discovery.DynamicEndpoint> , hizmet sözleşmesini temel alan hizmeti arar.</span><span class="sxs-lookup"><span data-stu-id="967a1-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="967a1-114">Aramayı varsayılan olarak bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> olarak yapar. <xref:System.ServiceModel.Discovery.DynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="967a1-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="967a1-115">Bir hizmet uç noktası bulduktan sonra istemci, belirtilen bağlama üzerinden bu hizmete bağlanır.</span><span class="sxs-lookup"><span data-stu-id="967a1-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

<span data-ttu-id="967a1-116">İstemci, hizmetleri aramak için `InvokeCalculatorService` <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfını kullanan adlı bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="967a1-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="967a1-117">, <xref:System.ServiceModel.Discovery.DynamicEndpoint> `InvokeCalculatorService` Öğesinden <xref:System.ServiceModel.Description.ServiceEndpoint>devralır, bu nedenle yöntemine geçirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="967a1-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="967a1-118">Örnek daha sonra `CalculatorServiceClient` örneğini oluşturmak <xref:System.ServiceModel.Discovery.DynamicEndpoint> için öğesini kullanır ve hesap makinesi hizmetinin çeşitli işlemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="967a1-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="967a1-119">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="967a1-119">To use this sample</span></span>

1. <span data-ttu-id="967a1-120">Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="967a1-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="967a1-121">Daha fazla bilgi için bkz. [http ve https yapılandırma](https://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="967a1-121">For more information, see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="967a1-122">Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="967a1-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="967a1-123">Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="967a1-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="967a1-124">Visual Studio 2012 kullanarak, Basic. sln ' yi açın ve örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="967a1-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>

3. <span data-ttu-id="967a1-125">Service. exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="967a1-125">Run the service.exe application.</span></span>

4. <span data-ttu-id="967a1-126">Hizmet başladıktan sonra Client. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="967a1-126">After the service has started, run the client.exe.</span></span>

5. <span data-ttu-id="967a1-127">İstemcinin adresini bilmeden hizmeti bulabildiğinin gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="967a1-127">Observe that the client was able to find the service without knowing its address.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="967a1-128">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="967a1-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="967a1-129">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="967a1-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="967a1-130">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="967a1-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="967a1-131">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="967a1-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
