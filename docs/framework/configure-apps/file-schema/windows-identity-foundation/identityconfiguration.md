---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251990"
---
# \<identityConfiguration>

Hizmet düzeyi kimlik ayarlarını belirtir.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

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
|name|Kimlik yapılandırma bölümünün adı. Bu adı, belirli bir yapılandırma bölümüne başvurmak için kullanabilirsiniz. Hiçbir `name` öznitelik belirtilmemişse, Bölüm varsayılan yapılandırmayı tanımlar. Varsayılan yapılandırma, Pasif Federasyon senaryolarında her zaman kullanılır. Daha fazla bilgi için, bkz [\<federationConfiguration>](federationconfiguration.md) . öğesi.|
|Savebootstrapbağlamı|Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir. Değer, öğe üzerinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda de ayarlanabilir `saveBootstrapContext` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) . Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|
|maximumClockSkew|<xref:System.TimeSpan>İzin verilen maksimum saat eğriliğini belirten bir. Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler. Varsayılan değer 5 dakikadır, "00:05:00". Değerlerin nasıl belirtilmesi hakkında daha fazla bilgi için <xref:System.TimeSpan> bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md). Öğe üzerinde özniteliği ayarlanarak, bir belirteç işleyici koleksiyonunda maksimum saat eğriltme de ayarlanabilir `maximumClockSkew` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) . Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<caches>](caches.md)|Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|
|[\<certificateValidation>](certificatevalidation.md)|Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder. İsteğe bağlı.|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|Gelen talepler için bir talep Yetkilendirme Yöneticisi kaydeder. İsteğe bağlı.|
|[\<claimTypeRequired>](claimtyperequired.md)|Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir. İsteğe bağlı.|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Bir güvenlik belirteci işleyicileri koleksiyonunu belirtir. Sıfır veya daha fazla güvenlik belirteci işleyicisi koleksiyonu belirtilebilir. İsteğe bağlı.|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir. , Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir. İsteğe bağlı.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.|

## <a name="remarks"></a>Açıklamalar

Her biri benzersiz bir ada sahip birden çok kimlik yapılandırması tanımlanabilir. Davranış aşağıdaki gibidir:

1. Eğer hiçbir `<identityConfiguration>` öğe belirtilmemişse. Çalışma zamanında varsayılan bir kimlik yapılandırması oluşturulur ve varsayılan değerlerle doldurulur.

2. Tek bir `<identityConfiguration>` öğe belirtilmişse. Varsayılan kimlik yapılandırması. Adlandırılmış veya adlandırılmamış bir önemi yoktur.

3. Birden çok `<identityConfiguration>` öğe belirtilmişse. Adlandırılmamış öğe varsayılan kimlik yapılandırmasını belirtir. Birden çok `<identityConfiguration>` öğe belirttiğinizde, bunlardan birinin adlandırılmamış olması önerilir.

> [!WARNING]
> Birden çok öğe belirtirseniz `<identityConfiguration>` , bunlardan biri adlandırılmamış olmalıdır. Adlandırılmamış öğe varsayılan kimlik yapılandırması olacaktır.

 Öğesinde belirtilen ayarlardan bazıları `<identityConfiguration>` bir güvenlik belirteci işleyici koleksiyonundaki ayarlar veya ayrı güvenlik belirteci işleyicilerindeki ayarlar tarafından geçersiz kılınabilir.

> [!IMPORTANT]
> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, öğesinin başvurduğu kimlik yapılandırması, `<federationConfiguration>` yetkilendirme kararları vermek için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandırır. Bu, pasif Web senaryoları olmayan senaryolarda bile, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama için de geçerlidir. Uygulama pasif bir Web uygulaması değilse, [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) başvurulan kimlik yapılandırmasının öğesi (ve varsa alt ilke öğeleri) uygulanan tek ayarlardır. Diğer tüm ayarlar yoksayılır. Daha fazla bilgi için, bkz [\<federationConfiguration>](federationconfiguration.md) . öğesi.

`<identityConfiguration>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> . Bir kimlik yapılandırma bölümü sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityConfiguration> .

> [!IMPORTANT]
> Aşağıdaki öğeleri öğesinin alt öğeleri olarak belirtmek `<identityConfiguration>` kullanım dışı bırakılmıştır, ancak davranış geriye dönük uyumluluk için hala desteklenir. Bu öğeler, bunun yerine öğesi altında belirtilmelidir [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) .
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

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
