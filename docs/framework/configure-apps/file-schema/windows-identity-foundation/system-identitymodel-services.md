---
title: '&lt;system.identityModel.services&gt;'
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ca108d7dd0498b0d7c08bb632ab45c7229ff58c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemidentitymodelservicesgt"></a>&lt;system.identityModel.services&gt;
WS-Federasyon protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.  
  
 \<system.identityModel.services >  
  
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
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Yapılandırma ayarlarını içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modülleri.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 Yok.  
  
## <a name="remarks"></a>Açıklamalar  
 Ekleme bir `<system.identityModel.services>` SAM ve WSFAM için ayarları sağlamak için uygulamanızın yapılandırma dosyasına bölümü.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> talep Yetkilendirme Yöneticisi'ni kodunuzda talep tabanlı erişim denetimi sağlamak için sınıfı (<xref:System.Security.Claims.ClaimsAuthorizationManager>) ve yetkilendirme kararları vermek için kullanılan ilke aracılığıyla yapılandırılmış olan bir `<identityConfiguration>` içinden örtük veya açık olarak başvuruda öğesi bir `<federationConfiguration>` bu bölümdeki öğesi. Daha fazla bilgi için bkz: **açıklamalar** altında [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.  
  
 `<system.identityModel.services>` Bölümünde belirtildiği <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sınıfı. Alt koleksiyonunu `<federationConfiguration>` bölümünde yapılandırılmış öğeleri ile temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML nasıl ekleneceğini gösterir bir `<system.identityModel.services>` bölümüne bir yapılandırma dosyası. İlk bölüm bildirimlerin her ikisi için de eklemelisiniz `<system.identityModel.services>` bölüm ve `<system.identityModel>` bölümler. (Eklediğinizde bir `<system.identityModel.services>` bölüm için bir bildirim de eklemeniz `<system.identityModel>` varsayılan emin olmak için bölüm `<identityConfiguration>` bölüm gerekirse çalışma zamanı tarafından oluşturulabilir.) Bölüm bildirimlerin ekledikten sonra Federasyon kimlik doğrulaması ayarlar altında yapılandırabilirsiniz `<system.identityModel.services>` öğesi.  
  
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
