---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152742"
---
# <a name="federationconfiguration"></a>\<federasyonKonfigürasyon>
WS-Federation <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> protokolü aracılığıyla federe <xref:System.IdentityModel.Services.SessionAuthenticationModule> kimlik doğrulaması kullanırken (WSFAM) ve (SAM) yapılandırır. Talep tabanlı <xref:System.Security.Claims.ClaimsAuthorizationManager> erişim <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> denetimi <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sağlamak için sınıfı veya sınıfı kullanırken yapılandırır.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federasyonKonfigürasyon>**  
  
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
|ad|Bu federasyon yapılandırma öğesinin adı. Bu öznitelik öncelikle gelecekteki protokoller için bir genişletilebilirlik noktası sağlar. İsteğe bağlı.|  
|identityConfigurationName|Kimlik yapılandırma bölümünde belirtildiği [ \<](identityconfiguration.md) gibi adı Yapılandırma>öğesi kullanmak. Bu öznitelik belirtilmemişse, varsayılan kimlik yapılandırma sı. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|SAM tarafından kullanılan çerez işleyicisini yapılandırır. İsteğe bağlı.|  
|[\<serviceSertifika>](servicecertificate.md)|Belirteçleri şifrelemek ve şifresini çözmek için kullanılan sertifikayı yapılandırır. İsteğe bağlı.|  
|[\<wsFederasyon>](wsfederation.md)|WS-Federation Kimlik Doğrulama Modüllerini (WSFAM) yapılandırır. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|WS-Federation protokolünü kullanarak kimlik doğrulama için yapılandırma bölümü.|  
  
## <a name="remarks"></a>Açıklamalar  
 FederasyonYapılandırma \<> öğesi iki farklı senaryoda ayarlar sağlar:  
  
- Pasif bir Web uygulamasında WS-Federation kullanırken, öğe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) yapılandıran ayarları içerir. Ayrıca, güvenlik belirteç işleyicileri ve sertifikalarını yapılandırmak için kullanılacak kimlik yapılandırmasına ve talep yetkilendirme yöneticisi ve talep kimlik doğrulama yöneticisi gibi bileşenlere de başvurur.  
  
- Parolanızda <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> talep <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> tabanlı erişim denetimi sağlamak için sınıfı veya sınıfı kullanırken, öğe yetkilendirme yöneticisini yapılandıran kimlik yapılandırmasına ve yetkilendirme kararları almak için kullanılan ilkeye başvurur. Bu, pasif Web senaryoları olmayan senaryolarda bile doğrudur; örneğin, Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama. Uygulama pasif bir Web uygulaması değilse, `<federationConfiguration>` öğe tarafından başvurulan kimlik yapılandırmasının [ \<claimsAuthorizationManager>](claimsauthorizationmanager.md) öğesi (ve varsa alt ilke öğeleri) yalnızca uygulanan ayarlardır. Diğerleri göz ardı edilir.  
  
 Senaryodan bağımsız olarak, çalışma zamanı varsayılan federasyon yapılandırmasını yükler. Davranış aşağıdaki gibi tanımlanır:  
  
1. Öğe yoksa, `<federationConfiguration>` çalışma zamanı bir federasyon yapılandırması oluşturur ve varsayılan değerlerle doldurur. Bu varsayılan federasyon yapılandırması varsayılan kimlik yapılandırması başvurur.  
  
2. Tek `<federationConfiguration>` bir öğe varsa, adı veya adı açıklanmayan ne olursa olsun varsayılan federasyon yapılandırmasıdır. `identityConfiguration` Özniteliği belirtilirse, adlandırılmış kimlik yapılandırmasına başvurulur; aksi takdirde, varsayılan kimlik yapılandırması başvurur.  
  
3. Adı açıklanmayan `<federationConfiguration>` bir öğe varsa, varsayılan federasyon yapılandırmasıdır. `identityConfiguration` Özniteliği belirtilirse, adlandırılmış kimlik yapılandırmasına başvurulur; aksi takdirde, varsayılan kimlik yapılandırması başvurur.  
  
4. Birden çok `<federationConfiguration>` adlandırılmış öğe `<federationConfiguration>` varsa ve adsız öğe yoksa, bir özel durum atılır.  
  
 Genellikle, yalnızca tek `<federationConfiguration>` bir bölüm tanımlanır. Bu bölüm varsayılan federasyon yapılandırmasıdır. Birden çok, benzersiz adlandırılmış `<federationConfiguration>` öğe belirtebilirsiniz; ancak, bu durumda, adı açıklanmayan bir federasyon yapılandırması dışında bir federasyon yapılandırması yüklemek istiyorsanız, bir işleyici sağlamanız gerekir. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>olay ve <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> yapılandırma dosyasında uygun `<federationConfiguration>` <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> öğeden değerleri ile başharfe bir nesne için işleyici içinde özelliği ayarlayın.  
  
 Öğe `<federationConfiguration>` <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> sınıf tarafından temsil edilir. Yapılandırma nesnesinin kendisi <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> sınıf tarafından temsil edilir. Tek <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> bir örnek <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özellik üzerinde ayarlanır ve uygulama için federe yapılandırma sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, `<federationConfiguration>` WSFAM ayarlarını belirten ve varsayılan çerez işleyicisinin <xref:System.IdentityModel.Services.ChunkedCookieHandler> (sınıfın bir örneği) SAM tarafından kullanılmasını belirten bir öğe gösterir.  
  
> [!WARNING]
> Bu örnekte, ne çerez işleyicisi ne de WSFAM'nin HTTPS kullanması gerekmez. Bunun nedeni, `requireHttps` öğedeki `<wsFederation>` öznitelik `requireSsl` ve `<cookieHandlerElement>` öznitelik. `false` Bu ayarlar, bir güvenlik riski sunabileceğiiçin çoğu üretim ortamı için önerilmez.  
  
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
- [\<identityConfiguration>](identityconfiguration.md)
