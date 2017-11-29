---
title: '&lt;knownCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e1ce8be4dfa71685933512c1c0db36000ce93c12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltknowncertificatesgt"></a><span data-ttu-id="6c313-102">&lt;knownCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="6c313-102">&lt;knownCertificates&gt;</span></span>
<span data-ttu-id="6c313-103">Bir güvenlik belirteci hizmeti (STS) gelen verilen güvenlik kimlik bilgilerini doğrulamak için sağlanan X.509 sertifikalarını koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c313-103">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="6c313-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6c313-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c313-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="6c313-105">\<behaviors></span></span>  
<span data-ttu-id="6c313-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6c313-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6c313-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6c313-107">\<behavior></span></span>  
<span data-ttu-id="6c313-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="6c313-108">\<serviceCredentials></span></span>  
<span data-ttu-id="6c313-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="6c313-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="6c313-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="6c313-110">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c313-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c313-111">Syntax</span></span>  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c313-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c313-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6c313-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="6c313-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c313-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c313-114">Attributes</span></span>  
 <span data-ttu-id="6c313-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c313-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6c313-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c313-116">Child Elements</span></span>  
  
|<span data-ttu-id="6c313-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c313-117">Element</span></span>|<span data-ttu-id="6c313-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c313-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c313-119">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="6c313-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="6c313-120">Bir X.509 sertifikası koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="6c313-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c313-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c313-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6c313-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c313-122">Element</span></span>|<span data-ttu-id="6c313-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c313-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c313-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="6c313-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="6c313-125">Bir hizmeti kimlik bilgileri verilen bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c313-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c313-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c313-126">Remarks</span></span>  
 <span data-ttu-id="6c313-127">Verilen belirteç senaryo üç aşamadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="6c313-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="6c313-128">İlk aşamada, bir hizmet erişmeye çalışan istemci bilinir bir *güvenli belirteç hizmeti*.</span><span class="sxs-lookup"><span data-stu-id="6c313-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="6c313-129">Güvenli belirteç hizmeti istemcinin kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylar biçimlendirme dili (SAML) belirteci bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="6c313-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="6c313-130">İstemci ardından belirteci ile hizmetine döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c313-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="6c313-131">Hizmet belirteci ve bu nedenle istemci kimliğini doğrulamak hizmet veren veriler için belirteç inceler.</span><span class="sxs-lookup"><span data-stu-id="6c313-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="6c313-132">Belirteç kimlik doğrulaması için sertifika güvenli belirteç hizmeti kullandığı hizmete bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="6c313-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="6c313-133">[ \<İssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo böyle herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="6c313-133">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="6c313-134">Sertifika eklemek için kullanın [ \<knownCertificates > öğesi](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="6c313-134">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="6c313-135">INSERT bir [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.</span><span class="sxs-lookup"><span data-stu-id="6c313-135">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="6c313-136">Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c313-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="6c313-137">Bu ", istemciler yalnızca yasal olun sertifikaları bilinen" hizmet erişebilir.</span><span class="sxs-lookup"><span data-stu-id="6c313-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="6c313-138">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi yanı sıra, bir Federasyon Hizmeti tarafından kimliği doğrulanmış bir istemci için gereken koşulları gözden geçirmek için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="6c313-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="6c313-139">Federasyon senaryoları hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="6c313-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="6c313-140">Yapılandırma koleksiyonunda doldurmak nasıl oluşturulduğunu gösteren örnek için bkz: [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="6c313-140">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c313-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c313-141">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [<span data-ttu-id="6c313-142">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="6c313-142">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="6c313-143">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="6c313-143">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="6c313-144">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="6c313-144">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="6c313-145">Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın</span><span class="sxs-lookup"><span data-stu-id="6c313-145">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="6c313-146">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="6c313-146">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="6c313-147">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="6c313-147">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="6c313-148">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="6c313-148">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="6c313-149">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="6c313-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
