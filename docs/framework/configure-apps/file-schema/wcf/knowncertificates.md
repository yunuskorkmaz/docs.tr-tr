---
title: '&lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 394ae246ad29a0747f3814b36fae2557b04c235a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748249"
---
# <a name="ltknowncertificatesgt"></a><span data-ttu-id="1d29e-102">&lt;knownCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="1d29e-102">&lt;knownCertificates&gt;</span></span>
<span data-ttu-id="1d29e-103">Bir güvenlik belirteci hizmeti (STS) gelen verilen güvenlik kimlik bilgilerini doğrulamak için sağlanan X.509 sertifikalarını koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d29e-103">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="1d29e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1d29e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d29e-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="1d29e-105">\<behaviors></span></span>  
<span data-ttu-id="1d29e-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1d29e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1d29e-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1d29e-107">\<behavior></span></span>  
<span data-ttu-id="1d29e-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1d29e-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1d29e-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1d29e-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="1d29e-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="1d29e-110">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d29e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d29e-111">Syntax</span></span>  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d29e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d29e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1d29e-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="1d29e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d29e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d29e-114">Attributes</span></span>  
 <span data-ttu-id="1d29e-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d29e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d29e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d29e-116">Child Elements</span></span>  
  
|<span data-ttu-id="1d29e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d29e-117">Element</span></span>|<span data-ttu-id="1d29e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d29e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d29e-119">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1d29e-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="1d29e-120">Bir X.509 sertifikası koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="1d29e-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d29e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d29e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1d29e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d29e-122">Element</span></span>|<span data-ttu-id="1d29e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d29e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d29e-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1d29e-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="1d29e-125">Bir hizmeti kimlik bilgileri verilen bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d29e-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d29e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d29e-126">Remarks</span></span>  
 <span data-ttu-id="1d29e-127">Verilen belirteç senaryo üç aşamadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d29e-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="1d29e-128">İlk aşamada, bir hizmet erişmeye çalışan istemci bilinir bir *güvenli belirteç hizmeti*.</span><span class="sxs-lookup"><span data-stu-id="1d29e-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="1d29e-129">Güvenli belirteç hizmeti istemcinin kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylar biçimlendirme dili (SAML) belirteci bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="1d29e-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="1d29e-130">İstemci ardından belirteci ile hizmetine döndürür.</span><span class="sxs-lookup"><span data-stu-id="1d29e-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="1d29e-131">Hizmet belirteci ve bu nedenle istemci kimliğini doğrulamak hizmet veren veriler için belirteç inceler.</span><span class="sxs-lookup"><span data-stu-id="1d29e-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="1d29e-132">Belirteç kimlik doğrulaması için sertifika güvenli belirteç hizmeti kullandığı hizmete bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="1d29e-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="1d29e-133">[ \<İssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo böyle herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="1d29e-133">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="1d29e-134">Sertifika eklemek için kullanın [ \<knownCertificates > öğesi](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="1d29e-134">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="1d29e-135">INSERT bir [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.</span><span class="sxs-lookup"><span data-stu-id="1d29e-135">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="1d29e-136">Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d29e-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="1d29e-137">Bu ", istemciler yalnızca yasal olun sertifikaları bilinen" hizmet erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1d29e-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="1d29e-138">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi yanı sıra, bir Federasyon Hizmeti tarafından kimliği doğrulanmış bir istemci için gereken koşulları gözden geçirmek için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="1d29e-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="1d29e-139">Federasyon senaryoları hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="1d29e-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="1d29e-140">Yapılandırma koleksiyonunda doldurmak nasıl oluşturulduğunu gösteren örnek için bkz: [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="1d29e-140">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d29e-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d29e-141">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [<span data-ttu-id="1d29e-142">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1d29e-142">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="1d29e-143">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1d29e-143">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="1d29e-144">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="1d29e-144">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1d29e-145">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1d29e-145">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="1d29e-146">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="1d29e-146">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="1d29e-147">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="1d29e-147">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1d29e-148">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1d29e-148">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="1d29e-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1d29e-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
