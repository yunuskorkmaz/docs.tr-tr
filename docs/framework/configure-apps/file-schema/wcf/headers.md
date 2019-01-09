---
title: '&lt;Üst bilgileri&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 84b9a9437d4b0dfae72a6e625b21f2b830eb28d8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147869"
---
# <a name="ltheadersgt"></a>&lt;Üst bilgileri&gt;
Bir uç nokta temel URI'sini ek olarak bir veya daha fazla SOAP üstbilgileri çözülebilir. Bu faydalı olduğu senaryolar bir kümesi, burada aracıların hedeflenen SOAP başlıkları da eklediğinizden istemcilerin bu uç noktanın bir uç nokta gerektiriyor SOAP Ara senaryoları kümesidir. Bu yapılandırma öğesi, bu tür özel adres üstbilgileri tanımlamak için kullanılabilir. Giriş uç noktası üst bilgisi koleksiyonu kullanıcı tarafından tanımlanan XML öğeleri şunlardır: Her öğenin biçimlendirilmiş olması gerekir XML.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Bölge||  
|Üye||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Farklı uç noktalar için yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 İsteğe bağlı üst bilgileri tanımlamak veya uç nokta ile etkileşime geçmek için adresleme daha ayrıntılı bilgi sağlar. Örneğin, gelen iletileri işlemek nasıl, nerede uç nokta bir yanıt iletisi göndermelidir veya birden fazla örneği bulunduğunda, belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin üst bilgileri belirtebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [Uç noktalar: Adresleri, bağlamalar ve sözleşmeler](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
