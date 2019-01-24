---
title: 'Nasıl yapılır: Bir WCF hizmeti ve istemci programlı bir şekilde Keşfedilebilirlik ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: a0240d09c07a23c2c578008885e5bca00169acdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643136"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Nasıl yapılır: Bir WCF hizmeti ve istemci programlı bir şekilde Keşfedilebilirlik ekleme
Bu konuda, bir Windows Communication Foundation (WCF) hizmeti bulunabilir hale açıklanmaktadır. Dayanır [barındırma](https://go.microsoft.com/fwlink/?LinkId=145523) örnek.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Bulma için var olan barındırılan hizmet örneği yapılandırmak için  
  
1.  Barındırma çözümü Visual Studio 2012'de açın. Örnek TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.  
  
2.  Bir başvuru ekleyin `System.ServiceModel.Discovery.dll` hizmet projesi için. "Sistemi. hata mesajını görebilirsiniz. ServiceModel.Discovery.dll veya bağımlılıklarından biri daha sonraki bir sürümü gerektirir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] belirtilenden projede... " Bu iletiyi görürseniz, Çözüm Gezgini'nde projeye sağ tıklayıp seçin **özellikleri**. İçinde **proje özellikleri** penceresinde emin **hedef Framework'ü** olan [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3.  Adını da dosyasını açın ve aşağıdakileri ekleyin `using` deyimi.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  İçinde `Main()` yöntemi, iç `using` deyimi ekleyin bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> örneğine hizmet ana bilgisayarı.  
  
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
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Uygulanmış şekilde hizmet bulunabilir olduğunu belirtir.  
  
5.  Ekleme bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ekler kodundan hemen sonra hizmet ana bilgisayarı için <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Bu kod, standart UDP bulma uç noktası için bulma ileti gönderilmesi gerektiğini belirtir.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Bulma hizmeti çağırmak amacıyla kullanan bir istemci uygulaması oluşturmak için  
  
1.  Adlı bir çözüm için yeni bir konsol uygulaması Ekle `DiscoveryClientApp`.  
  
2.  Bir başvuru ekleyin `System.ServiceModel.dll` ve `System.ServiceModel.Discovery.dll`  
  
3.  GeneratedClient.cs ve App.config dosyaları var olan istemci projeden DiscoveryClientApp yeni projeye kopyalayın. Bunu yapmak için dosyaları sağ **Çözüm Gezgini**seçin **kopyalama**ve ardından **DiscoveryClientApp** proje için sağ tıklayın ve seçin**Yapıştır**.  
  
4.  Program.cs dosyasını açın.  
  
5.  Aşağıdaki `using` deyimleri.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  Adlı statik bir yöntem ekleyin `FindCalculatorServiceAddress()` için `Program` sınıfı.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Bu yöntem, aranacak bulma kullanır. `CalculatorService` hizmeti.  
  
7.  İçinde `FindCalculatorServiceAddress` yöntemi, yeni bir <xref:System.ServiceModel.Discovery.DiscoveryClient> örneği öğesinde geçen bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Oluşturucusu.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Bu, WCF bildirir <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfı bulma ileti göndermek ve almak için standart UDP bulma uç noktası kullanmalıdır.  
  
8.  Sonraki satırda çağrı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi belirtin bir <xref:System.ServiceModel.Discovery.FindCriteria> aramak istediğiniz hizmet sözleşmesi içeren örneği. Bu durumda, belirtin `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Çağrısından sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, eşleşen en az bir hizmet olup olmadığını denetleyin ve dönüş <xref:System.ServiceModel.EndpointAddress> ilk eşleşen servis. Aksi takdirde dönüş `null`.  
  
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
  
10. Adlı statik bir yöntem ekleyin `InvokeCalculatorService` için `Program` sınıfı.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Bu yöntemde döndürüldüğü uç nokta adresi `FindCalculatorServiceAddress` hesaplayıcı hizmeti çağırmak için.  
  
11. İçinde `InvokeCalculatorService` yöntemi, bir örneğini oluşturmak `CalculatorServiceClient` sınıfı. Bu sınıf tarafından tanımlanan [barındırma](https://go.microsoft.com/fwlink/?LinkId=145523) örnek. Svcutil.exe kullanılarak oluşturuldu.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Sonraki satırda, istemcinin uç nokta adresini döndürüldüğü uç nokta adresi ayarlayın `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Hemen sonra kodu için önceki adımı, hesaplayıcı hizmeti tarafından kullanıma sunulan yöntemleri çağırın.  
  
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
  
14. Kodu `Main()` yönteminde `Program` çağırmak için sınıf `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Sonraki satırda çağrı `InvokeCalculatorService()` ve döndürülen uç nokta adresini geçirin `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Yükseltilmiş bir komut istemi açın ve Service.exe çalıştırın.  
  
2.  Bir komut istemi açın ve Discoveryclientapp.exe çalıştırın.  
  
3.  Service.exe çıkışı aşağıdaki çıktı gibi görünmelidir.  
  
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
  
4.  Discoveryclientapp.exe çıkışı aşağıdaki çıktı gibi görünmelidir.  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Örnek  
 Bu örneğe yönelik kodun bir listesi verilmiştir. Bu kod bağlı olduğu [barındırma](https://go.microsoft.com/fwlink/?LinkId=145523) örnek, değiştirilen dosyalar listelenir. Barındırma örnek hakkında daha fazla bilgi için bkz: [kurulum yönergelerini](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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
- [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [WCF Bulma Nesne Modeli](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
