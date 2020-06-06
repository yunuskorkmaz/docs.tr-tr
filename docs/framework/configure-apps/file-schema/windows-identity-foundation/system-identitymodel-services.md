---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152510"
---
# \<system.identityModel.services>
WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
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
 Yok  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) http modüllerini yapılandıran ayarları içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 Yok  
  
## <a name="remarks"></a>Açıklamalar  
 `<system.identityModel.services>`Sam ve WSFAE ayarlarını sağlamak için uygulamanızın yapılandırma dosyasına bir bölüm ekleyin.  
  
> [!IMPORTANT]
> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, <xref:System.Security.Claims.ClaimsAuthorizationManager> yetkilendirme kararları vermek için kullanılan talep Yetkilendirme Yöneticisi () ve ilke, `<identityConfiguration>` Bu bölümdeki bir öğeden örtük olarak veya açıkça başvurulan bir öğe aracılığıyla yapılandırılır `<federationConfiguration>` . Daha fazla bilgi için, öğesinin **altındaki açıklamalara** bakın [\<federationConfiguration>](federationconfiguration.md) .  
  
 `<system.identityModel.services>`Bölümü sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> . `<federationConfiguration>`Bölümünde yapılandırılan alt öğelerin koleksiyonu sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, `<system.identityModel.services>` bir yapılandırma dosyasına bir bölümün nasıl ekleneceğini gösterir. Öncelikle bölüm ve bölümler için bölüm bildirimleri eklemeniz gerekir `<system.identityModel.services>` `<system.identityModel>` . (Bir `<system.identityModel.services>` bölümü eklediğinizde, `<system.identityModel>` `<identityConfiguration>` gerekirse çalışma zamanı tarafından varsayılan bir bölümün oluşturulabilmelidir emin olmak için bölüm için bir bildirim de eklemeniz gerekir.) Bölüm bildirimleri eklendikten sonra, öğesinin altında federal kimlik doğrulama ayarlarını yapılandırabilirsiniz `<system.identityModel.services>` .  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```
