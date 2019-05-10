---
title: "Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme"
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: 053ace300610cd4129c4541f4e2658ac8d09da85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626979"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="be6ac-102">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="be6ac-102">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>
<span data-ttu-id="be6ac-103">Bu konuda, Keşif proxy'si uygulama anlatılmaktadır dört konuları saniyedir.</span><span class="sxs-lookup"><span data-stu-id="be6ac-103">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="be6ac-104">Önceki konu [nasıl yapılır: Keşif proxy'si uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), Keşif proxy'si uygulanır.</span><span class="sxs-lookup"><span data-stu-id="be6ac-104">In the previous topic, [How to: Implement a Discovery Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="be6ac-105">Bu konu başlığında, duyuru iletiler gönderen bir WCF hizmeti oluşturma (`Hello` ve `Bye`) kaydetmek ve kendisi ile keşif proxy'si kaydını silmek keşif proxy'si için neden olur.</span><span class="sxs-lookup"><span data-stu-id="be6ac-105">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>

### <a name="to-define-the-service-contract"></a><span data-ttu-id="be6ac-106">Hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="be6ac-106">To define the service contract</span></span>

1. <span data-ttu-id="be6ac-107">Yeni bir konsol uygulama projesi Ekle `DiscoveryProxyExample` adlı çözüm `Service`.</span><span class="sxs-lookup"><span data-stu-id="be6ac-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>

2. <span data-ttu-id="be6ac-108">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="be6ac-108">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="be6ac-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be6ac-109">System.ServiceModel</span></span>

    2. <span data-ttu-id="be6ac-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="be6ac-110">System.ServiceModel.Discovery</span></span>

3. <span data-ttu-id="be6ac-111">Adlı projeye yeni bir sınıf ekleyin `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="be6ac-111">Add a new class to the project called `CalculatorService`.</span></span>

4. <span data-ttu-id="be6ac-112">Aşağıdaki using deyimlerini.</span><span class="sxs-lookup"><span data-stu-id="be6ac-112">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    ```

5. <span data-ttu-id="be6ac-113">CalculatorService.cs içinde hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="be6ac-113">Within CalculatorService.cs, define the service contract.</span></span>

    ```csharp
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
    ```

6. <span data-ttu-id="be6ac-114">Ayrıca CalculatorService.cs içinde hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="be6ac-114">Also within CalculatorService.cs, implement the service contract.</span></span>

    ```csharp
    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
    ```

### <a name="to-host-the-service"></a><span data-ttu-id="be6ac-115">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="be6ac-115">To host the service</span></span>

1. <span data-ttu-id="be6ac-116">Projeyi oluşturduğunuzda oluşturulan Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="be6ac-116">Open the Program.cs file that was generated when you created the project.</span></span>

2. <span data-ttu-id="be6ac-117">Aşağıdaki using deyimlerini.</span><span class="sxs-lookup"><span data-stu-id="be6ac-117">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="be6ac-118">İçinde `Main()` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="be6ac-118">Within the `Main()` method, add the following code:</span></span>

    ```csharp
    // Define the base address of the service
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
    // Define the endpoint address where announcement messages will be sent
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Create the service host
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
    try
    {
        // Add a service endpoint
        ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
            new NetTcpBinding(), string.Empty);

        // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
            new EndpointAddress(announcementEndpointAddress));

        // Create a ServiceDiscoveryBehavior and add the announcement endpoint
        ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
        serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

        // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable
        serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

        // Start listening for messages
        serviceHost.Open();

        Console.WriteLine("Calculator Service started at {0}", baseAddress);
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        serviceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (serviceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        serviceHost.Abort();
    }
    ```

<span data-ttu-id="be6ac-119">Kayıtlı bir bulunabilir hizmet uygulama tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="be6ac-119">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="be6ac-120">Geçin [nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="be6ac-120">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).</span></span>

## <a name="example"></a><span data-ttu-id="be6ac-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="be6ac-121">Example</span></span>
 <span data-ttu-id="be6ac-122">Bu konu başlığında kullanılan kod tam listesi budur.</span><span class="sxs-lookup"><span data-stu-id="be6ac-122">This is the full listing of the code used in this topic.</span></span>

```csharp
// CalculatorService.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;

namespace Microsoft.Samples.Discovery
{
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }

    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
  
        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
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
using System.ServiceModel;
using System.ServiceModel.Description;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
            try
            {
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
                    new NetTcpBinding(), string.Empty);

                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
                    new EndpointAddress(announcementEndpointAddress));

                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

                // Make the service discoverable
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

                serviceHost.Open();

                Console.WriteLine("Calculator Service started at {0}", baseAddress);
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                serviceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (serviceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                serviceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="be6ac-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be6ac-123">See also</span></span>

- [<span data-ttu-id="be6ac-124">WCF Bulma</span><span class="sxs-lookup"><span data-stu-id="be6ac-124">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [<span data-ttu-id="be6ac-125">Nasıl yapılır: Keşif proxy'si uygulama</span><span class="sxs-lookup"><span data-stu-id="be6ac-125">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="be6ac-126">Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama</span><span class="sxs-lookup"><span data-stu-id="be6ac-126">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
