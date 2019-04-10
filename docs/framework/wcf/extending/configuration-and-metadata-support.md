---
title: Yapılandırma ve Meta Veri Desteği
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: abc9177fcc7b338a365d61721b63041ddcd68ab9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298311"
---
# <a name="configuration-and-metadata-support"></a>Yapılandırma ve Meta Veri Desteği
Bu konu, bağlamalar ve bağlama öğeleri yapılandırma ve meta veri desteğini etkinleştirmek açıklar.  
  
## <a name="overview-of-configuration-and-metadata"></a>Yapılandırma ve meta veri genel bakış  
 İsteğe bağlı öğeler 1, 2 ve 4 aşağıdaki görevleri bu konuda ele alınmıştır, [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md) görev listesi.  
  
-   Yapılandırma dosyası bir bağlama öğesi desteğini etkinleştirme.  
  
-   Yapılandırma dosyası bağlama desteğini etkinleştirme.  
  
-   WSDL ve ilke onaylamaları için bir bağlama öğesi veriliyor.  
  
-   WSDL ve ilke Onaylamalar eklemek ve bağlama veya bağlama öğesi yapılandırmak için tanımlayıcı.  
  
 Kullanıcı tanımlı bağlamalar ve bağlama öğeleri oluşturma hakkında daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) ve [BindingElement oluşturma](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)sırasıyla.  
  
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Yapılandırma dosyası bir kanal desteğini etkinleştirmek için iki yapılandırma bölümlerini uygulamalıdır <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, bağlama öğeleri, yapılandırma desteği sağlar ve <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, yapılandırma desteğini etkinleştir bağlamalar.  
  
 Bunu yapmak için daha kolay bir yolu kullanmaktır [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) bağlamalar ve bağlama öğeleri yapılandırma kodunu oluşturmak için örnek araç.  
  
### <a name="extending-bindingelementextensionelement"></a>BindingElementExtensionElement genişletme  
 Aşağıdaki kod örneği alınır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek. `UdpTransportElement` Olduğu bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> kullanıma sunan `UdpTransportBindingElement` yapılandırma sistemi için. Birkaç temel geçersiz kılmaları ile örnek yapılandırma bölümü adı, bağlama öğesi türü ve bağlama öğesi oluşturulacağını tanımlar. Kullanıcılar ardından uzantısı bölümüne bir yapılandırma dosyasında şu şekilde kaydedebilirsiniz.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Uzantı UDP taşıma kullanmak için özel bağlamalar başvurulabilir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a>Bir bağlama için yapılandırması ekleniyor  
 Bölüm `SampleProfileUdpBindingCollectionElement` olduğu bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `SampleProfileUdpBinding` yapılandırma sistemi için. Toplu uygulama için temsilci `SampleProfileUdpBindingConfigurationElement`, öğesinden türetildiğini <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` Üzerinde özelliklerine karşılık gelen özelliklerle sahip `SampleProfileUdpBinding`ve eşlenecek işlevleri `ConfigurationElement` bağlama. Son olarak, `OnApplyConfiguration` yöntemi geçersiz kılınmıştır `SampleProfileUdpBinding`aşağıdaki örnek kodda gösterildiği gibi.  
  
```csharp 
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 Bu işleyici yapılandırma sistemi ile kaydetmek için aşağıdaki bölümde ilgili yapılandırma dosyasına ekleyin.  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Öğesinden sonra başvurulabilir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma bölümü.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Bir bağlama öğesi meta veri desteği eklendi  
 Bir kanal meta verileri sisteme tümleştirmek için içeri aktarma ve dışarı aktarma İlkesi desteklemelidir. Bu gibi araçlar sağlayan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bağlama öğesi istemcileri oluşturulacak.  
  
### <a name="adding-wsdl-support"></a>WSDL desteği ekleme  
 Bir bağlamadaki aktarım bağlama öğesinin dışarı ve içeri aktarma adres bilgilerini meta verilerinde sorumludur. SOAP bağlama kullanırken, aktarım bağlama öğesinin de meta verilerde doğru aktarım URI dışarı aktarmanız gerekir. Aşağıdaki kod örneği alınır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
