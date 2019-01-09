---
title: '&lt;servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: a22a905744980d0b370023e6236734a9bb0d6357
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150649"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="3f6bb-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="3f6bb-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="3f6bb-103">Bir hizmet tarafından hizmet asıl adı (SPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="3f6bb-104">SPN hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3f6bb-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="3f6bb-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="3f6bb-105">\<identity></span></span>  
<span data-ttu-id="3f6bb-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="3f6bb-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6bb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f6bb-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f6bb-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f6bb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3f6bb-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f6bb-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f6bb-110">Attributes</span></span>  
  
|<span data-ttu-id="3f6bb-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3f6bb-111">Attribute</span></span>|<span data-ttu-id="3f6bb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f6bb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f6bb-113">value</span><span class="sxs-lookup"><span data-stu-id="3f6bb-113">value</span></span>|<span data-ttu-id="3f6bb-114">Adı, bir istemci bir hizmet örneğini benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="3f6bb-115">Bir ormandaki bilgisayarlarda bir hizmet birden çok örneğini yükleyin, her örnek kendi SPN olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="3f6bb-116">İstemci kimlik doğrulaması için kullanıyor olabileceğiniz birden fazla adı varsa, verili hizmet örneğine birden çok SPN'ler olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f6bb-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f6bb-117">Child Elements</span></span>  
 <span data-ttu-id="3f6bb-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f6bb-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f6bb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3f6bb-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f6bb-120">Element</span></span>|<span data-ttu-id="3f6bb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f6bb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f6bb-122">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="3f6bb-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3f6bb-123">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f6bb-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f6bb-124">Remarks</span></span>  
 <span data-ttu-id="3f6bb-125">Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken SPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6bb-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f6bb-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="3f6bb-127">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="3f6bb-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="3f6bb-128">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="3f6bb-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
