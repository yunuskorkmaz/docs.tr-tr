---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943653"
---
# <a name="systemidentitymodelservices"></a>\<System. IdentityModel. Services >
WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.  
  
 \<System. IdentityModel. Services >  
  
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
|[\<federationConfiguration >](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfab) <xref:System.IdentityModel.Services.SessionAuthenticationModule> ve (Sam) http modüllerini yapılandıran ayarları içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 Yok.  
  
## <a name="remarks"></a>Açıklamalar  
 Sam ve `<system.identityModel.services>` wsfae ayarlarını sağlamak için uygulamanızın yapılandırma dosyasına bir bölüm ekleyin.  
  
> [!IMPORTANT]
> Kodunuzda talep tabanlı <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> erişim denetimi <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sağlamak için veya sınıfını kullanırken, yetkilendirme kararları almak için kullanılan talep Yetkilendirme Yöneticisi (<xref:System.Security.Claims.ClaimsAuthorizationManager>) ve ilkesi bir `<identityConfiguration>` Bu bölümdeki bir `<federationConfiguration>` öğeden örtük veya açık olarak başvurulan öğe. Daha fazla bilgi için [ \<FederationConfiguration >](federationconfiguration.md) öğesinin altındaki açıklamalara bakın.  
  
 `<system.identityModel.services>` Bölümü sınıfı<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> tarafından temsil edilir. Bölümünde yapılandırılan alt `<federationConfiguration>` öğelerin koleksiyonu <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> sınıfı tarafından temsil edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, bir yapılandırma dosyasına bir `<system.identityModel.services>` bölümün nasıl ekleneceğini gösterir. Öncelikle `<system.identityModel.services>` bölüm`<system.identityModel>` ve bölümler için bölüm bildirimleri eklemeniz gerekir. (Bir `<system.identityModel.services>` bölümü eklediğinizde, gerekirse çalışma zamanı tarafından varsayılan `<identityConfiguration>` bir bölümün oluşturulabilmelidir emin `<system.identityModel>` olmak için bölüm için bir bildirim de eklemeniz gerekir.) Bölüm bildirimleri eklendikten sonra, `<system.identityModel.services>` öğesinin altında federal kimlik doğrulama ayarlarını yapılandırabilirsiniz.  
  
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
