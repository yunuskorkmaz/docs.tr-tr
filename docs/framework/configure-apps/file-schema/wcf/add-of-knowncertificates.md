---
title: <add> , <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 022030489551bfaf48cffd4ba983bbd3c99abc87
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274293"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="39a0a-102">\<Ekle >, \<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="39a0a-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="39a0a-103">Bilinen sertifika koleksiyonuna bir X.509 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="39a0a-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="39a0a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39a0a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39a0a-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="39a0a-105">\<behaviors></span></span>  
<span data-ttu-id="39a0a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="39a0a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="39a0a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="39a0a-107">\<behavior></span></span>  
<span data-ttu-id="39a0a-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="39a0a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="39a0a-109">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="39a0a-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="39a0a-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="39a0a-110">\<knownCertificates></span></span>  
<span data-ttu-id="39a0a-111">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="39a0a-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a0a-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39a0a-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39a0a-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a0a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="39a0a-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39a0a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39a0a-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39a0a-115">Attributes</span></span>  
  
|<span data-ttu-id="39a0a-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39a0a-116">Attribute</span></span>|<span data-ttu-id="39a0a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a0a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39a0a-118">findValue</span><span class="sxs-lookup"><span data-stu-id="39a0a-118">findValue</span></span>|<span data-ttu-id="39a0a-119">dize.</span><span class="sxs-lookup"><span data-stu-id="39a0a-119">String.</span></span> <span data-ttu-id="39a0a-120">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="39a0a-120">The value to search for.</span></span>|  
|<span data-ttu-id="39a0a-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="39a0a-121">storeLocation</span></span>|<span data-ttu-id="39a0a-122">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="39a0a-122">Enumeration.</span></span> <span data-ttu-id="39a0a-123">İki birini aranacak konumların depolayın.</span><span class="sxs-lookup"><span data-stu-id="39a0a-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="39a0a-124">storeName</span><span class="sxs-lookup"><span data-stu-id="39a0a-124">storeName</span></span>|<span data-ttu-id="39a0a-125">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="39a0a-125">Enumeration.</span></span> <span data-ttu-id="39a0a-126">Aranacak bir sistemin depolar.</span><span class="sxs-lookup"><span data-stu-id="39a0a-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="39a0a-127">X509FindType</span><span class="sxs-lookup"><span data-stu-id="39a0a-127">x509FindType</span></span>|<span data-ttu-id="39a0a-128">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="39a0a-128">Enumeration.</span></span> <span data-ttu-id="39a0a-129">Aranacak sertifika alanlardan biri.</span><span class="sxs-lookup"><span data-stu-id="39a0a-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="39a0a-130">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="39a0a-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="39a0a-131">Değer</span><span class="sxs-lookup"><span data-stu-id="39a0a-131">Value</span></span>|<span data-ttu-id="39a0a-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a0a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39a0a-133">Dize</span><span class="sxs-lookup"><span data-stu-id="39a0a-133">String</span></span>|<span data-ttu-id="39a0a-134">Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranan.</span><span class="sxs-lookup"><span data-stu-id="39a0a-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="39a0a-135">Örneğin, bir parmak izi için arama değeri bir dize onaltılık bir sayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39a0a-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="39a0a-136">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="39a0a-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="39a0a-137">Değer</span><span class="sxs-lookup"><span data-stu-id="39a0a-137">Value</span></span>|<span data-ttu-id="39a0a-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a0a-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39a0a-139">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="39a0a-139">Enumeration</span></span>|<span data-ttu-id="39a0a-140">Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="39a0a-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="39a0a-141">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="39a0a-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="39a0a-142">Değer</span><span class="sxs-lookup"><span data-stu-id="39a0a-142">Value</span></span>|<span data-ttu-id="39a0a-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a0a-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39a0a-144">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="39a0a-144">Enumeration</span></span>|<span data-ttu-id="39a0a-145">LocalMachine ya da CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="39a0a-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="39a0a-146">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="39a0a-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="39a0a-147">Değer</span><span class="sxs-lookup"><span data-stu-id="39a0a-147">Value</span></span>|<span data-ttu-id="39a0a-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a0a-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39a0a-149">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="39a0a-149">Enumeration</span></span>|<span data-ttu-id="39a0a-150">Değerler şunlardır: Adres Defteri, AuthRoot, CertificateAuthority, My izni, kök, TrustedPeople ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="39a0a-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39a0a-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a0a-151">Child Elements</span></span>  
 <span data-ttu-id="39a0a-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="39a0a-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39a0a-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a0a-153">Parent Elements</span></span>  
  
|<span data-ttu-id="39a0a-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="39a0a-154">Element</span></span>|<span data-ttu-id="39a0a-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a0a-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39a0a-156">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="39a0a-156">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|<span data-ttu-id="39a0a-157">Doğrulama güvenlik belirteçleri için bir güvenlik belirteci hizmeti (STS) tarafından sağlanan X.509 Sertifika koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39a0a-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39a0a-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39a0a-158">Remarks</span></span>  
 <span data-ttu-id="39a0a-159">Verilen belirteç senaryo üç aşamadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="39a0a-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="39a0a-160">Bir istemci bir hizmeti erişmeye ilk aşamada, başvurulan bir *güvenli belirteç hizmeti*.</span><span class="sxs-lookup"><span data-stu-id="39a0a-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="39a0a-161">Güvenli belirteç hizmeti daha sonra istemci kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylama işaretleme dili (SAML) belirteci bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="39a0a-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="39a0a-162">İstemci, ardından belirteci ile hizmetine döndürür.</span><span class="sxs-lookup"><span data-stu-id="39a0a-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="39a0a-163">Belirteç için belirteç ve bu nedenle istemci kimliğini doğrulamak hizmet veren bir veri hizmeti inceler.</span><span class="sxs-lookup"><span data-stu-id="39a0a-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="39a0a-164">Belirteç kimlik doğrulaması için sertifika hizmete güvenli belirteç hizmeti kullandığı olarak bilinmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="39a0a-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="39a0a-165">[ \<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo gibi herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="39a0a-165">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="39a0a-166">Sertifikaları eklemek için [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="39a0a-166">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="39a0a-167">INSERT bir [ \<Ekle > öğesi \<knownCertificates > öğesi](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.</span><span class="sxs-lookup"><span data-stu-id="39a0a-167">Insert an [\<add> element \<knownCertificates> Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="39a0a-168">Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39a0a-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="39a0a-169">Bu "sertifikalar, istemciler yalnızca yasal olun bilinen" bir hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="39a0a-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="39a0a-170">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi yanı sıra, bir Federasyon Hizmeti tarafından doğrulanması bir istemci için gereken koşulları gözden geçirmek için bkz: [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="39a0a-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="39a0a-171">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="39a0a-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39a0a-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="39a0a-172">Example</span></span>  
 <span data-ttu-id="39a0a-173">Aşağıdaki örnek, herhangi bir STS sertifika deposu için sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="39a0a-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39a0a-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39a0a-174">See also</span></span>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="39a0a-175">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="39a0a-175">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)
- [<span data-ttu-id="39a0a-176">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="39a0a-176">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="39a0a-177">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="39a0a-177">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="39a0a-178">Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="39a0a-178">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="39a0a-179">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="39a0a-179">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
