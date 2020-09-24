---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: bb9468b6005361a2a480f7c0ebfb2cbb9e9199c2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157388"
---
# \<identity>

Identity öğesi, bir istemci geliştiricisinin, hizmetin beklenen kimliği olan tasarım zamanında belirtmesini sağlar. İstemci ve hizmet arasındaki el sıkışma işleminde, Windows Communication Foundation (WCF) altyapısı, beklenen hizmetin kimliğinin bu öğenin değerleriyle eşleştiğinden emin olur ve bu nedenle kimlik doğrulaması yapılabilir. Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|sertifika|X. 509.440 sertifikasının ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateElement> . `encodedValue`Bu, bu sertifika tarafından kodlanan değeri belirten String olan bir özniteliği içerir.|  
|certificateReference|X. 509.440 sertifika doğrulamasının ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .|  
|dns|Bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının DNS 'sini belirtir. Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir.|  
|rsa|Bir istemciye bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının RSA alanının değerini belirtir. Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir|  
|servicePrincipalName|Bir hizmetin bir örneğini benzersiz bir şekilde tanımlamak için bir istemci tarafından kullanılan asıl ad olan bir sunucu asıl adı (SPN) kimliğini belirtir. Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .|  
|userPrincipalName|Bir ağdaki kullanıcının oturum açma adı türü olan bir Kullanıcı asıl adı (UPN) kimliğini belirtir. Kullanıcı asıl adı, Active Directory ' de kullanılan Kullanıcı nesne adından \@ ve ardından genellikle etki alanı adı sistemi üst etki alanına sahip. Örneğin, Fabrikam.com etki alanı ağacındaki Jeff, Kullanıcı asıl adına sahip olabilir [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .  Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<custom>](custom.md)|NetPeerTcpBinding için özel bir eş çözümleyici belirtir.|  
|[\<endpoint>](endpoint-element.md)|Hizmet uç noktalarını yapılandırır.|  
|[\<endpoint> durumunu \<client>](endpoint-of-client.md)|Kanal uç noktalarını yapılandırır.|  
|[\<issuer>](issuer.md)|Federasyon Hizmeti için güvenlik belirteci hizmetini (STS) belirtir.|  
|[\<issuerMetadata>](issuermetadata.md)|Federasyon Hizmeti 'nin güvenlik belirteci hizmeti (STS) için meta veri uç noktasını belirtir.|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Özel bağlamadaki verilen belirtecin parametrelerini tanımlar.|  
|[\<localIssuer>](localissuer.md)|Yerel bir güvenlik belirteci hizmetini (STS) belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
