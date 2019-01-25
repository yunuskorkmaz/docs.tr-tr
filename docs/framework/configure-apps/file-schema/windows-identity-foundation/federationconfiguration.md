---
title: "&lt;Federationconfiguration'u&gt;"
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 6f658fb4746211ac9d7001899133111c64f22408
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645125"
---
# <a name="ltfederationconfigurationgt"></a>&lt;Federationconfiguration'u&gt;
Yapılandırır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) kullanırken, Federasyon kimlik doğrulaması WS-Federation protokolü aracılığıyla. Yapılandırır <xref:System.Security.Claims.ClaimsAuthorizationManager> kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> beyana dayalı erişim denetimi sağlamak için sınıf.  
  
 \<System.IdentityModel.Services >  
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
|name|Bu Federasyon yapılandırma öğesi adı. Bu öznitelik, gelecekteki protokoller için öncelikle bir genişletilebilirlik noktası sağlar. İsteğe bağlı.|  
|identityConfigurationName|Belirtilen kimlik yapılandırma bölümünün adını bir [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) kullanmak için öğesi. Bu öznitelik belirtilmezse, varsayılan kimlik yapılandırma bölümü kullanılır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|SAM tarafından kullanılan tanımlama bilgisi işleyicisi yapılandırır. İsteğe bağlı.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Şifreleme ve belirteç şifre çözme için kullanılan sertifikayı yapılandırır. İsteğe bağlı.|  
|[\<wsFederation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|WS-Federasyon kimlik doğrulama Modülü (WSFAM) yapılandırır. İsteğe bağlı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.IdentityModel.Services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|WS-Federasyon protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.|  
  
## <a name="remarks"></a>Açıklamalar  
 \<Federationconfiguration'a > öğesi iki farklı senaryolarda ayarları sağlar:  
  
-   WS-Federasyon Pasif bir Web uygulamasında kullanırken, yapılandırdığınız ayarları ögesinin <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Ayrıca, güvenlik belirteci işleyicileri ve sertifikaları ve talep Yetkilendirme Yöneticisi'ni ve talepler kimlik doğrulama Yöneticisi gibi bileşenleri yapılandırmak için kullanılacak kimlik yapılandırması başvuruyor.  
  
-   Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> kodunuzda beyana dayalı erişim denetimi sağlamak için sınıf, talep Yetkilendirme Yöneticisi'ni ve yetkilendirme sağlamak için kullanılan ilke yapılandırır kimlik yapılandırma öğesine başvuruda bulunuyor kararları. Bu da pasif Web senaryoları olmayan senaryolarda geçerlidir; Örneğin, Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı yer almayan bir uygulama. Uygulama Pasif bir Web uygulaması değilse [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) öğesini (ve alt ilke öğelerine, varsa) tarafından başvurulan kimlik yapılandırmasının `<federationConfiguration>` öğesi yalnızca ayarlar uygulanır. Diğerleri yoksayılır.  
  
 Senaryo bağımsız olarak, çalışma zamanı varsayılan Federasyon yapılandırması yükler. Davranışı şu şekilde tanımlanır:  
  
1.  Yoksa hiçbir `<federationConfiguration>` öğe yok, çalışma zamanı bir Federasyon yapılandırması oluşturur ve varsayılan değerlerle doldurur. Bu varsayılan Federasyon yapılandırma, varsayılan kimlik yapılandırması başvurur.  
  
2.  Tek bir varsa `<federationConfiguration>` öğe varsa, bunu adlı adlandırılmamış mı bağımsız olarak varsayılan Federasyon yapılandırması. Varsa, `identityConfiguration` özniteliği belirtilirse, adlandırılmış kimlik yapılandırması başvuruyor; Aksi takdirde varsayılan kimlik yapılandırması başvurulur.  
  
3.  Adlandırılmamış bir varsa `<federationConfiguration>` öğe varsa, varsayılan Federasyon yapılandırması. Varsa, `identityConfiguration` özniteliği belirtilirse, adlandırılmış kimlik yapılandırması başvuruyor; Aksi takdirde varsayılan kimlik yapılandırması başvurulur.  
  
4.  Birden çok adlı `<federationConfiguration>` öğeleri mevcut ve Hayır adlandırılmamış `<federationConfiguration>` öğe varsa, bir özel durum oluşturulur.  
  
 Genellikle, yalnızca tek bir `<federationConfiguration>` bölümünde tanımlanır. Bu bölümde varsayılan Federasyon yapılandırmasıdır. Birden çok, benzersiz olarak adlandırılmış belirtebilir `<federationConfiguration>` öğeleri; adlandırılmamış farklı bir Federasyon yapılandırması yüklemek istiyorsanız, ancak bu durumda, işleyici sağlamalısınız. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> Olay ve set <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> özellik işleyicisi içine bir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> uygun değerlerle başlatılan nesne `<federationConfiguration>` yapılandırma dosyasındaki öğesi.  
  
 `<federationConfiguration>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> sınıfı. Yapılandırma nesnesi tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> sınıfı. Tek bir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> örneğine ayarlanır <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği ve uygulama için Federasyon yapılandırma sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML gösterildiği bir `<federationConfiguration>` WSFAM ayarlarını belirler ve belirten öğe varsayılan tanımlama bilgisi işleyicisi (bir örneğini <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfı) tarafından SAM kullanılabilir.  
  
> [!WARNING]
>  Bu örnekte, tanımlama bilgisi işleyici ne WSFAM HTTPS kullanmak için gereklidir. Bunun nedeni, `requireHttps` özniteliği `<wsFederation>` öğesi ve `requireSsl` özniteliği `<cookieHandlerElement>` olan `false`. Bunlar bir güvenlik riski sunabilir gibi bu ayarların çoğu üretim ortamları için önerilmez.  
  
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
- [\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
