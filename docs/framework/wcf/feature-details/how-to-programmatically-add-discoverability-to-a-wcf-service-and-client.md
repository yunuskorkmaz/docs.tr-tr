---
title: 'Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: dd96bc168413eef99260a5251e74971aa1309ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184880"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme
Bu konu, bir Windows Communication Foundation (WCF) hizmetinin nasıl keşfedilebilir hale getirilebildiğini açıklar. [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) örneğine dayanır.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Discovery için varolan Self-Host hizmet örneğini yapılandırmak için  
  
1. Visual Studio 2012'de Self-Host çözümlerini açın. Örnek TechnologySamples\Basic\Service\Hosting\SelfHost dizininde yer alır.  
  
2. Hizmet projesine `System.ServiceModel.Discovery.dll` bir başvuru ekleyin. "Sistem" yazan bir hata iletisi görebilirsiniz. ServiceModel.Discovery.dll veya bağımlılıklarından biri ,.NET Framework'ün projede belirtilenden daha sonraki bir sürümünü gerektirir..." Bu iletiyi görürseniz, Çözüm Gezgini'ndeki projeyi sağ tıklatın ve **Özellikler'i**seçin. Project **Properties** penceresinde, **Hedef Çerçeve'nin** [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3. Service.cs dosyasını açın ve `using` aşağıdaki ifadeyi ekleyin.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. `Main()` Yöntemde, deyimin `using` içinde, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayara bir örnek ekleyin.  
  
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
  
     Uygulandığı <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmetin keşfedilebilir olduğunu belirtir.  
  
5. 'yi <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekleyen koddan hemen sonra <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>hizmet ana bilgisayara a ekleyin  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Bu kod, bulma iletilerinin standart UDP bulma bitiş noktasına gönderilmesi gerektiğini belirtir.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Hizmeti aramak için bulma kullanan bir istemci uygulaması oluşturmak için  
  
1. Çözüme yeni bir konsol `DiscoveryClientApp`uygulaması ekleyin.  
  
2. Bir referans `System.ServiceModel.dll` ekleyin ve`System.ServiceModel.Discovery.dll`  
  
3. Mevcut istemci projesinden GeneratedClient.cs ve App.config dosyalarını yeni DiscoveryClientApp projesine kopyalayın. Bunu yapmak **için, Çözüm Gezgini'ndeki**dosyalara sağ tıklayın , **Kopyala'yı**seçin ve ardından **DiscoveryClientApp** projesini seçin, sağ tıklayın ve **Yapıştır'ı**seçin.  
  
4. Açık Program.cs.  
  
5. Aşağıdaki `using` deyimlerini ekleyin.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. `Program` Sınıfa çağrılan `FindCalculatorServiceAddress()` statik bir yöntem ekleyin.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Bu yöntem, hizmeti aramak `CalculatorService` için bulma kullanır.  
  
7. Yöntemin `FindCalculatorServiceAddress` içinde, a'dan oluşturucuya geçerek yeni <xref:System.ServiceModel.Discovery.DiscoveryClient> bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> örnek oluşturun.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Bu, WCF'ye <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfın bulma iletileri göndermek ve almak için standart UDP bulma bitiş noktasını kullanması gerektiğini söyler.  
  
8. Sonraki satırda, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi arayın ve <xref:System.ServiceModel.Discovery.FindCriteria> aramak istediğiniz hizmet sözleşmesini içeren bir örnek belirtin. Bu durumda, `ICalculator`belirtin.  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Aramadan <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>sonra, en az bir eşleşen hizmet olup olmadığını <xref:System.ServiceModel.EndpointAddress> kontrol edin ve ilk eşleşen hizmetin döndürülmesini. Aksi `null`takdirde geri dönün.  
  
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
  
10. Sınıfa statik bir yöntem ekleyin. `InvokeCalculatorService` `Program`  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Bu yöntem, hesap makinesi `FindCalculatorServiceAddress` hizmetini aramak için döndürülen uç nokta adresini kullanır.  
  
11. Yöntemin `InvokeCalculatorService` içinde, sınıfın bir `CalculatorServiceClient` örneğini oluşturun. Bu sınıf [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) örneği tarafından tanımlanır. Svcutil.exe kullanılarak oluşturuldu.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Sonraki satırda, istemcinin bitiş noktası adresini 'den `FindCalculatorServiceAddress()`döndürülen bitiş noktası adresine ayarlayın.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Önceki adımın kodundan hemen sonra, hesap makinesi hizmetitarafından ortaya çıkarılan yöntemleri arayın.  
  
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
  
14. Çağrı yapmak `Main()` için sınıfta yönteme kod `FindCalculatorServiceAddress` `Program`  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Bir sonraki satırda, `InvokeCalculatorService()` 'den `FindCalculatorServiceAddress()`döndürülen bitiş noktası adresini arayın ve geçin.  
  
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
  
2. Bir komut istemi açın ve DiscoveryClientapp.exe çalıştırın.  
  
3. service.exe çıktısı aşağıdaki çıktı gibi görünmelidir.  
  
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
  
4. Discoveryclientapp.exe'den gelen çıktı aşağıdaki çıktı gibi görünmelidir.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıda, bu örnek için kodun bir listesi vetir. Bu kod [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) örneğini temel aldığı için, yalnızca değiştirilen dosyalar listelenir. Self-Host örneği hakkında daha fazla bilgi için [Kurulum Talimatları'na](https://go.microsoft.com/fwlink/?LinkId=145522)bakın.  
  
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

- [WCF Keşif Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [WCF Keşif Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
