---
title: Yapılandırma ve Meta Veri Desteği
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 3f6d506d719cbb1b2ecc8bae223dfe73e7e2d1a9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425141"
---
# <a name="configuration-and-metadata-support"></a>Yapılandırma ve Meta Veri Desteği
Bu konuda, bağlamalar ve bağlama öğeleri için yapılandırma ve meta veri desteğinin nasıl etkinleştirileceği açıklanır.  
  
## <a name="overview-of-configuration-and-metadata"></a>Yapılandırma ve meta verilere genel bakış  
 Bu konuda, [Kanallar geliştirme](developing-channels.md) görev listesinde 1, 2 ve 4 ' te isteğe bağlı olan aşağıdaki görevler ele alınmaktadır.  
  
- Bağlama öğesi için yapılandırma dosyası desteği etkinleştiriliyor.  
  
- Bağlama için yapılandırma dosyası desteğini etkinleştirme.  
  
- Bağlama öğesi için WSDL ve ilke onayları dışarı aktarılıyor.  
  
- Bağlama veya bağlama öğesini eklemek ve yapılandırmak için WSDL ve ilke onayları tanımlama.  
  
 Kullanıcı Tanımlı Bağlamalar ve bağlama öğeleri oluşturma hakkında daha fazla bilgi için, sırasıyla [Kullanıcı Tanımlı Bağlamalar Oluşturma](creating-user-defined-bindings.md) ve [bir BindingElement oluşturma](creating-a-bindingelement.md)hakkında bilgi için bkz.  
  
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Bir kanal için yapılandırma dosyası desteğini etkinleştirmek üzere, bağlama öğeleri için yapılandırma desteğinin etkinleştirildiği <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>bağlamaları için yapılandırma desteğini etkinleştiren iki yapılandırma bölümü uygulamanız gerekir.  
  
 Bunu yapmanın daha kolay bir yolu, bağlamalarınız ve bağlama öğeleriniz için yapılandırma kodu oluşturmak üzere [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) örnek aracını kullanmaktır.  
  
### <a name="extending-bindingelementextensionelement"></a>BindingElementExtensionElement genişletme  
 Aşağıdaki örnek kod [aktarımdan alınmıştır: UDP](../samples/transport-udp.md) örneği. `UdpTransportElement`, yapılandırma sistemine `UdpTransportBindingElement` sunan bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Birkaç temel geçersiz kılmalarla, örnek yapılandırma bölümü adını, bağlama öğesinin türünü ve bağlama öğesinin nasıl oluşturulacağını tanımlar. Kullanıcılar daha sonra uzantı bölümünü bir yapılandırma dosyasına aşağıdaki şekilde kaydedebilir.  
  
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
  
 Uzantıya, taşıma olarak UDP 'yi kullanmak için özel bağlamalardan başvurulabilir.  
  
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
  