#### <a name="wsdl-export"></a>WSDL dışarı aktarma  
 Adresleme bilgilerini dışarı aktarmak için `UdpTransportBindingElement` uygulayan <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimi. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Yöntemi WSDL bağlantı noktasına doğru adres bilgisi ekler.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Uygulaması <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> yöntemi uç nokta bir SOAP bağlama kullandığında bir aktarım URI ayrıca verir:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL içeri aktarma  
 Adresleri içeri aktarma işlemek için WSDL içeri aktarma sistemini genişletmek için aşağıdaki yapılandırma Svcutil.exe.config dosyasında gösterildiği Svcutil.exe için yapılandırma dosyasına ekleyin:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Svcutil.exe çalıştırırken, WSDL içeri aktarma uzantıları yüklemek için Svcutil.exe alma iki seçenek vardır:  
  
1. Noktası Svcutil.exe /SvcutilConfig kullanarak yapılandırma dosyasının:\<Dosya >.  
  
2. Yapılandırma bölümü Svcutil.exe.config için Svcutil.exe ile aynı dizinde ekleyin.  
  
 `UdpBindingElementImporter` Yazın uygular <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi. `ImportEndpoint` Yöntemi WSDL bağlantı noktasından adresini alır:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>İlke desteği ekleme  
 Özel bağlama öğesi bağlamasında, bağlama öğesi yeteneklerini ifade etmek için WSDL hizmet uç noktası ilke onaylamalarını dışa aktarabilirsiniz. Aşağıdaki kod örneği alınır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
#### <a name="policy-export"></a>İlkeyi dışarı aktarma  
 `UdpTransportBindingElement` Yazın uygular <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> ilke dışarı aktarma için destek eklemek için. Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> içerir `UdpTransportBindingElement` içerdiği herhangi bir bağlama için ilke oluşturma.  
  
 İçinde <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, kanal çok noktaya yayın modunda değilse, UDP ve başka bir onaylama için onaylama Ekle. Çok noktaya yayın modu etkilediğinden nasıl iletişim yığını oluşturulur ve bu nedenle her iki tarafın arasında koordine edilmelidir budur.  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Özel Aktarım bağlama öğeleriyle adresleme, işleme için sorumlu olduğundan <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> mantığınız `UdpTransportBindingElement` WS-Addressing sürümü belirtmek için uygun WS-Addressing ilke onaylamalarını dışa aktarma işlemesi gerekir kullanılan.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>İlke içeri aktarma  
 İlke içeri aktarma sistemini genişletmek için aşağıdaki yapılandırma yapılandırma dosyasına için Svcutil.exe Svcutil.exe.config dosyasında gösterildiği gibi ekleyin:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Biz uygulamak sonra <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> bizim kayıtlı sınıfından (`UdpBindingElementImporter`). İçinde <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, uygun ad alanındaki bir onayları incelemek ve işlemek olanları taşıma oluşturma ve çok noktaya yayın olup olmadığı denetleniyor. Ayrıca, içeri Aktarıcı işleyen bir onayları onaylar bağlama listeden kaldırın. Yeniden Svcutil.exe çalıştırırken tümleştirme için iki seçenek vardır:  
  
1. Noktası Svcutil.exe /SvcutilConfig kullanarak bizim yapılandırma dosyasına:\<Dosya >.  
  
2. Yapılandırma bölümü Svcutil.exe.config için Svcutil.exe ile aynı dizinde ekleyin.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Özel standart içeri Aktarıcı bağlama ekleme  
 Svcutil.exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü varsayılan olarak tanıyacak ve sistem tarafından sağlanan bağlamalar içeri aktarın. Aksi takdirde, bağlama olarak içeri aktarılan alır bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örneği. Svcutil.exe sağlamak ve <xref:System.ServiceModel.Description.WsdlImporter> içeri aktarmak için `SampleProfileUdpBinding` `UdpBindingElementImporter` da bir standart özel bağlama alıcısı davranır.  
  
 Standart özel bağlama içeri Aktarıcı uygulayan `ImportEndpoint` yöntemi <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> incelemek için arabirimi <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> , belirli bir standart bağlama tarafından oluşturulmuş, görmek için meta verileri içeri aktarılan örnek.  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Genellikle, bir özel standart bağlama içeri Aktarıcı uygulama standart bağlama tarafından ayarlanmış olabilir yalnızca özellikleri değiştirildi ve diğer tüm özellikler varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğeleri özelliklerini denetleme içerir. Standart bağlama içeri Aktarıcı uygulamak için temel bir strateji olan standart bağlama öğesinin bir örneğini oluşturur, standart bağlamayı destekleyen standart bağlama örneği ve karşılaştırma bağlama öğeleri özelliklerinden bağlama yayma içeri aktarılan bağlama öğeleri standart bağlama öğeleri.
