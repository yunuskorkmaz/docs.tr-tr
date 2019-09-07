---
title: <serviceCertificate><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399680"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="4ad6e-102">\<ServiceCertificate > \<ClientCredentials > öğesi</span><span class="sxs-lookup"><span data-stu-id="4ad6e-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="4ad6e-103">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
<span data-ttu-id="4ad6e-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4ad6e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4ad6e-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4ad6e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4ad6e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4ad6e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="4ad6e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4ad6e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="4ad6e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4ad6e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="4ad6e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="4ad6e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="4ad6e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="4ad6e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad6e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ad6e-111">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ad6e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ad6e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4ad6e-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ad6e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ad6e-114">Attributes</span></span>  
 <span data-ttu-id="4ad6e-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ad6e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ad6e-116">Child Elements</span></span>  
  
|<span data-ttu-id="4ad6e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ad6e-117">Element</span></span>|<span data-ttu-id="4ad6e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ad6e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad6e-119">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="4ad6e-119">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="4ad6e-120">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-120">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="4ad6e-121">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="4ad6e-121">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="4ad6e-122">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-122">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="4ad6e-123">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-123">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="4ad6e-124">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="4ad6e-124">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="4ad6e-125">İstemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-125">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ad6e-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ad6e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="4ad6e-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ad6e-127">Element</span></span>|<span data-ttu-id="4ad6e-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ad6e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad6e-129">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="4ad6e-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="4ad6e-130">İstemci tarafından bir hizmette kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-130">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad6e-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ad6e-131">Remarks</span></span>  
 <span data-ttu-id="4ad6e-132">Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanılarak hizmet tarafından sunulan sertifikayı doğrulamak için istemci tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-132">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="4ad6e-133">Ayrıca, istemcide ileti güvenliği kullanılarak iletileri şifrelemek için kullanılmak üzere açıkça yapılandırılmış hizmet için bir sertifika içerir.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-133">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="4ad6e-134">`serviceCertificate` Öğesinin öznitelikleri, [ \<ClientCertificate >](clientcertificate-of-clientcredentials-element.md)öznitelikleriyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-134">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad6e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ad6e-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="4ad6e-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="4ad6e-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="4ad6e-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4ad6e-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="4ad6e-138">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="4ad6e-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4ad6e-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4ad6e-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
