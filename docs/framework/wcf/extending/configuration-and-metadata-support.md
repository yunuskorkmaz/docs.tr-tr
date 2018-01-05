---
title: "Yapılandırma ve Meta Veri Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d22beac94d6055350961f62e43071b54a4916f04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-and-metadata-support"></a>Yapılandırma ve Meta Veri Desteği
Bu konu, bağlamalar ve bağlama öğeleri yapılandırma ve meta veri desteğini etkinleştirmek açıklar.  
  
## <a name="overview-of-configuration-and-metadata"></a>Yapılandırma ve meta veri genel bakış  
 Bu konuda 1, 2 ve 4 isteğe bağlı öğeleri aşağıdaki görevler ele alınmıştır içinde [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md) görev listesi.  
  
-   Yapılandırma dosyası bir bağlama öğesi desteğini etkinleştirme.  
  
-   Yapılandırma dosyası bir bağlama desteğini etkinleştirme.  
  
-   Bir bağlama öğesi için WSDL ve ilke onaylamalarını dışa aktarma.  
  
-   WSDL ve ilke onaylamalarını eklemek ve bağlama veya bağlama öğesi yapılandırmak için tanımlayıcı.  
  
 Kullanıcı tanımlı bağlamalar ve bağlama öğeleri oluşturma hakkında daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) ve [BindingElement oluşturma](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)sırasıyla.  
  
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Yapılandırma dosyası bir kanal desteğini etkinleştirmek için iki yapılandırma bölümlerinin uygulamalıdır <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, bağlama öğeleri, yapılandırma desteği sağlar ve <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, yapılandırma desteğini etkinleştir bağlamaları.  
  
 Bunu yapmak için daha kolay bir yolu kullanmaktır [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) bağlamalar ve bağlama öğeleri yapılandırma kodunu oluşturmak için örnek araç.  
  
