---
title: <add> / <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153093"
---
# <a name="add-of-claimtyperequirements"></a>\<claimTypeRequirements \<>> ekleyin
Federe kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir. Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgilerinin gereksinimlerini belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcı>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlik>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParametreleri>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Claimtype|Bir talebin türünü tanımlayan bir URI. Örneğin, bir Web sitesinden ürün satın almak için, kullanıcının yeterli kredi limitine sahip geçerli bir kredi kartı sunması gerekir. Talep türü kredi kartı URI olacaktır.|  
|ısoptional|Bu isteğe bağlı bir talep için olup olmadığını belirten bir Boolean değeri. Bu özniteliği, `false` gerekli bir talep olup olmadığını ayarlayın.<br /><br /> Hizmet bazı bilgiler istediğinde ancak gerektirmediğinde bu özniteliği kullanabilirsiniz. Örneğin, kullanıcının ad, soyad ve adresini girmesini istiyorsanız, ancak telefon numarasının isteğe bağlı olduğuna karar verin.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|Gerekli talep türlerinin bir koleksiyonunu belirtir.<br /><br /> Federe bir senaryoda, hizmetler gelen kimlik bilgileri gereksinimlerini belirtir. Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır. Bu koleksiyondaki her öğe, federe bir kimlik bilgisi içinde görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Federe bir senaryoda, hizmetler gelen kimlik bilgileri gereksinimlerini belirtir. Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır. Bu gereksinim bir güvenlik ilkesinde kendini gösterir. İstemci federe bir hizmetten (örneğin, CardSpace) kimlik bilgileri istediğinde, gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar, böylece federe hizmet gereksinimleri karşılayan kimlik bilgilerini buna göre verebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma, bir güvenlik bağlama iki talep türü gereksinimleri ekler.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
