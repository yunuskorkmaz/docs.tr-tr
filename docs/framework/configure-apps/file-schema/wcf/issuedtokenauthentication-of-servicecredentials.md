---
title: <issuedTokenAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400354"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="ae7e4-102">\<\<ServiceCredentials > IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ae7e4-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="ae7e4-103">Hizmet kimlik bilgisi olarak verilen özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-103">Specifies a custom token issued as a service credential.</span></span>  
  
<span data-ttu-id="ae7e4-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ae7e4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ae7e4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ae7e4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ae7e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ae7e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ae7e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ae7e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ae7e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ae7e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ae7e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ae7e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="ae7e4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuedTokenAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="ae7e4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7e4-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae7e4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae7e4-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae7e4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ae7e4-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="ae7e4-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae7e4-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae7e4-114">Attributes</span></span>  
  
|<span data-ttu-id="ae7e4-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae7e4-115">Attribute</span></span>|<span data-ttu-id="ae7e4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae7e4-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="ae7e4-117"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-117">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="ae7e4-118">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-118">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="ae7e4-119">Güvenilmeyen RSA sertifikası verenler için izin verilip verilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-119">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="ae7e4-120">Sertifikalar, özgünlük doğrulaması için sertifika yetkilileri (CA) tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-120">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="ae7e4-121">Güvenilmeyen bir veren, sertifikaları imzalamak için güvenilmeyecek şekilde belirtilmemiş bir CA 'dır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-121">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="ae7e4-122"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Güvenlik<xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> belirtecinin doğrulanıp doğrulanması gerekip gerekmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-122">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="ae7e4-123">Bu değer türünde <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-123">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="ae7e4-124">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-124">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="ae7e4-125">Sertifika doğrulama modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-125">Sets the certificate validation mode.</span></span> <span data-ttu-id="ae7e4-126">Geçerli değerlerinden <xref:System.ServiceModel.Security.X509CertificateValidationMode>biri.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-126">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="ae7e4-127">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-127">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="ae7e4-128">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-128">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="ae7e4-129">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-129">Optional string.</span></span> <span data-ttu-id="ae7e4-130">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-130">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="ae7e4-131">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-131">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="ae7e4-132">Bir iptal denetiminin oluşup oluşmadığını ve çevrimiçi veya çevrimdışı gerçekleştirildiğini belirten iptal modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-132">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="ae7e4-133">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-133">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="ae7e4-134">Hizmet kimlik bilgisi için kullanılan SamlSerializer türünü belirten isteğe bağlı bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-134">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="ae7e4-135">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-135">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="ae7e4-136">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-136">Optional enumeration.</span></span> <span data-ttu-id="ae7e4-137">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="ae7e4-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae7e4-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae7e4-138">Child Elements</span></span>  
  
|<span data-ttu-id="ae7e4-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae7e4-139">Element</span></span>|<span data-ttu-id="ae7e4-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae7e4-140">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="ae7e4-141">Hizmet kimlik bilgisi için <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> güvenilen verenler belirten bir öğe koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-141">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae7e4-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae7e4-142">Parent Elements</span></span>  
  
|<span data-ttu-id="ae7e4-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae7e4-143">Element</span></span>|<span data-ttu-id="ae7e4-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae7e4-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae7e4-145">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ae7e4-145">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="ae7e4-146">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-146">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae7e4-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae7e4-147">Remarks</span></span>  
 <span data-ttu-id="ae7e4-148">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-148">The issued token scenario has three stages.</span></span> <span data-ttu-id="ae7e4-149">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-149">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="ae7e4-150">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-150">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="ae7e4-151">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-151">The client then returns to the service with the token.</span></span> <span data-ttu-id="ae7e4-152">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-152">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="ae7e4-153">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-153">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="ae7e4-154">Bu öğe, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-154">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="ae7e4-155">Sertifika eklemek için, [ \<KnownCertificates >](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-155">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="ae7e4-156">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<ekleme >](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-156">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ae7e4-157">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-157">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="ae7e4-158">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-158">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="ae7e4-159">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-159">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7e4-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae7e4-160">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="ae7e4-161">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ae7e4-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ae7e4-162">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ae7e4-162">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
