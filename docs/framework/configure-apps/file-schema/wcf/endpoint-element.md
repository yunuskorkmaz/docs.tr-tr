---
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 94b6cc6225171d90164e6d6880e1095513f16ece
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354744"
---
# <a name="endpoint-element"></a>\<uç noktası > öğesi
Bağlama, anlaşma ve Hizmetleri kullanıma sunmak için kullanılan bir hizmet uç noktası için adres özelliklerini belirtir.  
  
 \<system.ServiceModel>  
\<Hizmet >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Bitiş noktasının adresini içeren bir dize. Adres mutlak veya göreli adres olarak belirtilebilir. Göreli adres sağlanırsa, konak bağlamasında kullanılan aktarım düzeni için uygun bir temel adres sağlamak için bekleniyor. Bir adresi yapılandırılmamışsa, temel adresini Bu uç nokta adresi olduğu varsayılır.<br /><br /> Varsayılan değer boş bir dizedir.|  
|behaviorConfiguration|Bitiş noktasında kullanılacak davranış adını içeren bir dize.|  
|bağlama|Kullanılacak bağlama türünü belirten bir dize özniteliği gerekli. Türü, başvurulabilmesi için kayıtlı yapılandırma bölümü olmalıdır. Türü kayıtlı bölüm adı yerine bağlama türü adı değil.|  
|bindingConfiguration|Bitiş noktası başlatıldığında kullanılacak bağlamanın bağlama adını belirten dize. Bağlama adını, uç nokta tanımlanan bir noktada kapsam içinde olması gerekir. Varsayılan değer boş bir dizedir.<br /><br /> Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki belirli bağlama yapılandırması başvurmak için. Özel bağlama kullanmaya çalışıyorsunuz. Bu özniteliği ayarlayın. Aksi takdirde, bir özel durum.|  
|bindingName|WSDL dışa aktarım tanımı için bağlamanın benzersiz nitelenmiş adını belirten dize. Varsayılan değer boş bir dizedir.|  
|bindingNamespace|WSDL dışarı tam tanımı için bağlamanın ad alanı adını belirten dize. Varsayılan değer boş bir dizedir.|  
|Sözleşme|Hangi anlaşmanın gösteren bir dize bu koncový bod vystavuje. Derleme sözleşme türünü uygulamalıdır. Bir hizmet uygulaması tek bir anlaşma türü uyguluyorsa, bu özellik atlanabilir. Varsayılan değer boş bir dizedir.|  
|endpointConfiguration|Tarafından ayarlanan standart bitiş noktası adını belirten bir dize `kind` bu standart bitiş noktası ek yapılandırma bilgilerinie başvuran öznitelik. Aynı ada tanımlanmalıdır `<standardEndpoints>` bölümü.|  
|isSystemEndpoint|Bir uç nokta altyapı uç noktası olup olmadığını belirten bir Boole değeri.|  
|tür|Uygulanan standart bitiş noktası türünü belirten bir dize. Türü kayıtlı olmalıdır `<extensions>` bölüm veya machine.config. Hiçbir şey belirtilmezse, ortak bir hizmet uç noktası oluşturulur.|  
|listenUriMode|Taşıma nasıl işler belirtir `ListenUri` hizmetin dinlemesi sağlanan. Geçerli değerler:<br /><br /> -Açık<br />-Benzersiz<br /><br /> Explicit varsayılan değerdir.|  
|listenUri|Hizmet uç noktasını dinleyen URI belirten bir dize. Varsayılan değer boş bir dizedir.|  
|name|İsteğe bağlı öznitelik. Hizmet uç noktası adını belirten dize. Bağlama adı ve sözleşme tanımı adı birleşimi varsayılan değerdir. Hizmetleri olabilir birden fazla uç nokta, bu nedenle uç noktanın `name` özniteliktir hizmet adından farklı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Adres üst bilgileri koleksiyonu.|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Hizmet >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Bir istemcinin bağlanabileceği uç noktaları listesi tanımlayan bir yapılandırma bölümü.|  
  
## <a name="example"></a>Örnek  
 Bu, bir hizmet uç noktası yapılandırması örneğidir.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [Uç noktalar: Adresleri, bağlamalar ve sözleşmeler](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
