---
title: <scopedCertificates> Öğesi
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399950"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="69317-102">\<scopedCertificates > öğesi</span><span class="sxs-lookup"><span data-stu-id="69317-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="69317-103">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="69317-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="69317-104">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69317-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
<span data-ttu-id="69317-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="69317-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="69317-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="69317-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="69317-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="69317-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="69317-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="69317-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="69317-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="69317-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="69317-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="69317-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="69317-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="69317-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="69317-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<scopedCertificates >**</span><span class="sxs-lookup"><span data-stu-id="69317-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69317-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69317-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69317-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="69317-114">Attributes and Elements</span></span>  
 <span data-ttu-id="69317-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69317-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69317-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="69317-116">Attributes</span></span>  
 <span data-ttu-id="69317-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="69317-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69317-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="69317-118">Child Elements</span></span>  
  
|<span data-ttu-id="69317-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="69317-119">Element</span></span>|<span data-ttu-id="69317-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69317-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69317-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="69317-121">\<add></span></span>](add-of-scopedcertificates-element.md)|<span data-ttu-id="69317-122">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="69317-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69317-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="69317-123">Parent Elements</span></span>  
  
|<span data-ttu-id="69317-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="69317-124">Element</span></span>|<span data-ttu-id="69317-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69317-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69317-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="69317-126">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="69317-127">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="69317-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69317-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69317-128">Remarks</span></span>  
 <span data-ttu-id="69317-129">Bu koleksiyon, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanılacak hizmet sertifikalarını yapılandırmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="69317-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="69317-130">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="69317-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="69317-131">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="69317-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="69317-132">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69317-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="69317-133">Daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Istemcisi](../../../wcf/feature-details/how-to-create-a-federated-client.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69317-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69317-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="69317-134">Example</span></span>  
 <span data-ttu-id="69317-135">Aşağıdaki örnek, etki alanı adı `http://www.contoso.com` http protokolünün üzerinde olan uç noktalarla iletişim kurarken İstemcinin kullanacağı bir hizmet sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="69317-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69317-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69317-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="69317-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="69317-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="69317-138">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="69317-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="69317-139">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="69317-139">\<add></span></span>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="69317-140">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="69317-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="69317-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="69317-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
