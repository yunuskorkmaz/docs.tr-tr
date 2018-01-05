---
title: "WCF Hizmetlerini Kodda Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 202214a6c9279eb61db560321a8f36943ce5d635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-wcf-services-in-code"></a>WCF Hizmetlerini Kodda Yapılandırma
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Yapılandırma dosyalarının veya kod kullanarak hizmetleri yapılandırma yayınlamasına izin verir.  Yapılandırma dosyaları bir hizmet dağıtılan sonra yapılandırılması gerektiğinde faydalıdır. Yapılandırma dosyaları kullanırken, bir BT Uzmanı yapılandırma dosyasını güncelleştirmek yeterlidir, hiçbir yeniden derlenmek gereklidir. Yapılandırma dosyaları, ancak, karmaşık ve korumak zor olabilir. Hata ayıklama yapılandırma dosyaları için desteği yoktur ve yapılandırma öğeleri zor ve hataya yatkın yapılandırma dosyalarını geliştirme kılan adları tarafından başvurulur. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Ayrıca Hizmetleri kodda yapılandırmanıza olanak sağlar. Önceki sürümlerinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 ve önceki) hizmetlerini kodda yapılandırma kendini barındıran senaryolarda kolay <xref:System.ServiceModel.ServiceHost> uç noktaları ve ServiceHost.Open çağırmadan önce davranışları yapılandırmak için sınıfa izin verilmiyor. Webde barındırılan senaryolarda, ancak, doğrudan erişiminiz yok <xref:System.ServiceModel.ServiceHost> sınıfı. Barındırılan hizmeti oluşturmak için gerekli bir web yapılandırmak için bir `System.ServiceModel.ServiceHostFactory` oluşturulan <xref:System.ServiceModel.Activation.ServiceHostFactory> ve gerekli olan herhangi bir yapılandırmaya gerçekleştirilir. .NET 4.5 ile başlayan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] daha kolay bir yolu kendi kendini barındıran her ikisi de yapılandırmak ve web hizmetlerini kodda barındırılan sağlar.  
  
## <a name="the-configure-method"></a>Yapılandırma yöntemi  
 Yalnızca adlı genel statik yöntemi tanımlayın `Configure` hizmet uygulaması sınıfınızda aşağıdaki imzayla:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Yapılandırma yöntemine geçen bir <xref:System.ServiceModel.ServiceConfiguration> uç noktaları ve davranışları eklemek Geliştirici etkinleştirir örneği. Bu yöntem tarafından çağrılır [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı açılmadan önce. Tanımlandığında, bir app.config veya web.config dosyasında belirtilen tüm hizmet yapılandırma ayarları göz ardı edilir.  
  
 Aşağıdaki kod parçacığını nasıl tanımlanacağı gösterilmektedir `Configure` yöntemi ve hizmet uç noktası, bir uç noktası davranışı ve hizmet davranışları ekleyin:  
  
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
            return string.Format("You entered: {0}", value);  
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
  
 Bir hizmet için https gibi bir protokolü etkinleştirmek için ya da açıkça protokolünü kullanan bir uç nokta ekleyebilir ve her taban adresi için bir uç nokta ekleyen ServiceConfiguration.EnableProtocol(Binding) çağırarak otomatik olarak uç noktalar ekleyebilirsiniz protokol ve tanımlanan her hizmet sözleşmesi ile uyumludur. Aşağıdaki kod ServiceConfiguration.EnableProtocol yönteminin nasıl kullanılacağını gösterir:  
  
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
  
 Ayarlarında <`protocolMappings`> bölümünde hiç uygulama uç nokta eklenir, yalnızca kullanılır <xref:System.ServiceModel.ServiceConfiguration> programlı olarak. Çağırarak hizmet yapılandırmasını varsayılan uygulama yapılandırma dosyasından isteğe bağlı olarak yükleyebilir <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ve ayarlarını değiştirin. <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Sınıfı ayrıca yapılandırma merkezi yapılandırmasından yük olanak tanır. Aşağıdaki kod, bu uygulama verilmektedir:  
  
```  
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
>  Unutmayın <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> yoksayar <`host`> içindeki ayarlar <`service`> etiket <`system.serviceModel`>. Kavramsal olarak, <`host`> ana bilgisayar yapılandırması, değil hizmet yapılandırmasını ve bu hakkında yapılandırma yöntemi yürütülmeden önce yüklenen alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [İstemci Davranışlarını Yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)  
 [Yapılandırma Temelli Etkinleştirme](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [Yapılandırma](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [Yapılandırma ve Meta Veri Desteği](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [Yapılandırma](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [Nasıl yapılır: Yapılandırmada Hizmet Bağlaması Belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Nasıl yapılır: Yapılandırmada İstemci Bağlaması Belirtme](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
