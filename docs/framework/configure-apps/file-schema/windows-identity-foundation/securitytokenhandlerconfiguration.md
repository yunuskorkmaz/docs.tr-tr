---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 168bdc4fbf640b201ebc61462d04727c23f838f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
Belirteç işleyicileri koleksiyonunu yapılandırmasını sağlar.  
  
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
|saveBootstrapContext|Oturum belirteci önyükleme belirteçlerini dahil edilip edilmeyeceğini belirtir. Değer ayrıca bir belirteç işleyici koleksiyonu ayarlayarak ayarlanabilir `saveBootstrapContext` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi. Bir değer belirteci işleyicisi koleksiyonda Ayarla hizmetinde değerini geçersiz kılar.|  
|maximumClockSkew|A <xref:System.TimeSpan> izin verilen maksimum saat eğriltme belirtir. İzin verilen maksimum saat eğriltme bir oturum açma oturumu sona erme süresini doğrulama gibi zamana duyarlı işlemlerini gerçekleştirirken denetler. 5 dakika, varsayılan değer "00: 05:00". Nasıl belirleneceği hakkında daha fazla bilgi için <xref:System.TimeSpan> değerler, bakın [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maksimum saat eğriltme Ayrıca hizmet düzeyinde ayarlayarak ayarlanabilir `maximumClockSkew` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi. Bir değer belirteci işleyicisi koleksiyonda Ayarla hizmetinde değerini geçersiz kılar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<AudienceUri >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Bu bağlı olan taraf kabul edilebilir tanımlayıcılardır URI'ler kümesini belirtir. İsteğe bağlı.|  
|[\<önbelleğe alan >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Sertifikaları doğrulamak için belirteci işleyicileri kullanma ayarlarını denetler. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. Belirli bir işleyici ile kendi Doğrulayıcı yapılandırdıysanız bu ayarları geçersiz kılınır. İsteğe bağlı.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan yayınlayıcı adı kaydını yapılandırır. İsteğe bağlı.|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan veren belirteci çözümleyiciyi kaydeder. Veren belirteç Çözümleyicisi gelen iletileri ve belirteç imzalama belirteçte çözmek için kullanılır. İsteğe bağlı.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder. Hizmet belirteç Çözümleyicisi gelen belirteçleri ve iletileri şifreleme belirteci çözmek için kullanılır. İsteğe bağlı.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Belirteç yeniden yürütme algılaması sağlar ve belirteçler için sona erme saati belirtir. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölüm için özellik değerlerini sağlayan bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesnesi. Bu bölümde yapılandırılan ayarları hizmetinde yapılandırılan ayarları geçersiz kılar. Bu ayarlardan bazıları sırayla, güvenlik belirteci işleyicisi koleksiyonuna bir işleyici eklediğinizde, belirtilen ayarlarla geçersiz kılınabilir.  
  
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
