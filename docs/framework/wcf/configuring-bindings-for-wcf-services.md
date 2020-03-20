---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174829"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
Bir uygulama oluştururken, genellikle uygulamanın dağıtımından sonra kararları yöneticiye ertelemek istersiniz. Örneğin, genellikle bir hizmet adresinin veya Tek düzen kaynak tanımlayıcısının (URI) ne olacağını önceden bilmenin bir yolu yoktur. Bir adresi zor kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir. Bu esneklik yapılandırma ile gerçekleştirilir.  
  
> [!NOTE]
> Hızlı yapılandırma dosyaları oluşturmak için `/config` geçiş ile [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
## <a name="major-sections"></a>Ana Bölümler  
 Windows Communication Foundation (WCF) yapılandırma şeması aşağıdaki`serviceModel`üç `bindings`ana `services`bölümü içerir ( , , ve):  
  
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
  
### <a name="servicemodel-elements"></a>ServiceModel Elemanları  
 Bir hizmet türünü bir veya `system.ServiceModel` daha fazla uç noktayla ve bir hizmet ayarlarını yapılandırmak için öğeyle sınırlanan bölümü kullanabilirsiniz. Her bitiş noktası daha sonra bir adres, bir sözleşme ve bir bağlama ile yapılandırılabilir. Uç noktalar hakkında daha fazla bilgi için Bkz. [Endpoint Oluşturma Genel Bakışı.](endpoint-creation-overview.md) Uç nokta belirtilmemişse, çalışma süresi varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](./samples/simplified-configuration-for-wcf-services.md)bakın.  
  
 Bağlayıcı, aktarımları (HTTP, TCP, pipes, Message Queuing) ve protokolleri (Güvenlik, Güvenilirlik, İşlem akışları) belirtir ve her biri bir uç noktanın dünyayla nasıl iletişim kurduğunu gösteren bağlayıcı öğelerden oluşur.  
  
 Örneğin, [ \<temel HttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) öğesini belirterek, bir bitiş noktası için aktarım olarak HTTP'nin kullanılacağını belirtir. Bu, bu bitiş noktasını kullanan hizmet in çalışma zamanında bitiş noktasını kablolamak için kullanılır.  
  
 İki tür bağlama vardır: önceden tanımlanmış ve özel. Önceden tanımlanmış bağlamalar, ortak senaryolarda kullanılan öğelerin yararlı birleşimlerini içerir. WCF'nin sağladığı önceden tanımlanmış bağlama türlerinin listesi için [bkz.](system-provided-bindings.md) Önceden tanımlanmış bağlama koleksiyonu, bir hizmet uygulamasının gereksinim duyduğu özelliklerin doğru birleşimine sahip değilse, uygulamagereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz. Özel bağlamalar hakkında daha fazla bilgi için [ \<>bkz. ](../configure-apps/file-schema/wcf/custombinding.md)  
  
 Aşağıdaki dört örnek, bir WCF hizmeti ayarlamak için kullanılan en yaygın bağlama yapılandırmalarını göstermektedir.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Bağlama Türü Kullanmak için Bir Bitiş Noktası Belirtme  
 İlk örnek, adres, sözleşme ve bağlama yla yapılandırılan bir bitiş noktasının nasıl belirtilen şekilde belirtilir.  
  
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
  
 Bu örnekte, `name` öznitelik yapılandırmaiçin hangi hizmet türü için olduğunu gösterir. Sözleşmeyle birlikte `HelloWorld` kodunuzda bir hizmet oluşturduğunuzda, örnek yapılandırmada tanımlanan tüm uç noktalarıyla baş harfe fişlenir. Derleme yalnızca bir hizmet sözleşmesi uygularsa, `name` hizmet kullanılabilir tek türü kullandığından öznitelik atlanabilir. Öznitelik biçiminde olması gereken bir dize alır`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 Öznitelik, `address` uri'yi diğer uç noktaların hizmetle iletişim kurmak için kullandığını belirtir. URI mutlak veya göreceli bir yol olabilir. Göreceli bir adres sağlanırsa, ana bilgisayara bağlamada kullanılan aktarım şemasına uygun bir temel adres sağlaması beklenir. Bir adres yapılandırılmamışsa, temel adresin bu bitiş noktasının adresi olduğu varsayılır.  
  
 Öznitelik, `contract` bu bitiş noktasının ortaya çıkardığı sözleşmeyi belirtir. Hizmet uygulama türü sözleşme türünü uygulamalıdır. Bir hizmet uygulaması tek bir sözleşme türü uygularsa, bu özellik atlanabilir.  
  
 Öznitelik, `binding` bu belirli bitiş noktası için kullanmak üzere önceden tanımlanmış veya özel bir bağlama seçer. Bağlayıcıyı açıkça seçmeyen bir bitiş noktası varsayılan bağlama seçimini `BasicHttpBinding`kullanır, yani.  
  
#### <a name="modifying-a-predefined-binding"></a>Önceden Tanımlanmış Bir Bağlamayı Değiştirme  
 Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilir. Daha sonra hizmetteki herhangi bir bitiş noktasını yapılandırmak için kullanılabilir. Bağlama <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> değeri 1 saniyeye ayarlayarak değiştirilir. Özelliğin bir <xref:System.TimeSpan> nesneyi döndürtettiğini unutmayın.  
  
 Bu değiştirilmiş bağlama bağlama bölümünde bulunur. Bu değiştirilmiş bağlama artık `binding` `endpoint` öğedeki özniteliği ayarlayarak herhangi bir uç nokta oluştururken kullanılabilir.  
  
> [!NOTE]
> Bağlamaya belirli bir ad verirseniz, hizmet bitiş noktasında `bindingConfiguration` belirtilen adonunla eşleşmelidir.  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Bir Hizmete Uygulanacak Davranışı Yapılandırma  
 Aşağıdaki örnekte, hizmet türü için belirli bir davranış yapılandırılır. Öğe, `ServiceMetadataBehavior` [ServiceModel Metadata Utility Tool'un (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti sorgulamasını ve meta verilerden Web Hizmetleri Açıklama Dili (WSDL) belgelerini oluşturmasını sağlamak için kullanılır.  
  
> [!NOTE]
> Davranışa belirli bir ad verirseniz, hizmet veya bitiş noktası bölümünde `behaviorConfiguration` belirtilen adla eşleşmesi gerekir.  
  
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
  
 Önceki yapılandırma, istemcinin "HelloWorld" türünde yazılan hizmetin meta verilerini aramasını ve almalarını sağlar.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Farklı Bağlama Değerleri Kullanarak İki Uç Noktası Olan Bir Hizmet Belirtme  
 Bu son örnekte, `HelloWorld` hizmet türü için iki uç nokta yapılandırılır. Her uç nokta aynı `bindingConfiguration` bağlama türünün farklı bir özelleştirilmiş özniteliği kullanır (her biri `basicHttpBinding`değiştirir).  
  
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
  
 Bir `protocolMapping` bölüm ekleyerek ve aşağıdaki örnekte gösterildiği gibi bağlamaları yapılandırarak varsayılan yapılandırmayı kullanarak aynı davranışı elde edebilirsiniz.  
  
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
- [Sistem Destekli Ciltler](system-provided-bindings.md)
- [Uç Noktası Oluşturma Genel Bakış](endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
