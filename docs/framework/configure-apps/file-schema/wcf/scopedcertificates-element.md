---
title: <scopedCertificates> Öğesi
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 73e78a6ca27ed45e1eadc7121987b75f79bc6aa5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145206"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="e55a2-102">\<scopedCertificates > öğesi</span><span class="sxs-lookup"><span data-stu-id="e55a2-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="e55a2-103">Belirli hizmetler (kapsamlı kimlik doğrulaması için) tarafından sağlanan X.509 Sertifika koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e55a2-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="e55a2-104">Bu koleksiyon, genellikle hizmet sertifikaları için güvenlik belirteci hizmetlerine federe bir senaryoda belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e55a2-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="e55a2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e55a2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e55a2-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="e55a2-106">\<behaviors></span></span>  
<span data-ttu-id="e55a2-107">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="e55a2-107">endpointBehaviors section</span></span>  
<span data-ttu-id="e55a2-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e55a2-108">\<behavior></span></span>  
<span data-ttu-id="e55a2-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e55a2-109">\<clientCredentials></span></span>  
<span data-ttu-id="e55a2-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e55a2-110">\<serviceCertificate></span></span>  
<span data-ttu-id="e55a2-111">\<scopedCertificates > öğesi</span><span class="sxs-lookup"><span data-stu-id="e55a2-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="e55a2-112">\<Ekle > öğesi için \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="e55a2-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55a2-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e55a2-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e55a2-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e55a2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e55a2-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e55a2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e55a2-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e55a2-116">Attributes</span></span>  
 <span data-ttu-id="e55a2-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="e55a2-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e55a2-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e55a2-118">Child Elements</span></span>  
  
|<span data-ttu-id="e55a2-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e55a2-119">Element</span></span>|<span data-ttu-id="e55a2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e55a2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e55a2-121">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="e55a2-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="e55a2-122">Kapsamlı sertifikalar koleksiyonuna bir X.509 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="e55a2-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e55a2-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e55a2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e55a2-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e55a2-124">Element</span></span>|<span data-ttu-id="e55a2-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e55a2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e55a2-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e55a2-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="e55a2-127">İstemci bir hizmete kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e55a2-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e55a2-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e55a2-128">Remarks</span></span>  
 <span data-ttu-id="e55a2-129">Bu koleksiyon, hizmet sertifikalarını kullanmak için yapılandırmak istemci kurduğu hizmet URL'sini temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="e55a2-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="e55a2-130">Bu, özellikle bir istemci birden çok hizmeti (uç hizmetinin yanı sıra Ara güvenlik belirteci hizmetlerine) burada iletişim verilen belirteç senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e55a2-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="e55a2-131">Bu sertifika, sertifika tabanlı ileti güvenliği kullanan bağlamaları için hizmet iletileri şifrelemek için kullanılır ve istemciye yanıt imzalama için hizmet tarafından kullanılmak üzere beklenir.</span><span class="sxs-lookup"><span data-stu-id="e55a2-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="e55a2-132">Bağlama, hizmet ve URL ScopedCertificates içinde bulunan hizmet için belirli bir sertifika için bir sertifika gerektiriyorsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e55a2-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="e55a2-133">Daha fazla bilgi için "Sertifikalar kapsamlı" bölümüne bakın. [nasıl yapılır: Federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="e55a2-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e55a2-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="e55a2-134">Example</span></span>  
 <span data-ttu-id="e55a2-135">Aşağıdaki örnek, bir hizmet uç noktaları ile iletişim kurulurken etki alanı adını kullanmak istemci sertifikası belirtir `http://www.contoso.com` HTTP protokolü üzerinden.</span><span class="sxs-lookup"><span data-stu-id="e55a2-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e55a2-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e55a2-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="e55a2-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="e55a2-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e55a2-138">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="e55a2-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e55a2-139">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="e55a2-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)
- [<span data-ttu-id="e55a2-140">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e55a2-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="e55a2-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e55a2-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
