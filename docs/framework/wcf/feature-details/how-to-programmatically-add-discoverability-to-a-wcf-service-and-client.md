---
title: 'Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: c28815d1d208d3e91785a13d95e03c09c0f02ed9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597000"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="956a2-102">Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme</span><span class="sxs-lookup"><span data-stu-id="956a2-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="956a2-103">Bu konuda Windows Communication Foundation (WCF) hizmetinin bulunabilir hale getirme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="956a2-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="956a2-104">Bu, [kendi kendine konak](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="956a2-104">It is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="956a2-105">Mevcut Self-Host hizmet örneğini bulma için yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="956a2-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="956a2-106">Visual Studio 2012 ' de Self-Host çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="956a2-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="956a2-107">Örnek, TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="956a2-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="956a2-108">Hizmet projesine bir başvuru ekleyin `System.ServiceModel.Discovery.dll` .</span><span class="sxs-lookup"><span data-stu-id="956a2-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="956a2-109">"Sistem" iletisini bildiren bir hata iletisi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="956a2-109">You may see an error message saying "System.</span></span> <span data-ttu-id="956a2-110">ServiceModel. Discovery. dll veya bağımlılıklarından biri, .NET Framework projede belirtiden daha yeni bir sürümünü gerektiriyor... " Bu iletiyi görürseniz, Çözüm Gezgini projeye sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="956a2-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="956a2-111">**Proje özellikleri** penceresinde, **hedef Framework 'ün** olduğundan emin olun [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="956a2-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="956a2-112">Service.cs dosyasını açın ve aşağıdaki `using` ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="956a2-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="956a2-113">Yönteminde, `Main()` `using` ifadesinin içinde, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına bir örnek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="956a2-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="956a2-114">, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Uygulandığı hizmetin bulunabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="956a2-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="956a2-115">Öğesini <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekleyen koddan hemen sonra hizmet ana bilgisayarına ekleyin <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .</span><span class="sxs-lookup"><span data-stu-id="956a2-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="956a2-116">Bu kod, bulma iletilerinin standart UDP bulma uç noktasına gönderilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="956a2-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="956a2-117">Hizmeti çağırmak için bulma kullanan bir istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="956a2-117">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="956a2-118">Adlı çözüme yeni bir konsol uygulaması ekleyin `DiscoveryClientApp` .</span><span class="sxs-lookup"><span data-stu-id="956a2-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="956a2-119">Ve için bir başvuru ekleyin `System.ServiceModel.dll``System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="956a2-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="956a2-120">GeneratedClient.cs ve App. config dosyalarını var olan istemci projesinden yeni DiscoveryClientApp projesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="956a2-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="956a2-121">Bunu yapmak için **Çözüm Gezgini**dosyalara sağ tıklayın, **Kopyala**' yı seçin ve ardından **DiscoveryClientApp** projesini seçin, sağ tıklayıp **Yapıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="956a2-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="956a2-122">Program.cs 'i açın.</span><span class="sxs-lookup"><span data-stu-id="956a2-122">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="956a2-123">Aşağıdaki `using` deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="956a2-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="956a2-124">Sınıfına adlı statik bir yöntem ekleyin `FindCalculatorServiceAddress()` `Program` .</span><span class="sxs-lookup"><span data-stu-id="956a2-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="956a2-125">Bu yöntem, hizmeti aramak için bulma kullanır `CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="956a2-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="956a2-126">Yöntemi içinde `FindCalculatorServiceAddress` , <xref:System.ServiceModel.Discovery.DiscoveryClient> oluşturucuya ' a geçirerek yeni bir örnek oluşturun <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="956a2-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="956a2-127">Bu, WCF 'ye, <xref:System.ServiceModel.Discovery.DiscoveryClient> bulma iletilerini göndermek ve almak için standart UDP bulma uç noktası kullanması gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="956a2-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="956a2-128">Sonraki satırda, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemini çağırın ve <xref:System.ServiceModel.Discovery.FindCriteria> aramak istediğiniz hizmet sözleşmesini içeren bir örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="956a2-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="956a2-129">Bu durumda, belirtin `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="956a2-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="956a2-130">' A çağrısından sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , en az bir eşleşen hizmet olup olmadığını ve <xref:System.ServiceModel.EndpointAddress> ilk eşleşen hizmeti döndürmesini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="956a2-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="956a2-131">Aksi takdirde döndürün `null` .</span><span class="sxs-lookup"><span data-stu-id="956a2-131">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="956a2-132">Sınıfına adlı statik bir yöntem ekleyin `InvokeCalculatorService` `Program` .</span><span class="sxs-lookup"><span data-stu-id="956a2-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="956a2-133">Bu yöntem `FindCalculatorServiceAddress` , hesap makinesi hizmetini çağırmak için öğesinden döndürülen uç nokta adresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="956a2-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="956a2-134">Yöntemi içinde `InvokeCalculatorService` , sınıfının bir örneğini oluşturun `CalculatorServiceClient` .</span><span class="sxs-lookup"><span data-stu-id="956a2-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="956a2-135">Bu sınıf, [self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) örneği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="956a2-135">This class is defined by the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span> <span data-ttu-id="956a2-136">Svcutil. exe kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="956a2-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="956a2-137">Sonraki satırda, istemcinin uç nokta adresini, tarafından döndürülen uç nokta adresi olarak ayarlayın `FindCalculatorServiceAddress()` .</span><span class="sxs-lookup"><span data-stu-id="956a2-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="956a2-138">Önceki adıma ait koddan hemen sonra, hesaplayıcı hizmeti tarafından kullanıma sunulan yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="956a2-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="956a2-139">`Main()` `Program` Çağırmak için sınıfındaki yöntemine kod ekleyin `FindCalculatorServiceAddress` .</span><span class="sxs-lookup"><span data-stu-id="956a2-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="956a2-140">Sonraki satırda, ' ı çağırın `InvokeCalculatorService()` ve öğesinden döndürülen uç nokta adresini geçirin `FindCalculatorServiceAddress()` .</span><span class="sxs-lookup"><span data-stu-id="956a2-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="956a2-141">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="956a2-141">To test the application</span></span>  
  
1. <span data-ttu-id="956a2-142">Yükseltilmiş bir komut istemi açın ve Service. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="956a2-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="956a2-143">Bir komut istemi açın ve DiscoveryClientApp. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="956a2-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="956a2-144">Service. exe ' den alınan çıktı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="956a2-144">The output from service.exe should look like the following output.</span></span>  
  
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
  
4. <span data-ttu-id="956a2-145">Discoveryclientapp. exe ' den alınan çıktı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="956a2-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="956a2-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="956a2-146">Example</span></span>  
 <span data-ttu-id="956a2-147">Bu örnek için kodun bir listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="956a2-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="956a2-148">Bu kod, [kendi kendine konak](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) örneğine bağlı olduğundan, yalnızca değiştirilen dosyalar listelenir.</span><span class="sxs-lookup"><span data-stu-id="956a2-148">Because this code is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="956a2-149">Self-Host örneği hakkında daha fazla bilgi için bkz. [Kurulum yönergeleri](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span><span class="sxs-lookup"><span data-stu-id="956a2-149">For more information about the Self-Host sample, see [Setup Instructions](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="956a2-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="956a2-150">See also</span></span>

- [<span data-ttu-id="956a2-151">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="956a2-151">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="956a2-152">WCF Keşif Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="956a2-152">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)
