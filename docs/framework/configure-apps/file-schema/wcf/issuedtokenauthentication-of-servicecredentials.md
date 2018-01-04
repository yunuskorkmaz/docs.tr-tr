---
title: "&lt;serviceCredentials&gt; için &lt;issuedTokenAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1007abbb91787ed7be4fe3a7f8c1b0173191d60e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="e0fdd-102">&lt;serviceCredentials&gt; için &lt;issuedTokenAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="e0fdd-102">&lt;issuedTokenAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="e0fdd-103">Bir hizmeti kimlik bilgileri özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="e0fdd-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e0fdd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0fdd-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="e0fdd-105">\<behaviors></span></span>  
<span data-ttu-id="e0fdd-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e0fdd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e0fdd-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e0fdd-107">\<behavior></span></span>  
<span data-ttu-id="e0fdd-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e0fdd-108">\<serviceCredentials></span></span>  
<span data-ttu-id="e0fdd-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e0fdd-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0fdd-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0fdd-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0fdd-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0fdd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e0fdd-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="e0fdd-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0fdd-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0fdd-113">Attributes</span></span>  
  
|<span data-ttu-id="e0fdd-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e0fdd-114">Attribute</span></span>|<span data-ttu-id="e0fdd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0fdd-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="e0fdd-116">Hedef URI kümesini alır, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="e0fdd-117">Bu öznitelik kullanma hakkında daha fazla bilgi için bkz: <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="e0fdd-118">Güvenilmeyen RSA sertifika verenler izinleri olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="e0fdd-119">Sertifikalar orijinalliğini doğrulamak için sertifika yetkililerini tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="e0fdd-120">Güvenilmeyen bir veren sertifikaları imzalamak için güvenilecek belirtilmemiş bir CA'dır.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="e0fdd-121">Belirten bir değeri alır olup olmadığını <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirtecinin <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="e0fdd-122">Bu değer türünde <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="e0fdd-123">Bu öznitelik kullanma hakkında daha fazla bilgi için bkz: <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="e0fdd-124">Sertifika doğrulama modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="e0fdd-125">Geçerli değerlerini birini <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="e0fdd-126">Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="e0fdd-127">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="e0fdd-128">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-128">Optional string.</span></span> <span data-ttu-id="e0fdd-129">Tür ve bir özel tür doğrulamak için kullanılan derleme.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="e0fdd-130">Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="e0fdd-131">İptal denetimi olup oluşur ve çevrimiçi veya çevrimdışı gerçekleştirilen varsa belirten iptal modu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="e0fdd-132">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="e0fdd-133">Hizmet kimlik bilgisi için kullanılan SamlSerializer türünü belirtir. isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="e0fdd-134">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="e0fdd-135">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-135">Optional enumeration.</span></span> <span data-ttu-id="e0fdd-136">İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0fdd-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0fdd-137">Child Elements</span></span>  
  
|<span data-ttu-id="e0fdd-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0fdd-138">Element</span></span>|<span data-ttu-id="e0fdd-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0fdd-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="e0fdd-140">Bir koleksiyonunu belirtir <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> öğeleri güvenilen verenler için hizmet kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0fdd-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0fdd-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e0fdd-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0fdd-142">Element</span></span>|<span data-ttu-id="e0fdd-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0fdd-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0fdd-144">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e0fdd-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="e0fdd-145">Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0fdd-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0fdd-146">Remarks</span></span>  
 <span data-ttu-id="e0fdd-147">Verilen belirteç senaryo üç aşamadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="e0fdd-148">İlk aşamada, bir hizmet erişmeye çalışan istemci bilinir bir *güvenli belirteç hizmeti*.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="e0fdd-149">Güvenli belirteç hizmeti istemcinin kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylar biçimlendirme dili (SAML) belirteci bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="e0fdd-150">İstemci ardından belirteci ile hizmetine döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="e0fdd-151">Hizmet belirteci ve bu nedenle istemci kimliğini doğrulamak hizmet veren veriler için belirteç inceler.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="e0fdd-152">Belirteç kimlik doğrulaması için sertifika güvenli belirteç hizmeti kullandığı hizmete bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="e0fdd-153">Bu öğe, bu tür bir güvenli belirteç hizmeti sertifikalar için depodur.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="e0fdd-154">Sertifika eklemek için kullanın [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="e0fdd-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="e0fdd-155">INSERT bir [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="e0fdd-156">Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="e0fdd-157">Bu ", istemciler yalnızca yasal olun sertifikaları bilinen" hizmet erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="e0fdd-158">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="e0fdd-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0fdd-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0fdd-159">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [<span data-ttu-id="e0fdd-160">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e0fdd-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e0fdd-161">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e0fdd-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
