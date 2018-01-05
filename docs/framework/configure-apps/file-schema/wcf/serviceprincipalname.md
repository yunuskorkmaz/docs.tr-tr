---
title: '&lt;servicePrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f9b4ec506097cf010af78b3504def08102e0774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="ddbaa-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="ddbaa-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="ddbaa-103">Bir hizmet tarafından kendi hizmet asıl adı (SPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="ddbaa-104">SPN ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ddbaa-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="ddbaa-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="ddbaa-105">\<identity></span></span>  
<span data-ttu-id="ddbaa-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="ddbaa-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbaa-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddbaa-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddbaa-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddbaa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ddbaa-109">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="ddbaa-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddbaa-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ddbaa-110">Attributes</span></span>  
  
|<span data-ttu-id="ddbaa-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ddbaa-111">Attribute</span></span>|<span data-ttu-id="ddbaa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddbaa-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddbaa-113">value</span><span class="sxs-lookup"><span data-stu-id="ddbaa-113">value</span></span>|<span data-ttu-id="ddbaa-114">Bir istemci bir hizmet örneğini benzersiz olarak tanımlayan adı.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="ddbaa-115">Bir orman genelinde bilgisayarlarda bir hizmet birden çok örneğini yükleyin, her örneğin kendi SPN olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="ddbaa-116">İstemciler için kimlik doğrulaması kullanabilirler birden fazla adı varsa verili hizmet örneği birden çok SPN'ler olabilir.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddbaa-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddbaa-117">Child Elements</span></span>  
 <span data-ttu-id="ddbaa-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ddbaa-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddbaa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ddbaa-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddbaa-120">Element</span></span>|<span data-ttu-id="ddbaa-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddbaa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddbaa-122">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="ddbaa-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="ddbaa-123">İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddbaa-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ddbaa-124">Remarks</span></span>  
 <span data-ttu-id="ddbaa-125">Güvenli [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Bu kimliğe sahip bir uç nokta bağlandığı istemcisi, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken SPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddbaa-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="ddbaa-127">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ddbaa-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="ddbaa-128">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="ddbaa-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
