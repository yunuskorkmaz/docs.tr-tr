---
description: 'Hakkında daha fazla bilgi edinin: <serviceCertificate> <clientCredentials> öğe'
title: <serviceCertificate><clientCredentials>öğesinin
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 5503c1a60b2d37f4f9359a2f49c019c37df71619
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682910"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="0669c-103">\<serviceCertificate>\<clientCredentials>öğesinin</span><span class="sxs-lookup"><span data-stu-id="0669c-103">\<serviceCertificate> of \<clientCredentials> Element</span></span>

<span data-ttu-id="0669c-104">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0669c-104">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="0669c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0669c-105">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0669c-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0669c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0669c-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0669c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0669c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0669c-108">Attributes</span></span>  

 <span data-ttu-id="0669c-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="0669c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0669c-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0669c-110">Child Elements</span></span>  
  
|<span data-ttu-id="0669c-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="0669c-111">Element</span></span>|<span data-ttu-id="0669c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0669c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="0669c-113">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="0669c-113">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="0669c-114">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0669c-114">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="0669c-115">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0669c-115">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="0669c-116">İstemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0669c-116">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0669c-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0669c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0669c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0669c-118">Element</span></span>|<span data-ttu-id="0669c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0669c-119">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="0669c-120">İstemci tarafından bir hizmette kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0669c-120">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0669c-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0669c-121">Remarks</span></span>  

 <span data-ttu-id="0669c-122">Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanılarak hizmet tarafından sunulan sertifikayı doğrulamak için istemci tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="0669c-122">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="0669c-123">Ayrıca, istemcide ileti güvenliği kullanılarak iletileri şifrelemek için kullanılmak üzere açıkça yapılandırılmış hizmet için bir sertifika içerir.</span><span class="sxs-lookup"><span data-stu-id="0669c-123">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="0669c-124">`serviceCertificate`Öğesinin öznitelikleri ile aynıdır [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0669c-124">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0669c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0669c-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="0669c-126">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="0669c-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0669c-127">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0669c-127">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0669c-128">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="0669c-128">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="0669c-129">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0669c-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
