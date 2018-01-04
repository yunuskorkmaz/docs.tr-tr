---
title: '&lt;identityConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48f9eef329f5d2e0e751fd2a03b0d3af9ddc355c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
Hizmet düzeyi kimlik ayarlarını belirtir.  
  
 \<System.IdentityModel >  
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
|name|Kimlik yapılandırma bölümünün adı. Belirli yapılandırma bölümü başvurmak için bu adı kullanın. Öyle değilse `name` özniteliği belirtilmezse, varsayılan yapılandırma bölümü tanımlar. Varsayılan yapılandırma her zaman pasif Federasyon senaryoları için kullanılır. Daha fazla bilgi için bkz: [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.|  
|saveBootstrapContext|Oturum belirteci önyükleme belirteçlerini dahil edilip edilmeyeceğini belirtir. Değer ayrıca bir belirteç işleyici koleksiyonu ayarlayarak ayarlanabilir `saveBootstrapContext` özniteliği [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi. Bir değer belirteci işleyicisi koleksiyonda Ayarla hizmetinde değerini geçersiz kılar.|  
|maximumClockSkew|A <xref:System.TimeSpan> izin verilen maksimum saat eğriltme belirtir. İzin verilen maksimum saat eğriltme bir oturum açma oturumu sona erme süresini doğrulama gibi zamana duyarlı işlemlerini gerçekleştirirken denetler. 5 dakika, varsayılan değer "00: 05:00". Nasıl belirleneceği hakkında daha fazla bilgi için <xref:System.TimeSpan> değerler, bakın [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maksimum saat eğriltme ayrıca bir belirteç işleyici koleksiyonu ayarlayarak ayarlanabilir `maximumClockSkew` özniteliği [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi. Bir değer belirteci işleyicisi koleksiyonda Ayarla hizmetinde değerini geçersiz kılar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<önbelleğe alan >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Sertifikaları doğrulamak için belirteci işleyicileri kullanma ayarlarını denetler. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder. İsteğe bağlı.|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Bir gelen talep için talep Yetkilendirme Yöneticisi kaydeder. İsteğe bağlı.|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Gelen güvenlik belirteçlerinin için gerekli talep kümesini belirtir. İsteğe bağlı.|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Güvenlik belirteci işleyicileri koleksiyonunu belirtir. Güvenlik belirteci işleyicileri sıfır veya daha fazla koleksiyonları belirtilebilir. İsteğe bağlı.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Belirteç yeniden yürütme algılaması sağlar ve belirteçler için sona erme saati belirtir. Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.IdentityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Windows Identity Foundation (WIF) seçenekleri uygulamalarında etkinleştirmek için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yapılandırmaları tanımlanabilir, birden çok kimlik her benzersiz bir ada sahip. Davranış aşağıdaki gibidir:  
  
1.  Öyle değilse `<identityConfiguration>` öğesi belirtilir. Varsayılan kimlik yapılandırması çalışma zamanında oluşturulur ve varsayılan değerlerle doldurulur.  
  
2.  Tek bir varsa `<identityConfiguration>` öğesi belirtilir. Bu varsayılan kimlik yapılandırmadır. Adlı veya adsız önemi değil.  
  
3.  Birden çok `<identityConfiguration>` öğeleri belirtilir. Adlandırılmamış öğesi varsayılan kimlik yapılandırması belirtir. Birden çok belirttiğinizde önerilir `<identityConfiguration>` öğeleri, bunlardan biri olmalıdır adlandırılmamış.  
  
> [!WARNING]
>  Birden çok belirtirseniz `<identityConfiguration>` öğeleri, bunlardan biri olmalıdır adlandırılmamış. Adlandırılmamış öğesi varsayılan kimlik yapılandırması olacaktır.  
  
 Belirtilen ayarlardan bazıları `<identityConfiguration>` öğesi geçersiz kılınmış bir güvenlik belirteci işleyicisi koleksiyon ayarlarını ya da ayrı bir güvenlik belirteci işleyicileri ayarları.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> tarafından başvurulan kimlik yapılandırması kodunuzda talep tabanlı erişim denetimi sağlamak için sınıf `<federationConfiguration>` öğesi yapılandırır talep Yetkilendirme Yöneticisi'ni ve yapmak için kullanılan İlkesi yetkilendirme kararları. Bu durum bile pasif Web senaryoları, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama değildir senaryolarda geçerlidir. Uygulama Pasif bir Web uygulaması değilse [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) öğesi (ve alt ilke öğeleri, varsa) başvurulan kimlik yapılandırması olan uygulanan ayarlar. Tüm diğer ayarlar yok sayılır. Daha fazla bilgi için bkz: [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.  
  
 `<identityConfiguration>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> sınıfı. Bir kimlik yapılandırma bölümü tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityConfiguration> sınıfı.  
  
> [!IMPORTANT]
>  Aşağıdaki öğeler alt öğeleri olarak belirterek `<identityConfiguration>` öğesi kullanım dışı bırakıldı, geriye dönük uyumluluk için davranış hala desteklense. Bu öğeleri bunun yerine, altında belirtilmelidir [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi.  
>   
>  -   [\<AudienceUri >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, "alternateConfiguration" adlı bir kimlik yapılandırması oluşturur. Kimlik yapılandırması varsayılan ayarları belirtir.  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
