---
title: <issuedTokenAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 280aa49019f68a0906307e24842a585a92c6600a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925362"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="92a69-102">\<\<ServiceCredentials > IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="92a69-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="92a69-103">Hizmet kimlik bilgisi olarak verilen özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="92a69-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="92a69-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92a69-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="92a69-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="92a69-105">\<behaviors></span></span>  
<span data-ttu-id="92a69-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="92a69-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="92a69-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="92a69-107">\<behavior></span></span>  
<span data-ttu-id="92a69-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="92a69-108">\<serviceCredentials></span></span>  
<span data-ttu-id="92a69-109">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="92a69-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a69-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92a69-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92a69-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="92a69-111">Attributes and Elements</span></span>  
 <span data-ttu-id="92a69-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="92a69-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92a69-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="92a69-113">Attributes</span></span>  
  
|<span data-ttu-id="92a69-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="92a69-114">Attribute</span></span>|<span data-ttu-id="92a69-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92a69-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="92a69-116"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="92a69-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="92a69-117">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="92a69-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="92a69-118">Güvenilmeyen RSA sertifikası verenler için izin verilip verilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="92a69-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="92a69-119">Sertifikalar, özgünlük doğrulaması için sertifika yetkilileri (CA) tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="92a69-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="92a69-120">Güvenilmeyen bir veren, sertifikaları imzalamak için güvenilmeyecek şekilde belirtilmemiş bir CA 'dır.</span><span class="sxs-lookup"><span data-stu-id="92a69-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="92a69-121"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Güvenlik<xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> belirtecinin doğrulanıp doğrulanması gerekip gerekmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="92a69-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="92a69-122">Bu değer türünde <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="92a69-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="92a69-123">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="92a69-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="92a69-124">Sertifika doğrulama modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="92a69-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="92a69-125">Geçerli değerlerinden <xref:System.ServiceModel.Security.X509CertificateValidationMode>biri.</span><span class="sxs-lookup"><span data-stu-id="92a69-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="92a69-126">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92a69-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="92a69-127">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="92a69-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="92a69-128">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="92a69-128">Optional string.</span></span> <span data-ttu-id="92a69-129">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="92a69-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="92a69-130">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92a69-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="92a69-131">Bir iptal denetiminin oluşup oluşmadığını ve çevrimiçi veya çevrimdışı gerçekleştirildiğini belirten iptal modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="92a69-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="92a69-132">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="92a69-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="92a69-133">Hizmet kimlik bilgisi için kullanılan SamlSerializer türünü belirten isteğe bağlı bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="92a69-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="92a69-134">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="92a69-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="92a69-135">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="92a69-135">Optional enumeration.</span></span> <span data-ttu-id="92a69-136">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="92a69-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92a69-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="92a69-137">Child Elements</span></span>  
  
|<span data-ttu-id="92a69-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="92a69-138">Element</span></span>|<span data-ttu-id="92a69-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92a69-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="92a69-140">Hizmet kimlik bilgisi için <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> güvenilen verenler belirten bir öğe koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="92a69-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92a69-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="92a69-141">Parent Elements</span></span>  
  
|<span data-ttu-id="92a69-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="92a69-142">Element</span></span>|<span data-ttu-id="92a69-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92a69-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92a69-144">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="92a69-144">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="92a69-145">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="92a69-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92a69-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92a69-146">Remarks</span></span>  
 <span data-ttu-id="92a69-147">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="92a69-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="92a69-148">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="92a69-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="92a69-149">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="92a69-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="92a69-150">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="92a69-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="92a69-151">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="92a69-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="92a69-152">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="92a69-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="92a69-153">Bu öğe, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır.</span><span class="sxs-lookup"><span data-stu-id="92a69-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="92a69-154">Sertifika eklemek için, [ \<KnownCertificates >](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="92a69-154">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="92a69-155">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<ekleme >](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92a69-155">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="92a69-156">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="92a69-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="92a69-157">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="92a69-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="92a69-158">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="92a69-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a69-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92a69-159">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="92a69-160">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="92a69-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="92a69-161">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="92a69-161">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