### <a name="extending-bindingelementextensionelement"></a>BindingElementExtensionElement genişletme  
 Aşağıdaki kod örneği alınırlar [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek. `UdpTransportElement` Olan bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> kullanıma sunan `UdpTransportBindingElement` yapılandırma sistemi. Birkaç temel geçersiz kılmalar, örnek yapılandırma bölümü adı, bağlama öğesi türü ve bağlama öğesi oluşturmak nasıl tanımlar. Kullanıcılar daha sonra uzantısı bölümüne bir yapılandırma dosyasında şu şekilde kaydedebilirsiniz.  
  
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
  
 Uzantı UDP taşıma olarak kullanmak için özel bağlamalar başvurulabilir.  
  
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
 Bölüm `SampleProfileUdpBindingCollectionElement` olan bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `SampleProfileUdpBinding` yapılandırma sistemi. Uygulama toplu temsilci için `SampleProfileUdpBindingConfigurationElement`, den türetilen <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` Özellikler üzerinde karşılık gelen özelliklere sahip `SampleProfileUdpBinding`ve eşlenecek işlevleri `ConfigurationElement` bağlama. Son olarak, `OnApplyConfiguration` yöntemi geçersiz kılınmıştır `SampleProfileUdpBinding`, aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Bir bağlama öğesi için meta verileri desteği ekleme  
 Bir kanal meta verileri sistemle tümleştirmek için içeri ve dışarı aktarma İlkesi desteklemelidir. Bu gibi araçlar sağlar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bağlama öğesi istemcileri oluşturmak için.  
  
### <a name="adding-wsdl-support"></a>WSDL desteği ekleme  
 Bir bağlama aktarım bağlama öğe meta verileri adresleme bilgilerini alma ve verme sorumludur. SOAP bağlama kullanırken, aktarım bağlama öğesi de meta verilerde doğru taşıma URI dışarı aktarmanız gerekir. Aşağıdaki kod örneği alınırlar [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
#### <a name="wsdl-export"></a>WSDL dışarı aktarma  
 Adresleme bilgilerini dışarı aktarmak için `UdpTransportBindingElement` uygulayan <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimi. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Yöntemi WSDL bağlantı noktasına doğru adresleme bilgilerini ekler.  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Uyarlamasını <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> yöntemi uç nokta bir SOAP bağlama kullandığında taşıma URI ayrıca verir:  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL içe aktarma  
 Adres alma işlemek için WSDL içe aktarma sistemini genişletmek için aşağıdaki yapılandırma Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına ekleyin:  
  
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
  
 Svcutil.exe çalıştırırken WSDL içe aktarma Uzantıları'nı yüklemek için Svcutil.exe alma için iki seçeneğiniz vardır:  
  
1.  /SvcutilConfig kullanarak yapılandırma dosyasının noktası Svcutil.exe:\<Dosya >.  
  
2.  Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.  
  
 `UdpBindingElementImporter` Yazın uygulayan <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi. `ImportEndpoint` Yöntemi WSDL bağlantı noktasından adresi alır:  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>İlke desteği ekleme  
 Özel bağlama öğesi bu bağlama öğesi özelliklerini ifade etmek için bir hizmet uç noktası için WSDL bağlama ilke onaylamalarını dışa aktarabilirsiniz. Aşağıdaki kod örneği alınırlar [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
#### <a name="policy-export"></a>İlke verme  
 `UdpTransportBindingElement` Yazın Implements''<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> İlkesi dışarı aktarma desteği eklemek için. Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> içeren `UdpTransportBindingElement` içerdiği bağlama için ilke oluşturma.  
  
 İçinde <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, kanal çok noktaya yayın modunda ise bir onaylama UDP ve başka bir onaylama için ekleyin. Çok noktaya yayın modu etkilediğinden nasıl iletişim yığını oluşturulur ve böylece her iki yüz arasındaki Eşgüdümlü olmalıdır budur.  
  
```  
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
  
 Özel Aktarım bağlama öğeleriyle adresleme, işleme için sorumlu olduğu için <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> mantığınız `UdpTransportBindingElement` WS adresleme sürümünü belirtmek için uygun WS adresleme ilke onaylamalarını dışa aktarma işlemesi gerekir kullanılan.  
  
```  
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
  
 Biz uygulamak sonra <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> bizim kayıtlı sınıfından (`UdpBindingElementImporter`). İçinde <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, uygun ad alanında onaylar inceleyin ve taşıma oluşturma ve çok noktaya yayın olup olmadığını denetlemek için kullanabileceğiniz olanları işlem. Ayrıca, alıcı işleme onaylar onaylar bağlama listesinden kaldırır. Yeniden Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:  
  
1.  /SvcutilConfig kullanarak bizim yapılandırma dosyasına noktası Svcutil.exe:\<Dosya >.  
  
2.  Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>İçeri Aktarıcı bağlama özel bir standart ekleme  
 Svcutil.exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü, varsayılan olarak algılar ve sistem tarafından sağlanan bağlamalar içeri aktarın. Aksi takdirde, bağlama içeri alır bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örneği. Svcutil.exe etkinleştirmek için ve <xref:System.ServiceModel.Description.WsdlImporter> almak için `SampleProfileUdpBinding` `UdpBindingElementImporter` da özel standart bağlama alıcısı davranır.  
  
 Özel standart bağlama alma uygulayan `ImportEndpoint` yöntemi <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> incelemek için arabirimi <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> , belirli standart bağlama tarafından oluşturulmuş, görmek için meta verileri içe örneği.  
  
```  
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
  
 Genellikle, özel standart bağlama alma uygulama standart bağlama tarafından ayarlayabilirsiniz yalnızca özellikleri değişti ve diğer tüm özellikleri varsayılanlarına olduğunu doğrulamak için içe aktarılan bağlama öğeleri özelliklerini denetleme içerir. Standart bağlama alma uygulamak için bir temel stratejidir standart bağlama örneği oluşturmak için bağlama öğeleri özelliklerinden standart bağlama destekler standart bağlama örneği ve karşılaştırmak için bağlama yayma içeri aktarılan bağlama öğeleri ile standart bağlama öğeleri.
