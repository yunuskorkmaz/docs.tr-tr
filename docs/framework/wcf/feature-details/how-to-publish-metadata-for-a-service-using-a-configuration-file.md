---
title: 'Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: f3fda88f4ec2f2695d6026d6e4df79243124b7b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643667"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu, bir Windows Communication Foundation (WCF) hizmet için meta verileri yayımlama gösteren iki nasıl yapılır konuları biridir. Hizmet yapılandırma dosyasını ve kod kullanarak meta verileri nasıl yayımlamalısınız belirtmenin iki yolu vardır. Bu konuda, bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.  
  
> [!CAUTION]
>  Bu konu, güvenli bir şekilde meta verileri yayımlama gösterilmektedir. Herhangi bir istemci hizmet meta verileri alabilir. Meta verileri güvenli bir şekilde yayımlamak için hizmetinize ihtiyaç duyuyorsanız bkz [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Kod meta verileri yayımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kod kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Meta veri yayımlama sağlayan bir WS aktarım GET isteği ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi. Kod çalıştığından emin olmak için temel bir WCF hizmeti oluşturma. Kolaylık olması için aşağıdaki kodda temel şirket içinde barındırılan bir hizmet sağlanır.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 Bu hizmet bir yapılandırma dosyası kullanılarak yapılandırılan şirket içinde barındırılan bir hizmettir. Aşağıdaki yapılandırma dosyası, başlangıç noktası olarak görev yapar.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak bir WCF hizmeti için meta verileri yayımlama  
  
1. App.config dosyasında Kapanıştan sonra `</services>` öğesi oluşturmak bir `<behaviors>` öğesi.  

2. İçinde `<behaviors>` öğe, Ekle bir `<serviceBehaviors>` öğesi.  

3. Ekleme bir `<behavior>` öğesine `<serviceBehaviors>` öğesi için bir değer belirtin `name` özniteliği `<behavior>` öğesi.  

4. Ekleme bir `<serviceMetadata>` öğesine `<behavior>` öğesi. Ayarlama `httpGetEnabled` özniteliğini `true` ve `policyVersion` Policy15 için özniteliği. `httpGetEnabled` bir HTTP GET isteği tarafından yapılan meta veri isteklerine hizmet verir. `policyVersion` Hizmet meta verilerini oluştururken için WS-Policy 1.5 uyacak şekilde söyler.  

5. Ekleme bir `behaviorConfiguration` özniteliğini `<service>` öğe belirtin `name` özniteliği `<behavior>` adım 1'de aşağıdaki kod örneğinde gösterildiği gibi eklenen öğe.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. Bir veya daha fazla Ekle `<endpoint>` sözleşmesi öğeleri kümesine `IMetadataExchange`aşağıdaki kod örneğinde gösterildiği gibi.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. Önceki adımda eklediğiniz meta veri uç noktaları için `binding` öznitelik aşağıdakilerden biri:  
  
    - `mexHttpBinding` için HTTP yayımlama.  
  
    - `mexHttpsBinding` HTTPS için yayımlama.  
  
    - `mexNamedPipeBinding` adlandırılmış kanal yayını.  
  
    - `mexTcpBinding` için TCP yayımlama.  
  
8. Bir önceki adımda eklediğiniz meta veri uç noktaları, adresi eşit olarak ayarlayın:  
  
    - Taban adresi meta veri bağlama ile aynı olduğunda konak uygulamanın temel adres yayın noktası olarak kullanmak için boş bir dize.  
  
    - Konak uygulamanın temel adres varsa göreli bir adres.  
  
    - Mutlak bir adres.  
  
9. Konsol uygulamasını derleyin ve çalıştırın.  
  
10. Hizmetin taban adresine göz atmak için Internet Explorer'ı kullanın (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlama açık olduğunu doğrulayın. Aksi durumda, sonuçta elde edilen sayfanın üst kısmındaki bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı bırakıldı."  
  
### <a name="to-use-default-endpoints"></a>Varsayılan uç noktalarını kullanacak şekilde  
  
1. Varsayılan uç noktalarını kullanan bir hizmet üzerinde meta verileri yapılandırmak için belirtmeniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırma dosyasını önceki örnekte olduğu gibi ancak tüm uç noktalar belirtmeyin. Yapılandırma dosyası, ardından şöyle görünebilir.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ile `httpGetEnabled` kümesine `true`etkin meta veri yayımlama hizmeti sahiptir ve uç nokta açıkça eklenmiş olduğundan, çalışma zamanı varsayılan uç noktalar ekler. Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, hizmet için meta verilerini yayımlayan yapılandırma dosyası ile temel bir WCF hizmeti ve uygulamasını gösterir.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Nasıl yapılır: Yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Kendini Barındırma](../../../../docs/framework/wcf/samples/self-host.md)
- [Meta Veri Mimarisine Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Nasıl yapılır: Kod kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
