---
title: <add> / <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400617"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="c9ab8-102">\<add> / \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="c9ab8-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="c9ab8-103">Bilinen sertifika koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c9ab8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9ab8-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9ab8-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9ab8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c9ab8-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9ab8-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9ab8-107">Attributes</span></span>  
  
|<span data-ttu-id="c9ab8-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab8-108">Attribute</span></span>|<span data-ttu-id="c9ab8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ab8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9ab8-110">findValue</span><span class="sxs-lookup"><span data-stu-id="c9ab8-110">findValue</span></span>|<span data-ttu-id="c9ab8-111">Dize.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-111">String.</span></span> <span data-ttu-id="c9ab8-112">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-112">The value to search for.</span></span>|  
|<span data-ttu-id="c9ab8-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c9ab8-113">storeLocation</span></span>|<span data-ttu-id="c9ab8-114">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-114">Enumeration.</span></span> <span data-ttu-id="c9ab8-115">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="c9ab8-116">storeName</span><span class="sxs-lookup"><span data-stu-id="c9ab8-116">storeName</span></span>|<span data-ttu-id="c9ab8-117">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-117">Enumeration.</span></span> <span data-ttu-id="c9ab8-118">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="c9ab8-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="c9ab8-119">x509FindType</span></span>|<span data-ttu-id="c9ab8-120">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-120">Enumeration.</span></span> <span data-ttu-id="c9ab8-121">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c9ab8-122">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9ab8-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="c9ab8-123">Değer</span><span class="sxs-lookup"><span data-stu-id="c9ab8-123">Value</span></span>|<span data-ttu-id="c9ab8-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ab8-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9ab8-125">Dize</span><span class="sxs-lookup"><span data-stu-id="c9ab8-125">String</span></span>|<span data-ttu-id="c9ab8-126">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="c9ab8-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c9ab8-127">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c9ab8-128">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9ab8-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c9ab8-129">Değer</span><span class="sxs-lookup"><span data-stu-id="c9ab8-129">Value</span></span>|<span data-ttu-id="c9ab8-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ab8-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9ab8-131">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c9ab8-131">Enumeration</span></span>|<span data-ttu-id="c9ab8-132">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, Findbyexten, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c9ab8-133">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9ab8-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c9ab8-134">Değer</span><span class="sxs-lookup"><span data-stu-id="c9ab8-134">Value</span></span>|<span data-ttu-id="c9ab8-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ab8-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9ab8-136">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c9ab8-136">Enumeration</span></span>|<span data-ttu-id="c9ab8-137">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c9ab8-138">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9ab8-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="c9ab8-139">Değer</span><span class="sxs-lookup"><span data-stu-id="c9ab8-139">Value</span></span>|<span data-ttu-id="c9ab8-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ab8-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9ab8-141">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c9ab8-141">Enumeration</span></span>|<span data-ttu-id="c9ab8-142">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9ab8-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9ab8-143">Child Elements</span></span>  
 <span data-ttu-id="c9ab8-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9ab8-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9ab8-145">Parent Elements</span></span>  
  
|<span data-ttu-id="c9ab8-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9ab8-146">Element</span></span>|<span data-ttu-id="c9ab8-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ab8-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="c9ab8-148">Güvenlik belirteçleri doğrulaması için bir güvenlik belirteci hizmeti (STS) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9ab8-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9ab8-149">Remarks</span></span>  
 <span data-ttu-id="c9ab8-150">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="c9ab8-151">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="c9ab8-152">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="c9ab8-153">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="c9ab8-154">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="c9ab8-155">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="c9ab8-156">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Öğesi, bu tür güvenli belirteç hizmeti sertifikalarının depolandığı depodur.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="c9ab8-157">Sertifika eklemek için öğesini kullanın [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="c9ab8-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="c9ab8-158">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<add> öğe \<knownCertificates> öğesi](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c9ab8-159">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="c9ab8-160">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="c9ab8-161">Bir istemcinin Federasyon Hizmeti tarafından doğrulanabilmesi ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi edinmek için, bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab8-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="c9ab8-162">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab8-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ab8-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9ab8-163">Example</span></span>  
 <span data-ttu-id="c9ab8-164">Aşağıdaki örnek, herhangi bir STS sertifikası için depoya sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9ab8-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="c9ab8-166">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c9ab8-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c9ab8-167">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c9ab8-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c9ab8-168">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9ab8-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="c9ab8-169">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c9ab8-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
