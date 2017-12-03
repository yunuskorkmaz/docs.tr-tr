---
title: "&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb12cc0162cabd75f176c636b9cd4d00309bb594
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a>&lt;wsFederationHttpBinding&gt; &lt;iletisi&gt; öğesi
İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<wsFederatedBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<wsFederationBinding>  
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
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Bu özniteliğin geçerli değerler "algorithmSuite özniteliği" tablosuna bakın. Varsayılan değer `Basic256` şeklindedir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.|  
|issuedKeyType|Kesilecek anahtar türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -SymmetricKey<br />-PublicKey<br /><br /> Varsayılan, `SymmetricKey` değeridir. Bu öznitelik türünde <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|issuedTokenType|Verilmesine Belirtecin türü belirten bir URI'yı içeren bir dize. Varsayılan, `null` değeridir.|  
|negotiateServiceCredential|Hizmet kimlik bilgilerini anlaşmasının bir parçası değiştirilen veya bant dışı kullanılabilir olup olmadığını belirten bir Boole değeri. Varsayılan değer `true`, hizmet kimlik bilgilerini anlaşılmadan anlamına gelir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Basic128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|Basic192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256|Basic256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic192 kullanın.|  
|TripleDes|TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic128Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Basic128 kullanın.|  
|TripleDesRsa15|TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.|  
|Basic128Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic128 kullanın.|  
|Basic192Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic192 kullanın.|  
|Basic256Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Basic256 kullanın.|  
|TripleDesSha256|TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.|  
|Basic128Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Basic128 kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Basic256 kullanın.|  
|TripleDesSha256Rsa15|TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Bu bağlama için talep türleri koleksiyonunu belirtir. Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|yayınlayan|Bir güvenlik belirteci verir bir uç nokta belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|issuerMetadata|Uç nokta adresi verenin belirtir.|  
|[\<tokenRequestParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|Belirteç isteği parametreleri topluluğu. Her bir XML öğesi parametresidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement`[Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
