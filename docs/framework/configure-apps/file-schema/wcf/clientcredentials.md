---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 6094006df24ee824c419a783ab29d7604757577c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201466"
---
# \<clientCredentials>

<span data-ttu-id="9bf8a-101">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="9bf8a-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bf8a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bf8a-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bf8a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9bf8a-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bf8a-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9bf8a-105">Attributes</span></span>  
  
|<span data-ttu-id="9bf8a-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9bf8a-106">Attribute</span></span>|<span data-ttu-id="9bf8a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf8a-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="9bf8a-108">Etkileşimli bir kullanıcının çalışma zamanında istemci kimlik bilgilerini seçmeye dahil edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="9bf8a-109">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="9bf8a-110">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bf8a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bf8a-111">Child Elements</span></span>  
  
|<span data-ttu-id="9bf8a-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bf8a-112">Element</span></span>|<span data-ttu-id="9bf8a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf8a-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="9bf8a-114">Hizmetin istemcinin kimliğini doğrulamak için kullanılan sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="9bf8a-115">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="9bf8a-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="9bf8a-116">İstemci kimliğini hizmette doğrulamak için kullanılan bir Özet belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="9bf8a-117">Bu öğe türündedir <xref:System.ServiceModel.Configuration.HttpDigestClientElement> .</span><span class="sxs-lookup"><span data-stu-id="9bf8a-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="9bf8a-118">İstemcinin kimliğini bir güvenli belirteç hizmeti 'ne (STS) doğrulamak için kullanılan özel bir belirteç türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="9bf8a-119">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> .</span><span class="sxs-lookup"><span data-stu-id="9bf8a-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="9bf8a-120">Geçerli bir eş kimlik bilgisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-120">Specifies a current peer credential.</span></span> <span data-ttu-id="9bf8a-121">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="9bf8a-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="9bf8a-122">İstemciye hizmetin kimliğini doğrulamak için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="9bf8a-123">Bu sertifika, hizmetten istemciye bant dışı verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="9bf8a-124">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="9bf8a-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="9bf8a-125">Windows kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-125">Specifies a Windows credential.</span></span> <span data-ttu-id="9bf8a-126">Varsayılan değer, geçerli iş parçacığının kimlik bilgileridir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="9bf8a-127">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsClientElement> .</span><span class="sxs-lookup"><span data-stu-id="9bf8a-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bf8a-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bf8a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9bf8a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bf8a-129">Element</span></span>|<span data-ttu-id="9bf8a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf8a-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9bf8a-131">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bf8a-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bf8a-132">Remarks</span></span>  

 <span data-ttu-id="9bf8a-133">İstemci kimlik bilgileri, karşılıklı kimlik doğrulamanın gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="9bf8a-134">Bu yapılandırma bölümü, istemcinin hizmet sertifikası ile iletileri güvenli hale getirmek zorunda olduğu senaryolara yönelik hizmet sertifikalarını belirtmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf8a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="9bf8a-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="9bf8a-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9bf8a-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9bf8a-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
