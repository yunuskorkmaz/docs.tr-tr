---
description: 'Hakkında daha fazla bilgi edinin: <clientCredentials>'
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: b10e046f8e4994e367db69d5863e54a0bfa07db5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638814"
---
# \<clientCredentials>

<span data-ttu-id="7d425-102">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d425-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="7d425-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d425-103">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d425-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d425-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7d425-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d425-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d425-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d425-106">Attributes</span></span>  
  
|<span data-ttu-id="7d425-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d425-107">Attribute</span></span>|<span data-ttu-id="7d425-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d425-108">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="7d425-109">Etkileşimli bir kullanıcının çalışma zamanında istemci kimlik bilgilerini seçmeye dahil edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7d425-109">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="7d425-110">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="7d425-110">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="7d425-111">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7d425-111">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d425-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d425-112">Child Elements</span></span>  
  
|<span data-ttu-id="7d425-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d425-113">Element</span></span>|<span data-ttu-id="7d425-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d425-114">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="7d425-115">Hizmetin istemcinin kimliğini doğrulamak için kullanılan sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d425-115">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="7d425-116">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="7d425-116">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="7d425-117">İstemci kimliğini hizmette doğrulamak için kullanılan bir Özet belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d425-117">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="7d425-118">Bu öğe türündedir <xref:System.ServiceModel.Configuration.HttpDigestClientElement> .</span><span class="sxs-lookup"><span data-stu-id="7d425-118">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="7d425-119">İstemcinin kimliğini bir güvenli belirteç hizmeti 'ne (STS) doğrulamak için kullanılan özel bir belirteç türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d425-119">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="7d425-120">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> .</span><span class="sxs-lookup"><span data-stu-id="7d425-120">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="7d425-121">Geçerli bir eş kimlik bilgisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d425-121">Specifies a current peer credential.</span></span> <span data-ttu-id="7d425-122">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="7d425-122">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="7d425-123">İstemciye hizmetin kimliğini doğrulamak için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d425-123">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="7d425-124">Bu sertifika, hizmetten istemciye bant dışı verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d425-124">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="7d425-125">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="7d425-125">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="7d425-126">Windows kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d425-126">Specifies a Windows credential.</span></span> <span data-ttu-id="7d425-127">Varsayılan değer, geçerli iş parçacığının kimlik bilgileridir.</span><span class="sxs-lookup"><span data-stu-id="7d425-127">The default is the credential of the current thread.</span></span> <span data-ttu-id="7d425-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsClientElement> .</span><span class="sxs-lookup"><span data-stu-id="7d425-128">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d425-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d425-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7d425-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d425-130">Element</span></span>|<span data-ttu-id="7d425-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d425-131">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7d425-132">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d425-132">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d425-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d425-133">Remarks</span></span>  

 <span data-ttu-id="7d425-134">İstemci kimlik bilgileri, karşılıklı kimlik doğrulamanın gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d425-134">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="7d425-135">Bu yapılandırma bölümü, istemcinin hizmet sertifikası ile iletileri güvenli hale getirmek zorunda olduğu senaryolara yönelik hizmet sertifikalarını belirtmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d425-135">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d425-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d425-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="7d425-137">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="7d425-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7d425-138">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7d425-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
