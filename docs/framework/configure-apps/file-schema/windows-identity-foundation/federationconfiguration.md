---
title: "&lt;Federationconfiguration'a&gt;"
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 44014d620dcd03e055eb58b50a1428b8e1b41186
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759393"
---
# <a name="ltfederationconfigurationgt"></a>&lt;Federationconfiguration'a&gt;
Yapılandırır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) kullanırken federe kimlik doğrulaması WS-Federasyon protokolü aracılığıyla. Yapılandırır <xref:System.Security.Claims.ClaimsAuthorizationManager> kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> talep tabanlı erişim denetimi sağlamak için sınıf.  
  
 \<system.identityModel.services >  
\<Federationconfiguration'a >  
  
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
|name|Bu Federasyon yapılandırma öğesinin adı. Bu öznitelik, gelecekteki iletişim kuralları için öncelikle bir genişletilebilirlik noktası sağlar. İsteğe bağlı.|  
|identityConfigurationName|Belirtilen kimlik yapılandırma bölümünün adını bir [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanın. Bu özniteliği belirtilmezse, varsayılan kimlik yapılandırma bölümü kullanılır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|SAM tarafından kullanılan tanımlama bilgisi işleyicisi yapılandırır. İsteğe bağlı.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Şifrelemek ve belirteçlerin şifresini çözmek için kullanılan sertifikayı yapılandırır. İsteğe bağlı.|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|WS-Federasyon kimlik doğrulama Modülü (WSFAM) yapılandırır. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|WS-Federasyon protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.|  
  
## <a name="remarks"></a>Açıklamalar  
 \<Federationconfiguration'a > öğesi, iki farklı senaryolar ayarlarında sağlar:  
  
-   WS-Federasyon pasif Web uygulamasında kullanırken, yapılandırdığınız ayarları ögesinin <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Güvenlik belirteci işleyicileri ve sertifikaları ve bileşenleri talep Yetkilendirme Yöneticisi ve talep gibi yapılandırmak için kullanılacak kimlik yapılandırması başvuruda bulunuyor.  
  
-   Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> kodunuzda talep tabanlı erişim denetimi sağlamak için sınıf, talep Yetkilendirme Yöneticisi'ni ve yetkilendirme yapmak için kullanılan ilke yapılandırır kimlik yapılandırması öğesine başvuruda bulunuyor kararlar. Bu bile pasif Web senaryoları olmayan senaryolarda geçerlidir; Örneğin, Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama. Uygulama Pasif bir Web uygulaması değilse [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) öğesi (ve alt ilke öğeleri, varsa) tarafından başvurulan kimlik yapılandırmasının `<federationConfiguration>` öğesi yalnızca ayarları uygulanır. Diğerleri yoksayılır.  
  
 Senaryo bağımsız olarak, varsayılan Federasyon yapılandırma çalışma zamanı yükler. Davranışı aşağıdaki gibi tanımlanır:  
  
1.  Varsa hiçbir `<federationConfiguration>` öğe yok, çalışma zamanı Federasyon yapılandırmasını oluşturur ve varsayılan değerlerle doldurur. Bu varsayılan Federasyon yapılandırma, varsayılan kimlik yapılandırması başvurur.  
  
2.  Tek bir varsa `<federationConfiguration>` öğesi mevcutsa, olup, adlı adlandırılmamış veya bağımsız olarak varsayılan Federasyon yapılandırması. Varsa, `identityConfiguration` özniteliği belirtilmediyse, adlandırılmış kimlik yapılandırması başvurulur; Aksi takdirde varsayılan kimlik yapılandırması başvuruluyor.  
  
3.  Bir adlandırılmamış varsa `<federationConfiguration>` öğe varsa, varsayılan Federasyon yapılandırma budur. Varsa, `identityConfiguration` özniteliği belirtilmediyse, adlandırılmış kimlik yapılandırması başvurulur; Aksi takdirde varsayılan kimlik yapılandırması başvuruluyor.  
  
4.  Birden çok adlandırırsanız `<federationConfiguration>` öğeleri mevcut ve Hayır adlandırılmamış `<federationConfiguration>` öğesi mevcutsa, bir özel durum.  
  
 Genellikle, yalnızca tek bir `<federationConfiguration>` bölümünde tanımlanır. Bu bölümde varsayılan Federasyon yapılandırmadır. Birden çok, benzersiz olarak adlandırılmış belirtebilir `<federationConfiguration>` öğeleri; adlandırılmamış farklı bir Federasyon yapılandırma yüklemek istiyorsanız, ancak bu durumda, bir işleyici sağlamanız gerekir. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> Olay ve kümesi <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> özelliği işleyicisine içinde bir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> uygun değerlerle başlatılan nesne `<federationConfiguration>` yapılandırma dosyası öğesi.  
  
 `<federationConfiguration>` Öğesi ile temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> sınıfı. Yapılandırma nesnesi tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> sınıfı. Tek bir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> örneği ayarlanmış <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği ve uygulama için Federasyon yapılandırma sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML gösterildiği bir `<federationConfiguration>` WSFAM ayarlarını belirtir ve belirten öğesi varsayılan tanımlama bilgisi işleyicisi (örneği <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfı) SAM tarafından kullanılabilir.  
  
> [!WARNING]
>  Bu örnekte, tanımlama bilgisi işleyici ne WSFAM HTTPS kullanmak için gereklidir. Bunun nedeni, `requireHttps` özniteliği `<wsFederation>` öğesi ve `requireSsl` özniteliği `<cookieHandlerElement>` olan `false`. Bir güvenlik riski sayılabilir gibi bu ayarların çoğu üretim ortamları için önerilmez.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
