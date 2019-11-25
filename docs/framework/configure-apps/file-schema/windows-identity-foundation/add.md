---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973810"
---
# <a name="add"></a>\<> Ekle
Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**  
  
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
|türü|Eklenecek belirteç işleyicisinin CLR tür adı. `type` özniteliğini belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[samlSecurityTokenRequirement > \<](samlsecuritytokenrequirement.md)|<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.|  
|[\<sessionTokenRequirement >](sessiontokenrequirement.md)|<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar için yapılandırma sağlar.|  
|[\<userNameSecurityTokenHandlerRequirement >](usernamesecuritytokenhandlerrequirement.md)|<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar için yapılandırma sağlar.|  
|[\<x509SecurityTokenHandlerRequirement >](x509securitytokenhandlerrequirement.md)|<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıfı veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](securitytokenhandlers.md)|Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<add>` öğesi, belirteç işleyicisinin yapılandırmasını belirten tek bir alt öğe alabilir. Bu, `<add>` öğesinin `type` özniteliği aracılığıyla başvurulan işleyici sınıfının bu özellik için destek sağlar. Bu özelliği sağlayan belirteç işleyici sınıfları bir <xref:System.Xml.XmlElement> nesnesi alan bir oluşturucuyu kullanıma sunmalıdır.  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Yerleşik güvenlik belirteci işleyici sınıflarından birkaçı bu işlevselliği sağlar. Bu sınıflar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>ve <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
> Belirteç işleyici koleksiyonu verilen herhangi bir tür için yalnızca tek bir işleyici içerebilir. Bu, örneğin, koleksiyona <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfından türetilmiş bir işleyici eklemek istiyorsanız, öncelikle varsayılan olarak bulunan <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, koleksiyondan kaldırmanız gerekir; Yani Koleksiyondan tek bir işleyiciyi kaldırmak için [\<remove >](remove.md) öğesini kullanabilir veya tüm işleyicileri koleksiyondan kaldırmak için [\<Clear >](clear.md) öğesini kullanabilirsiniz.  
  
 Bir işleyicide belirtilen ayarlar, [\<securitytokenhandlerconfiguration >](securitytokenhandlerconfiguration.md) öğesi altındaki belirteç işleyici koleksiyonunda belirtilen eşdeğer ayarları geçersiz kılar ve [\<IdentityConfiguration >](identityconfiguration.md) öğesi altındaki hizmet düzeyinde belirtilmiştir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, varsayılan oturum belirteci işleyicisini özel bir oturum belirteci işleyicisiyle değiştirmek için `<add>` ve `<remove>` öğelerinin kullanımını gösterir. XML `ClaimsAwareWebFarm` örneğinden alınır.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
