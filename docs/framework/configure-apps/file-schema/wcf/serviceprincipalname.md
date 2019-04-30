---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 75e95bcbaee229f19bdfdd119b548ed612f4ddaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758190"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="2ec88-101">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="2ec88-101">\<servicePrincipalName></span></span>
<span data-ttu-id="2ec88-102">Bir hizmet tarafından hizmet asıl adı (SPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ec88-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="2ec88-103">SPN hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2ec88-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="2ec88-104">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="2ec88-104">\<identity></span></span>  
<span data-ttu-id="2ec88-105">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="2ec88-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec88-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ec88-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ec88-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ec88-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2ec88-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ec88-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ec88-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2ec88-109">Attributes</span></span>  
  
|<span data-ttu-id="2ec88-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2ec88-110">Attribute</span></span>|<span data-ttu-id="2ec88-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ec88-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ec88-112">value</span><span class="sxs-lookup"><span data-stu-id="2ec88-112">value</span></span>|<span data-ttu-id="2ec88-113">Adı, bir istemci bir hizmet örneğini benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2ec88-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="2ec88-114">Bir ormandaki bilgisayarlarda bir hizmet birden çok örneğini yükleyin, her örnek kendi SPN olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ec88-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="2ec88-115">İstemci kimlik doğrulaması için kullanıyor olabileceğiniz birden fazla adı varsa, verili hizmet örneğine birden çok SPN'ler olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ec88-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ec88-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ec88-116">Child Elements</span></span>  
 <span data-ttu-id="2ec88-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="2ec88-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ec88-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ec88-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2ec88-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="2ec88-119">Element</span></span>|<span data-ttu-id="2ec88-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ec88-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ec88-121">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="2ec88-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2ec88-122">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ec88-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ec88-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ec88-123">Remarks</span></span>  
 <span data-ttu-id="2ec88-124">Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken SPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ec88-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec88-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ec88-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="2ec88-126">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="2ec88-126">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2ec88-127">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="2ec88-127">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
