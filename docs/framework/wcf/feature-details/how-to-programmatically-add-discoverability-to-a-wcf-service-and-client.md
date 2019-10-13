---
title: 'Nasıl yapılır: bir WCF hizmeti ve Istemcisine program aracılığıyla bulunabilirliği ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: a139eb4a15486be329bc6853ee6b3a3be06b0619
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291565"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="b10de-102">Nasıl yapılır: bir WCF hizmeti ve Istemcisine program aracılığıyla bulunabilirliği ekleme</span><span class="sxs-lookup"><span data-stu-id="b10de-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="b10de-103">Bu konuda Windows Communication Foundation (WCF) hizmetinin bulunabilir hale getirme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b10de-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="b10de-104">Bu, [kendi kendine konak](https://go.microsoft.com/fwlink/?LinkId=145523) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="b10de-104">It is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="b10de-105">Mevcut Self-Host hizmet örneğini bulma için yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b10de-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="b10de-106">Visual Studio 2012 ' de Self-Host çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="b10de-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="b10de-107">Örnek, TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b10de-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="b10de-108">Hizmet projesine `System.ServiceModel.Discovery.dll` ' a bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="b10de-109">"Sistem" iletisini bildiren bir hata iletisi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b10de-109">You may see an error message saying "System.</span></span> <span data-ttu-id="b10de-110">ServiceModel. Discovery. dll veya bağımlılıklarından biri, .NET Framework projede belirtiden daha yeni bir sürümünü gerektiriyor... " Bu iletiyi görürseniz, Çözüm Gezgini projeye sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b10de-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="b10de-111">**Proje özellikleri** penceresinde, **hedef Framework 'ün** [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b10de-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="b10de-112">Service.cs dosyasını açın ve aşağıdaki `using` ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="b10de-113">@No__t-0 yönteminde, `using` ifadesinin içinde hizmet ana bilgisayarına bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> örneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="b10de-114">@No__t-0, uygulandığı hizmetin bulunabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b10de-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="b10de-115">@No__t-1 ' i ekleyen koddan hemen sonra hizmet ana bilgisayarına <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="b10de-116">Bu kod, bulma iletilerinin standart UDP bulma uç noktasına gönderilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b10de-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="b10de-117">Hizmeti çağırmak için bulma kullanan bir istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b10de-117">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="b10de-118">@No__t-0 adlı çözüme yeni bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="b10de-119">@No__t-0 ve `System.ServiceModel.Discovery.dll` öğesine bir başvuru ekleyin</span><span class="sxs-lookup"><span data-stu-id="b10de-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="b10de-120">GeneratedClient.cs ve App. config dosyalarını var olan istemci projesinden yeni DiscoveryClientApp projesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b10de-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="b10de-121">Bunu yapmak için **Çözüm Gezgini**dosyalara sağ tıklayın, **Kopyala**' yı seçin ve ardından **DiscoveryClientApp** projesini seçin, sağ tıklayıp **Yapıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b10de-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="b10de-122">Program.cs 'i açın.</span><span class="sxs-lookup"><span data-stu-id="b10de-122">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="b10de-123">Aşağıdaki `using` deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="b10de-124">@No__t-1 sınıfına `FindCalculatorServiceAddress()` adlı bir statik yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="b10de-125">Bu yöntem `CalculatorService` hizmetini aramak için bulma kullanır.</span><span class="sxs-lookup"><span data-stu-id="b10de-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="b10de-126">@No__t-0 yönteminde, oluşturucuya bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> geçirerek yeni bir <xref:System.ServiceModel.Discovery.DiscoveryClient> örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b10de-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="b10de-127">Bu, WCF 'ye <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfının bulma iletilerini göndermek ve almak için standart UDP bulma uç noktasını kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b10de-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="b10de-128">Sonraki satırda <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemini çağırın ve aramak istediğiniz hizmet sözleşmesini içeren bir <xref:System.ServiceModel.Discovery.FindCriteria> örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="b10de-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="b10de-129">Bu durumda `ICalculator` belirtin.</span><span class="sxs-lookup"><span data-stu-id="b10de-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="b10de-130">@No__t-0 ' a çağrıdan sonra, en az bir eşleşen hizmet olup olmadığını denetleyin ve ilk eşleşen hizmetin <xref:System.ServiceModel.EndpointAddress> ' i döndürün.</span><span class="sxs-lookup"><span data-stu-id="b10de-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="b10de-131">Aksi takdirde `null` döndürün.</span><span class="sxs-lookup"><span data-stu-id="b10de-131">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="b10de-132">@No__t-1 sınıfına `InvokeCalculatorService` adlı bir statik yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="b10de-133">Bu yöntem, hesaplayıcı hizmetini çağırmak için `FindCalculatorServiceAddress` ' dan döndürülen uç nokta adresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b10de-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="b10de-134">@No__t-0 yönteminin içinde, `CalculatorServiceClient` sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b10de-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="b10de-135">Bu sınıf, [self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) örneği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b10de-135">This class is defined by the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="b10de-136">Svcutil. exe kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b10de-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="b10de-137">Sonraki satırda, istemcinin uç nokta adresini `FindCalculatorServiceAddress()` ' dan döndürülen uç nokta adresi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b10de-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="b10de-138">Önceki adıma ait koddan hemen sonra, hesaplayıcı hizmeti tarafından kullanıma sunulan yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="b10de-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="b10de-139">@No__t-2 ' i çağırmak için `Program` sınıfındaki `Main()` yöntemine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b10de-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="b10de-140">Sonraki satırda, `InvokeCalculatorService()` ' ı çağırın ve `FindCalculatorServiceAddress()` ' den döndürülen uç nokta adresini geçirin.</span><span class="sxs-lookup"><span data-stu-id="b10de-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="b10de-141">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="b10de-141">To test the application</span></span>  
  
1. <span data-ttu-id="b10de-142">Yükseltilmiş bir komut istemi açın ve Service. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b10de-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="b10de-143">Bir komut istemi açın ve DiscoveryClientApp. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b10de-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="b10de-144">Service. exe ' den alınan çıktı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="b10de-144">The output from service.exe should look like the following output.</span></span>  
  
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
  
4. <span data-ttu-id="b10de-145">Discoveryclientapp. exe ' den alınan çıktı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="b10de-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="b10de-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="b10de-146">Example</span></span>  
 <span data-ttu-id="b10de-147">Bu örnek için kodun bir listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b10de-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="b10de-148">Bu kod, [kendi kendine konak](https://go.microsoft.com/fwlink/?LinkId=145523) örneğine bağlı olduğundan, yalnızca değiştirilen dosyalar listelenir.</span><span class="sxs-lookup"><span data-stu-id="b10de-148">Because this code is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="b10de-149">Self-Host örneği hakkında daha fazla bilgi için bkz. [Kurulum yönergeleri](https://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="b10de-149">For more information about the Self-Host sample, see [Setup Instructions](https://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="b10de-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b10de-150">See also</span></span>

- [<span data-ttu-id="b10de-151">WCF bulmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="b10de-151">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="b10de-152">WCF bulma nesne modeli</span><span class="sxs-lookup"><span data-stu-id="b10de-152">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
