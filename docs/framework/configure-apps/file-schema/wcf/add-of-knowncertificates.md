---
description: 'Hakkında daha fazla bilgi <add> edinin: <knownCertificates>'
title: <add> / <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 1669495e6119a35543e39230fc5dcc986ee2dec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750292"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="54856-103">\<add> / \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="54856-103">\<add> of \<knownCertificates></span></span>

<span data-ttu-id="54856-104">Bilinen sertifika koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="54856-104">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="54856-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="54856-105">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54856-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54856-106">Attributes and Elements</span></span>  

 <span data-ttu-id="54856-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54856-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54856-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54856-108">Attributes</span></span>  
  
|<span data-ttu-id="54856-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="54856-109">Attribute</span></span>|<span data-ttu-id="54856-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54856-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54856-111">findValue</span><span class="sxs-lookup"><span data-stu-id="54856-111">findValue</span></span>|<span data-ttu-id="54856-112">Dize.</span><span class="sxs-lookup"><span data-stu-id="54856-112">String.</span></span> <span data-ttu-id="54856-113">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="54856-113">The value to search for.</span></span>|  
|<span data-ttu-id="54856-114">storeLocation</span><span class="sxs-lookup"><span data-stu-id="54856-114">storeLocation</span></span>|<span data-ttu-id="54856-115">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="54856-115">Enumeration.</span></span> <span data-ttu-id="54856-116">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="54856-116">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="54856-117">storeName</span><span class="sxs-lookup"><span data-stu-id="54856-117">storeName</span></span>|<span data-ttu-id="54856-118">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="54856-118">Enumeration.</span></span> <span data-ttu-id="54856-119">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="54856-119">One of the system stores to search.</span></span>|  
|<span data-ttu-id="54856-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="54856-120">x509FindType</span></span>|<span data-ttu-id="54856-121">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="54856-121">Enumeration.</span></span> <span data-ttu-id="54856-122">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="54856-122">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="54856-123">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="54856-123">findValue Attribute</span></span>  
  
|<span data-ttu-id="54856-124">Değer</span><span class="sxs-lookup"><span data-stu-id="54856-124">Value</span></span>|<span data-ttu-id="54856-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54856-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54856-126">Dize</span><span class="sxs-lookup"><span data-stu-id="54856-126">String</span></span>|<span data-ttu-id="54856-127">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="54856-127">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="54856-128">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54856-128">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="54856-129">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="54856-129">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="54856-130">Değer</span><span class="sxs-lookup"><span data-stu-id="54856-130">Value</span></span>|<span data-ttu-id="54856-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54856-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54856-132">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="54856-132">Enumeration</span></span>|<span data-ttu-id="54856-133">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, Findbyexten, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="54856-133">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="54856-134">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="54856-134">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="54856-135">Değer</span><span class="sxs-lookup"><span data-stu-id="54856-135">Value</span></span>|<span data-ttu-id="54856-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54856-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54856-137">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="54856-137">Enumeration</span></span>|<span data-ttu-id="54856-138">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="54856-138">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="54856-139">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="54856-139">storeName Attribute</span></span>  
  
|<span data-ttu-id="54856-140">Değer</span><span class="sxs-lookup"><span data-stu-id="54856-140">Value</span></span>|<span data-ttu-id="54856-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54856-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54856-142">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="54856-142">Enumeration</span></span>|<span data-ttu-id="54856-143">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="54856-143">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54856-144">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54856-144">Child Elements</span></span>  

 <span data-ttu-id="54856-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="54856-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54856-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54856-146">Parent Elements</span></span>  
  
|<span data-ttu-id="54856-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="54856-147">Element</span></span>|<span data-ttu-id="54856-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54856-148">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="54856-149">Güvenlik belirteçleri doğrulaması için bir güvenlik belirteci hizmeti (STS) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54856-149">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54856-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54856-150">Remarks</span></span>  

 <span data-ttu-id="54856-151">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="54856-151">The issued token scenario has three stages.</span></span> <span data-ttu-id="54856-152">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti* denir.</span><span class="sxs-lookup"><span data-stu-id="54856-152">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="54856-153">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="54856-153">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="54856-154">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="54856-154">The client then returns to the service with the token.</span></span> <span data-ttu-id="54856-155">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="54856-155">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="54856-156">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="54856-156">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="54856-157">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Öğesi, bu tür güvenli belirteç hizmeti sertifikalarının depolandığı depodur.</span><span class="sxs-lookup"><span data-stu-id="54856-157">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="54856-158">Sertifika eklemek için öğesini kullanın [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="54856-158">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="54856-159">Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<add> öğe \<knownCertificates> öğesi](add-of-knowncertificates.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54856-159">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="54856-160">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54856-160">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="54856-161">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="54856-161">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="54856-162">Bir istemcinin Federasyon Hizmeti tarafından doğrulanabilmesi ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi edinmek için, bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="54856-162">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="54856-163">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="54856-163">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54856-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="54856-164">Example</span></span>  

 <span data-ttu-id="54856-165">Aşağıdaki örnek, herhangi bir STS sertifikası için depoya sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="54856-165">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54856-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54856-166">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="54856-167">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="54856-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="54856-168">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="54856-168">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="54856-169">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="54856-169">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="54856-170">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="54856-170">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
