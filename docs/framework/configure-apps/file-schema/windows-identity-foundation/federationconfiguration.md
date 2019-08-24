---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: c4dbb31bb7961f0d33df9d1faee8fe36ecb520a3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988324"
---
# <a name="federationconfiguration"></a>\<federationConfiguration >
WS-Federation protokolü aracılığıyla federal kimlik doğrulaması kullanırken <xref:System.IdentityModel.Services.SessionAuthenticationModule> (wsfab)ve(Sam)öğesiniyapılandırır.<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> Talep tabanlı erişim denetimi sağlamak <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> için veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sınıfını kullanırken öğesini yapılandırır. <xref:System.Security.Claims.ClaimsAuthorizationManager>  
  
 \<System. IdentityModel. Services >  
\<federationConfiguration >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Bu Federasyon yapılandırma öğesinin adı. Bu öznitelik, öncelikle gelecekteki protokoller için bir genişletilebilirlik noktası sağlar. İsteğe bağlı.|  
|ıdentityconfigurationname|Kullanılacak bir [ \<IdentityConfiguration >](identityconfiguration.md) öğesinde belirtilen kimlik yapılandırma bölümünün adı. Bu öznitelik belirtilmemişse, varsayılan kimlik yapılandırma bölümü kullanılır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tanımlama, ıehandler >](cookiehandler.md)|SAM tarafından kullanılan tanımlama bilgisi işleyicisini yapılandırır. İsteğe bağlı.|  
|[\<serviceCertificate >](servicecertificate.md)|Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır. İsteğe bağlı.|  
|[\<wsFederation >](wsfederation.md)|WS-Federation Authentication modülünü (WSFAD) yapılandırır. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System. IdentityModel. Services >](system-identitymodel-services.md)|WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.|  
  
## <a name="remarks"></a>Açıklamalar  
 FederationConfiguration > öğesi, \<ayarları iki farklı senaryoda sağlar:  
  
- Bir pasif Web uygulamasında WS-Federation kullanılırken, öğesi <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (wsfak) <xref:System.IdentityModel.Services.SessionAuthenticationModule> ve (Sam) öğesini yapılandıran ayarları içerir. Ayrıca güvenlik belirteci işleyicilerini ve sertifikaları ve talep Yetkilendirme Yöneticisi ve talep kimlik doğrulama Yöneticisi gibi bileşenleri yapılandırmak için kullanılacak kimlik yapılandırmasına de başvurur.  
  
- Kodunuzda talep tabanlı <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> erişim denetimi <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sağlamak için veya sınıfını kullanırken, öğesi, yetkilendirme yapmak için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandıran kimlik yapılandırmasına başvurur kararlar. Bu, pasif Web senaryoları olmayan senaryolarda bile geçerlidir; Örneğin, Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama. Uygulama pasif bir Web uygulaması değilse, [ \<ClaimsAuthorizationManager >](claimsauthorizationmanager.md) öğesi (ve varsa alt ilke öğeleri) `<federationConfiguration>` öğe tarafından başvurulan kimlik yapılandırması tek ayarlardır uygulanmış. Diğerlerinin hepsi yok sayılır.  
  
 Senaryosundan bağımsız olarak, çalışma zamanı varsayılan Federasyon yapılandırmasını yükler. Davranış aşağıdaki gibi tanımlanır:  
  
1. Hiçbir `<federationConfiguration>` öğe yoksa, çalışma zamanı bir Federasyon yapılandırması oluşturur ve varsayılan değerlerle doldurur. Bu varsayılan Federasyon yapılandırması varsayılan kimlik yapılandırmasına başvuracaktır.  
  
2. Tek `<federationConfiguration>` bir öğe varsa, bu, adlandırılmış veya adlandırılmamış olmasına bakılmaksızın varsayılan Federasyon yapılandırmadır. `identityConfiguration` Özniteliği belirtilmişse, adlandırılmış kimlik yapılandırmasına başvurulur; Aksi takdirde, varsayılan kimlik yapılandırmasına başvurulur.  
  
3. Adlandırılmamış `<federationConfiguration>` bir öğe varsa, varsayılan Federasyon yapılandırması olur. `identityConfiguration` Özniteliği belirtilmişse, adlandırılmış kimlik yapılandırmasına başvurulur; Aksi takdirde, varsayılan kimlik yapılandırmasına başvurulur.  
  
4. Birden çok adlandırılmış `<federationConfiguration>` öğe varsa ve hiçbir adlandırılmamış `<federationConfiguration>` öğe yoksa, bir özel durum oluşturulur.  
  
 Genellikle yalnızca tek `<federationConfiguration>` bir bölüm tanımlanmıştır. Bu bölüm varsayılan Federasyon yapılandırması ' dır. Benzersiz olarak adlandırılmış `<federationConfiguration>` birden çok öğe belirtebilirsiniz; ancak, bu durumda, adlandırılmamış bir yapılandırma dışında bir Federasyon yapılandırması yüklemek istiyorsanız, için bir işleyici sağlamanız gerekir. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>olay ve işleyici içindeki <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> özelliği, yapılandırma dosyasındaki uygun `<federationConfiguration>` öğeden <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> alınan değerlerle başlatılan bir nesne olarak ayarlayın.  
  
 `<federationConfiguration>` Öğesi sınıfı<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> tarafından temsil edilir. Yapılandırma nesnesinin kendisi <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> sınıfı tarafından temsil edilir. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> Özellikte tek <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> bir örnek ayarlanır ve uygulama için Federal yapılandırma sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, wsfab için ayarları belirten bir `<federationConfiguration>` öğe gösterir ve varsayılan tanımlama bilgisi işleyicisinin ( <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfın bir örneği) Sam tarafından kullanılacağını belirtir.  
  
> [!WARNING]
> Bu örnekte, HTTPS kullanmak için tanımlama bilgisi işleyicisi veya WSFAE gerekmez. Bunun nedeni `requireHttps` , `<wsFederation>` öğesindeki özniteliği `requireSsl` veiçindeki`false`özniteliğidir. `<cookieHandlerElement>` Bu ayarlar, çoğu üretim ortamında bir güvenlik riski sunabilecek şekilde önerilmez.  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<IdentityConfiguration >](identityconfiguration.md)
