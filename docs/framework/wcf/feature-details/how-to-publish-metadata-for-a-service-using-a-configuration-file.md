---
title: 'Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 26894a3951b91879a7b3e6f66731891113394082
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045302"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu, bir Windows Communication Foundation (WCF) hizmeti için meta verileri yayımlamayı gösteren iki nasıl yapılır konuktan biridir. Bir hizmetin bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri nasıl yayımlayacağınızı belirten iki yol vardır. Bu konuda bir yapılandırma dosyası kullanarak bir hizmet için meta verilerin nasıl yayımlanacağı gösterilmektedir.  
  
> [!CAUTION]
> Bu konuda, meta verilerin güvensiz bir şekilde nasıl yayımlanacağı gösterilmektedir. Tüm istemciler, hizmetten meta verileri alabilir. Hizmetinizin meta verileri güvenli bir şekilde yayımlamasını istiyorsanız bkz. [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Kodda meta verileri yayımlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Kod](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)kullanarak bir hizmet için meta verileri yayımlayın. Meta veri yayımlama, `?wsdl` istemcilerin bir ws-Transfer get isteği veya sorgu dizesini kullanarak bir http/get isteği kullanarak meta verileri almasına izin verir. Kodun çalıştığından emin olmak için temel bir WCF hizmeti oluşturun. Basitlik sağlamak için, aşağıdaki kodda temel bir şirket içinde barındırılan bir hizmet sağlanır.  
  
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
  
 Bu hizmet, bir yapılandırma dosyası kullanılarak yapılandırılan, kendi kendine barındırılan bir hizmettir. Aşağıdaki yapılandırma dosyası bir başlangıç noktası olarak görev yapar.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Bir WCF hizmeti için meta verileri bir uygulama yapılandırma dosyası kullanarak yayımlamak için  
  
1. App. config dosyası içinde, kapanış `</services>` öğesinden sonra bir `<behaviors>` öğesi oluşturun.  

2. Öğesi içinde, bir `<serviceBehaviors>` öğesi ekleyin. `<behaviors>`  

3. Öğesine bir `<behavior>` `<serviceBehaviors>` öğesi ekleyin ve `<behavior>` öğesi `name` özniteliği için bir değer belirtin.  

4. `<behavior>` Öğeye bir `<serviceMetadata>` öğe ekleyin. `httpGetEnabled` Özniteliğini`true`veözniteliğiniPolicy15olarakayarlayın. `policyVersion` `httpGetEnabled`hizmetin bir HTTP GET isteği tarafından yapılan meta veri isteklerine yanıt vermesini sağlar. `policyVersion`meta verileri oluştururken Service 'in WS-Policy 1,5 ile uyumlu olduğunu söyler.  

5. `<service>` Öğesine bir `behaviorConfiguration` öznitelik ekleyin ve aşağıdaki kod örneğinde gösterildiği `name` gibi, 1 `<behavior>` . adımda eklenen öğenin özniteliğini belirtin.  
  
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
  
6. Aşağıdaki kod örneğinde gösterildiği `<endpoint>` gibi `IMetadataExchange`, sözleşmeye ayarlanmış bir veya daha fazla öğe ekleyin.  
  
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
  
7. Önceki adımda eklenen meta veri uç noktaları için, `binding` özniteliğini aşağıdakilerden birine ayarlayın:  
  
    - `mexHttpBinding`HTTP yayını için.  
  
    - `mexHttpsBinding`HTTPS yayını için.  
  
    - `mexNamedPipeBinding`Adlandırılmış Kanal yayını için.  
  
    - `mexTcpBinding`TCP yayını için.  
  
8. Önceki bir adımda eklenen meta veri uç noktaları için, adresi şuna eşit olarak ayarlayın:  
  
    - Temel adres meta veri bağlamasıyla aynıysa, yayın noktası olarak ana bilgisayar uygulamasının temel adresini kullanmak için boş bir dize.  
  
    - Ana bilgisayar uygulamasının bir temel adresi varsa göreli bir adres.  
  
    - Mutlak bir adres.  
  
9. Konsol uygulamasını derleyin ve çalıştırın.  
  
10. Internet Explorer 'ı kullanarak hizmetin temel adresine gidin (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlamanın açık olduğunu doğrulayın. Aksi takdirde, ortaya çıkan sayfanın en üstündeki bir ileti şunu görüntüler: "Bu hizmet için meta veri yayımlama Şu anda devre dışı."  
  
### <a name="to-use-default-endpoints"></a>Varsayılan uç noktaları kullanmak için  
  
1. Varsayılan uç noktaları kullanan bir hizmette meta verileri yapılandırmak için, yapılandırma dosyasında <xref:System.ServiceModel.Description.ServiceMetadataBehavior> önceki örnekte olduğu gibi ' i belirtin, ancak herhangi bir uç nokta belirtmeyin. Yapılandırma dosyası bu şekilde görünür.  
  
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
  
     Hizmeti, olarak `httpGetEnabled` ayarlanmış bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> öğesine `true`sahip olduğundan, hizmette yayımlama meta verileri etkindir ve hiçbir uç nokta açık olarak eklenmediğinden, çalışma zamanı varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, temel bir WCF hizmetinin ve hizmet için meta verileri yayımlayan yapılandırma dosyasının uygulamasını gösterir.  
  
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
- [Nasıl yapılır: Yönetilen bir uygulamada bir WCF hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Kendini Barındırma](../../../../docs/framework/wcf/samples/self-host.md)
- [Meta Veri Mimarisine Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Nasıl yapılır: Kod kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
