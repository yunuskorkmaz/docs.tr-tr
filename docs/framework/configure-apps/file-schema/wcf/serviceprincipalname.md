---
title: '&lt;servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 5d65b5956491e30066ece54a48374f1d7014552e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657612"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="4ac09-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="4ac09-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="4ac09-103">Bir hizmet tarafından hizmet asıl adı (SPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ac09-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="4ac09-104">SPN hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4ac09-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="4ac09-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="4ac09-105">\<identity></span></span>  
<span data-ttu-id="4ac09-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="4ac09-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac09-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ac09-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ac09-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ac09-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4ac09-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ac09-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ac09-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ac09-110">Attributes</span></span>  
  
|<span data-ttu-id="4ac09-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4ac09-111">Attribute</span></span>|<span data-ttu-id="4ac09-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ac09-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ac09-113">value</span><span class="sxs-lookup"><span data-stu-id="4ac09-113">value</span></span>|<span data-ttu-id="4ac09-114">Adı, bir istemci bir hizmet örneğini benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ac09-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="4ac09-115">Bir ormandaki bilgisayarlarda bir hizmet birden çok örneğini yükleyin, her örnek kendi SPN olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ac09-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="4ac09-116">İstemci kimlik doğrulaması için kullanıyor olabileceğiniz birden fazla adı varsa, verili hizmet örneğine birden çok SPN'ler olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ac09-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ac09-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ac09-117">Child Elements</span></span>  
 <span data-ttu-id="4ac09-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="4ac09-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ac09-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ac09-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4ac09-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ac09-120">Element</span></span>|<span data-ttu-id="4ac09-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ac09-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ac09-122">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="4ac09-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4ac09-123">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ac09-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ac09-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ac09-124">Remarks</span></span>  
 <span data-ttu-id="4ac09-125">Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken SPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ac09-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac09-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ac09-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="4ac09-127">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="4ac09-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4ac09-128">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="4ac09-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
