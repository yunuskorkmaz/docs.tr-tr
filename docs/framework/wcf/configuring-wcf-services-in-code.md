---
title: WCF Hizmetlerini Kodda Yapılandırma
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174816"
---
# <a name="configuring-wcf-services-in-code"></a>WCF Hizmetlerini Kodda Yapılandırma
Windows Communication Foundation (WCF), geliştiricilerin hizmetleri yapılandırma dosyalarını veya kodunu kullanarak yapılandırmalarına olanak tanır.  Yapılandırma dosyaları, bir hizmetin dağıtıldıktan sonra yapılandırılması gerektiğinde yararlıdır. Yapılandırma dosyalarını kullanırken, bt uzmanının yalnızca yapılandırma dosyasını güncelleştirmesi gerekir, yeniden derleme gerekmez. Ancak yapılandırma dosyaları karmaşık ve bakımı zor olabilir. Hata ayıklama yapılandırma dosyaları için destek yoktur ve yapılandırma öğeleri yapılandırma dosyaları yazma hata eğilimli ve zor kılan adlarla başvurur. WCF ayrıca hizmetleri kod halinde yapılandırmanıza da olanak tanır. WCF'nin önceki sürümlerinde (4.0 ve daha önceki) hizmetleri kodda yapılandırmak kendi kendine barındırılan senaryolarda kolaydı, <xref:System.ServiceModel.ServiceHost> sınıf ServiceHost.Open'ı aramadan önce uç noktaları ve davranışları yapılandırmanıza olanak sağladı. Ancak, web barındırılan senaryolarda <xref:System.ServiceModel.ServiceHost> sınıfa doğrudan erişiminiz yoktur. Web barındırılan bir hizmeti yapılandırmak `System.ServiceModel.ServiceHostFactory` için, <xref:System.ServiceModel.Activation.ServiceHostFactory> gerekli yapılandırmayı oluşturan ve gerçekleştiren bir web barındırma hizmeti oluşturmanız gerekiyordu. .NET 4.5 ile başlayarak WCF, hem kendi kendine barındırılan hem de web barındırılan hizmetleri kod halinde yapılandırmanın daha kolay bir yolunu sağlar.  
  
## <a name="the-configure-method"></a>Yapılandırma yöntemi  
 Hizmet uygulama sınıfınızda `Configure` aşağıdaki imzayla çağrılan genel statik bir yöntem tanımlamanız yeterlidir:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Yapılandırma yöntemi, geliştiricinin uç nokta ve davranış eklemesine olanak tanıyan bir <xref:System.ServiceModel.ServiceConfiguration> örnek alır. Bu yöntem, hizmet ana bilgisayarı açılmadan önce WCF tarafından çağrılır. Tanımlandığında, app.config veya web.config dosyasında belirtilen hizmet yapılandırma ayarları yoksayılır.  
  
 Aşağıdaki kod parçacığı `Configure` yöntemi tanımlamak ve bir hizmet bitiş noktası, bir bitiş noktası davranışı ve hizmet davranışları eklemek nasıl gösteriş:  
  
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
  
 Bir hizmet için https gibi bir protokolü etkinleştirmek için, protokolü kullanan bir bitiş noktası nı açıkça ekleyebilirsiniz veya her temel adres için bir bitiş noktası ekleyen ServiceConfiguration.EnableProtocol(Binding) numaralı telefonu arayarak otomatik olarak uç noktaları ekleyebilirsiniz protokol ve tanımlanan her hizmet sözleşmesi ile uyumludur. Aşağıdaki kod ServiceConfiguration.EnableProtocol yönteminin nasıl kullanılacağını göstermektedir:  
  
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
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 <`protocolMappings`> bölümündeki ayarlar yalnızca <xref:System.ServiceModel.ServiceConfiguration> programlı olarak uygulama uç noktaları eklenmezse kullanılır. Varsayılan uygulama yapılandırma dosyasından isteğe bağlı olarak <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> hizmet yapılandırmasını arayarak yükleyebilir ve ardından ayarları değiştirebilirsiniz. Sınıf <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> ayrıca merkezi bir yapılandırma yapılandırma yüklemenize olanak sağlar. Aşağıdaki kod, bunun nasıl uygulanacağını göstermektedir:  
  
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
> <`system.serviceModel` <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>> <`host` `service`> etiketindeki <> ayarları yok saydığını unutmayın. Kavramsal olarak, `host` <> hizmet yapılandırması ile değil, ana bilgisayar yapılandırması ile ilgilidir ve Yapılandırma yöntemi yürütülmeden önce yüklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)
- [İstemci Davranışlarını Yapılandırma](configuring-client-behaviors.md)
- [Basitleştirilmiş Yapılandırma](simplified-configuration.md)
- [Yapılandırma](./samples/configuration-sample.md)
- [IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [Yapılandırma ve Meta Veri Desteği](./extending/configuration-and-metadata-support.md)
- [Yapılandırma](./diagnostics/exceptions-reference/configuration.md)
- [Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme](how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme](how-to-specify-a-client-binding-in-configuration.md)
