---
title: '&lt;identityConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 11ba7df79ead1693fc6828aeabde413237680737
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193781"
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
Hizmet düzeyi kimlik ayarlarını belirtir.  
  
 \<system.identityModel>  
\<identityConfiguration >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Kimlik yapılandırma bölümünün adı. Bu ad, belirli yapılandırma bölümü başvurmak için kullanabilirsiniz. Hayır ise `name` özniteliği belirtilmezse, varsayılan yapılandırma bölümü tanımlar. Varsayılan yapılandırma, her zaman pasif Federasyon senaryolar için kullanılır. Daha fazla bilgi için [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.|  
|saveBootstrapContext|Oturum belirteci önyükleme simgeleri dahil edilip edilmeyeceğini belirtir. Değer aynı zamanda bir belirteci işleyicisi koleksiyonunda ayarlayarak ayarlanabilir `saveBootstrapContext` özniteliği [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi. Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.|  
|maximumClockSkew|A <xref:System.TimeSpan> en fazla izin verilen saat sapması belirtir. Bir oturum açma oturumu sona erme süresini doğrulama gibi zamana duyarlı işlemleri gerçekleştirirken, en fazla izin verilen saat sapması denetler. 5 dakika, varsayılan değer "00: 05:00". Belirtme hakkında daha fazla bilgi için <xref:System.TimeSpan> değerleri, görmek [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maksimum saat eğriltme da belirteci işleyicisi koleksiyonunda ayarlayarak ayarlanabilir `maximumClockSkew` özniteliği [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi. Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<önbelleğe alan >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder. İsteğe bağlı.|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Bir gelen talep için talep Yetkilendirme Yöneticisi kaydeder. İsteğe bağlı.|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Gelen güvenlik belirteçleri için gerekli talep kümesini belirtir. İsteğe bağlı.|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Güvenlik belirteci işleyicileri koleksiyonunu belirtir. Güvenlik belirteci işleyicileri, sıfır veya daha fazla koleksiyon belirtilebilir. İsteğe bağlı.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Belirteç yeniden yürütme algılaması sağlar ve belirteçleri sona erme süresini belirtir. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.IdentityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Windows Identity Foundation (WIF) seçenekleri uygulamalarda etkinleştirmek için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yapılandırmalar tanımlanabilir, birden çok kimlik her benzersiz bir ada sahip. Davranış aşağıdaki gibidir:  
  
1.  Hayır ise `<identityConfiguration>` öğesi belirtildi. Varsayılan kimlik yapılandırması çalışma zamanında oluşturulur ve varsayılan değerlerle doldurulur.  
  
2.  Tek bir varsa `<identityConfiguration>` öğesi belirtildi. Bu varsayılan kimlik yapılandırmasıdır. Adlı veya adlandırılmamış önemli değildir.  
  
3.  Birden çok `<identityConfiguration>` öğeleri belirtilir. Varsayılan kimlik yapılandırması adlandırılmamış öğesi belirtir. Birden çok belirttiğinizde önerilir `<identityConfiguration>` öğeleri, bunlardan biri olmalıdır adlandırılmamış.  
  
> [!WARNING]
>  Birden çok belirtirseniz `<identityConfiguration>` öğeleri, bunlardan biri olmalıdır adlandırılmamış. Adsız öğesi varsayılan kimlik yapılandırması olacaktır.  
  
 Belirtilen ayarlardan bazılarını `<identityConfiguration>` öğesi, bir güvenlik belirteci işleyicisi koleksiyon ayarlarını veya ayrı bir güvenlik belirteci işleyicileri ayarları kılınabilir.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sınıfı tarafından başvurulan kimlik yapılandırması kodunuzda beyana dayalı erişim denetimi sağlamak için `<federationConfiguration>` öğesi, talep Yetkilendirme Yöneticisi'ni ve yapmak için kullanılan ilke yapılandırır yetkilendirme kararları. Bu durum bile pasif Web senaryoları, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı yer almayan bir uygulama olmayan senaryolarda geçerlidir. Uygulama Pasif bir Web uygulaması değilse [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) öğesini (ve alt ilke öğelerine, varsa) başvurulan kimlik yapılandırmasını uygulanan yalnızca ayarlarıdır. Diğer tüm ayarları göz ardı edilir. Daha fazla bilgi için [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.  
  
 `<identityConfiguration>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> sınıfı. Bir kimlik yapılandırma bölümü tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityConfiguration> sınıfı.  
  
> [!IMPORTANT]
>  Aşağıdaki öğeleri alt öğeleri olarak belirterek `<identityConfiguration>` öğesi kullanımdan kaldırıldı, rağmen davranışı hala geriye dönük uyumluluk için desteklenir. Bu öğeleri bunun yerine, altında belirtilmelidir [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi.  
>   
>  -   [\<AudienceUri >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, "alternateConfiguration" adlı bir kimlik yapılandırması oluşturur. Kimlik yapılandırması, varsayılan ayarları belirtir.  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
