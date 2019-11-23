---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 92f9457dd0c118c9a7c578a7088f66cdea1e5ad0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320663"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
Uygulama oluştururken genellikle, uygulamanın dağıtımıyla sonra kararları yöneticiye erteleyebilirsiniz. Örneğin, bir hizmet adresinin veya Tekdüzen kaynak tanımlayıcısının (URI) ne kadar ilerlediğinin bilmesinin bir yolu yoktur. Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir. Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.  
  
> [!NOTE]
> Yapılandırma dosyalarını hızlıca oluşturmak için, `/config` anahtarıyla [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
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
 Bir hizmet türünü bir veya daha fazla uç nokta ile ve bir hizmetin ayarlarını yapılandırmak için `system.ServiceModel` öğesiyle sınırlanan bölümü kullanabilirsiniz. Her uç nokta daha sonra bir adresle, sözleşmeyle ve bağlamasıyla yapılandırılabilir. Uç noktalar hakkında daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md). Hiçbir uç nokta belirtilmemişse, çalışma zamanı varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
 Bir bağlama, aktarımları (HTTP, TCP, kanallar, Message Queuing) ve protokolleri (güvenlik, güvenilirlik, Işlem akışları) belirtir ve her biri bir uç noktanın dünya ile nasıl iletişim kuracağını belirten bağlama öğelerinden oluşur.  
  
 Örneğin, [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) öğesinin belirtilmesi, bir uç nokta için aktarım olarak http kullanacağınızı gösterir. Bu uç noktayı kullanan hizmet açıldığında bitiş noktasını çalışma zamanında bağlamak için kullanılır.  
  
 İki tür bağlama vardır: önceden tanımlanmış ve özel. Önceden tanımlanmış bağlamalar, yaygın senaryolarda kullanılan öğelerin yararlı birleşimlerini içerir. WCF 'nin sağladığı önceden tanımlanmış bağlama türlerinin bir listesi için bkz. [sistem tarafından sağlanan bağlamalar](system-provided-bindings.md). Önceden tanımlanmış bağlama koleksiyonu, bir hizmet uygulamasının ihtiyacı olan özelliklerin doğru birleşimine sahip değilse, uygulamanın gereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz. Özel Bağlamalar hakkında daha fazla bilgi için bkz. [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md).  
  
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
  
 Bu örnekte, `name` özniteliği yapılandırmanın hangi hizmet türüyle ilgili olduğunu gösterir. Kodunuzda `HelloWorld` sözleşmeyle bir hizmet oluşturduğunuzda, örnek yapılandırmasında tanımlanan tüm uç noktalar ile başlatılır. Derleme yalnızca bir hizmet sözleşmesi uygularsa, hizmet kullanılabilir tek türü kullandığından `name` özniteliği atlanabilir. Öznitelik, biçiminde olması gereken bir dize alır `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` özniteliği diğer uç noktaların hizmetle iletişim kurmak için kullandığı URI 'yi belirtir. URI mutlak ya da göreli yol olabilir. Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım düzeni için uygun bir temel adres sağlaması beklenir. Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.  
  
 `contract` özniteliği bu uç noktanın sunduğu sözleşmeyi belirtir. Hizmet uygulaması türü, anlaşma türünü uygulamalıdır. Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.  
  
 `binding` özniteliği, bu belirli uç nokta için kullanılmak üzere önceden tanımlanmış veya özel bir bağlama seçer. Açıkça bir bağlama olmayan bir uç nokta, `BasicHttpBinding`varsayılan bağlama seçimini kullanır.  
  
#### <a name="modifying-a-predefined-binding"></a>Önceden tanımlanmış bağlamayı değiştirme  
 Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilmiştir. Daha sonra, hizmette herhangi bir uç noktayı yapılandırmak için kullanılabilir. Bağlama <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> değeri 1 saniye olarak ayarlanarak değiştirilir. Özelliğinin bir <xref:System.TimeSpan> nesnesi döndürdüğünü unutmayın.  
  
 Değiştirilen bağlama bağlamalar bölümünde bulunur. Bu değiştirilmiş bağlama artık `endpoint` öğesindeki `binding` özniteliği ayarlanarak herhangi bir uç nokta oluştururken kullanılabilir.  
  
> [!NOTE]
> Bağlamaya belirli bir ad verirseniz, hizmet uç noktasında belirtilen `bindingConfiguration` onunla eşleşmelidir.  
  
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
 Aşağıdaki örnekte, hizmet türü için belirli bir davranış yapılandırılır. `ServiceMetadataBehavior` öğesi, [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti sorgulamak ve meta verilerden Web Hizmetleri Açıklama DILI (wsdl) belgeleri oluşturmak için kullanılır.  
  
> [!NOTE]
> Davranışa belirli bir ad verirseniz, hizmet veya uç nokta bölümünde belirtilen `behaviorConfiguration` aynı olmalıdır.  
  
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
 Bu son örnekte, `HelloWorld` hizmet türü için iki uç nokta yapılandırılır. Her uç nokta, aynı bağlama türünde farklı bir özelleştirilmiş `bindingConfiguration` özniteliği kullanır (her biri `basicHttpBinding`değiştirir).  
  
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
  
 Aşağıdaki örnekte gösterildiği gibi bir `protocolMapping` bölümü ekleyerek ve bağlamaları yapılandırarak varsayılan yapılandırmayı kullanarak aynı davranışı alabilirsiniz.  
  
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

- [Basitleştirilmiş Yapılandırma](simplified-configuration.md)
- [Sistem Tarafından Sağlanan Bağlamalar](system-provided-bindings.md)
- [Uç Nokta Oluşturmaya Genel Bakış](endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
