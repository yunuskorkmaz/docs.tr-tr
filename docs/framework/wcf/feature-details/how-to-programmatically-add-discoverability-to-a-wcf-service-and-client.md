---
title: 'Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: 0685694db8f67ed690cf2a8002bf70a05695a192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495489"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme
Bu konuda, Windows Communication Foundation (WCF) hizmetini bulunabilirlik nasıl oluşturulacağı açıklanmaktadır. Bağlı olduğu [kendini barındırma](http://go.microsoft.com/fwlink/?LinkId=145523) örnek.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Bulma için var olan kendi kendini barındıran hizmet örneği yapılandırmak için  
  
1.  Kendi kendini barındıran çözümde açmak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Örnek TechnologySamples\Basic\Service\Hosting\SelfHost dizininde bulunur.  
  
2.  Bir başvuru ekleyin `System.ServiceModel.Discovery.dll` hizmet projesi için. "Sistemi. belirten bir hata iletisi görebilirsiniz ServiceModel.Discovery.dll veya bağımlılıklarından biri daha sonraki bir sürümünü gerektirir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] belirtilenden projede... " Bu iletiyi görürseniz, Çözüm Gezgini'nde projeye sağ tıklayın ve seçin **özellikleri**. İçinde **proje özelliklerini** penceresinde olduğundan emin olun **hedef Framework** olan [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3.  Adını da dosyasını açın ve aşağıdakileri ekleyin `using` deyimi.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  İçinde `Main()` yöntemi, iç `using` deyimini ekleyin bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet barındırmak için.  
  
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
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Uygulanan için hizmet bulunabilirlik olduğunu belirtir.  
  
5.  Ekleme bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> hizmet ana bilgisayara sağ ekler koddan sonra <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Bu kod, bulma iletileri standart UDP bulma uç noktasına gönderilmesi gerektiğini belirtir.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Hizmeti çağırmak için bulma kullanan bir istemci uygulaması oluşturmak için  
  
1.  Adlı çözüm için yeni bir konsol uygulaması ekleyin `DiscoveryClientApp`.  
  
2.  Bir başvuru ekleyin `System.ServiceModel.dll` ve `System.ServiceModel.Discovery.dll`  
  
3.  GeneratedClient.cs ve App.config dosyaları var olan istemci projeden yeni DiscoveryClientApp projeye kopyalayın. Bunu yapmak için dosyaları sağ **Çözüm Gezgini**seçin **kopya**ve ardından **DiscoveryClientApp** proje, sağ tıklayın ve seçin**Yapıştır**.  
  
4.  Program.cs açın.  
  
5.  Aşağıdakileri ekleyin `using` deyimleri.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  Adlı bir statik yöntem ekleyin `FindCalculatorServiceAddress()` için `Program` sınıfı.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Bu yöntem bulma aramak için kullanır. `CalculatorService` hizmet.  
  
7.  İçinde `FindCalculatorServiceAddress` yöntemi, yeni bir <xref:System.ServiceModel.Discovery.DiscoveryClient> tümleştirilmesidir örneği, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Oluşturucusu.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Bu, WCF söyler <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfı bulma ileti gönderme ve alma için standart UDP bulma uç noktası kullanmalıdır.  
  
8.  Sonraki satırında, çağrı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi ve belirtin bir <xref:System.ServiceModel.Discovery.FindCriteria> aramak istediğiniz hizmet sözleşmesini içeren örneği. Bu durumda, belirtin `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Çağrısından sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, en az bir eşleşen hizmet olup olmadığını kontrol edin ve dönüş <xref:System.ServiceModel.EndpointAddress> ilk eşleşen hizmet. Aksi takdirde dönmek `null`.  
  
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
  
10. Adlı bir statik yöntem ekleyin `InvokeCalculatorService` için `Program` sınıfı.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Bu yöntem döndürülen uç noktası adresi kullanan `FindCalculatorServiceAddress` hesaplayıcı hizmetini çağırmak için.  
  
11. İçinde `InvokeCalculatorService` yöntemi, bir örneğini oluşturmak `CalculatorServiceClient` sınıfı. Bu sınıf tarafından tanımlanan [kendini barındırma](http://go.microsoft.com/fwlink/?LinkId=145523) örnek. Svcutil.exe kullanılarak oluşturuldu.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Sonraki satırında, döndürülen uç noktası adresi istemcinin uç nokta adresi koymak `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Hemen sonra kodu önceki adımı için hesap makinesi hizmeti tarafından sunulan yöntemlerini çağırın.  
  
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
  
14. Kodu ekleyin `Main()` yönteminde `Program` çağırmak için sınıf `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Sonraki satırında, çağrı `InvokeCalculatorService()` ve döndürülen uç noktası adresi geçirin `FindCalculatorServiceAddress()`.  
  
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
  
3.  Service.exe çıkışı aşağıdaki çıkış gibi görünmelidir.  
  
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
  
4.  Discoveryclientapp.exe çıkışı aşağıdaki çıkış gibi görünmelidir.  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Örnek  
 Bu örnek kod bir listesi verilmiştir. Bu kod bağlı olduğu [kendini barındırma](http://go.microsoft.com/fwlink/?LinkId=145523) örnek, yalnızca değiştirilen dosyalar listelenir. Kendini barındırma örneği hakkında daha fazla bilgi için bkz: [kurulum yönergelerini](http://go.microsoft.com/fwlink/?LinkId=145522).  
  
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

## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [WCF Bulma Nesne Modeli](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
