---
title: '&lt;Üstbilgileri&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747157"
---
# <a name="ltheadersgt"></a>&lt;Üstbilgileri&gt;
Bir uç nokta temel URI'sini yanı sıra bir veya daha fazla SOAP üstbilgileri çözülebilir. Bu faydalı olduğu senaryolar bir dizi, burada bir uç nokta aracılar hedeflenen SOAP üstbilgileri dahil etmek Bu uç noktanın gerektirir. istemciler SOAP Ara senaryoları kümesidir. Bu yapılandırma öğesi, bu tür özel adres üstbilgileri tanımlamak için kullanılabilir. Uç nokta üstbilgi koleksiyonu girişleri, kullanıcı tanımlı XML öğelerdir. Doğru biçimlendirilmiş olması her öğeye sahip XML.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
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
|[\<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Farklı türde uç noktalar yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 İsteğe bağlı üstbilgi tanımlamak veya uç noktasıyla etkileşim için adresleme daha ayrıntılı bilgi sağlar. Örneğin, üstbilgileri gelen iletiyi işlemeye nasıl, burada uç nokta bir yanıt iletisi göndermesi gerekir veya birden çok örneği kullanılamadığında belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin gösterebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
