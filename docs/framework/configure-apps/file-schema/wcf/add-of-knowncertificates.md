---
title: <add> / <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 453593918de15613edb801cca8a16c9dbf71aa90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176090"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="ed56e-102">\<add> / \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="ed56e-102">\<add> of \<knownCertificates></span></span>

<span data-ttu-id="ed56e-103">Bilinen sertifika koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="ed56e-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ed56e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ed56e-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed56e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed56e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ed56e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed56e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed56e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed56e-107">Attributes</span></span>  
  
|<span data-ttu-id="ed56e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed56e-108">Attribute</span></span>|<span data-ttu-id="ed56e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed56e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed56e-110">findValue</span><span class="sxs-lookup"><span data-stu-id="ed56e-110">findValue</span></span>|<span data-ttu-id="ed56e-111">Dize.</span><span class="sxs-lookup"><span data-stu-id="ed56e-111">String.</span></span> <span data-ttu-id="ed56e-112">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="ed56e-112">The value to search for.</span></span>|  
|<span data-ttu-id="ed56e-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="ed56e-113">storeLocation</span></span>|<span data-ttu-id="ed56e-114">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="ed56e-114">Enumeration.</span></span> <span data-ttu-id="ed56e-115">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="ed56e-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="ed56e-116">storeName</span><span class="sxs-lookup"><span data-stu-id="ed56e-116">storeName</span></span>|<span data-ttu-id="ed56e-117">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="ed56e-117">Enumeration.</span></span> <span data-ttu-id="ed56e-118">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="ed56e-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="ed56e-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="ed56e-119">x509FindType</span></span>|<span data-ttu-id="ed56e-120">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="ed56e-120">Enumeration.</span></span> <span data-ttu-id="ed56e-121">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="ed56e-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="ed56e-122">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="ed56e-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="ed56e-123">Değer</span><span class="sxs-lookup"><span data-stu-id="ed56e-123">Value</span></span>|<span data-ttu-id="ed56e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed56e-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed56e-125">Dize</span><span class="sxs-lookup"><span data-stu-id="ed56e-125">String</span></span>|<span data-ttu-id="ed56e-126">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="ed56e-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="ed56e-127">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed56e-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="ed56e-128">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="ed56e-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="ed56e-129">Değer</span><span class="sxs-lookup"><span data-stu-id="ed56e-129">Value</span></span>|<span data-ttu-id="ed56e-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed56e-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed56e-131">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ed56e-131">Enumeration</span></span>|<span data-ttu-id="ed56e-132">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, Findbyexten, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ed56e-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="ed56e-133">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="ed56e-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="ed56e-134">Değer</span><span class="sxs-lookup"><span data-stu-id="ed56e-134">Value</span></span>|<span data-ttu-id="ed56e-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed56e-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed56e-136">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ed56e-136">Enumeration</span></span>|<span data-ttu-id="ed56e-137">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ed56e-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="ed56e-138">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="ed56e-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="ed56e-139">Değer</span><span class="sxs-lookup"><span data-stu-id="ed56e-139">Value</span></span>|<span data-ttu-id="ed56e-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed56e-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed56e-141">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ed56e-141">Enumeration</span></span>|<span data-ttu-id="ed56e-142">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="ed56e-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed56e-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed56e-143">Child Elements</span></span>  

 <span data-ttu-id="ed56e-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="ed56e-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed56e-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed56e-145">Parent Elements</span></span>  
  
|<span data-ttu-id="ed56e-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed56e-146">Element</span></span>|<span data-ttu-id="ed56e-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed56e-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="ed56e-148">Güvenlik belirteçleri doğrulaması için bir güvenlik belirteci hizmeti (STS) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed56e-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed56e-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed56e-149">Remarks</span></span>  

 <span data-ttu-id="ed56e-150">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="ed56e-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="ed56e-151">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="ed56e-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="ed56e-152">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="ed56e-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="ed56e-153">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="ed56e-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="ed56e-154">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="ed56e-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="ed56e-155">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="ed56e-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="ed56e-156">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Öğesi, bu tür güvenli belirteç hizmeti sertifikalarının depolandığı depodur.</span><span class="sxs-lookup"><span data-stu-id="ed56e-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="ed56e-157">Sertifika eklemek için öğesini kullanın [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="ed56e-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="ed56e-158">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<add> öğe \<knownCertificates> öğesi](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed56e-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ed56e-159">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed56e-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="ed56e-160">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="ed56e-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="ed56e-161">Bir istemcinin Federasyon Hizmeti tarafından doğrulanabilmesi ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi edinmek için, bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="ed56e-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="ed56e-162">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="ed56e-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed56e-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed56e-163">Example</span></span>  

 <span data-ttu-id="ed56e-164">Aşağıdaki örnek, herhangi bir STS sertifikası için depoya sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="ed56e-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed56e-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed56e-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="ed56e-166">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="ed56e-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ed56e-167">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ed56e-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ed56e-168">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed56e-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="ed56e-169">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ed56e-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
