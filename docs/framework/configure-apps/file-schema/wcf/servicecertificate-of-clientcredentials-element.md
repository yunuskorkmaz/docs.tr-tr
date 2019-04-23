---
title: <serviceCertificate> ' ın <clientCredentials> öğesi
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4fe196ef8737c7abde939e36c2bb7afd5a0d86b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145346"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="748cd-102">\<serviceCertificate >, \<clientCredentials > öğesi</span><span class="sxs-lookup"><span data-stu-id="748cd-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="748cd-103">İstemci bir hizmete kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="748cd-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="748cd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="748cd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="748cd-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="748cd-105">\<behaviors></span></span>  
<span data-ttu-id="748cd-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="748cd-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="748cd-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="748cd-107">\<behavior></span></span>  
<span data-ttu-id="748cd-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="748cd-108">\<clientCredentials></span></span>  
<span data-ttu-id="748cd-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="748cd-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748cd-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="748cd-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="748cd-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="748cd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="748cd-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="748cd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="748cd-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="748cd-113">Attributes</span></span>  
 <span data-ttu-id="748cd-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="748cd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="748cd-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="748cd-115">Child Elements</span></span>  
  
|<span data-ttu-id="748cd-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="748cd-116">Element</span></span>|<span data-ttu-id="748cd-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="748cd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="748cd-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="748cd-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="748cd-119">Kullanılacak olan X.509 sertifikasını belirtir, STS veya hizmetin sağlamadığı anlaşma protokolü aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="748cd-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="748cd-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="748cd-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="748cd-121">Belirli hizmetler (kapsamlı kimlik doğrulaması için) tarafından sağlanan X.509 Sertifika koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="748cd-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="748cd-122">Bu koleksiyon, genellikle hizmet sertifikaları için güvenlik belirteci hizmetlerine federe bir senaryoda belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="748cd-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="748cd-123">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="748cd-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="748cd-124">Bir istemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="748cd-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="748cd-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="748cd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="748cd-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="748cd-126">Element</span></span>|<span data-ttu-id="748cd-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="748cd-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="748cd-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="748cd-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="748cd-129">Bir hizmete kendi kimliğini doğrulamak için istemci tarafından kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="748cd-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="748cd-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="748cd-130">Remarks</span></span>  
 <span data-ttu-id="748cd-131">Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanarak hizmeti tarafından sunulan sertifika doğrulamak için istemci tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="748cd-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="748cd-132">Ayrıca, hizmet ileti güveliği kullanarak iletileri şifrelemek için kullanılacak istemci üzerinde açıkça yapılandırılmış hizmeti için herhangi bir sertifika içerir.</span><span class="sxs-lookup"><span data-stu-id="748cd-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="748cd-133">Özniteliklerini `serviceCertificate` öğesi için öznitelikleri aynı [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="748cd-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748cd-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="748cd-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="748cd-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="748cd-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="748cd-136">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="748cd-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="748cd-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="748cd-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="748cd-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="748cd-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
