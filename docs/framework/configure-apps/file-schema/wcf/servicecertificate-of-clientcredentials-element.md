---
title: '&lt;clientCredentials&gt; Öğesi &lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 82fb39f15ea0dbf38d9c9b41d7fbdd50daebb823
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151988"
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="02256-102">&lt;clientCredentials&gt; Öğesi &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="02256-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="02256-103">İstemci bir hizmete kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="02256-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="02256-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="02256-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="02256-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="02256-105">\<behaviors></span></span>  
<span data-ttu-id="02256-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="02256-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="02256-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="02256-107">\<behavior></span></span>  
<span data-ttu-id="02256-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="02256-108">\<clientCredentials></span></span>  
<span data-ttu-id="02256-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="02256-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02256-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02256-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02256-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02256-111">Attributes and Elements</span></span>  
 <span data-ttu-id="02256-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02256-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02256-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02256-113">Attributes</span></span>  
 <span data-ttu-id="02256-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="02256-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02256-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02256-115">Child Elements</span></span>  
  
|<span data-ttu-id="02256-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="02256-116">Element</span></span>|<span data-ttu-id="02256-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02256-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02256-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="02256-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="02256-119">Kullanılacak olan X.509 sertifikasını belirtir, STS veya hizmetin sağlamadığı anlaşma protokolü aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="02256-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="02256-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="02256-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="02256-121">Belirli hizmetler (kapsamlı kimlik doğrulaması için) tarafından sağlanan X.509 Sertifika koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="02256-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="02256-122">Bu koleksiyon, genellikle hizmet sertifikaları için güvenlik belirteci hizmetlerine federe bir senaryoda belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02256-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="02256-123">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="02256-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="02256-124">Bir istemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02256-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02256-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02256-125">Parent Elements</span></span>  
  
|<span data-ttu-id="02256-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="02256-126">Element</span></span>|<span data-ttu-id="02256-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02256-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02256-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="02256-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="02256-129">Bir hizmete kendi kimliğini doğrulamak için istemci tarafından kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02256-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02256-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02256-130">Remarks</span></span>  
 <span data-ttu-id="02256-131">Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanarak hizmeti tarafından sunulan sertifika doğrulamak için istemci tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="02256-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="02256-132">Ayrıca, hizmet ileti güveliği kullanarak iletileri şifrelemek için kullanılacak istemci üzerinde açıkça yapılandırılmış hizmeti için herhangi bir sertifika içerir.</span><span class="sxs-lookup"><span data-stu-id="02256-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="02256-133">Özniteliklerini `serviceCertificate` öğesi için öznitelikleri aynı [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="02256-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02256-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02256-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="02256-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="02256-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="02256-136">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="02256-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="02256-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="02256-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="02256-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="02256-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
