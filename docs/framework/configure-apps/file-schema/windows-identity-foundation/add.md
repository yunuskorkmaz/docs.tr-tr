---
title: '&lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6ee6403fcfe741d3e38bf44eddb1cf52cf856ec8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757859"
---
# <a name="ltaddgt"></a>&lt;add&gt;
Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Eklenecek belirteci işleyicisi CLR türü adı. Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.|  
|[\<sessionTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıf veya türetilmiş sınıflar.|  
|[\<userNameSecurityTokenHandlerRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıf veya türetilmiş sınıflar.|  
|[\<x509SecurityTokenHandlerRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|İçin isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıf veya türetilmiş sınıflar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<add>` Öğesi belirteç işleyici yapılandırması belirten tek bir alt öğe alabilir. Bu olup olmadığını işleyici sınıfı aracılığıyla başvurulan üzerinde bağımlı `type` özniteliği `<add>` öğesi, bu özellik için destek sağlar. Bu özellik sağlayan belirteci işleyicisi sınıflar alan oluşturucu kullanıma gerekir bir <xref:System.Xml.XmlElement> nesnesi.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Birkaç yerleşik güvenlik belirteci işleyicisi sınıfların bu işlevsellik sağlar. Bu sınıflar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  Belirteç işleyici koleksiyonu yalnızca herhangi bir türde tek bir işleyici içerebilir. Türetilmiş bir işleyici eklemek istiyorsanız, örneğin, yani <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı önce kaldırmalısınız koleksiyona <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, koleksiyondan varsayılan olarak, mevcut olduğu. Kullanabileceğiniz [ \<Kaldır >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) tek bir işleyici koleksiyonu veya kullanım kaldırmak için öğesi [ \<temizleyin >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) tüm işleyiciler Koleksiyondan kaldırılacak öğe.  
  
 Üzerinde bir işleyici için belirtilen ayarları altında belirteci işleyicisi koleksiyonu belirtilen eşdeğer ayarları geçersiz kılar [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi ve altında hizmet düzeyindeki belirtilenlerle [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML kullanımı gösterilmiştir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi özel oturum belirteci işleyicisi ile değiştirin. XML alınırlar `ClaimsAwareWebFarm` örnek.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
