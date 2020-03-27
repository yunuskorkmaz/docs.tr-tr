---
title: Yapılandırma ve Meta Veri Desteği
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: fb4e1cc51b827f083e580362f57df27ced770179
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345293"
---
# <a name="configuration-and-metadata-support"></a>Yapılandırma ve Meta Veri Desteği
Bu konu, bağlamalar ve bağlama öğeleri için yapılandırma ve meta veri desteğinin nasıl etkinleştirilen açıklanır.  
  
## <a name="overview-of-configuration-and-metadata"></a>Yapılandırma ve Meta Verilere Genel Bakış  
 Bu konu, [Gelişmekte Olan Kanallar](developing-channels.md) görev listesinde isteğe bağlı öğeler 1, 2 ve 4 olan aşağıdaki görevleri tartışır.  
  
- Bağlama öğesi için yapılandırma dosyası desteğini etkinleştirme.  
  
- Bağlama için yapılandırma dosyası desteğini etkinleştirme.  
  
- Bağlayıcı bir öğe için WSDL ve ilke iddiaları dışa aktarma.  
  
- Bağlayıcı veya bağlayıcı öğenizi eklemek ve yapılandırmak için WSDL ve ilke iddialarını tanımlama.  
  
 Kullanıcı tanımlı bağlamalar ve bağlama öğeleri oluşturma hakkında bilgi için sırasıyla [Kullanıcı Tanımlı Bağlamalar Oluşturma](creating-user-defined-bindings.md) ve [Bağlama Öğesi Oluşturma'ya](creating-a-bindingelement.md)bakın.  
  
## <a name="adding-configuration-support"></a>Yapılandırma Desteği Ekleme  
 Bir kanal için yapılandırma dosyası desteğini etkinleştirmek için, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>bağlama öğeleri <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>için yapılandırma desteği sağlayan ve bağlayıcılar için yapılandırma desteğini etkinleştiren iki yapılandırma bölümü uygulamanız gerekir.  
  
 Bunu yapmanın daha kolay bir yolu, bağlamalarınız ve bağlama öğeleriniz için yapılandırma kodu oluşturmak için [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) örnek aracını kullanmaktır.  
  
### <a name="extending-bindingelementextensionelement"></a>CiltlemeElementExtensionElement  
 Aşağıdaki örnek kod [Transport: UDP](../samples/transport-udp.md) örneğinden alınmıştır. Yapılandırma `UdpTransportElement` sistemine <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> maruz `UdpTransportBindingElement` olan bir dir. Birkaç temel geçersiz kılmayla, örnek yapılandırma kesit adını, bağlama öğesinin türünü ve bağlama öğesinin nasıl oluşturulmasını tanımlar. Kullanıcılar daha sonra uzantı bölümünü bir yapılandırma dosyasına aşağıdaki gibi kaydedebilirler.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Uzantı, udp'yi aktarım olarak kullanmak için özel bağlamalardan başvurulabilir.  
  
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
  
### <a name="adding-configuration-for-a-binding"></a>Bağlama için Yapılandırma Ekleme  
 Bölüm, `SampleProfileUdpBindingCollectionElement` yapılandırma <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> sistemine `SampleProfileUdpBinding` maruz kalan bir bölümdür. Uygulamanın büyük bir kısmı `SampleProfileUdpBindingConfigurationElement`, ' den <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen . Üzerinde `SampleProfileUdpBindingConfigurationElement` özellikleri `SampleProfileUdpBinding`karşılık gelen özelliklere sahip ve `ConfigurationElement` bağlama eşlenecek işlevleri. Son olarak, `OnApplyConfiguration` `SampleProfileUdpBinding`yöntem, aşağıdaki örnek kodda gösterildiği gibi, geçersiz kılınmış.  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 Bu işleyiciyi yapılandırma sistemine kaydetmek için aşağıdaki bölümü ilgili yapılandırma dosyasına ekleyin.  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Daha sonra [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma bölümünden başvurulabilir.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Bağlayıcı Öğe için Meta Veri Desteği Ekleme  
 Bir kanalı meta veri sistemine entegre etmek için, hem ipolitikasının hem de dışa aktarmanın desteklenmesi gerekir. Bu, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gibi araçların bağlama öğesinin istemcilerini oluşturmasına olanak tanır.  
  
### <a name="adding-wsdl-support"></a>WSDL Desteği Ekleme  
 Bağlayıcıdaki aktarım bağlama öğesi, meta verilerdeki adresleme bilgilerinin dışa aktarılmasından ve aktarılmasından sorumludur. SOAP bağlama kullanırken, taşıma bağlama elemanı da meta verilerde doğru bir aktarım URI dışa aktarmalıdır. Aşağıdaki örnek kod [Transport: UDP](../samples/transport-udp.md) örneğinden alınmıştır.  
  
#### <a name="wsdl-export"></a>WSDL İhracat  
 Adres bilgilerini dışa `UdpTransportBindingElement` aktarmak için <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimi uygular. Yöntem, <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> WSDL bağlantı noktasına doğru adresbilgilerini ekler.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 Yöntemin `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> uygulanması, bitiş noktası BIR SOAP bağlama kullandığında bir taşıma URI'si de dışa aktarmaktadır:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL İthalat  
 WSDL alma sistemini adresleri alma işlemlerini işlemek için genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe yapılandırma dosyasına aşağıdaki yapılandırmayı ekleyin:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </wsdlImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Svcutil.exe çalıştırırken, WSDL alma uzantıları yüklemek için Svcutil.exe almak için iki seçenek vardır:  
  
1. /SvcutilConfig kullanarak yapılandırma dosyasına Point Svcutil.exe:\<dosya>.  
  
2. Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.  
  
 Tür `UdpBindingElementImporter` <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi uygular. Yöntem `ImportEndpoint` wsdl bağlantı noktasından adresi içeri zabıta:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>İlke Desteği Ekleme  
 Özel bağlama öğesi, bu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet bitiş noktası için WSDL bağlayıcıilki iddialarını dışa aktarabilir. Aşağıdaki örnek kod [Transport: UDP](../samples/transport-udp.md) örneğinden alınmıştır.  
  
#### <a name="policy-export"></a>İlke İhracatı  
 Tür, `UdpTransportBindingElement` dışa aktarma ilkesi için destek eklemek için uygular. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> `UdpTransportBindingElement` bunu içeren herhangi bir bağlama için ilke oluşturma içerir.  
  
 Kanal <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>çok noktaya yayın modundaysa, UDP için bir iddia ve başka bir iddia ekleyin. Bunun nedeni, çok noktaya yayın modunun iletişim yığınının nasıl oluşturulduğuna etki etmesi ve bu nedenle her iki taraf arasında koordine edilmesi dir.  
  
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
  
 Özel aktarım bağlama öğeleri adresleme işlemekten sorumlu olduğundan, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> ws-addressing sürümünü niçin kullanıldığını göstermek için uygun WS Adresleme ilkesi iddialarını dışa aktarma yı da ele almalıdır. `UdpTransportBindingElement`  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>İlke İthalatı  
 İlke alma sistemini genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına aşağıdaki yapılandırmayı ekleyin:  
  
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
  
 Sonra bizim <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> kayıtlı sınıftan`UdpBindingElementImporter`uygulamak ( ). In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, uygun ad alanında iddiaları incelemek ve taşıma oluşturmak ve çok noktaya mı olup olmadığını kontrol etmek için olanları işlemek. Ayrıca, içe aktarıcının işlediği iddiaları bağlayıcı iddialar listesinden kaldırın. Yine, Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:  
  
1. Svcutil.exe'yi /SvcutilConfig kullanarak yapılandırma\<dosyamıza yönlendirin: dosya>.  
  
2. Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Özel Standart Bağlama İthalatçısı Ekleme  
 Svcutil.exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü, varsayılan olarak, tanımak ve sistem tarafından sağlanan bağlamaları alma. Aksi takdirde, bağlama bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örnek olarak içe aktarılır. Svcutil.exe ve almak <xref:System.ServiceModel.Description.WsdlImporter> `SampleProfileUdpBinding` için `UdpBindingElementImporter` de özel bir standart bağlayıcı ithalatçı olarak hareket etmesini sağlamak için.  
  
 Özel bir standart bağlayıcı içe `ImportEndpoint` aktarıcı, meta <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> verilerden alınan örneği incelemek ve belirli bir standart bağlama tarafından oluşturulabilir mi diye görmek için <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimde yöntem uygular.  
  
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
  
 Genel olarak, özel bir standart bağlama içe aktarma işlemi, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılanları olduğunu doğrulamak için içe aktarılan bağlama öğelerinin özelliklerini denetlemeyi içerir. Standart bağlayıcı lık uygulamak için temel bir strateji, standart bağlamanın bir örneğini oluşturmak, özellikleri bağlama öğelerinden standart bağlamanın desteklediği standart bağlama örneğine yaymak ve bağlamayı karşılaştırmaktır. alınan bağlama elemanları ile standart bağlama öğeleri.
