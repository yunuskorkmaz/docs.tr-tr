---
title: "&lt;clientCredentials&gt; Öğesi &lt;serviceCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3fbb3ef0fddd287fa3feb30732b26c651ac0067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="95fb2-102">&lt;clientCredentials&gt; Öğesi &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="95fb2-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="95fb2-103">İstemci bir hizmete kimlik doğrulanırken kullanılacak bir sertifika belirtir.</span><span class="sxs-lookup"><span data-stu-id="95fb2-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="95fb2-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="95fb2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="95fb2-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="95fb2-105">\<behaviors></span></span>  
<span data-ttu-id="95fb2-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="95fb2-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="95fb2-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="95fb2-107">\<behavior></span></span>  
<span data-ttu-id="95fb2-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="95fb2-108">\<clientCredentials></span></span>  
<span data-ttu-id="95fb2-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="95fb2-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95fb2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95fb2-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95fb2-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95fb2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="95fb2-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95fb2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95fb2-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95fb2-113">Attributes</span></span>  
 <span data-ttu-id="95fb2-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="95fb2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="95fb2-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95fb2-115">Child Elements</span></span>  
  
|<span data-ttu-id="95fb2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="95fb2-116">Element</span></span>|<span data-ttu-id="95fb2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95fb2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95fb2-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="95fb2-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="95fb2-119">Kullanılacak bir X.509 sertifikası belirtir ne zaman bir hizmeti veya STS sağlamaz anlaşması protokolü aracılığıyla bir.</span><span class="sxs-lookup"><span data-stu-id="95fb2-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="95fb2-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="95fb2-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="95fb2-121">X.509 sertifikaları (kimlik doğrulaması için kapsamlı) belirli hizmetleri tarafından sağlanan bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="95fb2-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="95fb2-122">Bu koleksiyon, genellikle bir Federasyon senaryosunda için güvenlik belirteci Hizmetleri hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95fb2-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="95fb2-123">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="95fb2-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="95fb2-124">Bir istemci tarafından kullanılan hizmet sertifikalarını için kimlik doğrulama davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="95fb2-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95fb2-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95fb2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="95fb2-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="95fb2-126">Element</span></span>|<span data-ttu-id="95fb2-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95fb2-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95fb2-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="95fb2-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="95fb2-129">Bir hizmete kendi kimliğini doğrulamak için istemci tarafından kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="95fb2-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95fb2-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95fb2-130">Remarks</span></span>  
 <span data-ttu-id="95fb2-131">Bu yapılandırma öğesi SSL kimlik doğrulaması kullanarak hizmeti tarafından sunulan sertifika doğrulamak için istemci tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="95fb2-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="95fb2-132">Ayrıca, ileti güvenliği kullanarak hizmet iletileri şifrelemek için kullanılacak istemcide açıkça yapılandırılmış service için herhangi bir sertifikayı içerir.</span><span class="sxs-lookup"><span data-stu-id="95fb2-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="95fb2-133">Özniteliklerini `serviceCertificate` öğesi özniteliklerini için aynı [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="95fb2-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fb2-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95fb2-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="95fb2-135">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="95fb2-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="95fb2-136">İstemcilerinin güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="95fb2-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="95fb2-137">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="95fb2-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="95fb2-138">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="95fb2-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
