---
title: <add><claimTypeRequirements> öğesinin
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 249227c20dd1610cba088017ae39e84d6cb683d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920203"
---
# <a name="add-of-claimtyperequirements-element"></a>\<\<ClaimTypeRequirements > öğesi > ekleyin
Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir. Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgileri için gereksinimleri durum.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<wsFederatedBinding >  
\<bağlama >  
\<Güvenlik >  
\<ileti >  
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
|claimType|Bir talebin türünü tanımlayan URI. Örneğin, bir ürünün bir Web sitesinden satın alınması için, kullanıcının yeterli kredi limiti olan geçerli bir kredi kartı sunması gerekir. Talep türü kredi kartı URI 'SI olacaktır.|  
|IsOptional|Bunun isteğe bağlı bir talep olup olmadığını belirten bir Boolean değer. Bu gerekli bir talep `false` ise, bu özniteliği olarak ayarlayın.<br /><br /> Hizmet bazı bilgileri istediğinde ancak bunu gerektirmiyorsa bu özniteliği kullanabilirsiniz. Örneğin, kullanıcının adını, soyadını ve adresini girmesini gerektiriyorsa, ancak telefon numarasının isteğe bağlı olduğuna karar verin.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](claimtyperequirements-for-message.md)|Gerekli talep türlerinin koleksiyonunu belirtir. Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır. Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır. Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır. Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır. Bu gereksinim bir güvenlik ilkesinde oluşturulur. İstemci Federasyon hizmetinden kimlik bilgilerini istediğinde (örneğin, CardSpace), Federasyon hizmetinin gereksinimleri karşılayan kimlik bilgilerini vermesi için gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma, bir güvenlik bağlamaya iki talep türü gereksinimi ekler.  
  
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

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
