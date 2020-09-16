---
title: 'Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: c1b92568d90734a33a7b36af987fdb7cbbbe5149
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557833"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme
Bu konuda Windows Communication Foundation (WCF) hizmetinin bulunabilir hale getirme açıklanmaktadır. Bu, [kendi kendine konak](../samples/self-host.md) örneğine dayalıdır.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Mevcut Self-Host hizmet örneğini bulma için yapılandırmak için  
  
1. Visual Studio 2012 ' de Self-Host çözümünü açın. Örnek, TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.  
  
2. Hizmet projesine bir başvuru ekleyin `System.ServiceModel.Discovery.dll` . "Sistem" iletisini bildiren bir hata iletisi görebilirsiniz. ServiceModel.Discovery.dll veya bağımlılıklarından biri, .NET Framework projede belirtilenden daha sonraki bir sürümü gerektiriyor... " Bu iletiyi görürseniz, Çözüm Gezgini projeye sağ tıklayın ve **Özellikler**' i seçin. **Proje özellikleri** penceresinde, **hedef Framework 'ün** olduğundan emin olun [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .  
  
3. Service.cs dosyasını açın ve aşağıdaki `using` ifadeyi ekleyin.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. Yönteminde, `Main()` `using` ifadesinin içinde, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına bir örnek ekleyin.  
  
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
  
     , <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Uygulandığı hizmetin bulunabilir olduğunu belirtir.  
  
5. Öğesini <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekleyen koddan hemen sonra hizmet ana bilgisayarına ekleyin <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Bu kod, bulma iletilerinin standart UDP bulma uç noktasına gönderilmesi gerektiğini belirtir.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Hizmeti çağırmak için bulma kullanan bir istemci uygulaması oluşturmak için  
  
1. Adlı çözüme yeni bir konsol uygulaması ekleyin `DiscoveryClientApp` .  
  
2. Ve için bir başvuru ekleyin `System.ServiceModel.dll``System.ServiceModel.Discovery.dll`  
  
3. GeneratedClient.cs ve App.config dosyalarını var olan istemci projesinden yeni DiscoveryClientApp projesine kopyalayın. Bunu yapmak için **Çözüm Gezgini**dosyalara sağ tıklayın, **Kopyala**' yı seçin ve ardından **DiscoveryClientApp** projesini seçin, sağ tıklayıp **Yapıştır**' ı seçin.  
  
4. Program.cs 'i açın.  
  
5. Aşağıdaki `using` deyimlerini ekleyin.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Sınıfına adlı statik bir yöntem ekleyin `FindCalculatorServiceAddress()` `Program` .  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Bu yöntem, hizmeti aramak için bulma kullanır `CalculatorService` .  
  
7. Yöntemi içinde `FindCalculatorServiceAddress` , <xref:System.ServiceModel.Discovery.DiscoveryClient> oluşturucuya ' a geçirerek yeni bir örnek oluşturun <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Bu, WCF 'ye, <xref:System.ServiceModel.Discovery.DiscoveryClient> bulma iletilerini göndermek ve almak için standart UDP bulma uç noktası kullanması gerektiğini bildirir.  
  
8. Sonraki satırda, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemini çağırın ve <xref:System.ServiceModel.Discovery.FindCriteria> aramak istediğiniz hizmet sözleşmesini içeren bir örneği belirtin. Bu durumda, belirtin `ICalculator` .  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. ' A çağrısından sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , en az bir eşleşen hizmet olup olmadığını ve <xref:System.ServiceModel.EndpointAddress> ilk eşleşen hizmeti döndürmesini denetleyin. Aksi takdirde döndürün `null` .  
  
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
  
10. Sınıfına adlı statik bir yöntem ekleyin `InvokeCalculatorService` `Program` .  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Bu yöntem `FindCalculatorServiceAddress` , hesap makinesi hizmetini çağırmak için öğesinden döndürülen uç nokta adresini kullanır.  
  
11. Yöntemi içinde `InvokeCalculatorService` , sınıfının bir örneğini oluşturun `CalculatorServiceClient` . Bu sınıf, [self-Host](../samples/self-host.md) örneği tarafından tanımlanır. Svcutil.exe kullanılarak oluşturulmuştur.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Sonraki satırda, istemcinin uç nokta adresini, tarafından döndürülen uç nokta adresi olarak ayarlayın `FindCalculatorServiceAddress()` .  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Önceki adıma ait koddan hemen sonra, hesaplayıcı hizmeti tarafından kullanıma sunulan yöntemleri çağırın.  
  
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
  
14. `Main()` `Program` Çağırmak için sınıfındaki yöntemine kod ekleyin `FindCalculatorServiceAddress` .  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Sonraki satırda, ' ı çağırın `InvokeCalculatorService()` ve öğesinden döndürülen uç nokta adresini geçirin `FindCalculatorServiceAddress()` .  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1. Yükseltilmiş bir komut istemi açın ve Service.exe çalıştırın.  
  
2. Bir komut istemi açın ve Discoveryclientapp.exe çalıştırın.  
  
3. service.exe çıkışı aşağıdaki çıktı gibi görünmelidir.  
  
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
  
4. Discoveryclientapp.exe çıkışı aşağıdaki çıktı gibi görünmelidir.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Örnek  
 Bu örnek için kodun bir listesi aşağıda verilmiştir. Bu kod, [kendi kendine konak](../samples/self-host.md) örneğine bağlı olduğundan, yalnızca değiştirilen dosyalar listelenir. Self-Host örneği hakkında daha fazla bilgi için bkz. [Kurulum yönergeleri](../samples/set-up-instructions.md).  
  
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

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Keşif Genel Bakış](wcf-discovery-overview.md)
- [WCF Keşif Nesnesi Modeli](wcf-discovery-object-model.md)
