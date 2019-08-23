---
title: <scopedCertificates> Öğesi
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: ed53a42575a8d57c365f7a329a1a9c1df075d6d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935215"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="f77db-102">\<scopedCertificates > öğesi</span><span class="sxs-lookup"><span data-stu-id="f77db-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="f77db-103">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f77db-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="f77db-104">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f77db-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="f77db-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f77db-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f77db-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f77db-106">\<behaviors></span></span>  
<span data-ttu-id="f77db-107">Endpointdavranışlar bölümü</span><span class="sxs-lookup"><span data-stu-id="f77db-107">endpointBehaviors section</span></span>  
<span data-ttu-id="f77db-108">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="f77db-108">\<behavior></span></span>  
<span data-ttu-id="f77db-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f77db-109">\<clientCredentials></span></span>  
<span data-ttu-id="f77db-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="f77db-110">\<serviceCertificate></span></span>  
<span data-ttu-id="f77db-111">\<scopedCertificates > öğesi</span><span class="sxs-lookup"><span data-stu-id="f77db-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="f77db-112">\<ScopedCertificates için \<> öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="f77db-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f77db-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f77db-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f77db-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f77db-114">Attributes and Elements</span></span>  
 <span data-ttu-id="f77db-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f77db-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f77db-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f77db-116">Attributes</span></span>  
 <span data-ttu-id="f77db-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="f77db-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f77db-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f77db-118">Child Elements</span></span>  
  
|<span data-ttu-id="f77db-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="f77db-119">Element</span></span>|<span data-ttu-id="f77db-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f77db-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f77db-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="f77db-121">\<add></span></span>](add-of-scopedcertificates-element.md)|<span data-ttu-id="f77db-122">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="f77db-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f77db-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f77db-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f77db-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f77db-124">Element</span></span>|<span data-ttu-id="f77db-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f77db-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f77db-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="f77db-126">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="f77db-127">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f77db-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f77db-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f77db-128">Remarks</span></span>  
 <span data-ttu-id="f77db-129">Bu koleksiyon, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanılacak hizmet sertifikalarını yapılandırmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f77db-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="f77db-130">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f77db-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="f77db-131">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="f77db-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="f77db-132">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f77db-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="f77db-133">Daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Istemcisi](../../../wcf/feature-details/how-to-create-a-federated-client.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f77db-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f77db-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="f77db-134">Example</span></span>  
 <span data-ttu-id="f77db-135">Aşağıdaki örnek, etki alanı adı `http://www.contoso.com` http protokolünün üzerinde olan uç noktalarla iletişim kurarken İstemcinin kullanacağı bir hizmet sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f77db-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="f77db-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f77db-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="f77db-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="f77db-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f77db-138">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="f77db-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="f77db-139">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="f77db-139">\<add></span></span>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="f77db-140">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f77db-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="f77db-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f77db-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
