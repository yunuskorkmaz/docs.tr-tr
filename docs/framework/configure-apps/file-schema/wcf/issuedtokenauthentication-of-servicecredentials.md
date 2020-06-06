---
title: <issuedTokenAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400354"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="8f194-102">\<issuedTokenAuthentication> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="8f194-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="8f194-103">Hizmet kimlik bilgisi olarak verilen özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f194-103">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="8f194-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f194-104">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f194-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f194-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8f194-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="8f194-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f194-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f194-107">Attributes</span></span>  
  
|<span data-ttu-id="8f194-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f194-108">Attribute</span></span>|<span data-ttu-id="8f194-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f194-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="8f194-110"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin kümesini alır <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="8f194-110">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="8f194-111">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A> ..</span><span class="sxs-lookup"><span data-stu-id="8f194-111">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="8f194-112">Güvenilmeyen RSA sertifikası verenler için izin verilip verilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8f194-112">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="8f194-113">Sertifikalar, özgünlük doğrulaması için sertifika yetkilileri (CA) tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="8f194-113">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="8f194-114">Güvenilmeyen bir veren, sertifikaları imzalamak için güvenilmeyecek şekilde belirtilmemiş bir CA 'dır.</span><span class="sxs-lookup"><span data-stu-id="8f194-114">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="8f194-115"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Güvenlik belirtecinin doğrulanıp doğrulanması gerekip gerekmediğini belirten bir değer alır <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> .</span><span class="sxs-lookup"><span data-stu-id="8f194-115">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="8f194-116">Bu değer türünde <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="8f194-116">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="8f194-117">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A> ..</span><span class="sxs-lookup"><span data-stu-id="8f194-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="8f194-118">Sertifika doğrulama modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f194-118">Sets the certificate validation mode.</span></span> <span data-ttu-id="8f194-119">Geçerli değerlerinden biri <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="8f194-119">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="8f194-120">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f194-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="8f194-121">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="8f194-121">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="8f194-122">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="8f194-122">Optional string.</span></span> <span data-ttu-id="8f194-123">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="8f194-123">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="8f194-124">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="8f194-124">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="8f194-125">Bir iptal denetiminin oluşup oluşmadığını ve çevrimiçi veya çevrimdışı gerçekleştirildiğini belirten iptal modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f194-125">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="8f194-126">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="8f194-126">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="8f194-127">Hizmet kimlik bilgisi için kullanılan SamlSerializer türünü belirten isteğe bağlı bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8f194-127">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="8f194-128">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="8f194-128">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="8f194-129">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8f194-129">Optional enumeration.</span></span> <span data-ttu-id="8f194-130">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="8f194-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f194-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f194-131">Child Elements</span></span>  
  
|<span data-ttu-id="8f194-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f194-132">Element</span></span>|<span data-ttu-id="8f194-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f194-133">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="8f194-134"><xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>Hizmet kimlik bilgisi için güvenilen verenler belirten bir öğe koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f194-134">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f194-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f194-135">Parent Elements</span></span>  
  
|<span data-ttu-id="8f194-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f194-136">Element</span></span>|<span data-ttu-id="8f194-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f194-137">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="8f194-138">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f194-138">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f194-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f194-139">Remarks</span></span>  
 <span data-ttu-id="8f194-140">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="8f194-140">The issued token scenario has three stages.</span></span> <span data-ttu-id="8f194-141">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="8f194-141">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="8f194-142">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="8f194-142">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="8f194-143">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="8f194-143">The client then returns to the service with the token.</span></span> <span data-ttu-id="8f194-144">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="8f194-144">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="8f194-145">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="8f194-145">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="8f194-146">Bu öğe, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır.</span><span class="sxs-lookup"><span data-stu-id="8f194-146">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="8f194-147">Sertifika eklemek için öğesini kullanın [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="8f194-147">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="8f194-148">[\<add>](add-of-knowncertificates.md)Aşağıdaki örnekte gösterildiği gibi her sertifika için bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8f194-148">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="8f194-149">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f194-149">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="8f194-150">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="8f194-150">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="8f194-151">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="8f194-151">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f194-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f194-152">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="8f194-153">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8f194-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8f194-154">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8f194-154">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
