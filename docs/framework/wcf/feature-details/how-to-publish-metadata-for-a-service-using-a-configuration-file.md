---
title: 'Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 7ea0a2aa386f747b89f56f21d75a97e4409140a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184878"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu, bir Windows Communication Foundation (WCF) hizmeti için meta veri yayımlama gösteren iki nasıl yapılır konularından biridir. Bir yapılandırma dosyası kullanarak ve kodu kullanarak, bir hizmetin meta verileri nasıl yayımlayacağını belirtmenin iki yolu vardır. Bu konu, yapılandırma dosyasını kullanarak bir hizmet için meta verilerin nasıl yayımlandırılabildiğini gösterir.  
  
> [!CAUTION]
> Bu konu, meta verilerin güvenli olmayan bir şekilde nasıl yayımlandırılabildiğini gösterir. Herhangi bir istemci hizmetten meta verileri alabilir. Hizmetinizin meta verileri güvenli bir şekilde yayımlamasını istiyorsanız, [bkz.](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
  
 Meta verileri kodda yayımlama hakkında daha fazla bilgi için [bkz: Kod Kullanan Bir Hizmet için Meta Veri Yayımlama.](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md) Meta verileri yayımlama, istemcilerin sorgu dizesini kullanarak `?wsdl` bir WS-Transfer GET isteği veya http/GET isteği kullanarak meta verileri almasına olanak tanır. Kodun çalıştığından emin olmak için temel bir WCF hizmeti oluşturun. Basitlik için, aşağıdaki kodda temel bir kendi kendine barındırılan hizmet sağlanır.  
  
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
  
 Bu hizmet, yapılandırma dosyası kullanılarak yapılandırılan, kendi kendine barındırılan bir hizmettir. Aşağıdaki yapılandırma dosyası bir başlangıç noktası olarak hizmet vermektedir.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Bir uygulama yapılandırma dosyasını kullanarak bir WCF hizmeti için meta veri yayımlamak için  
  
1. App.config dosyası içinde, kapanış `</services>` öğesisonra, `<behaviors>` bir öğe oluşturun.  

2. Öğe `<behaviors>` içinde, bir `<serviceBehaviors>` öğe ekleyin.  

3. Öğeye `<behavior>` bir öğe ekleyin ve `name` öğenin özniteliği için bir değer belirtin. `<behavior>` `<serviceBehaviors>`  

4. `<behavior>` Öğeye bir `<serviceMetadata>` öğe ekleyin. Özniteliği ve `policyVersion` `true` Özniteliği İlke15'e ayarlayın. `httpGetEnabled` `httpGetEnabled`hizmetin bir HTTP GET isteği tarafından yapılan meta veri isteklerine yanıt vermesine olanak tanır. `policyVersion`meta veri oluştururken hizmete WS-İlke 1.5'e uymasını söyler.  

5. Öğeye `behaviorConfiguration` bir öznitelik ekleyin ve aşağıdaki `<behavior>` kod örneğinde gösterildiği gibi, adım 1'de eklenen öğenin özniteliğini belirtin. `name` `<service>`  
  
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
  
6. Aşağıdaki kod `<endpoint>` örneğinde gösterildiği `IMetadataExchange`gibi, sözleşme ayarlanmış bir veya daha fazla öğe ekleyin.  
  
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
  
7. Önceki adımda eklenen meta veri uç noktaları `binding` için özniteliği aşağıdakilerden birine ayarlayın:  
  
    - `mexHttpBinding`HTTP yayını için.  
  
    - `mexHttpsBinding`HTTPS yayını için.  
  
    - `mexNamedPipeBinding`adlı boru yayını için.  
  
    - `mexTcpBinding`TCP yayını için.  
  
8. Önceki adımda eklenen meta veri uç noktaları için adresi aşağıdakilere eşit olarak ayarlayın:  
  
    - Temel adres meta veri bağlama ile aynıysa, ana bilgisayar uygulamasının temel adresini yayın noktası olarak kullanmak için boş bir dize.  
  
    - Ana bilgisayar uygulamasının temel adresi varsa göreli bir adres.  
  
    - Mutlak bir adres.  
  
9. Konsol uygulamasını derleyin ve çalıştırın.  
  
10. Hizmetin temel adresine (buhttp://localhost:8001/MetadataSample örnekte) göz atmak ve meta veri yayımlamanın açık olduğunu doğrulamak için Internet Explorer'ı kullanın. Değilse, ortaya çıkan sayfanın üst kısmındaki bir ileti görüntülenir: "Bu hizmet için meta veri yayımlama şu anda devre dışı bırakılır."  
  
### <a name="to-use-default-endpoints"></a>Varsayılan uç noktaları kullanmak için  
  
1. Varsayılan uç noktaları kullanan bir hizmetteki meta verileri <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırmak için yapılandırma dosyasındakileri önceki örnekte olduğu gibi belirtin, ancak herhangi bir uç nokta belirtmeyin. Yapılandırma dosyası daha sonra bu gibi görünür.  
  
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
  
     Hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> `httpGetEnabled` kümesi ile bir `true`olduğundan, hizmet meta veri yayımlama etkin ve hiçbir uç noktaları açıkça eklenmiştir çünkü, çalışma süresi varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, temel bir WCF hizmetinin uygulanmasını ve hizmet için meta verileri yayımlayan yapılandırma dosyasını gösterir.  
  
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
- [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Kendini Barındırma](../../../../docs/framework/wcf/samples/self-host.md)
- [Meta Veri Mimarisi Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
