---
title: <add> / <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 939718e8dacca2698b6f71a3bdc1262a5dc3ee20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926674"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="3fc03-102">\<\<KnownCertificates > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="3fc03-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="3fc03-103">Bilinen sertifika koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="3fc03-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="3fc03-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3fc03-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3fc03-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="3fc03-105">\<behaviors></span></span>  
<span data-ttu-id="3fc03-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3fc03-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3fc03-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="3fc03-107">\<behavior></span></span>  
<span data-ttu-id="3fc03-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3fc03-108">\<serviceCredentials></span></span>  
<span data-ttu-id="3fc03-109">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="3fc03-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="3fc03-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="3fc03-110">\<knownCertificates></span></span>  
<span data-ttu-id="3fc03-111">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="3fc03-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc03-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fc03-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fc03-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fc03-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3fc03-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fc03-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fc03-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3fc03-115">Attributes</span></span>  
  
|<span data-ttu-id="3fc03-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3fc03-116">Attribute</span></span>|<span data-ttu-id="3fc03-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fc03-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3fc03-118">findValue</span><span class="sxs-lookup"><span data-stu-id="3fc03-118">findValue</span></span>|<span data-ttu-id="3fc03-119">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="3fc03-119">String.</span></span> <span data-ttu-id="3fc03-120">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="3fc03-120">The value to search for.</span></span>|  
|<span data-ttu-id="3fc03-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="3fc03-121">storeLocation</span></span>|<span data-ttu-id="3fc03-122">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="3fc03-122">Enumeration.</span></span> <span data-ttu-id="3fc03-123">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="3fc03-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="3fc03-124">storeName</span><span class="sxs-lookup"><span data-stu-id="3fc03-124">storeName</span></span>|<span data-ttu-id="3fc03-125">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="3fc03-125">Enumeration.</span></span> <span data-ttu-id="3fc03-126">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="3fc03-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="3fc03-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="3fc03-127">x509FindType</span></span>|<span data-ttu-id="3fc03-128">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="3fc03-128">Enumeration.</span></span> <span data-ttu-id="3fc03-129">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="3fc03-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="3fc03-130">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="3fc03-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="3fc03-131">Değer</span><span class="sxs-lookup"><span data-stu-id="3fc03-131">Value</span></span>|<span data-ttu-id="3fc03-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fc03-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3fc03-133">Dize</span><span class="sxs-lookup"><span data-stu-id="3fc03-133">String</span></span>|<span data-ttu-id="3fc03-134">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="3fc03-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="3fc03-135">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="3fc03-136">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="3fc03-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="3fc03-137">Değer</span><span class="sxs-lookup"><span data-stu-id="3fc03-137">Value</span></span>|<span data-ttu-id="3fc03-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fc03-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3fc03-139">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3fc03-139">Enumeration</span></span>|<span data-ttu-id="3fc03-140">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="3fc03-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="3fc03-141">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="3fc03-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="3fc03-142">Değer</span><span class="sxs-lookup"><span data-stu-id="3fc03-142">Value</span></span>|<span data-ttu-id="3fc03-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fc03-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3fc03-144">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3fc03-144">Enumeration</span></span>|<span data-ttu-id="3fc03-145">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="3fc03-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="3fc03-146">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="3fc03-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="3fc03-147">Değer</span><span class="sxs-lookup"><span data-stu-id="3fc03-147">Value</span></span>|<span data-ttu-id="3fc03-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fc03-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3fc03-149">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3fc03-149">Enumeration</span></span>|<span data-ttu-id="3fc03-150">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="3fc03-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3fc03-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fc03-151">Child Elements</span></span>  
 <span data-ttu-id="3fc03-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="3fc03-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3fc03-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fc03-153">Parent Elements</span></span>  
  
|<span data-ttu-id="3fc03-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="3fc03-154">Element</span></span>|<span data-ttu-id="3fc03-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fc03-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fc03-156">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="3fc03-156">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="3fc03-157">Güvenlik belirteçleri doğrulaması için bir güvenlik belirteci hizmeti (STS) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3fc03-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fc03-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fc03-158">Remarks</span></span>  
 <span data-ttu-id="3fc03-159">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="3fc03-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="3fc03-160">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="3fc03-161">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="3fc03-162">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="3fc03-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="3fc03-163">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="3fc03-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="3fc03-164">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="3fc03-165">IssuedTokenAuthentication > öğesi, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="3fc03-165">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="3fc03-166">Sertifika eklemek için, [ \<KnownCertificates >](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="3fc03-166">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="3fc03-167">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<Add > element \<KnownCertificates > öğesi](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3fc03-167">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="3fc03-168">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="3fc03-169">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="3fc03-170">Bir istemcinin Federasyon Hizmeti tarafından doğrulanması ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için gereken koşulları gözden geçirmek için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3fc03-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="3fc03-171">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="3fc03-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fc03-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fc03-172">Example</span></span>  
 <span data-ttu-id="3fc03-173">Aşağıdaki örnek, herhangi bir STS sertifikası için depoya sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="3fc03-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="3fc03-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fc03-174">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="3fc03-175">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="3fc03-175">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="3fc03-176">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="3fc03-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3fc03-177">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="3fc03-177">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3fc03-178">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3fc03-178">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="3fc03-179">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3fc03-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
