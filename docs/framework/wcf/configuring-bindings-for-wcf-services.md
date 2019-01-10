---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 7b5a91091a0902928eb2b72bdf69612f2e3f2f48
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029417"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
Bir uygulama oluştururken, genellikle Uygulama dağıtıldıktan sonra yönetici kararları erteleme istersiniz. Örneğin, genellikle hizmeti adresi ya da Tekdüzen Kaynak Tanımlayıcısı (URI) ne olacağı önceden bilmesinin yolu yoktur. Sabit bir adresi kodlama yerine, bir hizmet oluşturduktan sonra bunu yapmak bir yönetici izin vermek için tercih edilir. Bu esnekliğin yapılandırma aracılığıyla gerçekleştirilir.  
  
> [!NOTE]
>  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile `/config` yapılandırma dosyaları hızlı bir şekilde oluşturmak için anahtar.  
  
## <a name="major-sections"></a>Ana bölümleri  
 Windows Communication Foundation (WCF) yapılandırma Şeması aşağıdaki üç ana bölümleri içerir (`serviceModel`, `bindings`, ve `services`):  
  
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
 Tarafından sınırlanan bölüm kullanabileceğiniz `system.ServiceModel` bir hizmet türünün hizmet ayarlarını yanı sıra, bir veya daha fazla uç noktası ile yapılandırmak için öğesi. Her uç nokta bir adresi, bir sözleşme ve bağlama ile yapılandırılabilir. Uç noktaları hakkında daha fazla bilgi için bkz. [uç nokta oluşturmaya genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md). Uç nokta yok belirtilirse, çalışma zamanı varsayılan uç noktalar ekler. Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Bir bağlama Aktarım (HTTP, TCP, Kanallar, Message Queuing) ve Protokolü (güvenlik, güvenilirlik, işlem akışları) belirtir ve bağlama öğeleri, her biri bir uç nokta nasıl iletişim kurduğu, bir özelliği sayesinde dünyanın belirtir oluşur.  
  
 Örneğin, belirten [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) HTTP, aktarım olarak bir uç noktası için kullanılacak öğesini belirtir. Bu uç nokta Bu uç nokta'ı kullanarak hizmeti açıldığında çalışma zamanında ayarlama kablo için.  
  
 Bağlama iki tür vardır: önceden tanımlanmış ve özel. Önceden tanımlanmış bağlamaları yararlı birleşimlerini yaygın senaryolarda kullanılan öğeleri içerir. WCF sağlayan önceden tanımlanmış bağlama türleri listesi için bkz. [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md). Önceden tanımlanmış bağlama koleksiyon doğru birleşimi bir hizmet uygulaması gereken özellikleri, varsa, uygulamanın gereksinimlerini karşılamak için özel bağlamaları oluşturabilirsiniz. Özel bağlamalar hakkında daha fazla bilgi için bkz: [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Aşağıdaki dört örnekler bir WCF hizmetini ayarlamak için kullanılan en yaygın bağlama yapılandırmaları gösterir.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Bağlama türü kullanmak için bir uç nokta belirtme  
 İlk örnek bir adresi, bir sözleşme ve bağlama ile yapılandırılan bir uç noktasının nasıl belirtileceğini göstermektedir.  
  
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
  
 Bu örnekte, `name` özniteliği yapılandırmadır için hangi hizmet türünü gösterir. Kodunuzu bir hizmet oluşturduğunuzda `HelloWorld` sözleşmesi, tüm örnek yapılandırmasında tanımlı uç noktaları ile başlatılır. Derleme yalnızca bir hizmet sözleşmesini uyguluyorsa `name` hizmeti yalnızca türü kullandığından, öznitelik atlanabilir. Öznitelik biçiminde olmalıdır bir dize alır. `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` Özniteliği, diğer uç noktalardan hizmetiyle iletişim kurmak için kullandığınız URI'sini belirtir. URI, mutlak veya göreli yol ya da olabilir. Göreli adres sağlanırsa, konak bağlamasında kullanılan aktarım düzeni için uygun olan temel adres sağlamak için bekleniyor. Bir adresi yapılandırılmamışsa, temel adresini Bu uç nokta adresi olduğu varsayılır.  
  
 `contract` Özniteliği bu uç noktayı kullanıma sunma sözleşme belirtir. Hizmet uygulaması türü sözleşme türünü uygulamalıdır. Bir hizmet uygulaması tek bir anlaşma türü uyguluyorsa, bu özellik atlanabilir.  
  
 `binding` Özniteliği, bu belirli bir uç noktası için kullanılacak önceden tanımlanmış ya da özel bir bağlama seçer. Açıkça bağlama seçmez bir uç nokta olan varsayılan bağlama seçimi kullanan `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Önceden tanımlanmış bir bağlama değiştirme  
 Aşağıdaki örnekte önceden tanımlanmış bir bağlama değiştirildi. Ardından, herhangi bir uç noktaya hizmeti yapılandırmak için de kullanılabilir. Bağlama ayarlayarak değiştirilir <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 1 saniye değeri. Özelliğin döndürdüğü Not bir <xref:System.TimeSpan> nesne.  
  
 Değiştirilmiş bağlama bağlamaları bölümünde bulunur. Bu değişiklik bağlama artık herhangi bir uç noktaya ayarlayarak oluşturulurken kullanılabilir `binding` özniteliğini `endpoint` öğesi.  
  
> [!NOTE]
>  Bağlama için belirli adını verirseniz `bindingConfiguration` hizmette belirtilen uç noktası ile eşleşmelidir.  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Bir hizmete uygulamak için bir davranışını yapılandırma  
 Aşağıdaki örnekte, belirli bir davranış hizmet için yapılandırılır. `ServiceMetadataBehavior` Etkinleştirmek için kullanılan öğe [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetini sorgulama ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri meta verileri oluşturmak için.  
  
> [!NOTE]
>  Belirli bir adı, davranıştır verirseniz `behaviorConfiguration` hizmet uç noktası belirtilen bölüm onu eşleşmesi gerekir.  
  
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
  
 Önceki arama ve "HelloWorld" meta verilerini almak için istemci yapılandırma etkinleştirir hizmeti yazdınız.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Bir hizmet farklı bağlama değerleri kullanarak iki uç noktaları ile belirtme  
 Bu Son örnekte iki uç nokta için yapılandırılmış olan `HelloWorld` hizmet türü. Her uç nokta farklı özelleştirilmiş kullanır `bindingConfiguration` öznitelik aynı bağlama türü (her değiştirir `basicHttpBinding`).  
  
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
  
 Aynı davranışı ekleyerek varsayılan yapılandırmayı kullanarak alabilirsiniz bir `protocolMapping` bölümü ve aşağıdaki örnekte gösterildiği gibi bağlamaları yapılandırma.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md)  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
