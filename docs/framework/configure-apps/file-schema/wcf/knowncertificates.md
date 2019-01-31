---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 4c1dc15621138aa692f0a30d285f729c2bd670d3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274124"
---
# <a name="knowncertificates"></a><span data-ttu-id="9f9eb-101">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-101">\<knownCertificates></span></span>
<span data-ttu-id="9f9eb-102">Bir güvenlik belirteci hizmeti (STS) öğesinden verilen güvenlik kimlik bilgilerinin doğrulanması için sağlanan X.509 Sertifika koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="9f9eb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f9eb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f9eb-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-104">\<behaviors></span></span>  
<span data-ttu-id="9f9eb-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9f9eb-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="9f9eb-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-106">\<behavior></span></span>  
<span data-ttu-id="9f9eb-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9f9eb-107">\<serviceCredentials></span></span>  
<span data-ttu-id="9f9eb-108">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="9f9eb-109">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f9eb-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f9eb-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f9eb-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f9eb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f9eb-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f9eb-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f9eb-113">Attributes</span></span>  
 <span data-ttu-id="9f9eb-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f9eb-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f9eb-115">Child Elements</span></span>  
  
|<span data-ttu-id="9f9eb-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f9eb-116">Element</span></span>|<span data-ttu-id="9f9eb-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f9eb-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f9eb-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="9f9eb-119">Koleksiyonuna bir X.509 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f9eb-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f9eb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9f9eb-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f9eb-121">Element</span></span>|<span data-ttu-id="9f9eb-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f9eb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f9eb-123">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="9f9eb-124">Bir hizmet kimlik bilgisi olarak verilen bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f9eb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f9eb-125">Remarks</span></span>  
 <span data-ttu-id="9f9eb-126">Verilen belirteç senaryo üç aşamadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="9f9eb-127">Bir istemci bir hizmeti erişmeye ilk aşamada, başvurulan bir *güvenli belirteç hizmeti*.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="9f9eb-128">Güvenli belirteç hizmeti daha sonra istemci kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylama işaretleme dili (SAML) belirteci bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="9f9eb-129">İstemci, ardından belirteci ile hizmetine döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="9f9eb-130">Belirteç için belirteç ve bu nedenle istemci kimliğini doğrulamak hizmet veren bir veri hizmeti inceler.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="9f9eb-131">Belirteç kimlik doğrulaması için sertifika hizmete güvenli belirteç hizmeti kullandığı olarak bilinmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="9f9eb-132">[ \<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo gibi herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-132">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="9f9eb-133">Sertifikaları eklemek için [ \<knownCertificates > öğesi](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="9f9eb-133">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="9f9eb-134">INSERT bir [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-134">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9f9eb-135">Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="9f9eb-136">Bu "sertifikalar, istemciler yalnızca yasal olun bilinen" bir hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="9f9eb-137">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi yanı sıra, bir Federasyon Hizmeti tarafından doğrulanması bir istemci için gereken koşulları gözden geçirmek için bkz: [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="9f9eb-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="9f9eb-138">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="9f9eb-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="9f9eb-139">Yapılandırma koleksiyonunda doldurmak nasıl gösteren bir örnek için bkz: [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="9f9eb-139">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f9eb-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f9eb-140">See also</span></span>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="9f9eb-141">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="9f9eb-142">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-142">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="9f9eb-143">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="9f9eb-143">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9f9eb-144">Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f9eb-144">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="9f9eb-145">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="9f9eb-145">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9f9eb-146">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9f9eb-146">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9f9eb-147">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="9f9eb-147">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="9f9eb-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9f9eb-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
