---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 74ca031f7017d51adaa7a71593f537b64abbeae6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942886"
---
# <a name="claimsauthorizationmanager"></a>\<claimsAuthorizationManager >
Gelen talepler için bir talep Yetkilendirme Yöneticisi kaydeder.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
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
|türü|<xref:System.Security.Claims.ClaimsAuthorizationManager> Sınıfından türetilen özel bir tür. `type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 `type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Öznitelik yoksa veya öznitelik sınıfa <xref:System.Security.Claims.ClaimsAuthorizationManager> başvuruyorsa, öğesialtöğelerialmaz;ancak,öğesindentüretilmişsınıflaraltyapılandırmaöğelerinitanımlayabilir.`<claimsAuthorizationManager>` `type`  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IdentityConfiguration >](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Security.Claims.ClaimsAuthorizationManager> Sınıfı aracılığıyla sunulan varsayılan davranış her zaman gelen talepleri yetkilendirir. Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı `<claimsAuthorizationManager>` belirtiyorsa, öğesi alt öğeleri almaz. Özel davranışı uygulamak için `type` <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz. Türetilmiş sınıflar, bu öğeleri işlemek için `<claimsAuthorizationManager>` <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir. Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.  
  
> [!IMPORTANT]
> Kodunuzda talep tabanlı <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> erişim denetimi <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sağlamak için ya da sınıfını kullanırken, `<federationConfiguration>` öğesi tarafından başvurulan kimlik yapılandırması, bu işlemi yapmak için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandırır yetkilendirme kararları. Bu, pasif Web senaryoları olmayan senaryolarda bile, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama için de geçerlidir. Uygulama pasif bir Web uygulaması değilse, `<claimsAuthorizationManager>` başvurulan kimlik yapılandırmasının öğesi (ve varsa alt ilke öğeleri) uygulanan tek ayarlardır. Diğer tüm ayarlar yoksayılır. Daha fazla bilgi için, bkz [ \<. FederationConfiguration >](federationconfiguration.md) öğesi.  
  
 Bu öğe <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> özelliği ayarlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, her biri kaynak Eylem çiftlerinden oluşan ilkeyi uygulayan, her birinin kaynak üzerinde eylemi gerçekleştirmek için sahip olması gereken taleplerin Boole birleşimlerini belirten bir talep Yetkilendirme Yöneticisi yapılandırmasını gösterir. Bu ilkeyi kullanan talep Yetkilendirme Yöneticisini uygulayan kod `ClaimsBasedAuthorization` örneğinde bulunabilir.  
  
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
