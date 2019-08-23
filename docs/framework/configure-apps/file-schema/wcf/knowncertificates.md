---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 1210e6282a7dd6c40198693d4948a89efe841d59
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913536"
---
# <a name="knowncertificates"></a><span data-ttu-id="c211a-101">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="c211a-101">\<knownCertificates></span></span>
<span data-ttu-id="c211a-102">Bir güvenlik belirteci hizmetinden (STS) verilen güvenlik kimlik bilgilerinin kimliğini doğrulamak için verilen bir X. 509.440 sertifikaları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c211a-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="c211a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c211a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c211a-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c211a-104">\<behaviors></span></span>  
<span data-ttu-id="c211a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c211a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c211a-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c211a-106">\<behavior></span></span>  
<span data-ttu-id="c211a-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c211a-107">\<serviceCredentials></span></span>  
<span data-ttu-id="c211a-108">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c211a-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="c211a-109">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="c211a-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c211a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c211a-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c211a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c211a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c211a-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c211a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c211a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c211a-113">Attributes</span></span>  
 <span data-ttu-id="c211a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="c211a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c211a-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c211a-115">Child Elements</span></span>  
  
|<span data-ttu-id="c211a-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c211a-116">Element</span></span>|<span data-ttu-id="c211a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c211a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c211a-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="c211a-118">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="c211a-119">Koleksiyona bir X. 509.952 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="c211a-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c211a-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c211a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c211a-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c211a-121">Element</span></span>|<span data-ttu-id="c211a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c211a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c211a-123">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c211a-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="c211a-124">Hizmet kimlik bilgisi olarak verilen bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="c211a-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c211a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c211a-125">Remarks</span></span>  
 <span data-ttu-id="c211a-126">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="c211a-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="c211a-127">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="c211a-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="c211a-128">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="c211a-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="c211a-129">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="c211a-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="c211a-130">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="c211a-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="c211a-131">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="c211a-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="c211a-132">IssuedTokenAuthentication > öğesi, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c211a-132">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="c211a-133">Sertifika eklemek için, [ \<KnownCertificates > öğesini](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="c211a-133">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="c211a-134">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<ekleme >](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c211a-134">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c211a-135">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c211a-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="c211a-136">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="c211a-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="c211a-137">Bir istemcinin Federasyon Hizmeti tarafından doğrulanması ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için gereken koşulları gözden geçirmek için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="c211a-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="c211a-138">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="c211a-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="c211a-139">Yapılandırmada koleksiyonun nasıl doldurulacağını gösteren bir örnek için bkz [ \<. Add >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="c211a-139">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c211a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c211a-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="c211a-141">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="c211a-141">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="c211a-142">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c211a-142">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="c211a-143">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="c211a-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c211a-144">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c211a-144">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="c211a-145">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c211a-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c211a-146">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c211a-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c211a-147">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="c211a-147">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="c211a-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c211a-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
