---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 834853d8a922148d2810cd391a64a281f2f9ae3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="39e01-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="39e01-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="39e01-103">Bir hizmet için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e01-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="39e01-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="39e01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39e01-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="39e01-105">\<behaviors></span></span>  
<span data-ttu-id="39e01-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="39e01-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="39e01-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="39e01-107">\<behavior></span></span>  
<span data-ttu-id="39e01-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="39e01-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e01-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39e01-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39e01-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39e01-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39e01-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39e01-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39e01-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39e01-112">Attributes</span></span>  
  
|<span data-ttu-id="39e01-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39e01-113">Attribute</span></span>|<span data-ttu-id="39e01-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39e01-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="39e01-115">Etkileşimli bir kullanıcı çalışma zamanında istemci kimlik bilgilerini seçme dahil olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="39e01-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="39e01-116">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="39e01-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="39e01-117">Bu yapılandırma öğesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="39e01-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39e01-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39e01-118">Child Elements</span></span>  
  
|<span data-ttu-id="39e01-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="39e01-119">Element</span></span>|<span data-ttu-id="39e01-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39e01-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39e01-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="39e01-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="39e01-122">Hizmeti için istemci kimlik doğrulaması için kullanılan sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e01-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="39e01-123">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="39e01-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="39e01-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="39e01-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="39e01-125">Hizmeti için istemci kimlik doğrulaması için kullanılan bir Özet belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e01-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="39e01-126">Bu öğe türünde <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="39e01-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="39e01-127">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="39e01-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="39e01-128">İçin bir güvenli belirteç hizmeti (STS) istemci kimlik doğrulaması için kullanılan özel bir belirteç türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e01-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="39e01-129">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="39e01-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="39e01-130">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="39e01-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="39e01-131">Geçerli bir eş kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e01-131">Specifies a current peer credential.</span></span> <span data-ttu-id="39e01-132">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="39e01-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="39e01-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="39e01-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="39e01-134">İstemci hizmete kimlik doğrulaması için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="39e01-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="39e01-135">Bu sertifika, sağlanan-bant hizmetinden istemciye olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39e01-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="39e01-136">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="39e01-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="39e01-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="39e01-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="39e01-138">Windows kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e01-138">Specifies a Windows credential.</span></span> <span data-ttu-id="39e01-139">Kimlik bilgisi geçerli iş parçacığının varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="39e01-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="39e01-140">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="39e01-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39e01-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39e01-141">Parent Elements</span></span>  
  
|<span data-ttu-id="39e01-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="39e01-142">Element</span></span>|<span data-ttu-id="39e01-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39e01-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39e01-144">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="39e01-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="39e01-145">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e01-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39e01-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39e01-146">Remarks</span></span>  
 <span data-ttu-id="39e01-147">İstemci kimlik bilgileri, karşılıklı kimlik doğrulaması gerekli olduğu durumlarda Hizmetleri için istemci kimlik doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39e01-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="39e01-148">Bu yapılandırma bölümü de senaryolar için hizmet sertifikaları belirtmek için İstemci Hizmeti'ne hizmetin sertifikayla iletileri burada güvenlik altına almanız gerekir kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39e01-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e01-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39e01-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="39e01-150">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="39e01-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="39e01-151">İstemcilerinin güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="39e01-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
