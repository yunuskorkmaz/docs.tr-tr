---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029335"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|saveBootstrapContext|Oturum belirteci önyükleme simgeleri dahil edilip edilmeyeceğini belirtir. Değer aynı zamanda bir belirteci işleyicisi koleksiyonunda ayarlayarak ayarlanabilir `saveBootstrapContext` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi. Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.|  
|maximumClockSkew|A <xref:System.TimeSpan> en fazla izin verilen saat sapması belirtir. Bir oturum açma oturumu sona erme süresini doğrulama gibi zamana duyarlı işlemleri gerçekleştirirken, en fazla izin verilen saat sapması denetler. 5 dakika, varsayılan değer "00: 05:00". Belirtme hakkında daha fazla bilgi için <xref:System.TimeSpan> değerleri, görmek [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maksimum saat eğriltme da hizmet düzeyinde ayarlayarak ayarlanabilir `maximumClockSkew` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi. Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<AudienceUri >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Bu bağlı olan tarafın tanımlayıcılardır kabul edilebilir bir URI'leri kümesini belirtir. İsteğe bağlı.|  
|[\<önbelleğe alan >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. Belirli bir işleyici kendi Doğrulayıcı ile yapılandırılmışsa, bu ayarlar geçersiz kılınır. İsteğe bağlı.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verenin ad Kayıt Defteri'ni yapılandırır. İsteğe bağlı.|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verici belirteç çözümleyici kaydeder. Veren belirteç Çözümleyici, imzalama belirtecinin gelen belirteçleri ve iletileri çözmek için kullanılır. İsteğe bağlı.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder. Hizmet belirteç Çözümleyici, gelen belirteçleri ve ileti şifreleme belirteci çözmek için kullanılır. İsteğe bağlı.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Belirteç yeniden yürütme algılaması sağlar ve belirteçleri sona erme süresini belirtir. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özellik değerleri için bu bölümde bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne. Bu bölümde, yapılandırılan ayarları hizmetinde yapılandırılan ayarları geçersiz kılar. Bu ayarlardan bazıları sırasıyla bir işleyici güvenlik belirteci işleyicisi koleksiyona eklendiğinde, belirtilen ayarları tarafından geçersiz kılınabilir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
