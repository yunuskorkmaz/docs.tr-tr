---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 9728f3caee4dba367e4fc4a3e68213b1055cc3d1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362961"
---
# <a name="systemidentitymodelservices"></a>\<System.IdentityModel.Services >
WS-Federasyon protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.  
  
 \<System.IdentityModel.Services >  
  
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
 Hiçbiri  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Yapılandırma ayarları içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modülleri.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 Hiçbiri  
  
## <a name="remarks"></a>Açıklamalar  
 Ekleme bir `<system.identityModel.services>` bölümüne uygulamanızın yapılandırma dosyasına WSFAM ve SAM için ayarları sağlamak için.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> kodunuzda, talep Yetkilendirme Yöneticisi'ni beyana dayalı erişim denetimi sağlamak için sınıfı (<xref:System.Security.Claims.ClaimsAuthorizationManager>) ve yetkilendirme kararları vermek için kullanılan İlkesi aracılığıyla yapılandırılmasını bir `<identityConfiguration>` gelen açıkça veya dolaylı olarak başvuruluyor öğesi bir `<federationConfiguration>` bu bölümdeki öğesi. Daha fazla bilgi için **açıklamalar** altında [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.  
  
 `<system.identityModel.services>` Bölümü tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sınıfı. Alt koleksiyonu `<federationConfiguration>` yapılandırma başlıklı bölümde öğeleri tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML nasıl ekleneceğini gösterir. bir `<system.identityModel.services>` bölümüne bir yapılandırma dosyası. İlk bölümü bildirimi hem de eklemeniz gerekir `<system.identityModel.services>` bölümü ve `<system.identityModel>` bölümler. (Eklediğinizde bir `<system.identityModel.services>` bölümünde bildirimi de eklemeniz `<system.identityModel>` varsayılan emin olmak için bölüm `<identityConfiguration>` bölüm gerekirse çalışma zamanı tarafından oluşturulabilir.) Bölümü bildirimleri ekledikten sonra şirket dışı kimlik doğrulaması ayarlar altında yapılandırabilirsiniz `<system.identityModel.services>` öğesi.  
  
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
