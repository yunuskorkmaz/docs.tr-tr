---
title: <serviceCertificate><clientCredentials>öğesinin
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399680"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="be763-102">\<serviceCertificate>\<clientCredentials>öğesinin</span><span class="sxs-lookup"><span data-stu-id="be763-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="be763-103">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="be763-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="be763-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be763-104">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be763-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be763-105">Attributes and Elements</span></span>  
 <span data-ttu-id="be763-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be763-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be763-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be763-107">Attributes</span></span>  
 <span data-ttu-id="be763-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="be763-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="be763-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be763-109">Child Elements</span></span>  
  
|<span data-ttu-id="be763-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="be763-110">Element</span></span>|<span data-ttu-id="be763-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be763-111">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="be763-112">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="be763-112">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="be763-113">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be763-113">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="be763-114">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be763-114">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="be763-115">İstemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be763-115">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be763-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be763-116">Parent Elements</span></span>  
  
|<span data-ttu-id="be763-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="be763-117">Element</span></span>|<span data-ttu-id="be763-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be763-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="be763-119">İstemci tarafından bir hizmette kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be763-119">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be763-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be763-120">Remarks</span></span>  
 <span data-ttu-id="be763-121">Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanılarak hizmet tarafından sunulan sertifikayı doğrulamak için istemci tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="be763-121">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="be763-122">Ayrıca, istemcide ileti güvenliği kullanılarak iletileri şifrelemek için kullanılmak üzere açıkça yapılandırılmış hizmet için bir sertifika içerir.</span><span class="sxs-lookup"><span data-stu-id="be763-122">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="be763-123">`serviceCertificate`Öğesinin öznitelikleri ile aynıdır [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="be763-123">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be763-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be763-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="be763-125">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="be763-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="be763-126">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="be763-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="be763-127">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="be763-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="be763-128">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="be763-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
