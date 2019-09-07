---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400329"
---
# <a name="knowncertificates"></a><span data-ttu-id="471fc-101">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="471fc-101">\<knownCertificates></span></span>
<span data-ttu-id="471fc-102">Bir güvenlik belirteci hizmetinden (STS) verilen güvenlik kimlik bilgilerinin kimliğini doğrulamak için verilen bir X. 509.440 sertifikaları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="471fc-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
<span data-ttu-id="471fc-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="471fc-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="471fc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="471fc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="471fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="471fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="471fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="471fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownCertificates >**</span><span class="sxs-lookup"><span data-stu-id="471fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="471fc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="471fc-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="471fc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="471fc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="471fc-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="471fc-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="471fc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="471fc-114">Attributes</span></span>  
 <span data-ttu-id="471fc-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="471fc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="471fc-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="471fc-116">Child Elements</span></span>  
  
|<span data-ttu-id="471fc-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="471fc-117">Element</span></span>|<span data-ttu-id="471fc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="471fc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="471fc-119">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="471fc-119">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="471fc-120">Koleksiyona bir X. 509.952 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="471fc-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="471fc-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="471fc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="471fc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="471fc-122">Element</span></span>|<span data-ttu-id="471fc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="471fc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="471fc-124">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="471fc-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="471fc-125">Hizmet kimlik bilgisi olarak verilen bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="471fc-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="471fc-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="471fc-126">Remarks</span></span>  
 <span data-ttu-id="471fc-127">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="471fc-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="471fc-128">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="471fc-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="471fc-129">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="471fc-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="471fc-130">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="471fc-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="471fc-131">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="471fc-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="471fc-132">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="471fc-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="471fc-133">IssuedTokenAuthentication > öğesi, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="471fc-133">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="471fc-134">Sertifika eklemek için, [ \<KnownCertificates > öğesini](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="471fc-134">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="471fc-135">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<ekleme >](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="471fc-135">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="471fc-136">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="471fc-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="471fc-137">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="471fc-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="471fc-138">Bir istemcinin Federasyon Hizmeti tarafından doğrulanması ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için gereken koşulları gözden geçirmek için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="471fc-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="471fc-139">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="471fc-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="471fc-140">Yapılandırmada koleksiyonun nasıl doldurulacağını gösteren bir örnek için bkz [ \<. Add >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="471fc-140">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="471fc-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="471fc-141">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="471fc-142">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="471fc-142">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="471fc-143">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="471fc-143">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="471fc-144">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="471fc-144">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="471fc-145">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="471fc-145">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="471fc-146">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="471fc-146">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="471fc-147">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="471fc-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="471fc-148">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="471fc-148">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="471fc-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="471fc-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
