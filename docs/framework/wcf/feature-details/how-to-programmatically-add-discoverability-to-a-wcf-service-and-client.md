---
title: 'Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: 407777b1545fb12eb3ed1787fdba86991c894fdb
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838461"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="d7475-102">Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme</span><span class="sxs-lookup"><span data-stu-id="d7475-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="d7475-103">Bu konuda, bir Windows Communication Foundation (WCF) hizmeti bulunabilir hale açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7475-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="d7475-104">Dayanır [barındırma](https://go.microsoft.com/fwlink/?LinkId=145523) örnek.</span><span class="sxs-lookup"><span data-stu-id="d7475-104">It is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="d7475-105">Bulma için var olan barındırılan hizmet örneği yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d7475-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1.  <span data-ttu-id="d7475-106">Barındırma çözümü Visual Studio 2012'de açın.</span><span class="sxs-lookup"><span data-stu-id="d7475-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="d7475-107">Örnek TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d7475-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2.  <span data-ttu-id="d7475-108">Bir başvuru ekleyin `System.ServiceModel.Discovery.dll` hizmet projesi için.</span><span class="sxs-lookup"><span data-stu-id="d7475-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="d7475-109">"Sistemi. hata mesajını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7475-109">You may see an error message saying "System.</span></span> <span data-ttu-id="d7475-110">ServiceModel.Discovery.dll veya bağımlılıklarından biri daha sonraki bir sürümü gerektirir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] belirtilenden projede... " Bu iletiyi görürseniz, Çözüm Gezgini'nde projeye sağ tıklayıp seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d7475-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="d7475-111">İçinde **proje özellikleri** penceresinde emin **hedef Framework'ü** olan [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7475-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3.  <span data-ttu-id="d7475-112">Adını da dosyasını açın ve aşağıdakileri ekleyin `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d7475-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  <span data-ttu-id="d7475-113">İçinde `Main()` yöntemi, iç `using` deyimi ekleyin bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> örneğine hizmet ana bilgisayarı.</span><span class="sxs-lookup"><span data-stu-id="d7475-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="d7475-114"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Uygulanmış şekilde hizmet bulunabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7475-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5.  <span data-ttu-id="d7475-115">Ekleme bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekler kodundan hemen sonra hizmet ana bilgisayarı için <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d7475-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="d7475-116">Bu kod, standart UDP bulma uç noktası için bulma ileti gönderilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7475-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="d7475-117">Bulma hizmeti çağırmak amacıyla kullanan bir istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d7475-117">To create a client application that uses discovery to call the service</span></span>  
  
1.  <span data-ttu-id="d7475-118">Adlı bir çözüm için yeni bir konsol uygulaması Ekle `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="d7475-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2.  <span data-ttu-id="d7475-119">Bir başvuru ekleyin `System.ServiceModel.dll` ve `System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="d7475-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3.  <span data-ttu-id="d7475-120">GeneratedClient.cs ve App.config dosyaları var olan istemci projeden DiscoveryClientApp yeni projeye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d7475-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="d7475-121">Bunu yapmak için dosyaları sağ **Çözüm Gezgini**seçin **kopyalama**ve ardından **DiscoveryClientApp** proje için sağ tıklayın ve seçin**Yapıştır**.</span><span class="sxs-lookup"><span data-stu-id="d7475-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4.  <span data-ttu-id="d7475-122">Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d7475-122">Open Program.cs.</span></span>  
  
5.  <span data-ttu-id="d7475-123">Aşağıdaki `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="d7475-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  <span data-ttu-id="d7475-124">Adlı statik bir yöntem ekleyin `FindCalculatorServiceAddress()` için `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d7475-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="d7475-125">Bu yöntem, aranacak bulma kullanır. `CalculatorService` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="d7475-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7.  <span data-ttu-id="d7475-126">İçinde `FindCalculatorServiceAddress` yöntemi, yeni bir <xref:System.ServiceModel.Discovery.DiscoveryClient> örneği öğesinde geçen bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="d7475-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="d7475-127">Bu, WCF bildirir <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfı bulma ileti göndermek ve almak için standart UDP bulma uç noktası kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7475-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8.  <span data-ttu-id="d7475-128">Sonraki satırda çağrı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi belirtin bir <xref:System.ServiceModel.Discovery.FindCriteria> aramak istediğiniz hizmet sözleşmesi içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="d7475-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="d7475-129">Bu durumda, belirtin `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="d7475-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="d7475-130">Çağrısından sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, eşleşen en az bir hizmet olup olmadığını denetleyin ve dönüş <xref:System.ServiceModel.EndpointAddress> ilk eşleşen servis.</span><span class="sxs-lookup"><span data-stu-id="d7475-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="d7475-131">Aksi takdirde dönüş `null`.</span><span class="sxs-lookup"><span data-stu-id="d7475-131">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="d7475-132">Adlı statik bir yöntem ekleyin `InvokeCalculatorService` için `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d7475-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="d7475-133">Bu yöntemde döndürüldüğü uç nokta adresi `FindCalculatorServiceAddress` hesaplayıcı hizmeti çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="d7475-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="d7475-134">İçinde `InvokeCalculatorService` yöntemi, bir örneğini oluşturmak `CalculatorServiceClient` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d7475-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="d7475-135">Bu sınıf tarafından tanımlanan [barındırma](https://go.microsoft.com/fwlink/?LinkId=145523) örnek.</span><span class="sxs-lookup"><span data-stu-id="d7475-135">This class is defined by the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="d7475-136">Svcutil.exe kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="d7475-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="d7475-137">Sonraki satırda, istemcinin uç nokta adresini döndürüldüğü uç nokta adresi ayarlayın `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="d7475-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="d7475-138">Hemen sonra kodu için önceki adımı, hesaplayıcı hizmeti tarafından kullanıma sunulan yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="d7475-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="d7475-139">Kodu `Main()` yönteminde `Program` çağırmak için sınıf `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="d7475-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="d7475-140">Sonraki satırda çağrı `InvokeCalculatorService()` ve döndürülen uç nokta adresini geçirin `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="d7475-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="d7475-141">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="d7475-141">To test the application</span></span>  
  
1.  <span data-ttu-id="d7475-142">Yükseltilmiş bir komut istemi açın ve Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d7475-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2.  <span data-ttu-id="d7475-143">Bir komut istemi açın ve Discoveryclientapp.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d7475-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3.  <span data-ttu-id="d7475-144">Service.exe çıkışı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="d7475-144">The output from service.exe should look like the following output.</span></span>  
  
    ```Output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4.  <span data-ttu-id="d7475-145">Discoveryclientapp.exe çıkışı aşağıdaki çıktı gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="d7475-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="d7475-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7475-146">Example</span></span>  
 <span data-ttu-id="d7475-147">Bu örneğe yönelik kodun bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7475-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="d7475-148">Bu kod bağlı olduğu [barındırma](https://go.microsoft.com/fwlink/?LinkId=145523) örnek, değiştirilen dosyalar listelenir.</span><span class="sxs-lookup"><span data-stu-id="d7475-148">Because this code is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="d7475-149">Barındırma örnek hakkında daha fazla bilgi için bkz: [kurulum yönergelerini](https://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="d7475-149">For more information about the Self-Host sample, see [Setup Instructions](https://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="d7475-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7475-150">See Also</span></span>  
 [<span data-ttu-id="d7475-151">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d7475-151">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="d7475-152">WCF Bulma Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="d7475-152">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
