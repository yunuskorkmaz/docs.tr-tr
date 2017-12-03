---
title: '&lt;claimTypeRequirements&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f1685564ff46ff168dac3ba79107e989067bc1d5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a>&lt;claimTypeRequirements&gt; &lt;ekleme&gt;
Federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir. Örneğin, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik bilgilerini gereksinimleri Hizmetleri durumu.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
\<İssuermetadata >  
\<claimTypeRequirements >  
  
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
|claimType|Bir talep türünü tanımlayan bir URI. Örneğin, bir Web sitesinden bir ürün satın almak için kullanıcının yeterli kredi limiti ile geçerli bir kredi kartı sunması gerekir. Talep türü URI kredi kartı olacaktır.|  
|isteğe bağlıdır|Bunun için isteğe bağlı bir talep olup olmadığını belirten bir Boole değeri. Bu öznitelik ayarlanırsa `false` bu gerekli bir talep ise.<br /><br /> Hizmet için bazı bilgiler ister, ancak gerekli olmadığı durumlarda bu özniteliği kullanabilirsiniz. Örneğin, kullanıcının ilk adını girmesini gerektiriyorsa, ad ve adres son ancak telefon numarası isteğe bağlı olduğuna karar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Gerekli talep türleri koleksiyonunu belirtir.<br /><br /> Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin. Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir. Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin. Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir. Bu gereksinim, bir güvenlik ilkesi bildirilmiş. Federasyon Hizmeti gereksinimlerini buna göre uygun kimlik bilgilerini vermek için istemci istekleri kimlik bilgileri, Federasyon Hizmeti (örneğin, CardSpace) bir belirteç isteğini (RequestSecurityToken) gereksinimlerini koyar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma, güvenlik bağlamaya iki talep türü gereksinimlerini ekler.  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel bağlama güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
