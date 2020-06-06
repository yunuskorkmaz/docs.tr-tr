---
title: <endpoint> / <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855325"
---
# <a name="endpoint-of-client"></a>\<endpoint> / \<client>
İstemciler tarafından sunucudaki hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktasının sözleşme, bağlama ve adres özelliklerini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
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
|adres|Gerekli dize özniteliği.<br /><br /> Uç noktanın adresini belirtir. Varsayılan değer boş bir dizedir. Adres, mutlak bir URI olmalıdır.|  
|behaviorConfiguration|Uç noktanın örneğini oluşturmak için kullanılacak davranışın davranış adını içeren bir dize. Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır. Varsayılan değer boş bir dizedir.|  
|bağlama|Gerekli dize özniteliği.<br /><br /> Kullanılacak bağlamanın türünü gösteren bir dize. Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır. Tür, bağlamanın tür adı yerine bölüm adı tarafından kaydedilir.|  
|bindingConfiguration|İsteğe bağlı. Uç nokta örneği oluşturulurken kullanılacak bağlama yapılandırmasının adını içeren bir dize. Bağlama yapılandırması, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır. Varsayılan değer boş bir dizedir.<br /><br /> Bu öznitelik, `binding` yapılandırma dosyasındaki belirli bir bağlama yapılandırmasına başvurmak için ile birlikte kullanılır. Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın. Aksi takdirde, bir özel durum oluşabilir.|  
|Sözleşmesi|Gerekli dize özniteliği.<br /><br /> Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize. Derlemenin anlaşma türünü uygulaması gerekir.|  
|endpointConfiguration|`kind`Bu standart uç noktanın ek yapılandırma bilgilerine başvuran özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize. Bölümünde aynı ad tanımlanmalıdır `<standardEndpoints>` .|  
|denetlenmesi|Uygulanan standart bitiş noktası türünü belirten bir dize. Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse, ortak bir kanal uç noktası oluşturulur.|  
|name|İsteğe bağlı dize özniteliği. Bu öznitelik, belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar. Belirli bir sözleşme türü için birden çok istemci tanımlayabilirsiniz. Her tanım benzersiz bir yapılandırma adıyla farklılaştıralınmalıdır. Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır. Varsayılan değer boş bir dizedir.<br /><br /> `name`Bir bağlamanın ÖZNITELIĞI WSDL aracılığıyla tanım dışarı aktarma için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Adres üst bilgileri koleksiyonu.|  
|[\<identity>](identity.md)|Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<client>](client.md)|Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.|  
  
## <a name="example"></a>Örnek  
 Bu bir kanal uç noktası yapılandırmasına bir örnektir.  
  
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
- [WCF İstemci Yapılandırması](../../../wcf/feature-details/client-configuration.md)
- [İstemciler](../../../wcf/feature-details/clients.md)
