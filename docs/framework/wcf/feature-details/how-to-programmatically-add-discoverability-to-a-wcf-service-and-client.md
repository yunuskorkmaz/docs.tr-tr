---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: program aracılığıyla bir WCF hizmeti ve Istemcisine bulunabilirliği ekleme'
title: 'Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: ad192c6fcc57a36d7001f230c98b1193c42262aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793720"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="60c47-103">Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme</span><span class="sxs-lookup"><span data-stu-id="60c47-103">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>

<span data-ttu-id="60c47-104">Bu konuda Windows Communication Foundation (WCF) hizmetinin bulunabilir hale getirme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60c47-104">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="60c47-105">Bu, [kendi kendine konak](../samples/self-host.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="60c47-105">It is based on the [Self-Host](../samples/self-host.md) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="60c47-106">Mevcut Self-Host hizmet örneğini bulma için yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="60c47-106">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="60c47-107">Visual Studio 2012 ' de Self-Host çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="60c47-107">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="60c47-108">Örnek, TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="60c47-108">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="60c47-109">Hizmet projesine bir başvuru ekleyin `System.ServiceModel.Discovery.dll` .</span><span class="sxs-lookup"><span data-stu-id="60c47-109">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="60c47-110">"Sistem" iletisini bildiren bir hata iletisi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c47-110">You may see an error message saying "System.</span></span> <span data-ttu-id="60c47-111">ServiceModel.Discovery.dll veya bağımlılıklarından biri, .NET Framework projede belirtilenden daha sonraki bir sürümü gerektiriyor... " Bu iletiyi görürseniz, Çözüm Gezgini projeye sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="60c47-111">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="60c47-112">**Proje özellikleri** penceresinde, **hedef Framework 'ün** olduğundan emin olun [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="60c47-112">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="60c47-113">Service.cs dosyasını açın ve aşağıdaki `using` ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60c47-113">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="60c47-114">Yönteminde, `Main()` `using` ifadesinin içinde, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına bir örnek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60c47-114">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
  
            // ...  
        }  
    }  
    ```  
  
     <span data-ttu-id="60c47-115">, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Uygulandığı hizmetin bulunabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c47-115">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="60c47-116">Öğesini <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekleyen koddan hemen sonra hizmet ana bilgisayarına ekleyin <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .</span><span class="sxs-lookup"><span data-stu-id="60c47-116">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="60c47-117">Bu kod, bulma iletilerinin standart UDP bulma uç noktasına gönderilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c47-117">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="60c47-118">Hizmeti çağırmak için bulma kullanan bir istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="60c47-118">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="60c47-119">Adlı çözüme yeni bir konsol uygulaması ekleyin `DiscoveryClientApp` .</span><span class="sxs-lookup"><span data-stu-id="60c47-119">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="60c47-120">Ve için bir başvuru ekleyin `System.ServiceModel.dll``System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="60c47-120">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="60c47-121">GeneratedClient.cs ve App.config dosyalarını var olan istemci projesinden yeni DiscoveryClientApp projesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="60c47-121">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="60c47-122">Bunu yapmak için **Çözüm Gezgini** dosyalara sağ tıklayın, **Kopyala**' yı seçin ve ardından **DiscoveryClientApp** projesini seçin, sağ tıklayıp **Yapıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="60c47-122">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="60c47-123">Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="60c47-123">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="60c47-124">Aşağıdaki `using` deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60c47-124">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="60c47-125">Sınıfına adlı statik bir yöntem ekleyin `FindCalculatorServiceAddress()` `Program` .</span><span class="sxs-lookup"><span data-stu-id="60c47-125">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="60c47-126">Bu yöntem, hizmeti aramak için bulma kullanır `CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="60c47-126">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="60c47-127">Yöntemi içinde `FindCalculatorServiceAddress` , <xref:System.ServiceModel.Discovery.DiscoveryClient> oluşturucuya ' a geçirerek yeni bir örnek oluşturun <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="60c47-127">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="60c47-128">Bu, WCF 'ye, <xref:System.ServiceModel.Discovery.DiscoveryClient> bulma iletilerini göndermek ve almak için standart UDP bulma uç noktası kullanması gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="60c47-128">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="60c47-129">Sonraki satırda, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemini çağırın ve <xref:System.ServiceModel.Discovery.FindCriteria> aramak istediğiniz hizmet sözleşmesini içeren bir örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="60c47-129">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="60c47-130">Bu durumda, belirtin `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="60c47-130">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="60c47-131">' A çağrısından sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , en az bir eşleşen hizmet olup olmadığını ve <xref:System.ServiceModel.EndpointAddress> ilk eşleşen hizmeti döndürmesini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="60c47-131">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="60c47-132">Aksi takdirde döndürün `null` .</span><span class="sxs-lookup"><span data-stu-id="60c47-132">Otherwise return `null`.</span></span>  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. <span data-ttu-id="60c47-133">Sınıfına adlı statik bir yöntem ekleyin `InvokeCalculatorService` `Program` .</span><span class="sxs-lookup"><span data-stu-id="60c47-133">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="60c47-134">Bu yöntem `FindCalculatorServiceAddress` , hesap makinesi hizmetini çağırmak için öğesinden döndürülen uç nokta adresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="60c47-134">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="60c47-135">Yöntemi içinde `InvokeCalculatorService` , sınıfının bir örneğini oluşturun `CalculatorServiceClient` .</span><span class="sxs-lookup"><span data-stu-id="60c47-135">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="60c47-136">Bu sınıf, [self-Host](../samples/self-host.md) örneği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="60c47-136">This class is defined by the [Self-Host](../samples/self-host.md) sample.</span></span> <span data-ttu-id="60c47-137">Svcutil.exe kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="60c47-137">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="60c47-138">Sonraki satırda, istemcinin uç nokta adresini, tarafından döndürülen uç nokta adresi olarak ayarlayın `FindCalculatorServiceAddress()` .</span><span class="sxs-lookup"><span data-stu-id="60c47-138">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="60c47-139">Önceki adıma ait koddan hemen sonra, hesaplayıcı hizmeti tarafından kullanıma sunulan yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="60c47-139">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
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
    ```  
  
14. <span data-ttu-id="60c47-140">`Main()` `Program` Çağırmak için sınıfındaki yöntemine kod ekleyin `FindCalculatorServiceAddress` .</span><span class="sxs-lookup"><span data-stu-id="60c47-140">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="60c47-141">Sonraki satırda, ' ı çağırın `InvokeCalculatorService()` ve öğesinden döndürülen uç nokta adresini geçirin `FindCalculatorServiceAddress()` .</span><span class="sxs-lookup"><span data-stu-id="60c47-141">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="60c47-142">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="60c47-142">To test the application</span></span>  
  
1. <span data-ttu-id="60c47-143">Yükseltilmiş bir komut istemi açın ve Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="60c47-143">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="60c47-144">Bir komut istemi açın ve Discoveryclientapp.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="60c47-144">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="60c47-145">service.exe çıkışı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="60c47-145">The output from service.exe should look like the following output.</span></span>  
  
    ```output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4. <span data-ttu-id="60c47-146">Discoveryclientapp.exe çıkışı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="60c47-146">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="60c47-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="60c47-147">Example</span></span>  

 <span data-ttu-id="60c47-148">Bu örnek için kodun bir listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="60c47-148">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="60c47-149">Bu kod, [kendi kendine konak](../samples/self-host.md) örneğine bağlı olduğundan, yalnızca değiştirilen dosyalar listelenir.</span><span class="sxs-lookup"><span data-stu-id="60c47-149">Because this code is based on the [Self-Host](../samples/self-host.md) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="60c47-150">Self-Host örneği hakkında daha fazla bilgi için bkz. [Kurulum yönergeleri](../samples/set-up-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="60c47-150">For more information about the Self-Host sample, see [Setup Instructions](../samples/set-up-instructions.md).</span></span>  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
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
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="60c47-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60c47-151">See also</span></span>

- [<span data-ttu-id="60c47-152">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="60c47-152">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="60c47-153">WCF Keşif Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="60c47-153">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)
