---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 0f5eace346fd0ed2c0532fb602585c4593d97291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220363"
---
# <a name="identity"></a>\<Kimliği >
Kimlik öğesi, bir istemci geliştiricisinin beklenen hizmet kimliğini tasarım zamanında belirtmenizi sağlar. Anlaşma işlemi istemci ve hizmet arasındaki Windows Communication Foundation (WCF) altyapı beklenen hizmet eşleşme değerleri bu öğenin kimliğini emin olur ve bu nedenle doğrulanabilir. Daha fazla bilgi için [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  <usePrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|sertifika|X.509 sertifikası ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.CertificateElement>. Özniteliğin içerdiği `encodedValue` Bu sertifika tarafından kodlanmış bir değer belirtir yani bir dizesi.|  
|certificateReference|X.509 Sertifika doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Bir hizmetin kimliğini doğrulamak için kullanılan bir X.509 sertifikasının DNS belirtir. Bu öğeyi içeren bir öznitelik `value` bir dizedir ve gerçek kimlik içeriyor.|  
|rsa|Bir hizmete istemcinin kimliğini doğrulamak için kullanılan bir X.509 sertifikasının RSA alanın değerini belirtir. Bu öğeyi içeren bir öznitelik `value` bir dizedir ve gerçek kimlik içeriyor|  
|servicePrincipalName|Bir hizmet örneğini benzersiz şekilde tanımlamak için bir istemci tarafından kullanılan asıl adı bir sunucu asıl adı (SPN) kimliğini belirtir. Bu öğeyi içeren bir öznitelik `value` bir dizedir ve gerçek asıl adını içerir. Bu öğe türünde <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Bir kullanıcı ağda oturum açma adı türü bir kullanıcı asıl adı (UPN) kimliğini belirtir. Ardından Active Directory'de kullanılan kullanıcı nesne adı, kullanıcı asıl adı oluşur simgesini (\@) ve ardından, genellikle, etki alanı adı sistemi üst etki alanı. Örneğin, Jeff Fabrikam.com etki alanı ağacındaki kullanıcı asıl adı olabilir [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Bu öğeyi içeren bir öznitelik `value` bir dizedir ve gerçek asıl adını içerir. Bu öğe türünde <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Özel >](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Özel eş Çözücü için bir netPeerTcpBinding belirtir.|  
|[\<uç noktası >](endpoint-element.md)|Hizmet uç noktaları yapılandırır.|  
|[\<uç noktası >'ın \<istemci >](endpoint-of-client.md)|Kanal uç noktaları yapılandırır.|  
|[\<veren >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Güvenlik belirteci hizmeti (STS) Federasyon Hizmeti için belirtir.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Güvenlik belirteci hizmeti (STS için) Federasyon Hizmeti meta veri uç noktası belirtir.|  
|[\<İssuermetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Verilen bir belirteç parametrelerini özel bir bağlama tanımlar.|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Bir yerel güvenlik belirteci hizmeti (STS) belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Uç noktalar: Adresleri, bağlamalar ve sözleşmeler](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
