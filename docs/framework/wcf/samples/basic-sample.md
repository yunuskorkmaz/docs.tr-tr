---
title: Temel Örnek
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: db560ec7dea3912ecec8d84943cc9a01512d1f33
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575777"
---
# <a name="basic-sample"></a><span data-ttu-id="026da-102">Temel Örnek</span><span class="sxs-lookup"><span data-stu-id="026da-102">Basic Sample</span></span>

<span data-ttu-id="026da-103">Bu örnek, bir hizmetin bulunabilir hale getirme ve keşfedilebilir bir hizmeti nasıl arayılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="026da-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="026da-104">Bu örnek iki projeden oluşur: hizmet ve istemci.</span><span class="sxs-lookup"><span data-stu-id="026da-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="026da-105">Bu örnek kodda bulma işlemini uygular.</span><span class="sxs-lookup"><span data-stu-id="026da-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="026da-106">Yapılandırmada bulmayı uygulayan bir örnek için bkz. [yapılandırma](configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="026da-106">For a sample that implements discovery in configuration, see [Configuration](configuration-sample.md).</span></span>

## <a name="service"></a><span data-ttu-id="026da-107">Hizmet</span><span class="sxs-lookup"><span data-stu-id="026da-107">Service</span></span>

<span data-ttu-id="026da-108">Bu, basit bir Hesaplayıcı hizmet uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="026da-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="026da-109">Bulma ile ilgili kod, `Main` <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına eklenen ve <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki kodda gösterildiği gibi eklenen yerlerde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="026da-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>

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

## <a name="client"></a><span data-ttu-id="026da-110">İstemci</span><span class="sxs-lookup"><span data-stu-id="026da-110">Client</span></span>

<span data-ttu-id="026da-111">İstemci <xref:System.ServiceModel.Discovery.DynamicEndpoint> , hizmetini bulmak için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="026da-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="026da-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>Standart bir uç nokta, istemci açıldığında hizmetin uç noktasını çözer.</span><span class="sxs-lookup"><span data-stu-id="026da-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="026da-113">Bu durumda, hizmet <xref:System.ServiceModel.Discovery.DynamicEndpoint> sözleşmesini temel alan hizmeti arar.</span><span class="sxs-lookup"><span data-stu-id="026da-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="026da-114"><xref:System.ServiceModel.Discovery.DynamicEndpoint>Aramayı <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Varsayılan olarak bir olarak yapar.</span><span class="sxs-lookup"><span data-stu-id="026da-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="026da-115">Bir hizmet uç noktası bulduktan sonra istemci, belirtilen bağlama üzerinden bu hizmete bağlanır.</span><span class="sxs-lookup"><span data-stu-id="026da-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

<span data-ttu-id="026da-116">İstemci, `InvokeCalculatorService` <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri aramak için sınıfını kullanan adlı bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="026da-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="026da-117">, <xref:System.ServiceModel.Discovery.DynamicEndpoint> Öğesinden devralır <xref:System.ServiceModel.Description.ServiceEndpoint> , bu nedenle yöntemine geçirilebilirler `InvokeCalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="026da-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="026da-118">Örnek daha sonra <xref:System.ServiceModel.Discovery.DynamicEndpoint> örneğini oluşturmak için öğesini kullanır `CalculatorServiceClient` ve hesap makinesi hizmetinin çeşitli işlemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="026da-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="026da-119">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="026da-119">To use this sample</span></span>

1. <span data-ttu-id="026da-120">Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="026da-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="026da-121">Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="026da-121">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="026da-122">Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="026da-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="026da-123">Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="026da-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="026da-124">Visual Studio 2012 kullanarak, Basic. sln ' yi açın ve örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="026da-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>

3. <span data-ttu-id="026da-125">Service. exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="026da-125">Run the service.exe application.</span></span>

4. <span data-ttu-id="026da-126">Hizmet başladıktan sonra Client. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="026da-126">After the service has started, run the client.exe.</span></span>

5. <span data-ttu-id="026da-127">İstemcinin adresini bilmeden hizmeti bulabildiğinin gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="026da-127">Observe that the client was able to find the service without knowing its address.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="026da-128">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="026da-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="026da-129">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="026da-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="026da-130">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="026da-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="026da-131">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="026da-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
