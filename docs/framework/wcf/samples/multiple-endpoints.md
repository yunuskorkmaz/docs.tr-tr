---
description: 'Daha fazla bilgi edinin: birden fazla uç nokta'
title: Birden Fazla Uç Noktası
ms.date: 03/30/2017
helpviewer_keywords:
- Multiple EndPoints
ms.assetid: 8f0c2e1f-9aee-41c2-8301-c72b7f664412
ms.openlocfilehash: f11110cdc53c6e9a8abc876f0304b144a2d82964
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752255"
---
# <a name="multiple-endpoints"></a><span data-ttu-id="71b32-103">Birden Fazla Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="71b32-103">Multiple Endpoints</span></span>

<span data-ttu-id="71b32-104">Birden çok uç nokta örneği, bir hizmette birden çok uç noktanın nasıl yapılandırılacağını ve bir istemciden gelen her bir uç nokta ile nasıl iletişim kuracağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="71b32-104">The Multiple Endpoints sample demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span> <span data-ttu-id="71b32-105">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="71b32-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="71b32-106">Hizmet yapılandırması, sözleşmeyi destekleyen iki uç nokta tanımlamak üzere değiştirilmiştir `ICalculator` , ancak her biri farklı bir bağlama kullanılarak farklı bir adreste bulunur.</span><span class="sxs-lookup"><span data-stu-id="71b32-106">The service configuration has been modified to define two endpoints that support the `ICalculator` contract, but each at a different address using a different binding.</span></span> <span data-ttu-id="71b32-107">İstemci yapılandırması ve kodu, hizmet uç noktaları ile iletişim kuracak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="71b32-107">The client configuration and code have been modified to communicate with both of the service endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71b32-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="71b32-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="71b32-109">Service Web.config dosyası, her biri aynı sözleşmeyi destekleyen iki uç nokta tanımlamak üzere değiştirilmiştir `ICalculator` , ancak farklı bağlamalar kullanan farklı adreslerdir.</span><span class="sxs-lookup"><span data-stu-id="71b32-109">The service Web.config file has been modified to define two endpoints, each supporting the same `ICalculator` contract, but at different addresses using different bindings.</span></span> <span data-ttu-id="71b32-110">İlk uç nokta, `basicHttpBinding` güvenliği etkinleştirilmemiş olan bağlama kullanılarak temel adreste tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="71b32-110">The first endpoint is defined at the base address using a `basicHttpBinding` binding, which does not have security enabled.</span></span> <span data-ttu-id="71b32-111">İkinci uç nokta, `wsHttpBinding` Windows kimlik doğrulamasıyla WS-Security kullanarak varsayılan olarak güvenli olan bir bağlama kullanılarak {BaseAddress}/Secure konumunda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="71b32-111">The second endpoint is defined at {baseaddress}/secure using a `wsHttpBinding` binding, which is secure by default, using WS-Security with Windows authentication.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- This endpoint is exposed at the base address provided by host:  
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- secure endpoint exposed at {base address}/secure:  
       http://localhost/servicemodelsamples/service.svc/secure -->  
  <endpoint address="secure"  
            binding="wsHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="71b32-112">Ayrıca, istemci üzerinde her iki uç nokta de yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="71b32-112">Both endpoints are also configured on the client.</span></span> <span data-ttu-id="71b32-113">Bu uç noktalara, çağıranın istenen uç nokta adını istemcinin oluşturucusuna geçirebilmesi için adlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="71b32-113">These endpoints are given names so that the caller can pass the desired endpoint name into the constructor of the client.</span></span>  
  
```xml  
<client>  
  <!-- Passing "basic" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="basic"  
            address="http://localhost/servicemodelsamples/service.svc"
            binding="basicHttpBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- Passing "secure" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="secure"  
            address="http://localhost/servicemodelsamples/service.svc/secure"
            binding="wsHttpBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="71b32-114">İstemci aşağıdaki kodda gösterildiği gibi her iki uç noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="71b32-114">The client uses both endpoints as shown in the following code.</span></span>  
  
```csharp  
static void Main()  
{  
    // Create a client to the basic endpoint configuration.  
    CalculatorClient client = new CalculatorClient("basic");  
    Console.WriteLine("Communicate with basic endpoint.");  
    // call operations  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    // Create a client to the secure endpoint configuration.  
    client = new CalculatorClient("secure");  
    Console.WriteLine("Communicate with secure endpoint.");  
    // Call operations.  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="71b32-115">İstemcisini çalıştırdığınızda her iki uç nokta içeren etkileşimler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="71b32-115">When you run the client, interactions with both endpoints are displayed.</span></span>  
  
```console
Communicate with basic endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Communicate with secure endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71b32-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="71b32-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="71b32-117">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="71b32-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="71b32-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="71b32-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="71b32-119">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="71b32-119">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="71b32-120">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="71b32-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="71b32-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="71b32-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="71b32-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="71b32-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71b32-123">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="71b32-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpoints`  
