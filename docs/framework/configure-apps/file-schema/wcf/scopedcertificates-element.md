---
description: 'Daha fazla bilgi edinin: <scopedCertificates> öğesi'
title: <scopedCertificates> Öğesi
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 7aa108031831539396e8f737a214982655dd6bb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683339"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="32b89-103">\<scopedCertificates> Öğesi</span><span class="sxs-lookup"><span data-stu-id="32b89-103">\<scopedCertificates> Element</span></span>

<span data-ttu-id="32b89-104">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="32b89-104">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="32b89-105">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32b89-105">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="32b89-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="32b89-106">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32b89-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32b89-107">Attributes and Elements</span></span>  

 <span data-ttu-id="32b89-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32b89-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32b89-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32b89-109">Attributes</span></span>  

 <span data-ttu-id="32b89-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="32b89-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32b89-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32b89-111">Child Elements</span></span>  
  
|<span data-ttu-id="32b89-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="32b89-112">Element</span></span>|<span data-ttu-id="32b89-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b89-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="32b89-114">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="32b89-114">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32b89-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32b89-115">Parent Elements</span></span>  
  
|<span data-ttu-id="32b89-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="32b89-116">Element</span></span>|<span data-ttu-id="32b89-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b89-117">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="32b89-118">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="32b89-118">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32b89-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32b89-119">Remarks</span></span>  

 <span data-ttu-id="32b89-120">Bu koleksiyon, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanılacak hizmet sertifikalarını yapılandırmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="32b89-120">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="32b89-121">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="32b89-121">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="32b89-122">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="32b89-122">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="32b89-123">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32b89-123">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="32b89-124">Daha fazla bilgi için bkz. [nasıl yapılır: federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)konusunun "kapsamlı sertifikalar" bölümü.</span><span class="sxs-lookup"><span data-stu-id="32b89-124">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b89-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="32b89-125">Example</span></span>  

 <span data-ttu-id="32b89-126">Aşağıdaki örnek, etki alanı adı HTTP protokolünün üzerinde olan uç noktalarla iletişim kurarken İstemcinin kullanacağı bir hizmet sertifikasını belirtir `http://www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="32b89-126">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32b89-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32b89-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="32b89-128">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="32b89-128">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="32b89-129">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="32b89-129">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="32b89-130">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="32b89-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="32b89-131">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="32b89-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
