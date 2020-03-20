---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152510"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
WS-Federation protokolünü kullanarak kimlik doğrulama için yapılandırma bölümü.  
  
[**\<yapılandırma>**](../configuration-element.md)\
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
 None  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<federasyonKonfigürasyon>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modüllerini yapılandıran ayarları içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 None  
  
## <a name="remarks"></a>Açıklamalar  
 SAM `<system.identityModel.services>` ve WSFAM ayarlarını sağlamak için uygulamanızın yapılandırma dosyasına bir bölüm ekleyin.  
  
> [!IMPORTANT]
> Kodunuzda <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> talep <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> tabanlı erişim denetimi sağlamak için sınıfı veya sınıfı<xref:System.Security.Claims.ClaimsAuthorizationManager>kullanırken, talep yetkilendirme yöneticisi ( ) ve `<identityConfiguration>` yetkilendirme kararları vermek için kullanılan ilke, bu bölümdeki bir `<federationConfiguration>` öğeden örtülü veya açıkça başvurulan bir öğe aracılığıyla yapılandırılır. Daha fazla bilgi için [ \<federasyonYapılandırma>](federationconfiguration.md) öğesi altındaki **Açıklamalar'a** bakın.  
  
 Bölüm `<system.identityModel.services>` <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sınıf tarafından temsil edilir. Bölümde yapılandırılan `<federationConfiguration>` alt öğelerin toplanması <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> sınıf tarafından temsil edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, yapılandırma dosyasına `<system.identityModel.services>` nasıl bir bölüm ekleyeceğinigösterir. Öncelikle `<system.identityModel.services>` hem bölüm hem de bölümler için `<system.identityModel>` bölüm bildirimleri eklemeniz gerekir. (Bir `<system.identityModel.services>` bölüm eklediğinizde, gerekirse çalışma süresine `<system.identityModel>` kadar varsayılan `<identityConfiguration>` bir bölümün oluşturulabilmesini sağlamak için bölüm için bir bildirim de eklemelisiniz.) Bölüm bildirimleri eklendikten sonra, öğenin `<system.identityModel.services>` altında federal kimlik doğrulama ayarlarını yapılandırabilirsiniz.  
  
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
