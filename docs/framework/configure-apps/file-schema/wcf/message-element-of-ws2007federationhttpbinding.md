---
title: <message>öğesi<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 4340727026cb151f2efe813dfa005c1c5a1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931618"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a>\<ileti > \<WS2007FederationHttpBinding > öğesi
WS2007FederationHttpBinding > öğesi için [ \<](ws2007federationhttpbinding.md) ileti düzeyi güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<ws2007FederationHttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<ileti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
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
|`algorithmSuite`|İsteğe bağlı. İleti şifrelemesini, imzayı ve anahtar sarması algoritmalarını ayarlar. Algoritmalar ve anahtar boyutları <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfına göre belirlenir. Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Olası değerler için aşağıdaki tabloya bakın. Varsayılan değer Basic256 ' dir.|  
|`issuedKeyType`|Verilecek anahtarın türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -SymmetricKey<br />-PublicKey<br />-Yataerkey<br /><br /> Varsayılan değer SymmetricKey ' dir. Bu öznitelik türü <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|`issuedTokenType`|Verilecek belirtecin türünü belirten bir URI. Varsayılan, `null` değeridir.|  
|`negotiateServiceCredential`|Hizmet kimlik bilgisinin, anlaşmanın parçası olarak alınıp alınmayacağını veya bant dışı kullanılabilir olup olmadığını belirten bir değer. Varsayılan `true`olarak, hizmet kimlik bilgisinin anlaşıldığı anlamına gelir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|Anahtar kaydırması için AES128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.|  
|Basic192|Anahtar kaydırması için Aes192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic256|Anahtar kaydırması için AES256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic256Rsa15|İleti şifreleme için AES256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic192Rsa15|İleti şifreleme için Aes192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDes|Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic128Rsa15|İleti şifreleme için AES128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDesRsa15|TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic128Sha256|İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|Basic192Sha256|İleti için Aes192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|Basic256Sha256|İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|TripleDesSha256|İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.|  
|Basic128Sha256Rsa15|İleti şifreleme için AES128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme için AES256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDesSha256Rsa15|İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](claimtyperequirements-element.md)|Bu bağlama için bir talep türleri koleksiyonu belirtir. Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|[\<veren >](issuer.md)|Bir güvenlik belirteci veren bir uç nokta belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|[\<IssuerMetadata >](issuermetadata.md)|Verenin uç nokta adresini belirtir.|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|Belirteç isteği parametrelerinin bir koleksiyonu. Her parametre bir XML öğesidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-element-of-ws2007federationhttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
