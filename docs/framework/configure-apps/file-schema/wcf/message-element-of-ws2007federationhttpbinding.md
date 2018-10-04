---
title: '&lt;ws2007FederationHttpBinding&gt; &lt;iletisi&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 6954a7b9646b35ee03aab311deae026a711be9cd
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778685"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a>&lt;ws2007FederationHttpBinding&gt; &lt;iletisi&gt; öğesi
İleti düzeyi güvenlik ayarlarını tanımlar [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğesi.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<ws2007FederationHttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ws2007FederationBinding>  
   <binding >  
      <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
            <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
            </issuer>  
            <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
            </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
         </message>  
      </security>  
   </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`algorithmSuite`|İsteğe bağlı. İleti şifreleme, imza ve anahtar-wrap algoritmaları ayarlar. Algoritmalar ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.<br /><br /> Olası değerler için aşağıdaki tabloya bakın. Basic256 varsayılan değerdir.|  
|`issuedKeyType`|Kesilecek anahtar türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -SymmetricKey<br />-PublicKey<br />-BearerKey<br /><br /> SymmetricKey varsayılandır. Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|`issuedTokenType`|Verilmesi için belirteç türünü belirten bir URI. Varsayılan, `null` değeridir.|  
|`negotiateServiceCredential`|Hizmet kimlik bilgisi anlaşmasının bir parçası değiştirilen veya bant dışından mevcut olup olmadığını belirten bir değeri. Varsayılan `true`, hizmet kimlik bilgisi anlaşılır anlamına gelir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes192 şifrelemesi kullanın.|  
|Basic256|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes256 şifrelemesi kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes192 kullanın.|  
|TripleDes|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 TripleDes şifrelemesi kullanın.|  
|Basic128Rsa15|İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.|  
|TripleDesRsa15|İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 TripleDes şifrelemesi kullanın.|  
|Basic128Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.|  
|Basic192Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes192 kullanın.|  
|Basic256Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.|  
|TripleDesSha256|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p ileti şifreleme için kullanın.|  
|Basic128Sha256Rsa15|İleti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes192 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes256 kullanın.|  
|TripleDesSha256Rsa15|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Bu bağlama için talep türlerinin koleksiyonunu belirtir. Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|[\<veren >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Bir güvenlik belirteci veren bir uç noktasını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|[\<İssuedtokenparameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Verenin uç nokta adresini belirtir.|  
|[\<tokenRequestParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|Belirteç isteği parametreleri koleksiyonu. Her bir XML öğesi parametredir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|Bir bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
