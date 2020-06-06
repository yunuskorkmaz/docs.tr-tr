---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251870"
---
# \<securityTokenHandlers>
Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Belirteç işleyici koleksiyonunun adını belirtir. Framework tarafından tanınan tek değerler şunlardır "ActAs" ve "OnBehalfOf". Belirteç işleyici koleksiyonları bu adlardan biriyle belirtilirse, sırasıyla ActAs veya OnBehalfOf belirteçleri işlenirken koleksiyon kullanılacaktır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<add>](add.md)|Belirteç işleyici koleksiyonuna bir güvenlik belirteci işleyicisi ekler.|  
|[\<clear>](clear.md)|Belirteç işleyici koleksiyonundan tüm güvenlik belirteci işleyicilerini temizler.|  
|[\<remove>](remove.md)|Belirteç işleyici koleksiyonundan bir güvenlik belirteci işleyicisini kaldırır.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hizmet yapılandırmasında bir veya daha fazla adlandırılmış güvenlik belirteci işleyici koleksiyonu belirtebilirsiniz. Özniteliğini kullanarak bir koleksiyon için bir ad belirtebilirsiniz `name` . Framework 'ün işlediği tek adlar "ActAs" ve "OnBehalfOf" dir. Bu koleksiyonlarda işleyiciler varsa, bunlar işleme `ActAs` ve belirteçlere göre varsayılan işleyiciler yerine bir güvenlik belirteci hizmeti (STS) tarafından kullanılır `OnBehalfOf` .  
  
 Varsayılan olarak, koleksiyon aşağıdaki işleyici türleriyle doldurulur: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> . Koleksiyonunu `<add>` ,, `<remove>` ve öğelerini kullanarak değiştirebilirsiniz `<clear>` . Koleksiyonda yalnızca belirli bir türün tek bir işleyicisinin mevcut olduğundan emin olmanız gerekir. Örneğin, sınıfından bir işleyici türetirsiniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , işleyiciniz ya da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> tek bir koleksiyonda yapılandırılmış olabilir, ancak her ikisi birden değil.  
  
 `<securityTokenHandlerConfiguration>`Koleksiyondaki işleyiciler için yapılandırma ayarlarını belirtmek için öğesini kullanın. Bu öğe aracılığıyla belirtilen ayarlar, bu öğe aracılığıyla hizmette belirtilen ayarları geçersiz kılar [\<identityConfiguration>](identityconfiguration.md) . Bazı işleyiciler (yerleşik işleyici türlerinin birkaçı dahil), öğesinin bir alt öğesi aracılığıyla ek yapılandırmayı destekleyebilir `<add>` . Bir işleyicide belirtilen ayarlar, koleksiyonda veya hizmette belirtilen eşdeğer ayarları geçersiz kılar.
