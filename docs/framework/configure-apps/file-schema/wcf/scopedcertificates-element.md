---
title: '&lt;scopedCertificates&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: d95e608fa9b94086dac72341eb599f258dae6097
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltscopedcertificatesgt-element"></a><span data-ttu-id="84c7d-102">&lt;scopedCertificates&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="84c7d-102">&lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="84c7d-103">X.509 sertifikaları (kimlik doğrulaması için kapsamlı) belirli hizmetleri tarafından sağlanan bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84c7d-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="84c7d-104">Bu koleksiyon, genellikle bir Federasyon senaryosunda için güvenlik belirteci Hizmetleri hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84c7d-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="84c7d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="84c7d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="84c7d-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="84c7d-106">\<behaviors></span></span>  
<span data-ttu-id="84c7d-107">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="84c7d-107">endpointBehaviors section</span></span>  
<span data-ttu-id="84c7d-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="84c7d-108">\<behavior></span></span>  
<span data-ttu-id="84c7d-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="84c7d-109">\<clientCredentials></span></span>  
<span data-ttu-id="84c7d-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="84c7d-110">\<serviceCertificate></span></span>  
<span data-ttu-id="84c7d-111">\<scopedCertificates > öğesi</span><span class="sxs-lookup"><span data-stu-id="84c7d-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="84c7d-112">\<Ekle > öğesi için \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="84c7d-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c7d-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84c7d-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84c7d-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="84c7d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="84c7d-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84c7d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84c7d-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="84c7d-116">Attributes</span></span>  
 <span data-ttu-id="84c7d-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="84c7d-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84c7d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="84c7d-118">Child Elements</span></span>  
  
|<span data-ttu-id="84c7d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="84c7d-119">Element</span></span>|<span data-ttu-id="84c7d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84c7d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84c7d-121">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="84c7d-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="84c7d-122">Bir X.509 sertifikası kapsamlı sertifikaları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="84c7d-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84c7d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="84c7d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="84c7d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="84c7d-124">Element</span></span>|<span data-ttu-id="84c7d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84c7d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84c7d-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="84c7d-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="84c7d-127">İstemci bir hizmete kimlik doğrulanırken kullanılacak bir sertifika belirtir.</span><span class="sxs-lookup"><span data-stu-id="84c7d-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84c7d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84c7d-128">Remarks</span></span>  
 <span data-ttu-id="84c7d-129">Bu koleksiyon kurduğu hizmetinin URL'sini göre kullanmak için hizmet sertifikalarını yapılandırmak istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="84c7d-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="84c7d-130">Bu, özellikle bir istemci birden fazla hizmet için (son hizmet yanı sıra Ara güvenlik belirteci Hizmetleri) burada iletişim verilen belirteç senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="84c7d-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="84c7d-131">Bu sertifika, sertifika tabanlı ileti güvenliği kullanan bağlamaları için hizmet iletileri şifrelemek için kullanılan ve istemci yanıtlar imzalama hizmeti tarafından kullanılacak beklenen.</span><span class="sxs-lookup"><span data-stu-id="84c7d-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="84c7d-132">Bir bağlama hizmeti ve URL ScopedCertificates bulunan hizmet için belirli bir sertifika için bir sertifika gerektiriyorsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84c7d-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="84c7d-133">Daha fazla bilgi için "Sertifikalar kapsamlı" bölümüne bakın [nasıl yapılır: federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="84c7d-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84c7d-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="84c7d-134">Example</span></span>  
 <span data-ttu-id="84c7d-135">Aşağıdaki örnek etki alanı adı uç ile iletişim kurmasını olduğunda kullanılacak istemci için bir hizmet sertifikası belirtir http://www.contoso.com HTTP protokolü üzerinden.</span><span class="sxs-lookup"><span data-stu-id="84c7d-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is http://www.contoso.com over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84c7d-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84c7d-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="84c7d-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="84c7d-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="84c7d-138">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="84c7d-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="84c7d-139">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="84c7d-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 [<span data-ttu-id="84c7d-140">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="84c7d-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="84c7d-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="84c7d-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
