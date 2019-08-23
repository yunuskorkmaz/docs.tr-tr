---
title: <serviceCertificate><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936335"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="04c03-102">\<ServiceCertificate > \<ClientCredentials > öğesi</span><span class="sxs-lookup"><span data-stu-id="04c03-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="04c03-103">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c03-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="04c03-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04c03-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="04c03-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="04c03-105">\<behaviors></span></span>  
<span data-ttu-id="04c03-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="04c03-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="04c03-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="04c03-107">\<behavior></span></span>  
<span data-ttu-id="04c03-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="04c03-108">\<clientCredentials></span></span>  
<span data-ttu-id="04c03-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="04c03-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04c03-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04c03-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04c03-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="04c03-111">Attributes and Elements</span></span>  
 <span data-ttu-id="04c03-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="04c03-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04c03-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="04c03-113">Attributes</span></span>  
 <span data-ttu-id="04c03-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="04c03-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04c03-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="04c03-115">Child Elements</span></span>  
  
|<span data-ttu-id="04c03-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="04c03-116">Element</span></span>|<span data-ttu-id="04c03-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04c03-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04c03-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="04c03-118">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="04c03-119">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c03-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="04c03-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="04c03-120">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="04c03-121">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="04c03-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="04c03-122">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04c03-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="04c03-123">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="04c03-123">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="04c03-124">İstemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c03-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04c03-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="04c03-125">Parent Elements</span></span>  
  
|<span data-ttu-id="04c03-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="04c03-126">Element</span></span>|<span data-ttu-id="04c03-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04c03-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04c03-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="04c03-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="04c03-129">İstemci tarafından bir hizmette kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c03-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04c03-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04c03-130">Remarks</span></span>  
 <span data-ttu-id="04c03-131">Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanılarak hizmet tarafından sunulan sertifikayı doğrulamak için istemci tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c03-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="04c03-132">Ayrıca, istemcide ileti güvenliği kullanılarak iletileri şifrelemek için kullanılmak üzere açıkça yapılandırılmış hizmet için bir sertifika içerir.</span><span class="sxs-lookup"><span data-stu-id="04c03-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="04c03-133">`serviceCertificate` Öğesinin öznitelikleri, [ \<ClientCertificate >](clientcertificate-of-clientcredentials-element.md)öznitelikleriyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="04c03-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c03-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04c03-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="04c03-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="04c03-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="04c03-136">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="04c03-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="04c03-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="04c03-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="04c03-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="04c03-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
