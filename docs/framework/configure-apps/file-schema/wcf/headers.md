---
title: "&lt;üstbilgileri&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5e0a56055df588e9e42c4e1855c352c3f0d1b2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltheadersgt"></a>&lt;üstbilgileri&gt;
Bir uç nokta temel URI'sini yanı sıra bir veya daha fazla SOAP üstbilgileri çözülebilir. Bu faydalı olduğu senaryolar bir dizi, burada bir uç nokta aracılar hedeflenen SOAP üstbilgileri dahil etmek Bu uç noktanın gerektirir. istemciler SOAP Ara senaryoları kümesidir. Bu yapılandırma öğesi, bu tür özel adres üstbilgileri tanımlamak için kullanılabilir. Uç nokta üstbilgi koleksiyonu girişleri, kullanıcı tanımlı XML öğelerdir. Doğru biçimlendirilmiş olması her öğeye sahip XML.  
  
 \<Sistem. ServiceModel >  
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
 [Uç noktalar: Adresler, bağlamalar ve sözleşmeler](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
