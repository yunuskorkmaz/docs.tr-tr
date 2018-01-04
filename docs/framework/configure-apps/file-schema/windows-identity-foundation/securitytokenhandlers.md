---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: de19fffdeae801163ec991ecf08d00b1286781d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.  
  
 \<System.IdentityModel >  
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
|name|Bir belirteci işleyicisi koleksiyonunun adını belirtir. Çerçevesi tarafından kabul edilen değerler yalnızca "ActAs" ve "OnBehalfOf" dir. Belirteci işleyicisi koleksiyonları şu adlardan birini kullanarak belirtilirse, koleksiyon ActAs veya OnBehalfOf işleme sırasıyla belirteçler olduğunda kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Tüm güvenlik belirteci işleyicileri belirteci işleyicisi koleksiyondan kaldırır.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Belirteç işleyicileri koleksiyonunu yapılandırmasını sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmet yapılandırmasında güvenlik belirteci işleyicileri bir veya daha fazla adlandırılmış koleksiyonları belirtebilirsiniz. Kullanarak bir koleksiyon için bir ad belirtebilirsiniz `name` özniteliği. Çerçeve işleme yalnızca "ActAs" ve "OnBehalfOf" adlardır. İşleyicileri bu koleksiyonları yoksa, bir güvenlik belirteci hizmeti (STS) yerine varsayılan işleyicileri işlerken kullanıldıkları `ActAs` ve `OnBehalfOf` belirteçleri.  
  
 Varsayılan olarak, koleksiyon şu işleyici türlerini ile doldurulur: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Koleksiyon kullanarak değiştirebileceğiniz `<add>`, `<remove>`, ve `<clear>` öğeleri. Herhangi bir tür için tek bir işleyici koleksiyonunda var olduğundan emin olmalısınız. Örneğin, bir işleyicisinden türetirseniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı, ya da işleyicinizi veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> tek bir koleksiyon, ancak ikisini yapılandırılabilir.  
  
 Kullanım `<securityTokenHandlerConfiguration>` öğe koleksiyonda işleyicileri için yapılandırma ayarlarını belirtin. Hizmet aracılığıyla belirtilen bu öğe belirtilen ayarları geçersiz kılar [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi. Bazı işleyicileri (birkaç yerleşik işleyici türlerini dahil) bir alt öğesi aracılığıyla ek yapılandırma destekleyebilir `<add>` öğesi. Üzerinde bir işleyici için belirtilen ayarları koleksiyon veya hizmeti belirtilen eşdeğer ayarları geçersiz kılar.
