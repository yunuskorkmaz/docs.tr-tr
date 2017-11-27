---
title: '&lt;claimsAuthorizationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4b4d86204d5f7225f167be125ce017488c851e98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
Bir gelen talep için talep Yetkilendirme Yöneticisi kaydeder.  
  
 \<System.IdentityModel >  
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
|türü|Türetilen bir özel tür <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı. Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Varsa hiçbir `type` özniteliği veya `type` özniteliği başvuruları <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthorizationManager>` öğesi alt öğe olmaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthorizationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üzerinden sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı, gelen talepleri her zaman yetkilendirir. Öyle değilse `type` özniteliği belirtilmediyse veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı, `<claimsAuthorizationManager>` öğesi alt öğe olmaz. Belirleyebileceğiniz `type` türü kaydetmek için öznitelik türetilen <xref:System.Security.Claims.ClaimsAuthorizationManager> özel davranışı uygulamak için sınıf. Türetilen sınıflar, alt öğelerinin üzerinden yapılandırmayı destekleyebilir `<claimsAuthorizationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> bu öğeleri işlemek için yöntem. Alt öğeler için tanımlanan şema Sınıf Tasarımcısı kadar olur.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> tarafından başvurulan kimlik yapılandırması kodunuzda talep tabanlı erişim denetimi sağlamak için sınıf `<federationConfiguration>` öğesi yapılandırır talep Yetkilendirme Yöneticisi'ni ve yapmak için kullanılan İlkesi yetkilendirme kararları. Bu durum bile pasif Web senaryoları, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama değildir senaryolarda geçerlidir. Uygulama Pasif bir Web uygulaması değilse `<claimsAuthorizationManager>` öğesi (ve alt ilke öğeleri, varsa) başvurulan kimlik yapılandırması olan uygulanan ayarlar. Tüm diğer ayarlar yok sayılır. Daha fazla bilgi için bkz: [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.  
  
 Bu öğe ayarlar <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML her biri kaynak eylemi gerçekleştirmek için bir istek sahibi sahip olması gerekir talepleri boolean birleşimleri belirtir kaynak eylem çiftlerinden oluşan ilke uyguluyor Yöneticisi talep yetkilendirme için yapılandırmayı gösterir. Bu ilke kullanma yeteneği talep Yetkilendirme Yöneticisi uygulayan kod bulunabilir `ClaimsBasedAuthorization` örnek.  
  
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
