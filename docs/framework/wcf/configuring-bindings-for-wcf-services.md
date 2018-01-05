---
title: "Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b11810e0a39c5b6091a63ef33e5abfccb95b7555
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
Bir uygulama oluştururken, genellikle uygulama dağıtımdan sonra yönetici kararları erteleneceği istersiniz. Örneğin, genellikle bir hizmet adresi ya da Tekdüzen Kaynak Tanımlayıcısı (URI) ne olacağını önceden bilmesinin yolu yoktur. Sabit bir adresi kodlama yerine, bir hizmet oluşturduktan sonra bunu yapmak için yönetici izin vermek için tercih edilir. Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.  
  
> [!NOTE]
>  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile `/config` hızlı bir şekilde yapılandırma dosyaları oluşturmak için anahtar.  
  
## <a name="major-sections"></a>Ana bölümleri  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Yapılandırma Şeması aşağıdaki üç ana bölümleri içerir (`serviceModel`, `bindings`, ve `services`):  
  
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
 İlişkisindeki tarafından bölüm kullanabilirsiniz `system.ServiceModel` öğesi bir hizmet türünün bir veya daha fazla uç noktaları gibi bir hizmete yönelik ayarları yapılandırın. Her uç nokta bir adresi, bir sözleşme ve bağlama ile yapılandırılabilir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]uç noktaları, bkz: [uç noktası oluşturma genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md). Uç nokta yok belirtilirse, çalışma zamanı varsayılan uç noktaları ekler. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Bir bağlama taşımaları (HTTP, TCP, Kanallar, Message Queuing) ve protokolleri (güvenlik, güvenilirlik, işlem akışları) belirtir ve bağlama öğeleri, her biri bir uç nokta nasıl iletişim kurduğu en/boy dünyayla belirtir oluşur.  
  
 Örneğin, belirten [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi belirten HTTP taşıma olarak bir uç noktası için kullanılacak. Bu kullanılan kablo uç noktası Bu uç nokta kullanarak hizmet açıldığında çalışma zamanında ayarlama için.  
  
 Bağlamalar iki tür vardır: önceden tanımlanmış ve özel. Önceden tanımlanmış bağlamaları yararlı birleşimlerini ortak senaryolarda kullanılır öğeleri içerir. Önceden tanımlanmış bağlama listesi türleri için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sağlar, bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md). Önceden tanımlanmış bağlama koleksiyonu bir hizmet uygulaması gereken özellikleri doğru birleşimini varsa, uygulamanın gereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Özel bağlamalar bkz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Aşağıdaki dört örnekler ayarlamak için kullanılan en yaygın bağlama yapılandırmaları göstermek bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Bağlama türü kullanmak için bir uç nokta belirtme  
 İlk örnek bir adresi, bir sözleşme ve bağlama ile yapılandırılan bir uç noktası belirtmek nasıl gösterilmektedir.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 Bu örnekte, `name` özniteliği yapılandırmadır için hangi hizmet türünü gösterir. Kodunuzu ile bir hizmet oluşturduğunuzda `HelloWorld` sözleşme, örnek yapılandırmada tanımlanan bitiş noktalarının tümü ile başlatıldı. Derleme yalnızca bir hizmet sözleşmesi, uyguluyorsa `name` hizmeti yalnızca kullanılabilir türü kullandığından özniteliği'nin etmeyebilirsiniz. Öznitelik biçiminde olması gereken bir dize alır`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` Özniteliği, diğer uç noktaları için hizmet iletişim kurmak için kullandıkları URI belirtir. URI mutlak veya göreli yol ya da olabilir. Göreli bir adresi sağlanırsa, konak bağlama kullanılan aktarma düzeni için uygun bir taban adresi sağlaması beklenir. Bir adresi yapılandırılmamışsa, taban adresi Bu uç nokta adresi olduğu varsayılır.  
  
 `contract` Özniteliği bu bitiş noktasının sunduğu sözleşme belirtir. Hizmet uygulama türü sözleşme türü uygulamalıdır. Bir hizmet uygulaması tek anlaşma türü uygularsa, bu özellik atlanabilir.  
  
 `binding` Özniteliği bu belirli uç noktası için kullanılacak önceden tanımlanmış veya özel bir bağlama seçer. Açıkça bağlama seçmez bir uç nokta olan varsayılan bağlama seçimi kullanır `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Önceden tanımlanmış bir bağlama değiştirme  
 Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilir. Ardından, herhangi bir uç nokta hizmetinde yapılandırmak için de kullanılabilir. Bağlama ayarlayarak değiştiren <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 1 saniye için değer. Özelliğin döndürdüğü Not bir <xref:System.TimeSpan> nesnesi.  
  
 Değiştirilmiş bağlama bağlamaları bölümünde bulunur. Bu değişiklik bağlama artık herhangi bir uç nokta ayarlayarak oluştururken kullanılabilir `binding` özniteliğini `endpoint` öğesi.  
  
> [!NOTE]
>  Bağlama, belirli bir adı verirseniz `bindingConfiguration` hizmetinde belirtilen bitiş noktası ile eşleşmelidir.  
  
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
 Aşağıdaki örnekte, belirli bir davranışı hizmet türü için yapılandırılır. `ServiceMetadataBehavior` Öğesi etkinleştirmek için kullanılan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet sorgulamak ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri meta verileri oluşturmak için.  
  
> [!NOTE]
>  Davranış için belirli bir adı verirseniz `behaviorConfiguration` hizmet uç noktası belirtilen bölüm onu eşleşmesi gerekir.  
  
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
  
 Önceki yapılandırma sağlayan bir çağrı ve "HelloWorld" meta verilerini almak için istemci hizmeti belirtilmiş.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Bir hizmet farklı bağlama değerleri kullanarak iki uç nokta ile belirtme  
 Son Bu örnekte, iki uç nokta için yapılandırılmış olan `HelloWorld` hizmet türü. Her uç nokta farklı bir özelleştirilmiş kullanır `bindingConfiguration` öznitelik aynı bağlama türü (her değiştirir `basicHttpBinding`).  
  
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
  
 Ekleyerek varsayılan yapılandırmayı kullanarak aynı davranışı elde edebilirsiniz bir `protocolMapping` bölümü ve aşağıdaki örnekte gösterildiği gibi bağlamaları yapılandırma.  
  
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
