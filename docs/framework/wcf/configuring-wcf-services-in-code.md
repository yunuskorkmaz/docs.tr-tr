---
title: WCF Hizmetlerini Kodda Yapılandırma
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: d55c4994dfa322619f7e5e5911c23d68b439646a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718773"
---
# <a name="configuring-wcf-services-in-code"></a>WCF Hizmetlerini Kodda Yapılandırma
Windows Communication Foundation (WCF) hizmetlerini yapılandırma dosyalarının veya kod kullanarak yapılandırmak geliştiricilerin sağlar.  Yapılandırma dosyalarını, hizmet dağıtıldıktan sonra yapılandırılması gerektiğinde kullanışlıdır. Yapılandırma dosyalarını kullanarak, bir BT Uzmanı yalnızca yapılandırma dosyasını güncelleştirmeniz gerekir, hiçbir yeniden derleme gereklidir. Yapılandırma dosyaları, ancak karmaşık ve sürdürülmesi zor olabilir. Yapılandırma dosyalarında hata ayıklama desteği yoktur ve yapılandırma öğelerini yazma yapılandırma dosyalarını zor ve hata yapmaya açık olmasını sağlayan adlarına göre başvuru yapılır. WCF hizmetlerini kodda yapılandırma sağlar. Önceki sürümlerinde (4.0 ve daha önceki) WCF yapılandırma Hizmetleri kod kendinden senaryolarda kolaydı <xref:System.ServiceModel.ServiceHost> uç noktalar ve davranışlar ServiceHost.Open çağırmadan önce yapılandırmanıza izin sınıfı. Barındırılan web senaryolarda, ancak doğrudan için erişiminiz yoksa <xref:System.ServiceModel.ServiceHost> sınıfı. Barındırılan hizmet oluşturmak için gerekli bir web yapılandırmak için bir `System.ServiceModel.ServiceHostFactory` oluşturulan <xref:System.ServiceModel.Activation.ServiceHostFactory> ve tüm gerekli yapılandırma. .NET 4.5 ile başlayarak, her ikisi de yapılandırmak için daha kolay bir yolu şirket içinde barındırılan ve web hizmetleri kod barındırılan WCF sağlar.  
  
## <a name="the-configure-method"></a>Yapılandırma yöntemi  
 Adlı bir ortak statik metodun yalnızca tanımlama `Configure` aşağıdaki hizmet uygulaması sınıfınızın imzasında ile:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Yapılandırma yöntemi alır bir <xref:System.ServiceModel.ServiceConfiguration> uç noktalar ve davranışlar eklemek geliştiricinin örneği. Bu yöntem, hizmet ana bilgisayarı açılmadan önce WCF tarafından çağrılır. Tanımlandığında, bir app.config veya web.config dosyasında belirtilen tüm hizmet yapılandırma ayarları göz ardı edilir.  
  
 Aşağıdaki kod parçacığını nasıl tanımlanacağı anlatılmakta `Configure` yöntemi ve bir hizmet uç noktası, bir uç nokta davranışı ve hizmet davranışlarını ekleyin:  
  
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
  
 Https için bir hizmet gibi bir protokolü etkinleştirmek için ya da açıkça protokolünü kullanan bir uç nokta ekleyebilirsiniz veya otomatik olarak, her bir temel adres için bir uç nokta ekleyen ServiceConfiguration.EnableProtocol(Binding) çağırarak uç noktalar ekleyebilirsiniz protokol ve tanımlanan her bir hizmet sözleşmesi ile uyumlu. Aşağıdaki kod ServiceConfiguration.EnableProtocol yönteminin nasıl kullanılacağını göstermektedir:  
  
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
  
 Ayarları <`protocolMappings`> bölüm yalnızca uygulama uç nokta için eklenirse kullanılan <xref:System.ServiceModel.ServiceConfiguration> programlı olarak. Çağırarak hizmet yapılandırmasını varsayılan uygulama yapılandırma dosyasından isteğe bağlı olarak yükleyebilir <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ve ayarlarını değiştirin. <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Sınıfı ayrıca yapılandırma merkezi yapılandırmasından yük olanak tanır. Aşağıdaki kod bunu uygulamak nasıl gösterir:  
  
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
>  Unutmayın <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> yoksayar <`host`> ayarlarında <`service`> etiketi <`system.serviceModel`>. Kavramsal olarak, <`host`> ana bilgisayar yapılandırması, olmayan hizmet yapılandırması ve onu hakkında yapılandırma yöntemi yürütülmeden önce yüklenen alır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [İstemci Davranışlarını Yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)
- [Yapılandırma](../../../docs/framework/wcf/samples/configuration-sample.md)
- [IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [Yapılandırma ve Meta Veri Desteği](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [Yapılandırma](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [Nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Nasıl yapılır: Yapılandırmada istemci bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