### <a name="adding-configuration-for-a-binding"></a>Bağlama için yapılandırma ekleme  
 `SampleProfileUdpBindingCollectionElement` bölüm, yapılandırma sistemine `SampleProfileUdpBinding` sunan bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>. Uygulamanın toplu işlemi, <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen `SampleProfileUdpBindingConfigurationElement`için temsilci olarak oluşturulur. `SampleProfileUdpBindingConfigurationElement`, `SampleProfileUdpBinding`özelliklere ve `ConfigurationElement` bağlamalarından eşlenecek işlevlere karşılık gelen özelliklere sahiptir. Son olarak, aşağıdaki örnek kodda gösterildiği gibi `OnApplyConfiguration` yöntemi `SampleProfileUdpBinding`geçersiz kılınır.  
  
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
  
 Bu işleyiciyi yapılandırma sistemine kaydetmek için, ilgili yapılandırma dosyasına aşağıdaki bölümü ekleyin.  
  
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
  
 Daha sonra [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma bölümünden başvurulabilirler.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Bağlama öğesi için meta veri desteği ekleme  
 Bir kanalı meta veri sistemiyle bütünleştirmek için, ilkenin hem içeri ve dışarı aktarılmasını desteklemesi gerekir. Bu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gibi araçların bağlama öğesinin istemcilerini oluşturmasını sağlar.  
  
### <a name="adding-wsdl-support"></a>WSDL desteği ekleme  
 Bir bağlamadaki aktarım bağlama öğesi, meta verilerde adres bilgilerinin dışarı ve içeri aktarılmasından sorumludur. SOAP bağlama kullanılırken, aktarım bağlama öğesi meta verilerde doğru bir taşıma URI 'sini de dışarı aktarmalıdır. Aşağıdaki örnek kod [aktarımdan alınmıştır: UDP](../samples/transport-udp.md) örneği.  
  
#### <a name="wsdl-export"></a>WSDL dışarı aktarma  
 Adres bilgilerini dışarı aktarmak için `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimini uygular. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> yöntemi, WSDL bağlantı noktasına doğru adres bilgilerini ekler.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> yönteminin `UdpTransportBindingElement` uygulanması, uç nokta bir SOAP bağlama kullandığında bir aktarım URI 'sini de dışarı aktarır:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Içeri aktarma  
 WSDL içeri aktarma sistemini adresleri içeri aktarmayı işleyecek şekilde genişletmek için, Svcutil. exe. config dosyasında gösterildiği gibi Svcutil. exe için yapılandırma dosyasına aşağıdaki yapılandırmayı ekleyin:  
  
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
  
 Svcutil. exe dosyasını çalıştırırken, Svcutil. exe ' nin WSDL içeri aktarma uzantılarını yüklemesi için iki seçenek vardır:  
  
1. /SvcutilConfig:\<Dosya > kullanarak Svcutil. exe ' yi yapılandırma dosyasına yazın.  
  
2. Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.  
  
 `UdpBindingElementImporter` türü <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimini uygular. `ImportEndpoint` yöntemi, adresi WSDL bağlantı noktasından içeri aktarır:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Ilke desteği ekleme  
 Özel bağlama öğesi, söz konusu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet uç noktası için WSDL bağlamasındaki ilke onaylamalarını dışarı aktarabilir. Aşağıdaki örnek kod [aktarımdan alınmıştır: UDP](../samples/transport-udp.md) örneği.  
  
#### <a name="policy-export"></a>İlke dışarı aktarma  
 `UdpTransportBindingElement` türü, ilke dışarı aktarma desteği eklemek için <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> uygular. Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>, kendisini içeren herhangi bir bağlama için ilkenin oluşturulmasına `UdpTransportBindingElement` ekler.  
  
 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, kanal çok noktaya yayın modundaysa UDP ve başka bir onaylama için onay ekleyin. Bunun nedeni, çok noktaya yayın modunun iletişim yığınının oluşturulmasını etkilemesi ve bu nedenle her iki taraf arasında koordine olması gerekir.  
  
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
  
 Özel aktarım bağlama öğeleri, adresleme 'yi işlemekten sorumlu olduğundan, `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> uygulamasının, kullanılan WS-Addressing sürümünü göstermek için uygun WS-Addressing ilke onayları vermeyi de işlemesi gerekir.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>İlke Içeri aktarma  
 İlke içeri aktarma sistemini genişletmek için, Svcutil. exe. config dosyasında gösterildiği gibi Svcutil. exe için yapılandırma dosyasına aşağıdaki yapılandırmayı ekleyin:  
  
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
  
 Ardından, kayıtlı sınıfımızdan <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> uyguladık (`UdpBindingElementImporter`). <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, uygun ad alanındaki onaylamaları inceleyin ve nakliyenlerin oluşturulması ve çok noktaya yayın olup olmadığını kontrol etmek için bunları işleyin. Ayrıca, içeri aktarıcıların bağlama onayları listesinden işlediği onayları kaldırın. Yine, Svcutil. exe dosyasını çalıştırırken, tümleştirme için iki seçenek vardır:  
  
1. Svcutil. exe ' yi,/SvcutilConfig:\<Dosya > kullanarak yapılandırma dosyanıza yazın.  
  
2. Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Özel standart bağlama Içeri aktarıcı ekleme  
 Svcutil. exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü, varsayılan olarak sistem tarafından belirtilen bağlamaları tanır ve içeri aktarır. Aksi takdirde, bağlama bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örneği olarak içeri aktarılır. Svcutil. exe ' yi ve <xref:System.ServiceModel.Description.WsdlImporter> `UdpBindingElementImporter` `SampleProfileUdpBinding` içeri aktarmak için bir özel standart bağlama alma işlemi olarak da çalışır.  
  
 Özel standart bağlama İçeri Aktarıcı, belirli bir standart bağlama tarafından oluşturulup oluşturulmadığını görmek için meta verilerden içeri aktarılan <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örneğini incelemek üzere <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimindeki `ImportEndpoint` yöntemini uygular.  
  
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
  
 Genellikle, özel bir standart bağlama alma programı uygulamak, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğelerinin özelliklerinin denetlenmesini içerir. Standart bağlama alma işlemi uygulamaya yönelik temel bir strateji, standart bağlamanın bir örneğini oluşturmaktır, bağlama öğelerinden özellikleri standart bağlamanın desteklediği standart bağlama örneğine yayar ve bağlamayı karşılaştırın İçeri aktarılan bağlama öğeleriyle standart bağlamalardan öğeler.
