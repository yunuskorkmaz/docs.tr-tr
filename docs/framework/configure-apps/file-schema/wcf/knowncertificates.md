---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 7ddb292b8f0ffe38133c7f142be751a87d2be11c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150914"
---
# \<knownCertificates>

<span data-ttu-id="9ee41-101">Bir güvenlik belirteci hizmetinden (STS) verilen güvenlik kimlik bilgilerinin kimliğini doğrulamak için verilen bir X. 509.440 sertifikaları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9ee41-101">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="9ee41-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ee41-102">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ee41-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ee41-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9ee41-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="9ee41-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ee41-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ee41-105">Attributes</span></span>  

 <span data-ttu-id="9ee41-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ee41-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ee41-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ee41-107">Child Elements</span></span>  
  
|<span data-ttu-id="9ee41-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ee41-108">Element</span></span>|<span data-ttu-id="9ee41-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ee41-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="9ee41-110">Koleksiyona bir X. 509.952 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="9ee41-110">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ee41-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ee41-111">Parent Elements</span></span>  
  
|<span data-ttu-id="9ee41-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ee41-112">Element</span></span>|<span data-ttu-id="9ee41-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ee41-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="9ee41-114">Hizmet kimlik bilgisi olarak verilen bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ee41-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ee41-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ee41-115">Remarks</span></span>  

 <span data-ttu-id="9ee41-116">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="9ee41-116">The issued token scenario has three stages.</span></span> <span data-ttu-id="9ee41-117">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir.</span><span class="sxs-lookup"><span data-stu-id="9ee41-117">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="9ee41-118">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="9ee41-118">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="9ee41-119">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="9ee41-119">The client then returns to the service with the token.</span></span> <span data-ttu-id="9ee41-120">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="9ee41-120">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="9ee41-121">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="9ee41-121">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="9ee41-122">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Öğesi, bu tür güvenli belirteç hizmeti sertifikalarının depolandığı depodur.</span><span class="sxs-lookup"><span data-stu-id="9ee41-122">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="9ee41-123">Sertifika eklemek için [ \<knownCertificates> öğesini](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ee41-123">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="9ee41-124">[\<add>](add-of-knowncertificates.md)Aşağıdaki örnekte gösterildiği gibi her sertifika için bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9ee41-124">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9ee41-125">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ee41-125">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="9ee41-126">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="9ee41-126">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="9ee41-127">Bir istemcinin Federasyon Hizmeti tarafından doğrulanabilmesi ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi edinmek için, bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="9ee41-127">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="9ee41-128">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="9ee41-128">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="9ee41-129">Yapılandırmada koleksiyonun nasıl doldurulacağını gösteren bir örnek için bkz [\<add>](add-of-knowncertificates.md) ..</span><span class="sxs-lookup"><span data-stu-id="9ee41-129">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee41-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ee41-130">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="9ee41-131">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="9ee41-131">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9ee41-132">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9ee41-132">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="9ee41-133">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="9ee41-133">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9ee41-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9ee41-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="9ee41-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9ee41-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
