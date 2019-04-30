---
title: <add> / <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 97d3ecca369aeffb7b2e8464f385eeae13bd470f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704485"
---
# <a name="add-of-claimtyperequirements"></a>\<Ekle >, \<claimTypeRequirements >
Birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir. Örneğin, hizmetleri, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik gereksinimleri belirtin.  
  
 \<system.serviceModel>  
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
|ClaimType|Bir talep türünü tanımlayan URI. Örneğin, bir Web sitesine ait bir ürün satın almak için kullanıcının yeterli kredi sınırına geçerli bir kredi kartı sunması gerekir. Talep türü URI kredi kartı olacaktır.|  
|isteğe bağlıdır|Bu isteğe bağlı bir talep olup olmadığını belirten bir Boole değeri. Bu öznitelik ayarlanan `false` bu gerekli bir talep ise.<br /><br /> Hizmet için bazı bilgiler ister, ancak gerekli olmadığı durumlarda bu özniteliği kullanabilirsiniz. Örneğin, kullanıcının ilk adını girmesini gerekiyorsa, ad ve adres son ancak telefon numarası isteğe bağlı olduğuna karar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Gerekli talep türlerinin koleksiyonunu belirtir.<br /><br /> Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin. Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir. Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin. Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir. Bu gereksinim, bir güvenlik ilkesinde bildirilen. Buna göre gereksinimlerini karşılayan kimlik Federasyon Hizmeti verebilir böylece istemci istekleri kimlik bilgileri, bir Federasyon Hizmeti (örneğin, CardSpace) bir belirteç isteğini (RequestSecurityToken) gereksinimleri koyar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma, güvenlik bağlama iki talep türü gereksinimleri ekler.  
  
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
- [\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
