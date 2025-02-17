---
description: 'Hakkında daha fazla bilgi edinin: <federationConfiguration>'
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: f8793a8fbd6fc6d5e6994c8e368f587b740e5973
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748992"
---
# \<federationConfiguration>

<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> WS-Federation protokolü aracılığıyla federal kimlik doğrulaması kullanırken (wsfab) ve (Sam) öğesini yapılandırır. <xref:System.Security.Claims.ClaimsAuthorizationManager> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken öğesini yapılandırır.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a>Syntax  
  
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
|ıdentityconfigurationname|Kullanılacak bir öğede belirtilen kimlik yapılandırma bölümünün adı [\<identityConfiguration>](identityconfiguration.md) . Bu öznitelik belirtilmemişse, varsayılan kimlik yapılandırma bölümü kullanılır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|SAM tarafından kullanılan tanımlama bilgisi işleyicisini yapılandırır. İsteğe bağlı.|  
|[\<serviceCertificate>](servicecertificate.md)|Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır. İsteğe bağlı.|  
|[\<wsFederation>](wsfederation.md)|WS-Federation kimlik doğrulama modülünü (WSFAD) yapılandırır. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.|  
  
## <a name="remarks"></a>Açıklamalar  

 \<federationConfiguration>Öğesi iki farklı senaryoda ayarlar sağlar:  
  
- Pasif bir Web uygulamasında WS-Federation kullanırken, öğesi <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (wsfab) ve (Sam) öğesini yapılandıran ayarları içerir <xref:System.IdentityModel.Services.SessionAuthenticationModule> . Ayrıca güvenlik belirteci işleyicilerini ve sertifikaları ve talep Yetkilendirme Yöneticisi ve talep kimlik doğrulama Yöneticisi gibi bileşenleri yapılandırmak için kullanılacak kimlik yapılandırmasına de başvurur.  
  
- <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, öğesi, yetkilendirme kararları almak için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandıran kimlik yapılandırmasına başvurur. Bu, pasif Web senaryoları olmayan senaryolarda bile geçerlidir; Örneğin, Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama. Uygulama pasif bir Web uygulaması değilse, öğesi [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) tarafından başvurulan kimlik yapılandırmasının öğesi (ve varsa alt ilke öğeleri) `<federationConfiguration>` uygulanır. Diğerlerinin hepsi yok sayılır.  
  
 Senaryosundan bağımsız olarak, çalışma zamanı varsayılan Federasyon yapılandırmasını yükler. Davranış aşağıdaki gibi tanımlanır:  
  
1. Hiçbir `<federationConfiguration>` öğe yoksa, çalışma zamanı bir Federasyon yapılandırması oluşturur ve varsayılan değerlerle doldurur. Bu varsayılan Federasyon yapılandırması varsayılan kimlik yapılandırmasına başvuracaktır.  
  
2. Tek bir öğe varsa, bu, `<federationConfiguration>` adlandırılmış veya adlandırılmamış olmasına bakılmaksızın varsayılan Federasyon yapılandırmadır. `identityConfiguration`Özniteliği belirtilmişse, adlandırılmış kimlik yapılandırmasına başvurulur; Aksi takdirde, varsayılan kimlik yapılandırmasına başvurulur.  
  
3. Adlandırılmamış bir `<federationConfiguration>` öğe varsa, varsayılan Federasyon yapılandırması olur. `identityConfiguration`Özniteliği belirtilmişse, adlandırılmış kimlik yapılandırmasına başvurulur; Aksi takdirde, varsayılan kimlik yapılandırmasına başvurulur.  
  
4. Birden çok adlandırılmış `<federationConfiguration>` öğe varsa ve hiçbir adlandırılmamış `<federationConfiguration>` öğe yoksa, bir özel durum oluşturulur.  
  
 Genellikle yalnızca tek bir `<federationConfiguration>` bölüm tanımlanmıştır. Bu bölüm varsayılan Federasyon yapılandırması ' dır. Benzersiz olarak adlandırılmış birden çok `<federationConfiguration>` öğe belirtebilirsiniz; ancak, bu durumda, adlandırılmamış bir yapılandırma dışında bir Federasyon yapılandırması yüklemek istiyorsanız, için bir işleyici sağlamanız gerekir. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> olay ve <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> işleyici içindeki özelliği, <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> yapılandırma dosyasındaki uygun öğeden alınan değerlerle başlatılan bir nesne olarak ayarlayın `<federationConfiguration>` .  
  
 `<federationConfiguration>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> . Yapılandırma nesnesinin kendisi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> . Özellikte tek bir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> örnek ayarlanır <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ve uygulama için Federal yapılandırma sağlar.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki XML, `<federationConfiguration>` WSFAB için ayarları belirten bir öğe gösterir ve varsayılan tanımlama bilgisi işleyicisinin (sınıfın bir örneği <xref:System.IdentityModel.Services.ChunkedCookieHandler> ) Sam tarafından kullanılacağını belirtir.  
  
> [!WARNING]
> Bu örnekte, HTTPS kullanmak için tanımlama bilgisi işleyicisi veya WSFAE gerekmez. Bunun nedeni, `requireHttps` öğesindeki özniteliği ve içindeki `<wsFederation>` `requireSsl` özniteliğidir `<cookieHandlerElement>` `false` . Bu ayarlar, çoğu üretim ortamında bir güvenlik riski sunabilecek şekilde önerilmez.  
  
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
