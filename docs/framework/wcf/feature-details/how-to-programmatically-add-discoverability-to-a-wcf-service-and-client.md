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
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Nasıl yapılır: bir WCF hizmeti ve Istemcisine program aracılığıyla bulunabilirliği ekleme
Bu konuda Windows Communication Foundation (WCF) hizmetinin bulunabilir hale getirme açıklanmaktadır. Bu, [kendi kendine konak](https://go.microsoft.com/fwlink/?LinkId=145523) örneğine dayalıdır.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Mevcut Self-Host hizmet örneğini bulma için yapılandırmak için  
  
1. Visual Studio 2012 ' de Self-Host çözümünü açın. Örnek, TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.  
  
2. Hizmet projesine `System.ServiceModel.Discovery.dll` ' a bir başvuru ekleyin. "Sistem" iletisini bildiren bir hata iletisi görebilirsiniz. ServiceModel. Discovery. dll veya bağımlılıklarından biri, .NET Framework projede belirtiden daha yeni bir sürümünü gerektiriyor... " Bu iletiyi görürseniz, Çözüm Gezgini projeye sağ tıklayın ve **Özellikler**' i seçin. **Proje özellikleri** penceresinde, **hedef Framework 'ün** [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] olduğundan emin olun.  
  
3. Service.cs dosyasını açın ve aşağıdaki `using` ifadesini ekleyin.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. @No__t-0 yönteminde, `using` ifadesinin içinde hizmet ana bilgisayarına bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> örneği ekleyin.  
  
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
  
     @No__t-0, uygulandığı hizmetin bulunabilir olduğunu belirtir.  
  
5. @No__t-1 ' i ekleyen koddan hemen sonra hizmet ana bilgisayarına <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekleyin.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Bu kod, bulma iletilerinin standart UDP bulma uç noktasına gönderilmesi gerektiğini belirtir.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Hizmeti çağırmak için bulma kullanan bir istemci uygulaması oluşturmak için  
  
1. @No__t-0 adlı çözüme yeni bir konsol uygulaması ekleyin.  
  
2. @No__t-0 ve `System.ServiceModel.Discovery.dll` öğesine bir başvuru ekleyin  
  
3. GeneratedClient.cs ve App. config dosyalarını var olan istemci projesinden yeni DiscoveryClientApp projesine kopyalayın. Bunu yapmak için **Çözüm Gezgini**dosyalara sağ tıklayın, **Kopyala**' yı seçin ve ardından **DiscoveryClientApp** projesini seçin, sağ tıklayıp **Yapıştır**' ı seçin.  
  
4. Program.cs 'i açın.  
  
5. Aşağıdaki `using` deyimlerini ekleyin.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. @No__t-1 sınıfına `FindCalculatorServiceAddress()` adlı bir statik yöntem ekleyin.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Bu yöntem `CalculatorService` hizmetini aramak için bulma kullanır.  
  
7. @No__t-0 yönteminde, oluşturucuya bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> geçirerek yeni bir <xref:System.ServiceModel.Discovery.DiscoveryClient> örneği oluşturun.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Bu, WCF 'ye <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfının bulma iletilerini göndermek ve almak için standart UDP bulma uç noktasını kullanması gerektiğini belirtir.  
  
8. Sonraki satırda <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemini çağırın ve aramak istediğiniz hizmet sözleşmesini içeren bir <xref:System.ServiceModel.Discovery.FindCriteria> örneği belirtin. Bu durumda `ICalculator` belirtin.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. @No__t-0 ' a çağrıdan sonra, en az bir eşleşen hizmet olup olmadığını denetleyin ve ilk eşleşen hizmetin <xref:System.ServiceModel.EndpointAddress> ' i döndürün. Aksi takdirde `null` döndürün.  
  
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
  
10. @No__t-1 sınıfına `InvokeCalculatorService` adlı bir statik yöntem ekleyin.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Bu yöntem, hesaplayıcı hizmetini çağırmak için `FindCalculatorServiceAddress` ' dan döndürülen uç nokta adresini kullanır.  
  
11. @No__t-0 yönteminin içinde, `CalculatorServiceClient` sınıfının bir örneğini oluşturun. Bu sınıf, [self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) örneği tarafından tanımlanır. Svcutil. exe kullanılarak oluşturulmuştur.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Sonraki satırda, istemcinin uç nokta adresini `FindCalculatorServiceAddress()` ' dan döndürülen uç nokta adresi olarak ayarlayın.  
  
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
  
14. @No__t-2 ' i çağırmak için `Program` sınıfındaki `Main()` yöntemine kod ekleyin.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Sonraki satırda, `InvokeCalculatorService()` ' ı çağırın ve `FindCalculatorServiceAddress()` ' den döndürülen uç nokta adresini geçirin.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1. Yükseltilmiş bir komut istemi açın ve Service. exe ' yi çalıştırın.  
  
2. Bir komut istemi açın ve DiscoveryClientApp. exe ' yi çalıştırın.  
  
3. Service. exe ' den alınan çıktı aşağıdaki çıktı gibi görünmelidir.  
  
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
  
4. Discoveryclientapp. exe ' den alınan çıktı aşağıdaki çıktı gibi görünmelidir.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Örnek  
 Bu örnek için kodun bir listesi aşağıda verilmiştir. Bu kod, [kendi kendine konak](https://go.microsoft.com/fwlink/?LinkId=145523) örneğine bağlı olduğundan, yalnızca değiştirilen dosyalar listelenir. Self-Host örneği hakkında daha fazla bilgi için bkz. [Kurulum yönergeleri](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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

- [WCF bulmaya genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [WCF bulma nesne modeli](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
