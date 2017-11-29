---
title: '&lt;knownCertificates&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e19bb495f360352b7304595323265d28773660a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltknowncertificatesgt"></a><span data-ttu-id="f99aa-102">&lt;knownCertificates&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="f99aa-102">&lt;add&gt; of &lt;knownCertificates&gt;</span></span>
<span data-ttu-id="f99aa-103">Bir X.509 sertifikası bilinen sertifikaları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="f99aa-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="f99aa-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f99aa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f99aa-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="f99aa-105">\<behaviors></span></span>  
<span data-ttu-id="f99aa-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f99aa-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f99aa-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f99aa-107">\<behavior></span></span>  
<span data-ttu-id="f99aa-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f99aa-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f99aa-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f99aa-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="f99aa-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="f99aa-110">\<knownCertificates></span></span>  
<span data-ttu-id="f99aa-111">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="f99aa-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99aa-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f99aa-112">Syntax</span></span>  
  
```xml  
<knownCertificates>   
   <add findValue="String"  
      storeLocation="CurrentUser/LocalMachine"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f99aa-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f99aa-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f99aa-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f99aa-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f99aa-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f99aa-115">Attributes</span></span>  
  
|<span data-ttu-id="f99aa-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f99aa-116">Attribute</span></span>|<span data-ttu-id="f99aa-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f99aa-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f99aa-118">findValue</span><span class="sxs-lookup"><span data-stu-id="f99aa-118">findValue</span></span>|<span data-ttu-id="f99aa-119">Dize.</span><span class="sxs-lookup"><span data-stu-id="f99aa-119">String.</span></span> <span data-ttu-id="f99aa-120">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="f99aa-120">The value to search for.</span></span>|  
|<span data-ttu-id="f99aa-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="f99aa-121">storeLocation</span></span>|<span data-ttu-id="f99aa-122">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f99aa-122">Enumeration.</span></span> <span data-ttu-id="f99aa-123">İki birini aramak için konuma depolayın.</span><span class="sxs-lookup"><span data-stu-id="f99aa-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="f99aa-124">storeName</span><span class="sxs-lookup"><span data-stu-id="f99aa-124">storeName</span></span>|<span data-ttu-id="f99aa-125">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f99aa-125">Enumeration.</span></span> <span data-ttu-id="f99aa-126">Sistem aramak için depolar.</span><span class="sxs-lookup"><span data-stu-id="f99aa-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="f99aa-127">X509FindType</span><span class="sxs-lookup"><span data-stu-id="f99aa-127">x509FindType</span></span>|<span data-ttu-id="f99aa-128">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f99aa-128">Enumeration.</span></span> <span data-ttu-id="f99aa-129">Aranacak sertifika alanlardan biri.</span><span class="sxs-lookup"><span data-stu-id="f99aa-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="f99aa-130">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="f99aa-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="f99aa-131">Değer</span><span class="sxs-lookup"><span data-stu-id="f99aa-131">Value</span></span>|<span data-ttu-id="f99aa-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f99aa-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f99aa-133">Dize</span><span class="sxs-lookup"><span data-stu-id="f99aa-133">String</span></span>|<span data-ttu-id="f99aa-134">Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranmakta.</span><span class="sxs-lookup"><span data-stu-id="f99aa-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="f99aa-135">Örneğin, bir parmak izi için arama değeri bir onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f99aa-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="f99aa-136">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="f99aa-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="f99aa-137">Değer</span><span class="sxs-lookup"><span data-stu-id="f99aa-137">Value</span></span>|<span data-ttu-id="f99aa-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f99aa-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f99aa-139">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f99aa-139">Enumeration</span></span>|<span data-ttu-id="f99aa-140">Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="f99aa-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="f99aa-141">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="f99aa-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="f99aa-142">Değer</span><span class="sxs-lookup"><span data-stu-id="f99aa-142">Value</span></span>|<span data-ttu-id="f99aa-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f99aa-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f99aa-144">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f99aa-144">Enumeration</span></span>|<span data-ttu-id="f99aa-145">Currentuser'a veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="f99aa-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="f99aa-146">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="f99aa-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="f99aa-147">Değer</span><span class="sxs-lookup"><span data-stu-id="f99aa-147">Value</span></span>|<span data-ttu-id="f99aa-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f99aa-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f99aa-149">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f99aa-149">Enumeration</span></span>|<span data-ttu-id="f99aa-150">Değerler: adres defteri, AuthRoot, sertifika yetkilisi, izin verilmeyen, My, kök, TrustedPeople ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="f99aa-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f99aa-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f99aa-151">Child Elements</span></span>  
 <span data-ttu-id="f99aa-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="f99aa-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f99aa-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f99aa-153">Parent Elements</span></span>  
  
|<span data-ttu-id="f99aa-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="f99aa-154">Element</span></span>|<span data-ttu-id="f99aa-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f99aa-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f99aa-156">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="f99aa-156">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|<span data-ttu-id="f99aa-157">Güvenlik belirteçleri doğrulama için bir güvenlik belirteci hizmeti (STS) tarafından sağlanan X.509 sertifikalarını koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f99aa-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f99aa-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f99aa-158">Remarks</span></span>  
 <span data-ttu-id="f99aa-159">Verilen belirteç senaryo üç aşamadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="f99aa-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="f99aa-160">İlk aşamada, bir hizmet erişmeye çalışan istemci bilinir bir *güvenli belirteç hizmeti*.</span><span class="sxs-lookup"><span data-stu-id="f99aa-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="f99aa-161">Güvenli belirteç hizmeti istemcinin kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylar biçimlendirme dili (SAML) belirteci bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="f99aa-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="f99aa-162">İstemci ardından belirteci ile hizmetine döndürür.</span><span class="sxs-lookup"><span data-stu-id="f99aa-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="f99aa-163">Hizmet belirteci ve bu nedenle istemci kimliğini doğrulamak hizmet veren veriler için belirteç inceler.</span><span class="sxs-lookup"><span data-stu-id="f99aa-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="f99aa-164">Belirteç kimlik doğrulaması için sertifika güvenli belirteç hizmeti kullandığı hizmete bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="f99aa-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="f99aa-165">[ \<İssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo böyle herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="f99aa-165">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="f99aa-166">Sertifika eklemek için kullanın [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="f99aa-166">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="f99aa-167">INSERT bir [ \<Ekle > öğesi \<knownCertificates > öğesi](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.</span><span class="sxs-lookup"><span data-stu-id="f99aa-167">Insert an [\<add> element \<knownCertificates> Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="f99aa-168">Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f99aa-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="f99aa-169">Bu ", istemciler yalnızca yasal olun sertifikaları bilinen" hizmet erişebilir.</span><span class="sxs-lookup"><span data-stu-id="f99aa-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="f99aa-170">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi yanı sıra, bir Federasyon Hizmeti tarafından kimliği doğrulanmış bir istemci için gereken koşulları gözden geçirmek için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="f99aa-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="f99aa-171">Federasyon senaryoları hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="f99aa-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f99aa-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="f99aa-172">Example</span></span>  
 <span data-ttu-id="f99aa-173">Aşağıdaki örnek depo herhangi bir STS sertifika için sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="f99aa-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <serviceCredentials>  
   <issuedTokenAuthentication>  
    <knownCertificates>  
     <add findValue="www.contoso.com" storeLocation="LocalMachine"   
           storeName="CertificateAuthority"  
           x509FindType="FindByIssuerName" />  
     </knownCertificates>  
    </issuedTokenAuthentication>  
   </serviceCredentials>  
  </behavior>  
 </serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f99aa-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f99aa-174">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [<span data-ttu-id="f99aa-175">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="f99aa-175">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)  
 [<span data-ttu-id="f99aa-176">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f99aa-176">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="f99aa-177">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="f99aa-177">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f99aa-178">Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın</span><span class="sxs-lookup"><span data-stu-id="f99aa-178">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="f99aa-179">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="f99aa-179">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
