---
title: '&lt;istemci&gt; &lt;uç noktası&gt;'
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: a7d95ee819c911d80178e38a37aeaccc5b1f1764
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598311"
---
# <a name="ltendpointgt-of-ltclientgt"></a>&lt;istemci&gt; &lt;uç noktası&gt;
Sözleşmeyi, bağlamayı ve istemciler tarafından sunucu üzerinde hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktalarının adres özelliklerini belirtir.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Gerekli dize özniteliği.<br /><br /> Uç nokta adresini belirtir. Varsayılan değer boş bir dizedir. Adres mutlak URI olmalıdır.|  
|behaviorConfiguration|Uç noktayı örneklemek için kullanılacak davranış adını içeren bir dize. Davranış adı, hizmet tanımlı bir noktada kapsam içinde olması gerekir. Varsayılan değer boş bir dizedir.|  
|bağlama|Gerekli dize özniteliği.<br /><br /> Kullanılacak bağlamanın türünü belirten bir dize. Türü, başvurulabilmesi için kayıtlı yapılandırma bölümü olmalıdır. Türü bölüm adına göre yerine bağlama türü adına göre kaydedilir.|  
|bindingConfiguration|İsteğe bağlı. Uç nokta örneklendiğinde kullanılan bağlama yapılandırmasının adını içeren bir dize. Bağlama yapılandırma uç noktaları kapsamında olması gerekir. Varsayılan değer boş bir dizedir.<br /><br /> Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki belirli bağlama yapılandırması başvurmak için. Özel bağlama kullanmaya çalışıyorsunuz. Bu özniteliği ayarlayın. Aksi takdirde, bir özel durum.|  
|Sözleşme|Gerekli dize özniteliği.<br /><br /> Hangi anlaşmanın gösteren bir dize bu koncový bod vystavuje. Derleme sözleşme türünü uygulamalıdır.|  
|endpointConfiguration|Tarafından ayarlanan standart bitiş noktası adını belirten bir dize `kind` bu standart bitiş noktası ek yapılandırma bilgilerinie başvuran öznitelik. Aynı ada tanımlanmalıdır `<standardEndpoints>` bölümü.|  
|tür|Uygulanan standart bitiş noktası türünü belirten bir dize. Türü kayıtlı olmalıdır `<extensions>` bölüm veya machine.config. Hiçbir şey belirtilmezse, ortak bir kanal uç noktası oluşturulur.|  
|name|İsteğe bağlı dize özniteliği. Bu öznitelik, bir uç nokta verilen bir sözleşme için benzersiz olarak tanımlar. Verilen bir sözleşme türü için birden çok istemci tanımlayabilirsiniz. Her tanımı bir benzersiz yapılandırma adına göre ayırt edilebilir. Bu öznitelik belirtilmezse, karşılık gelen uç noktası belirtilen sözleşme türü ile ilişkili varsayılan uç nokta olarak kullanılır. Varsayılan değer boş bir dizedir.<br /><br /> `name` Bağlama özniteliği WSDL dışa aktarım tanımı için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Adres üst bilgileri koleksiyonu.|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İstemci >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Bir istemcinin bağlanabileceği uç noktaları listesi tanımlayan bir yapılandırma bölümü.|  
  
## <a name="example"></a>Örnek  
 Bu, bir kanal uç nokta yapılandırması örneğidir.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [WCF İstemci Yapılandırması](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [İstemciler](../../../../../docs/framework/wcf/feature-details/clients.md)
