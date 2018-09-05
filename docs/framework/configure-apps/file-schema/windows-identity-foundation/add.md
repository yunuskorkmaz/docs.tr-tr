---
title: '&lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ddbf1b822550876d849f830d80cff9a74311ba9c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506780"
---
# <a name="ltaddgt"></a>&lt;add&gt;
Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<Ekle >  
  
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
|türü|Belirteci işleyicisi eklenecek CLR türü adı. Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.|  
|[\<sessionTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.|  
|[\<userNameSecurityTokenHandlerRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.|  
|[\<x509SecurityTokenHandlerRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|İsteğe bağlı yapılandırma için sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıfı veya türetilmiş sınıflar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<add>` Öğesi belirteç işleyici yapılandırması belirten tek bir alt öğe alabilir. Bu bağımlı olup olmadığını işleyicisi sınıfı aracılığıyla başvurulan üzerinde `type` özniteliği `<add>` öğesi, bu özellik için destek sağlar. Bu özelliği sağlayan belirteci işleyicisi sınıflar alan bir oluşturucu kullanıma gereken bir <xref:System.Xml.XmlElement> nesne.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Birkaç yerleşik güvenlik belirteci işleyici sınıflarını, bu işlevselliği sağlar. Bu sınıflar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  Belirteci işleyicisi koleksiyon, yalnızca belirli herhangi bir türde tek bir işleyici içerebilir. Türetilen bir işleyici eklemek istiyorsanız, örneğin, yani <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı koleksiyona önce kaldırmalısınız <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, koleksiyondan varsayılan olarak, mevcut olduğu. Kullanabilirsiniz [ \<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) tek bir işleyici koleksiyonu veya kullanım kaldırmak için öğeyi [ \<Temizle >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) tüm işleyiciler Koleksiyondan kaldırılacak öğe.  
  
 Belirtilen bir işleyici ayarları geçersiz kılma eşdeğer ayarlar altında belirteci işleyicisi koleksiyonu belirtilen [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi ve altında hizmet düzeyinde belirtilenlerden [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML kullanımını gösterir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi bir özel oturum belirteci işleyicisi ile değiştirilecek. XML alınır `ClaimsAwareWebFarm` örnek.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
