---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 59d47eda97e97629408ece12a1d1dfbe804feb3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667320"
---
# <a name="claimsauthorizationmanager"></a>\<claimsAuthorizationManager >
Bir gelen talep için talep Yetkilendirme Yöneticisi kaydeder.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<claimsAuthorizationManager >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Öğesinden türetilen özel bir tür <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı. Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yoksa hiçbir `type` özniteliği veya `type` başvuruları öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthorizationManager>` öğenin alt öğeleri almaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthorizationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı, gelen talepler her zaman yetkilendirir. Hayır ise `type` özniteliği veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı `<claimsAuthorizationManager>` öğenin alt öğeleri almaz. Belirtebileceğiniz `type` sınıfından türetilen bir tür kaydetmek için öznitelik <xref:System.Security.Claims.ClaimsAuthorizationManager> özel davranışı uygulamak sınıfı. Türetilen sınıflar, alt öğelerinin konfigürasyonuyla destekleyebilir `<claimsAuthorizationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> bu öğelerini işlemek için yöntemi. Sınıf Tasarımcısı kadar alt öğeleri için tanımlanan şema var.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sınıfı tarafından başvurulan kimlik yapılandırması kodunuzda beyana dayalı erişim denetimi sağlamak için `<federationConfiguration>` öğesi, talep Yetkilendirme Yöneticisi'ni ve yapmak için kullanılan ilke yapılandırır yetkilendirme kararları. Bu durum bile pasif Web senaryoları, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı yer almayan bir uygulama olmayan senaryolarda geçerlidir. Uygulama Pasif bir Web uygulaması değilse `<claimsAuthorizationManager>` öğesini (ve alt ilke öğelerine, varsa) başvurulan kimlik yapılandırmasını uygulanan yalnızca ayarlarıdır. Diğer tüm ayarları göz ardı edilir. Daha fazla bilgi için [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.  
  
 Bu öğe ayarlar <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML kaynak Eylem çiftleri oluşan ilke her biri kaynak eylemi gerçekleştirmek için bir istek sahibine sahip olması gerekir talepleri Boole birleşimlerini belirtir uygulayan manager talep yetkilendirme yapılandırmasını gösterir. Bu ilke kullanma yeteneği talep Yetkilendirme Yöneticisi uygulayan kod bulunabilir `ClaimsBasedAuthorization` örnek.  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
