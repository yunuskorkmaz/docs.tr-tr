---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: a5af3893ab72d23c2b3814569decfc50431b8e55
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277530"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers >
Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.  
  
 \<system.identityModel>  
\<identityConfiguration >  
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
|name|Bir belirteci işleyicisi koleksiyonunun adını belirtir. Framework tarafından kabul edilen değerler yalnızca "ActAs" ve "OnBehalfOf" dir. Bu adlardan birini kullanarak belirteci işleyicisi koleksiyonları belirtilirse, koleksiyon ActAs veya OnBehalfOf işleme sırasıyla belirteçler olduğunda kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.|  
|[\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Tüm güvenlik belirteci işleyicileri belirteci işleyicisi koleksiyondan kaldırır.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmet yapılandırmasında güvenlik belirteci işleyicileri bir veya daha fazla adlandırılmış koleksiyonları belirtebilirsiniz. Kullanarak bir koleksiyon için bir ad belirtebilirsiniz `name` özniteliği. Çerçeve işleme yalnızca "ActAs" ve "OnBehalfOf" adlarıdır. İşleyiciler bu koleksiyonlarında varsa, bunlar bir güvenlik belirteci hizmeti (STS) yerine varsayılan işleyicileri işlenirken kullanılır `ActAs` ve `OnBehalfOf` belirteçleri.  
  
 Varsayılan olarak, koleksiyonun şu işleyici türlerini ile doldurulur: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Koleksiyon kullanarak değiştirebileceğiniz `<add>`, `<remove>`, ve `<clear>` öğeleri. Yalnızca tek bir işleyici herhangi bir tür koleksiyonunda var olduğundan emin olmanız gerekir. Örneğin, bir işleyiciden türetirseniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ya da sınıf işleyicinizi veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> tek bir koleksiyon bulunmalıdır, ikisi yapılandırılabilir.  
  
 Kullanım `<securityTokenHandlerConfiguration>` koleksiyonda işleyiciler için yapılandırma ayarlarını belirtmek için öğesi. Bu hizmet aracılığıyla belirtilen bu öğe belirtilen ayarlarını geçersiz kıl [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi. Bazı işleyiciler (birkaç yerleşik işleyici türlerini dahil) bir alt öğesi aracılığıyla ek yapılandırma destekleyebilir `<add>` öğesi. Belirtilen bir işleyici ayarları koleksiyonu veya hizmet üzerinde belirtilen eşdeğer ayarları geçersiz kılar.
