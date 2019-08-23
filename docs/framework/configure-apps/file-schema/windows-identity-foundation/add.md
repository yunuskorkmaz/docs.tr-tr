---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 9505970c1fd7fcdfe62d3c6ef58f5d653fab4106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941989"
---
# <a name="add"></a>\<> Ekle
Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<> Ekle  
  
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
|türü|Eklenecek belirteç işleyicisinin CLR tür adı. `type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](samlsecuritytokenrequirement.md)|<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.|  
|[\<sessionTokenRequirement >](sessiontokenrequirement.md)|<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.|  
|[\<userNameSecurityTokenHandlerRequirement >](usernamesecuritytokenhandlerrequirement.md)|<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.|  
|[\<x509SecurityTokenHandlerRequirement >](x509securitytokenhandlerrequirement.md)|<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](securitytokenhandlers.md)|Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<add>` Öğesi, belirteç işleyicisinin yapılandırmasını belirten tek bir alt öğe alabilir. Bu, `type` `<add>` öğesinin özniteliği aracılığıyla başvurulan işleyici sınıfının bu özellik için destek sağlar. Bu özelliği sağlayan belirteç işleyici sınıfları bir <xref:System.Xml.XmlElement> nesne alan oluşturucuyu kullanıma sunmalıdır.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Yerleşik güvenlik belirteci işleyici sınıflarından birkaçı bu işlevselliği sağlar. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Bu sınıflar <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>,, ve<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>' dir. <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>  
  
> [!IMPORTANT]
> Belirteç işleyici koleksiyonu verilen herhangi bir tür için yalnızca tek bir işleyici içerebilir. Bu, örneğin, koleksiyona <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfından türetilmiş bir işleyici eklemek istiyorsanız, öncelikle varsayılan olarak bulunan öğesini koleksiyondan <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>kaldırmanız gerektiği anlamına gelir. Koleksiyondan tek bir işleyiciyi kaldırmak veya [ \<Clear >](clear.md) öğesini kullanarak koleksiyondan tüm işleyicileri kaldırmak için [ \<Remove >](remove.md) öğesini kullanabilirsiniz.  
  
 Bir işleyicide belirtilen ayarlar, [ \<SecurityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) öğesi altındaki belirteç işleyici koleksiyonunda belirtilen eşdeğer ayarları geçersiz kılar ve [ \< IdentityConfiguration >](identityconfiguration.md) öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, varsayılan oturum belirteci işleyicisini özel `<add>` bir `<remove>` oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir. XML `ClaimsAwareWebFarm` örnekten alınır.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
