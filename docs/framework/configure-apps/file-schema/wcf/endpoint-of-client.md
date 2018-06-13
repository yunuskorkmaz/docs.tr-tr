---
title: '&lt;istemci&gt; &lt;uç noktası&gt;'
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f9a69483ab058823fd419edc84868e801b91d2c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748067"
---
# <a name="ltendpointgt-of-ltclientgt"></a>&lt;istemci&gt; &lt;uç noktası&gt;
Sözleşme, bağlama ve istemciler tarafından sunucuda hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktası adresi özelliklerini belirtir.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Gerekli dize özniteliği.<br /><br /> Uç nokta adresini belirtir. Varsayılan boş bir dizedir. Adres bir mutlak URI olmalıdır.|  
|behaviorConfiguration|Uç nokta örneği oluşturmak için kullanılacak davranış davranışı adını içeren dize. Davranış adı Hizmet tanımlı bir noktada kapsamında olması gerekir. Varsayılan boş bir dizedir.|  
|bağlama|Gerekli dize özniteliği.<br /><br /> Kullanılacak bağlama türünü belirten bir dize. Tür başvuru için kayıtlı yapılandırma bölümü içermelidir. Türü bölümü adıyla yerine bağlama tür adıyla kaydedilir.|  
|bindingConfiguration|İsteğe bağlı. Uç nokta örneği oluşturulduğunda kullanılacak bağlama yapılandırması adını içeren dize. Bağlama yapılandırması uç noktaları kapsamında olması gerekir. Varsayılan boş bir dizedir.<br /><br /> Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki özel bağlama yapılandırma başvurmak için. Özel bağlama kullanmaya çalıştığınız gerekiyorsa, bu öznitelik ayarlanır. Aksi halde, bir özel durum.|  
|Sözleşme|Gerekli dize özniteliği.<br /><br /> Bu uç noktaya sunduğu sözleşmeyi belirten bir dize. Derleme sözleşme türü uygulamalıdır.|  
|endpointConfiguration|Tarafından belirlenen standart uç noktanın adını belirten dize `kind` standart Bu uç noktanın ek yapılandırma bilgilerini başvuran özniteliği. Aynı adı tanımlanmalıdır `<standardEndpoints>` bölümü.|  
|türü|Standart uç nokta uygulanan türünü belirten bir dize. Türü kaydedilmelidir `<extensions>` bölüm veya machine.config dosyasındaki. Hiçbir şey belirtilirse, ortak bir kanal uç oluşturulur.|  
|name|İsteğe bağlı dize özniteliği. Bu öznitelik bir uç nokta belirli bir sözleşme için benzersiz olarak tanımlar. Belirli bir sözleşme türde birden fazla istemciye tanımlayabilirsiniz. Her tanımı bir benzersiz yapılandırma adıyla Ayrıştırılan gerekir. Bu öznitelik atlanırsa, karşılık gelen endpoint belirtilen sözleşme türüyle ilişkili varsayılan uç noktası olarak kullanılır. Varsayılan boş bir dizedir.<br /><br /> `name` Özniteliği bağlaması WSDL aracılığıyla tanımı dışa aktarma için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Adres üstbilgileri koleksiyonu.|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İstemci >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar yapılandırma bölümü.|  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [WCF İstemci Yapılandırması](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [İstemciler](../../../../../docs/framework/wcf/feature-details/clients.md)
