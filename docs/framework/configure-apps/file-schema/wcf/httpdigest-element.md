---
title: '&lt;httpDigest&gt; Öğesi'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 75579a583b774896f43099d3cc30f1679b10a889
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="75232-102">&lt;httpDigest&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="75232-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="75232-103">Bir Özet belirten bir hizmet için istemci kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="75232-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="75232-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="75232-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="75232-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="75232-105">\<behaviors></span></span>  
<span data-ttu-id="75232-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="75232-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="75232-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="75232-107">\<behavior></span></span>  
<span data-ttu-id="75232-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="75232-108">\<clientCredentials></span></span>  
<span data-ttu-id="75232-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="75232-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75232-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75232-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75232-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75232-111">Attributes and Elements</span></span>  
 <span data-ttu-id="75232-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75232-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75232-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75232-113">Attributes</span></span>  
  
|<span data-ttu-id="75232-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75232-114">Attribute</span></span>|<span data-ttu-id="75232-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75232-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="75232-116">İstemci iletişim kuruyorsa kimliğe bürünme tercih sunucuya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="75232-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="75232-117">İstemcinin kimliğe bürünme modu sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="75232-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="75232-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="75232-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="75232-119">-Kimliği: Sunucunun kimliğini ve istemci ayrıcalıkların alabilir, ancak istemci alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="75232-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="75232-120">-Kimliğe bürünme: Sunucu istemcinin güvenlik bağlamı yerel sistemde kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="75232-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="75232-121">-Temsilci: Sunucu istemcinin güvenlik bağlamı uzak sistemlere kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="75232-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="75232-122">-Anonim: Sunucusu taklit veya istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="75232-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="75232-123">-Hiçbiri: Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="75232-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="75232-124">Varsayılan kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="75232-124">The default is Identification.</span></span> <span data-ttu-id="75232-125">Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="75232-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75232-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75232-126">Child Elements</span></span>  
 <span data-ttu-id="75232-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="75232-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75232-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75232-128">Parent Elements</span></span>  
  
|<span data-ttu-id="75232-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="75232-129">Element</span></span>|<span data-ttu-id="75232-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75232-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75232-131">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="75232-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="75232-132">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75232-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75232-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75232-133">Remarks</span></span>  
 <span data-ttu-id="75232-134">Bir Özet bir karma algoritma ve girişleri kümesi kullanarak belirlenen var.</span><span class="sxs-lookup"><span data-stu-id="75232-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="75232-135">Doğrulayıcı ve kimliği doğrulanmış bir algoritma kabul ediyorum ve girdi olarak kullanılan veri değişimi.</span><span class="sxs-lookup"><span data-stu-id="75232-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="75232-136">İstemci, karmayı hesaplar ve hizmete gönderin.</span><span class="sxs-lookup"><span data-stu-id="75232-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="75232-137">Hizmet ayrıca karmayı hesaplar ve değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="75232-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="75232-138">Bir eşleşme istemci doğrular.</span><span class="sxs-lookup"><span data-stu-id="75232-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="75232-139">Bu özellik, Windows ve Internet Information Services (IIS) üzerinde Active Directory ile etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="75232-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="75232-140">Daha fazla bilgi için bkz: [IIS 6.0 Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="75232-140">For more information, see [Digest Authentication in IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75232-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75232-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="75232-142">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="75232-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="75232-143">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="75232-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="75232-144">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="75232-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="75232-145">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="75232-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
