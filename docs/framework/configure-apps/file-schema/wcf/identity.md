---
title: '&lt;Kimlik&gt;'
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 9cfd1d6cc7c278fd7e95c13df0a6f801cfabbc33
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltidentitygt"></a>&lt;Kimlik&gt;
Kimlik öğesi tasarım zamanında hizmet beklenen kimliğini belirtmek bir istemci Geliştirici sağlar. Anlaşma işlemi istemci ve hizmet arasındaki Windows Communication Foundation (WCF) altyapısı, beklenen hizmet eşleşen değerleri bu öğenin kimliği ilişkilendirilmesini sağlar ve böylece doğrulanabilir. Daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|sertifika|Bir X.509 sertifikası ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.CertificateElement>. Bir öznitelik içeriyor `encodedValue` diğer bir deyişle bu sertifika tarafından kodlanmış değeri belirten bir dize,.|  
|certificateReference|X.509 Sertifika doğrulama ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Bir hizmetin kimliğini doğrulamak için kullanılan bir X.509 sertifikası DNS belirtir. Bu öğe bir öznitelik içeriyor `value` , bir dizedir ve gerçek kimliğini içerir.|  
|rsa|Bir hizmet için bir istemci kimlik doğrulaması için kullanılan bir X.509 sertifikası RSA alanının değerini belirtir. Bu öğe bir öznitelik içeriyor `value` , bir dizedir ve gerçek kimliğini içerir|  
|servicePrincipalName|Bir hizmet örneğini benzersiz şekilde tanımlamak için bir istemci tarafından kullanılan asıl ad sunucu asıl adı (SPN) kimliğini belirtir. Bu öğe bir öznitelik içeriyor `value` , bir dizedir ve gerçek asıl adını içerir. Bu öğe türünde <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Bir kullanıcı ağda oturum açma adı türünde bir kullanıcı asıl adı (UPN) kimliğini belirtir. Ardından, Active Directory içinde kullanılan kullanıcı nesne adı, kullanıcı asıl adı oluşur simgesini (@) ve ardından, genellikle, etki alanı adı sistemi üst etki alanı. Örneğin, kullanıcı asıl adı Jeff Fabrikam.com etki alanı ağacındaki olabilir [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Bu öğe bir öznitelik içeriyor `value` , bir dizedir ve gerçek asıl adını içerir. Bu öğe türünde <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Özel >](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Bir netPeerTcpBinding için özel eş çözümleyici belirtir.|  
|[\<uç noktası >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)|Farklı türde uç noktalar yapılandırır.|  
|[\<veren >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Güvenlik belirteci hizmeti (STS) Federasyon Hizmeti için belirtir.|  
|[\<İssuedtokenparameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Güvenlik belirteci hizmeti (STS için) Federasyon Hizmeti meta veri uç noktasının belirtir.|  
|[\<İssuermetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|İçinde özel bağlama verilen bir belirteç parametrelerini tanımlar.|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Bir yerel güvenlik belirteci hizmeti (STS) belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
