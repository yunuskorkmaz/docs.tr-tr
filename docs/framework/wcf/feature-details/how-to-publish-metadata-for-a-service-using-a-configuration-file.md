---
title: "Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e94fe7135d51c4e1578ca69768b6d0ba2aa6ae6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu meta veri yayımlama için gösteren iki nasıl yapılır konuları biridir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet. Bir hizmeti bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri, nasıl yayınlamalıdır belirtmek için iki yolu vardır. Bu konuda, bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.  
  
> [!CAUTION]
>  Bu konu, güvenli olmayan bir şekilde meta verileri yayımlama gösterilmektedir. Herhangi bir istemci hizmetinden meta verileri alabilir. Hizmetinizin meta verileri güvenli bir şekilde yayımlamak için gerekli olup olmadığını görmek [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: kod içinde meta veri yayımlama [nasıl yapılır: meta verileri kullanarak bir hizmet kodu yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Meta veri yayımlama sağlayan bir WS-aktarımı GET isteği ya da bir HTTP/GET isteği kullanarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi. Kod çalıştığından emin olmak için bir temel oluşturmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Kolaylık olması için temel bir kendi kendini barındıran hizmet aşağıdaki kodu sağlanır.  
  
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
  
 Bu hizmet bir yapılandırma dosyası kullanarak yapılandırılan kendi kendini barındıran bir hizmettir. Aşağıdaki yapılandırma dosyası bir başlangıç noktası olarak görev yapar.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak bir WCF Hizmeti meta verilerini yayımlamak için  
  
1.  Kapatma sonrasında App.config dosyası içinde `</services>` öğesini oluşturmak bir `<behaviors>` öğesi.  
  
  
  
2.  İçinde `<behaviors>` öğesi ekleme bir `<serviceBehaviors>` öğesi.  
  
  
  
3.  Ekleme bir `<behavior>` öğesine `<serviceBehaviors>` öğesi için bir değer belirtin `name` özniteliği `<behavior>` öğesi.  
  
  
  
4.  Ekleme bir `<serviceMetadata>` öğesine `<behavior>` öğesi. Ayarlama `httpGetEnabled` özniteliğini `true` ve `policyVersion` özniteliği için Policy15. `httpGetEnabled`bir HTTP GET isteği tarafından yapılan meta veri isteklerine hizmet sağlar. `policyVersion`WS-Policy 1.5 meta verilerini oluştururken uygun hizmete bildirir.  
  
  
  
5.  Ekleme bir `behaviorConfiguration` özniteliğini `<service>` öğesi ve belirtin `name` özniteliği `<behavior>` adım 1 ' de eklenen aşağıdaki kod örneğinde gösterildiği gibi öğesi.  
  
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
  
6.  Bir veya daha fazla Ekle `<endpoint>` sözleşme ile öğeleri kümesine `IMetadataExchange`aşağıdaki kod örneğinde gösterildiği gibi.  
  
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
  
7.  Önceki adımda eklediğiniz meta veri uç noktaları için ayarlamak `binding` özniteliği şunlardan biri:  
  
    -   `mexHttpBinding`için HTTP yayımlama.  
  
    -   `mexHttpsBinding`için HTTPS yayımlama.  
  
    -   `mexNamedPipeBinding`adlandırılmış kanal yayını için.  
  
    -   `mexTcpBinding`için TCP yayımlama.  
  
8.  Bir önceki adımda eklediğiniz meta veri uç noktaları için adres eşit olarak ayarlayın:  
  
    -   Temel adres meta veri bağlama ile aynı olduğunda ana uygulamanın taban adresi yayın noktası olarak kullanmak için boş bir dize.  
  
    -   Ana bilgisayar uygulamasını taban adresi varsa, göreli bir adres.  
  
    -   Mutlak bir adres.  
  
9. Derleme ve konsol uygulamasını çalıştırın.  
  
10. (Bu örnekte, http://localhost:8001/MetadataSample) hizmetinin temel adresine göz atın ve meta veri yayımlama açık olduğunu doğrulamak için Internet Explorer'ı kullanın. Değilse, sayfanın üst kısmındaki ortaya çıkan bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı."  
  
### <a name="to-use-default-endpoints"></a>Varsayılan uç noktalar kullanmak için  
  
1.  Meta veri varsayılan uç noktaları kullanan bir hizmeti yapılandırmak için belirtmeniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırmasında dosya önceki örnekte olduğu gibi ancak uç nokta belirtmeyin. Yapılandırma dosyası ardından şuna benzer.  
  
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
  
     Hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ile `httpGetEnabled` kümesine `true`hizmeti etkin meta veri yayımlama sahiptir ve uç nokta yok açıkça eklenmiş olduğundan çalışma zamanı varsayılan uç noktaları ekler. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği temel bir gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ve hizmet için meta verilerini yayımlayan yapılandırma dosyası.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md)  
 [Meta veri mimarisi genel bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Meta verilerini kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Nasıl yapılır: kod kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
