---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942467"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers >
Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
  
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
|[\<> Ekle](add.md)|Belirteç işleyici koleksiyonuna bir güvenlik belirteci işleyicisi ekler.|  
|[\<> Temizle](clear.md)|Belirteç işleyici koleksiyonundan tüm güvenlik belirteci işleyicilerini temizler.|  
|[\<> Kaldır](remove.md)|Belirteç işleyici koleksiyonundan bir güvenlik belirteci işleyicisini kaldırır.|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IdentityConfiguration >](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hizmet yapılandırmasında bir veya daha fazla adlandırılmış güvenlik belirteci işleyici koleksiyonu belirtebilirsiniz. `name` Özniteliğini kullanarak bir koleksiyon için bir ad belirtebilirsiniz. Framework 'ün işlediği tek adlar "ActAs" ve "OnBehalfOf" dir. Bu koleksiyonlarda işleyiciler varsa, bunlar işleme `ActAs` ve `OnBehalfOf` belirteçlere göre varsayılan işleyiciler yerine bir güvenlik belirteci hizmeti (STS) tarafından kullanılır.  
  
 Varsayılan olarak, koleksiyon aşağıdaki işleyici <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>türleriyle doldurulur:, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>,, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Koleksiyonunu `<add>`, `<remove>`, ve`<clear>` öğelerini kullanarak değiştirebilirsiniz. Koleksiyonda yalnızca belirli bir türün tek bir işleyicisinin mevcut olduğundan emin olmanız gerekir. Örneğin, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfından bir işleyici türetirsiniz, işleyiciniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ya da tek bir koleksiyonda yapılandırılmış olabilir, ancak her ikisi birden değil.  
  
 Koleksiyondaki işleyiciler için yapılandırma ayarlarını belirtmek için öğesinikullanın.`<securityTokenHandlerConfiguration>` Bu öğe aracılığıyla belirtilen ayarlar, [ \<IdentityConfiguration >](identityconfiguration.md) öğesi aracılığıyla hizmette belirtilen ayarları geçersiz kılar. Bazı işleyiciler (yerleşik işleyici türlerinin birkaçı dahil), `<add>` öğesinin bir alt öğesi aracılığıyla ek yapılandırmayı destekleyebilir. Bir işleyicide belirtilen ayarlar, koleksiyonda veya hizmette belirtilen eşdeğer ayarları geçersiz kılar.
