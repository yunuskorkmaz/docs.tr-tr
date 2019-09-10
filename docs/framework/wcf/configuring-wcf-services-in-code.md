---
title: WCF Hizmetlerini Kodda Yapılandırma
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: d2ef7b2095bf7f238a25f2db0e5d3cf47e885550
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855649"
---
# <a name="configuring-wcf-services-in-code"></a>WCF Hizmetlerini Kodda Yapılandırma
Windows Communication Foundation (WCF), geliştiricilerin yapılandırma dosyalarını veya kodu kullanarak hizmetleri yapılandırmalarına olanak tanır.  Yapılandırma dosyaları, bir hizmetin dağıtıldıktan sonra yapılandırılması gerektiğinde faydalıdır. Yapılandırma dosyalarını kullanırken, bir BT uzmanı 'nın yalnızca yapılandırma dosyasını güncelleştirmesi gerekir, yeniden derleme gerekmez. Bununla birlikte yapılandırma dosyaları, karmaşık ve bakım açısından zor olabilir. Yapılandırma dosyalarını hata ayıklama desteği yoktur ve yapılandırma öğeleri, yazma yapılandırma dosyalarını hata-açık ve zor hale getiren adlara göre başvurulur. WCF Ayrıca koddaki Hizmetleri yapılandırmanıza de olanak tanır. WCF 'nin önceki sürümlerinde (4,0 ve önceki sürümler), kodda hizmetleri yapılandırmak kendi kendine barındırılan senaryolarda kolaydır, <xref:System.ServiceModel.ServiceHost> sınıf ServiceHost. Open çağrılmadan önce uç noktaları ve davranışları yapılandırmanıza izin verilir. Ancak, Web 'de barındırılan senaryolarda <xref:System.ServiceModel.ServiceHost> sınıfına doğrudan erişiminiz yoktur. Web 'de barındırılan bir hizmeti yapılandırmak için, `System.ServiceModel.ServiceHostFactory` <xref:System.ServiceModel.Activation.ServiceHostFactory> oluşturmuş ve gerekli tüm yapılandırmaları gerçekleştirmiş bir oluşturma gerekiyordu. WCF, .NET 4,5 ile başlayarak, kodda hem şirket içinde barındırılan hem de Web 'de barındırılan Hizmetleri yapılandırmanın daha kolay bir yolunu sunar.  
  
## <a name="the-configure-method"></a>Configure yöntemi  
 Hizmet uygulama Sınıfınıza aşağıdaki imzayla çağrılan `Configure` bir ortak statik yöntem tanımlamanız yeterlidir:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure yöntemi, geliştiricinin uç <xref:System.ServiceModel.ServiceConfiguration> noktalar ve davranışlar eklemesini sağlayan bir örnek alır. Bu yöntem, hizmet ana bilgisayarı açılmadan önce WCF tarafından çağırılır. Tanımlandığında, bir App. config veya Web. config dosyasında belirtilen herhangi bir hizmet yapılandırma ayarı yok sayılır.  
  
 Aşağıdaki kod parçacığı, `Configure` yönteminin nasıl tanımlanacağını ve bir hizmet uç noktası, bir uç nokta davranışı ve hizmet davranışı nasıl ekleneceğini göstermektedir:  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 Bir hizmet için https gibi bir protokolü etkinleştirmek için, protokolü kullanan bir uç noktayı açıkça ekleyebilir veya her temel adres için bir uç nokta ekleyen ServiceConfiguration. EnableProtocol (bağlama) çağırarak uç noktaları otomatik olarak ekleyebilirsiniz protokolle ve tanımlanan her hizmet sözleşmesiyle uyumludur. Aşağıdaki kod, ServiceConfiguration. EnableProtocol yönteminin nasıl kullanılacağını göstermektedir:  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <`protocolMappings`> Bölümündeki ayarlar yalnızca <xref:System.ServiceModel.ServiceConfiguration> program aracılığıyla hiçbir uygulama uç noktası eklenmemişse kullanılır. İsteğe bağlı olarak, hizmet yapılandırmasını çağırarak <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> varsayılan uygulama yapılandırma dosyasından yükleyebilirsiniz ve sonra ayarları değiştirebilirsiniz. Sınıfı <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> , merkezi bir yapılandırmadan yapılandırmayı yüklemenize de olanak tanır. Aşağıdaki kod, bunun nasıl uygulanacağını göstermektedir:  
  
```csharp
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
> <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> `host`<><`service`> Etiketindeki < > ayarlarını yok saymadığını unutmayın.`system.serviceModel` Kavramsal olarak,`host`< >, hizmet yapılandırması değil konak yapılandırması ile ilgilidir ve Configure Yöntemi yürütülmeden önce yüklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [İstemci Davranışlarını Yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)
- [Yapılandırma](../../../docs/framework/wcf/samples/configuration-sample.md)
- [IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [Yapılandırma ve Meta Veri Desteği](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [Yapılandırma](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [Nasıl yapılır: Yapılandırmada bir hizmet bağlaması belirtin](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Yapılandırmada bir hizmet uç noktası oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Nasıl yapılır: Yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Nasıl yapılır: Yapılandırmada bir Istemci bağlaması belirtme](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
