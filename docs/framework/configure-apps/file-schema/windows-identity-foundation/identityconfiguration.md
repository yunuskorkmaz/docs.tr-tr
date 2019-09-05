---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251990"
---
# <a name="identityconfiguration"></a>\<IdentityConfiguration >

Hizmet düzeyi kimlik ayarlarını belirtir.

[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<IdentityConfiguration >**  

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
|name|Kimlik yapılandırma bölümünün adı. Bu adı, belirli bir yapılandırma bölümüne başvurmak için kullanabilirsiniz. Hiçbir `name` öznitelik belirtilmemişse, Bölüm varsayılan yapılandırmayı tanımlar. Varsayılan yapılandırma, Pasif Federasyon senaryolarında her zaman kullanılır. Daha fazla bilgi için, bkz [ \<. FederationConfiguration >](federationconfiguration.md) öğesi.|
|Savebootstrapbağlamı|Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir. Ayrıca, `saveBootstrapContext` [ \<SecurityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) öğesinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda değer de ayarlanabilir. Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|
|maximumClockSkew|İzin <xref:System.TimeSpan> verilen maksimum saat eğriliğini belirten bir. Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler. Varsayılan değer 5 dakikadır, "00:05:00". Değerlerin nasıl belirtilmesi <xref:System.TimeSpan> hakkında daha fazla bilgi için bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md). Bir belirteç işleyici koleksiyonunda, `maximumClockSkew` [ \<SecurityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) öğesinde özniteliği ayarlanarak maksimum saat eğriltme de ayarlanabilir. Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<önbellekler >](caches.md)|Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|
|[\<certificateValidation >](certificatevalidation.md)|Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|
|[\<claimsAuthenticationManager >](claimsauthenticationmanager.md)|Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder. İsteğe bağlı.|
|[\<claimsAuthorizationManager >](claimsauthorizationmanager.md)|Gelen talepler için bir talep Yetkilendirme Yöneticisi kaydeder. İsteğe bağlı.|
|[\<claimTypeRequired >](claimtyperequired.md)|Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir. İsteğe bağlı.|
|[\<securityTokenHandlers >](securitytokenhandlers.md)|Bir güvenlik belirteci işleyicileri koleksiyonunu belirtir. Sıfır veya daha fazla güvenlik belirteci işleyicisi koleksiyonu belirtilebilir. İsteğe bağlı.|
|[\<tokenReplayDetection >](tokenreplaydetection.md)|Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<System. IdentityModel >](system-identitymodel.md)|Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.|

## <a name="remarks"></a>Açıklamalar

Her biri benzersiz bir ada sahip birden çok kimlik yapılandırması tanımlanabilir. Davranış aşağıdaki gibidir:

1. Eğer hiçbir `<identityConfiguration>` öğe belirtilmemişse. Çalışma zamanında varsayılan bir kimlik yapılandırması oluşturulur ve varsayılan değerlerle doldurulur.

2. Tek `<identityConfiguration>` bir öğe belirtilmişse. Varsayılan kimlik yapılandırması. Adlandırılmış veya adlandırılmamış bir önemi yoktur.

3. Birden çok `<identityConfiguration>` öğe belirtilmişse. Adlandırılmamış öğe varsayılan kimlik yapılandırmasını belirtir. Birden çok `<identityConfiguration>` öğe belirttiğinizde, bunlardan birinin adlandırılmamış olması önerilir.

> [!WARNING]
> Birden çok `<identityConfiguration>` öğe belirtirseniz, bunlardan biri adlandırılmamış olmalıdır. Adlandırılmamış öğe varsayılan kimlik yapılandırması olacaktır.

 `<identityConfiguration>` Öğesinde belirtilen ayarlardan bazıları bir güvenlik belirteci işleyici koleksiyonundaki ayarlar veya ayrı güvenlik belirteci işleyicilerindeki ayarlar tarafından geçersiz kılınabilir.

> [!IMPORTANT]
> Kodunuzda talep tabanlı <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> erişim denetimi <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sağlamak için ya da sınıfını kullanırken, `<federationConfiguration>` öğesi tarafından başvurulan kimlik yapılandırması, bu işlemi yapmak için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandırır yetkilendirme kararları. Bu, pasif Web senaryoları olmayan senaryolarda bile, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama için de geçerlidir. Uygulama pasif bir Web uygulaması değilse, [ \<başvurulan kimlik yapılandırmasının ClaimsAuthorizationManager >](claimsauthorizationmanager.md) öğesi (ve varsa alt ilke öğeleri) uygulanan tek ayarlardır. Diğer tüm ayarlar yoksayılır. Daha fazla bilgi için, bkz [ \<. FederationConfiguration >](federationconfiguration.md) öğesi.

`<identityConfiguration>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.IdentityConfigurationElement> tarafından temsil edilir. Bir kimlik yapılandırma bölümü <xref:System.IdentityModel.Configuration.IdentityConfiguration> sınıfı tarafından temsil edilir.

> [!IMPORTANT]
> Aşağıdaki öğeleri `<identityConfiguration>` öğesinin alt öğeleri olarak belirtmek kullanım dışı bırakılmıştır, ancak davranış geriye dönük uyumluluk için hala desteklenir. Bunun yerine, bu öğeler, [ \<SecurityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) öğesi altında belirtilmelidir.
>
> - [\<audienceUris >](audienceuris.md)
> - [\<ıssuernameregbakanlığı >](issuernameregistry.md)
> - [\<IssuerTokenResolver >](issuertokenresolver.md)
> - [\<serviceTokenResolver >](servicetokenresolver.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, "alternateConfiguration" adlı bir kimlik yapılandırması oluşturur. Kimlik yapılandırması varsayılan ayarları belirtir.

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
