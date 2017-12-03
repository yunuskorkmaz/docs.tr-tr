---
title: "&lt;claimTypeRequirements&gt; öğesi &lt;ekleme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc644648ad244eb642f96fdc93213fbd38152f48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a>&lt;claimTypeRequirements&gt; öğesi &lt;ekleme&gt;
Federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir. Örneğin, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik bilgilerini gereksinimleri Hizmetleri durumu.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<wsFederatedBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
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
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Gerekli talep türleri koleksiyonunu belirtir. Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin. Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir. Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.|  
  
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
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
