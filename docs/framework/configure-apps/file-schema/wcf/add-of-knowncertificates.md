---
title: <add> / <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400617"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="dd4fe-102">\<\<KnownCertificates > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="dd4fe-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="dd4fe-103">Bilinen sertifika koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
<span data-ttu-id="dd4fe-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dd4fe-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dd4fe-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="dd4fe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="dd4fe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="dd4fe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="dd4fe-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="dd4fe-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownCertificates >** ](knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)</span></span>\
<span data-ttu-id="dd4fe-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="dd4fe-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4fe-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd4fe-113">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd4fe-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd4fe-114">Attributes and Elements</span></span>  
 <span data-ttu-id="dd4fe-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd4fe-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dd4fe-116">Attributes</span></span>  
  
|<span data-ttu-id="dd4fe-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dd4fe-117">Attribute</span></span>|<span data-ttu-id="dd4fe-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd4fe-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd4fe-119">findValue</span><span class="sxs-lookup"><span data-stu-id="dd4fe-119">findValue</span></span>|<span data-ttu-id="dd4fe-120">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-120">String.</span></span> <span data-ttu-id="dd4fe-121">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-121">The value to search for.</span></span>|  
|<span data-ttu-id="dd4fe-122">storeLocation</span><span class="sxs-lookup"><span data-stu-id="dd4fe-122">storeLocation</span></span>|<span data-ttu-id="dd4fe-123">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-123">Enumeration.</span></span> <span data-ttu-id="dd4fe-124">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-124">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="dd4fe-125">storeName</span><span class="sxs-lookup"><span data-stu-id="dd4fe-125">storeName</span></span>|<span data-ttu-id="dd4fe-126">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-126">Enumeration.</span></span> <span data-ttu-id="dd4fe-127">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-127">One of the system stores to search.</span></span>|  
|<span data-ttu-id="dd4fe-128">x509FindType</span><span class="sxs-lookup"><span data-stu-id="dd4fe-128">x509FindType</span></span>|<span data-ttu-id="dd4fe-129">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-129">Enumeration.</span></span> <span data-ttu-id="dd4fe-130">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-130">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="dd4fe-131">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="dd4fe-131">findValue Attribute</span></span>  
  
|<span data-ttu-id="dd4fe-132">Değer</span><span class="sxs-lookup"><span data-stu-id="dd4fe-132">Value</span></span>|<span data-ttu-id="dd4fe-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd4fe-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd4fe-134">Dize</span><span class="sxs-lookup"><span data-stu-id="dd4fe-134">String</span></span>|<span data-ttu-id="dd4fe-135">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="dd4fe-135">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="dd4fe-136">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-136">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="dd4fe-137">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="dd4fe-137">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="dd4fe-138">Değer</span><span class="sxs-lookup"><span data-stu-id="dd4fe-138">Value</span></span>|<span data-ttu-id="dd4fe-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd4fe-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd4fe-140">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="dd4fe-140">Enumeration</span></span>|<span data-ttu-id="dd4fe-141">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-141">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="dd4fe-142">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="dd4fe-142">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="dd4fe-143">Değer</span><span class="sxs-lookup"><span data-stu-id="dd4fe-143">Value</span></span>|<span data-ttu-id="dd4fe-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd4fe-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd4fe-145">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="dd4fe-145">Enumeration</span></span>|<span data-ttu-id="dd4fe-146">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-146">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="dd4fe-147">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="dd4fe-147">storeName Attribute</span></span>  
  
|<span data-ttu-id="dd4fe-148">Değer</span><span class="sxs-lookup"><span data-stu-id="dd4fe-148">Value</span></span>|<span data-ttu-id="dd4fe-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd4fe-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd4fe-150">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="dd4fe-150">Enumeration</span></span>|<span data-ttu-id="dd4fe-151">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-151">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd4fe-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd4fe-152">Child Elements</span></span>  
 <span data-ttu-id="dd4fe-153">Yok.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd4fe-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd4fe-154">Parent Elements</span></span>  
  
|<span data-ttu-id="dd4fe-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd4fe-155">Element</span></span>|<span data-ttu-id="dd4fe-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd4fe-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd4fe-157">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="dd4fe-157">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="dd4fe-158">Güvenlik belirteçleri doğrulaması için bir güvenlik belirteci hizmeti (STS) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-158">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd4fe-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd4fe-159">Remarks</span></span>  
 <span data-ttu-id="dd4fe-160">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-160">The issued token scenario has three stages.</span></span> <span data-ttu-id="dd4fe-161">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-161">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="dd4fe-162">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-162">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="dd4fe-163">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-163">The client then returns to the service with the token.</span></span> <span data-ttu-id="dd4fe-164">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-164">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="dd4fe-165">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-165">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="dd4fe-166">IssuedTokenAuthentication > öğesi, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="dd4fe-166">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="dd4fe-167">Sertifika eklemek için, [ \<KnownCertificates >](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-167">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="dd4fe-168">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<Add > element \<KnownCertificates > öğesi](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-168">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="dd4fe-169">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-169">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="dd4fe-170">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-170">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="dd4fe-171">Bir istemcinin Federasyon Hizmeti tarafından doğrulanması ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için gereken koşulları gözden geçirmek için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-171">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="dd4fe-172">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="dd4fe-172">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd4fe-173">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd4fe-173">Example</span></span>  
 <span data-ttu-id="dd4fe-174">Aşağıdaki örnek, herhangi bir STS sertifikası için depoya sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-174">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd4fe-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd4fe-175">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="dd4fe-176">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="dd4fe-176">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="dd4fe-177">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="dd4fe-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="dd4fe-178">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="dd4fe-178">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dd4fe-179">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dd4fe-179">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="dd4fe-180">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dd4fe-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
