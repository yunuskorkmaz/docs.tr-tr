---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: hizmet bulmak için keşif proxy 'Si kullanan bir Istemci uygulaması uygulama"
title: "Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma"
ms.date: 03/30/2017
ms.assetid: 62b41a75-cf40-4c52-a842-a5f1c70e247f
ms.openlocfilehash: 316e7f446e497cb1d3de806043c7ba4f9a8659d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743635"
---
# <a name="how-to-implement-a-client-application-that-uses-the-discovery-proxy-to-find-a-service"></a><span data-ttu-id="c7b55-103">Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="c7b55-103">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>

<span data-ttu-id="c7b55-104">Bu konu, bulma proxy 'nin nasıl uygulanacağını ele alan üçüncü üç konudan oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7b55-104">This topic is the third of three topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="c7b55-105">Önceki konu başlığında, [nasıl yapılır: bulma proxy 'Sine kaydolduktan sonra keşfedilebilir bir hizmeti uygulama](discoverable-service-that-registers-with-the-discovery-proxy.md), kendisini bulma proxy 'sine KAYDEDEN bir WCF hizmeti uyguladık.</span><span class="sxs-lookup"><span data-stu-id="c7b55-105">In the previous topic, [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](discoverable-service-that-registers-with-the-discovery-proxy.md), you implemented a WCF service that registers itself with the discovery proxy.</span></span> <span data-ttu-id="c7b55-106">Bu konuda, WCF hizmetini bulmak için keşif proxy 'sini kullanan bir WCF istemcisi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c7b55-106">In this topic you create a WCF client that uses the discovery proxy to find the WCF service.</span></span>  
  
### <a name="implement-the-client"></a><span data-ttu-id="c7b55-107">İstemciyi uygulama</span><span class="sxs-lookup"><span data-stu-id="c7b55-107">Implement the client</span></span>  
  
1. <span data-ttu-id="c7b55-108">Adlı çözüme yeni bir konsol uygulama projesi ekleyin `DiscoveryProxyExample` `Client` .</span><span class="sxs-lookup"><span data-stu-id="c7b55-108">Add a new console application project to the `DiscoveryProxyExample` solution called `Client`.</span></span>  
  
2. <span data-ttu-id="c7b55-109">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7b55-109">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="c7b55-110">System. ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c7b55-110">System.ServiceModel</span></span>  
  
    2. <span data-ttu-id="c7b55-111">System. ServiceModel. Discovery</span><span class="sxs-lookup"><span data-stu-id="c7b55-111">System.ServiceModel.Discovery</span></span>  
  
3. <span data-ttu-id="c7b55-112">Bu konunun en altında bulunan GeneratedClient.cs ' i projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7b55-112">Add the GeneratedClient.cs found at the bottom of this topic to the project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c7b55-113">Bu dosya genellikle Svcutil.exe gibi bir araç kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c7b55-113">This file is usually generated using a tool such as Svcutil.exe.</span></span> <span data-ttu-id="c7b55-114">Bu, görevi basitleştirmek için bu konuda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7b55-114">It is provided in this topic to simplify the task.</span></span>  
  
4. <span data-ttu-id="c7b55-115">Program.cs dosyasını açın ve aşağıdaki yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7b55-115">Open the Program.cs file and add the following method.</span></span> <span data-ttu-id="c7b55-116">Bu yöntem bir uç nokta adresi alır ve hizmet istemcisini (proxy) başlatmak için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7b55-116">This method takes an endpoint address and uses it to initialize the service client (proxy).</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
        // Create a client  
        CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
        Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
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

        // Closing the client gracefully closes the connection and cleans up resources  
        client.Close();  
    }  
    ```  
  
5. <span data-ttu-id="c7b55-117">`Main` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7b55-117">Add the following code to the `Main` method.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
        Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  

        // Create a DiscoveryClient passing in the discovery endpoint  
        DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  

        Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
        Console.WriteLine();  

        try  
        {  
            // Search for services that implement ICalculatorService
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  

            Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
            Console.WriteLine();  

            // Check to see if endpoints were found, if so then invoke the service.  
            if (findResponse.Endpoints.Count > 0)  
            {  
                InvokeCalculatorService(findResponse.Endpoints[0].Address);  
            }  
        }  
        catch (TargetInvocationException)  
        {  
            Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
        }  

        Console.WriteLine("Press <ENTER> to exit.");  
        Console.ReadLine();  
    }  
    ```  
  
 <span data-ttu-id="c7b55-118">İstemci uygulamasını uygulamayı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="c7b55-118">You have completed implementing the client application.</span></span> <span data-ttu-id="c7b55-119">[Nasıl yapılır: keşif proxy 'Sini test etme](how-to-test-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="c7b55-119">Continue on to [How to: Test the Discovery Proxy](how-to-test-the-discovery-proxy.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7b55-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7b55-120">Example</span></span>  

 <span data-ttu-id="c7b55-121">Bu, bu konunun tam kod listesidir.</span><span class="sxs-lookup"><span data-stu-id="c7b55-121">This is the full code listing for this topic.</span></span>  
  
```csharp  
// GeneratedClient.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1434  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace Microsoft.Samples.Discovery  
{  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    [System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.Samples.Discovery", ConfigurationName = "ICalculatorService")]  
    public interface ICalculatorService  
    {  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Add", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/AddResponse")]  
        double Add(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Subtract", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/SubtractResponse")]  
        double Subtract(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Multiply", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/MultiplyResponse")]  
        double Multiply(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Divide", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/DivideResponse")]  
        double Divide(double n1, double n2);  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public interface ICalculatorServiceChannel : ICalculatorService, System.ServiceModel.IClientChannel  
    {  
    }  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public partial class CalculatorServiceClient : System.ServiceModel.ClientBase<ICalculatorService>, ICalculatorService  
    {  
  
        public CalculatorServiceClient()  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName) :  
            base(endpointConfigurationName)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, string remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(binding, remoteAddress)  
        {  
        }  
  
        public double Add(double n1, double n2)  
        {  
            return base.Channel.Add(n1, n2);  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            return base.Channel.Subtract(n1, n2);  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            return base.Channel.Multiply(n1, n2);  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            return base.Channel.Divide(n1, n2);  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Reflection;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Client  
    {  
        public static void Main()  
        {  
            // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
            DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
  
            DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  
  
            Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
            Console.WriteLine();  
  
            try  
            {  
                // Find ICalculatorService endpoints
                FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  
  
                Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
                Console.WriteLine();  
  
                // Check to see if endpoints were found, if so then invoke the service.  
                if (findResponse.Endpoints.Count > 0)  
                {  
                    InvokeCalculatorService(findResponse.Endpoints[0].Address);  
                }  
            }  
            catch (TargetInvocationException)  
            {  
                Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
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
  
            // Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7b55-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7b55-122">See also</span></span>

- [<span data-ttu-id="c7b55-123">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c7b55-123">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="c7b55-124">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="c7b55-124">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="c7b55-125">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="c7b55-125">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
