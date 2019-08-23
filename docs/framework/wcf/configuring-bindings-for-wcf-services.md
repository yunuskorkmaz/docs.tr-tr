---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: bfcdcd172d96660c3351926a9c42d298ac3fa654
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928561"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
Uygulama oluştururken genellikle, uygulamanın dağıtımıyla sonra kararları yöneticiye erteleyebilirsiniz. Örneğin, bir hizmet adresinin veya Tekdüzen kaynak tanımlayıcısının (URI) ne kadar ilerlediğinin bilmesinin bir yolu yoktur. Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir. Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.  
  
> [!NOTE]
> Yapılandırma dosyalarını hızlı bir şekilde oluşturmak için [ServiceModel meta veri yardımcı programı 'nı (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) `/config` anahtarla birlikte kullanın.  
  
## <a name="major-sections"></a>Ana bölümler  
 Windows Communication Foundation (WCF) yapılandırma şeması, aşağıdaki üç ana bölümü içerir (`serviceModel`, `bindings`ve `services`):  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a>ServiceModel öğeleri  
 Bir hizmet türünü bir veya daha fazla uç `system.ServiceModel` nokta ile ve bir hizmetin ayarlarını yapılandırmak için, öğesiyle sınırlanan bölümü kullanabilirsiniz. Her uç nokta daha sonra bir adresle, sözleşmeyle ve bağlamasıyla yapılandırılabilir. Uç noktalar hakkında daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md). Hiçbir uç nokta belirtilmemişse, çalışma zamanı varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
 Bir bağlama, aktarımları (HTTP, TCP, kanallar, Message Queuing) ve protokolleri (güvenlik, güvenilirlik, Işlem akışları) belirtir ve her biri bir uç noktanın dünya ile nasıl iletişim kuracağını belirten bağlama öğelerinden oluşur.  
  
 Örneğin, [ \<BasicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesinin belirtilmesi, bir uç nokta için aktarım olarak http kullanacağınızı gösterir. Bu uç noktayı kullanan hizmet açıldığında bitiş noktasını çalışma zamanında bağlamak için kullanılır.  
  
 İki tür bağlama vardır: önceden tanımlanmış ve özel. Önceden tanımlanmış bağlamalar, yaygın senaryolarda kullanılan öğelerin yararlı birleşimlerini içerir. WCF 'nin sağladığı önceden tanımlanmış bağlama türlerinin bir listesi için bkz. [sistem tarafından sağlanan bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md). Önceden tanımlanmış bağlama koleksiyonu, bir hizmet uygulamasının ihtiyacı olan özelliklerin doğru birleşimine sahip değilse, uygulamanın gereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz. Özel Bağlamalar hakkında daha fazla bilgi için bkz [ \<. CustomBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Aşağıdaki dört örnekte, bir WCF hizmeti ayarlamak için kullanılan en yaygın bağlama yapılandırmalarının gösterilmektedir.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Bağlama türünü kullanmak için bir uç nokta belirtme  
 İlk örnek, bir adres, sözleşme ve bağlama ile yapılandırılan bir uç noktanın nasıl belirtildiğini gösterir.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 Bu örnekte `name` öznitelik, yapılandırmanın hangi hizmet türüyle ilgili olduğunu gösterir. `HelloWorld` Sözleşmeniz ile kodunuzda bir hizmet oluşturduğunuzda, örnek yapılandırmasında tanımlanan tüm uç noktalar ile başlatılır. Derleme yalnızca bir hizmet sözleşmesi uygularsa, `name` hizmet kullanılabilir tek türü kullandığından öznitelik atlanabilir. Öznitelik, biçiminde olması gereken bir dize alır`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` Özniteliği diğer uç noktaların hizmetle iletişim kurmak için kullandığı URI 'yi belirtir. URI mutlak ya da göreli yol olabilir. Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım düzeni için uygun bir temel adres sağlaması beklenir. Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.  
  
 `contract` Öznitelik, bu uç noktanın sunduğu sözleşmeyi belirtir. Hizmet uygulaması türü, anlaşma türünü uygulamalıdır. Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.  
  
 Öznitelik `binding` , bu belirli uç nokta için kullanılmak üzere önceden tanımlanmış veya özel bir bağlama seçer. Açıkça bir bağlama olmayan bir uç nokta, varsayılan bağlama seçimini `BasicHttpBinding`kullanır.  
  
#### <a name="modifying-a-predefined-binding"></a>Önceden tanımlanmış bağlamayı değiştirme  
 Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilmiştir. Daha sonra, hizmette herhangi bir uç noktayı yapılandırmak için kullanılabilir. Bağlama <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> değeri 1 saniye olarak ayarlanarak değiştirilir. Özelliğin bir <xref:System.TimeSpan> nesne döndürdüğünü unutmayın.  
  
 Değiştirilen bağlama bağlamalar bölümünde bulunur. Bu değiştirilmiş bağlama artık `binding` `endpoint` öğedeki özniteliği ayarlanarak herhangi bir uç nokta oluşturulurken kullanılabilir.  
  
> [!NOTE]
> Bağlama için belirli bir ad verirseniz, hizmet uç noktasında `bindingConfiguration` belirtilen ' ın onunla eşleşmesi gerekir.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Bir hizmete uygulanacak davranışı yapılandırma  
 Aşağıdaki örnekte, hizmet türü için belirli bir davranış yapılandırılır. Öğesi, [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti sorgulamak ve meta verilerden Web Hizmetleri Açıklama Dili (wsdl) belgeleri oluşturmak için kullanılır. `ServiceMetadataBehavior`  
  
> [!NOTE]
> Davranışa belirli bir ad verirseniz, `behaviorConfiguration` hizmet veya uç nokta bölümünde belirtilen bir ad ile aynı olmalıdır.  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 Önceki yapılandırma, bir istemcinin "HelloWorld" türü belirlenmiş hizmetin meta verilerini aramasını ve almasını sağlar.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Farklı bağlama değerleri kullanarak Iki uç nokta içeren bir hizmet belirtme  
 Bu son örnekte, `HelloWorld` hizmet türü için iki uç nokta yapılandırılır. Her uç nokta aynı bağlama türünün `bindingConfiguration` farklı bir özelleştirilmiş özniteliğini kullanır (her biri ' nı `basicHttpBinding`değiştirir).  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 Aşağıdaki örnekte gösterildiği gibi bir `protocolMapping` bölüm ekleyerek ve bağlamaları yapılandırarak varsayılan yapılandırmayı kullanarak aynı davranışı sağlayabilirsiniz.  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md)
- [Uç Nokta Oluşturmaya Genel Bakış](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
