---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936161"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="7c04a-101">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="7c04a-101">\<servicePrincipalName></span></span>
<span data-ttu-id="7c04a-102">Hizmet sorumlusu adına (SPN) göre bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c04a-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="7c04a-103">SPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7c04a-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="7c04a-104">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="7c04a-104">\<identity></span></span>  
<span data-ttu-id="7c04a-105">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="7c04a-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c04a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c04a-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c04a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c04a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7c04a-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="7c04a-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c04a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7c04a-109">Attributes</span></span>  
  
|<span data-ttu-id="7c04a-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7c04a-110">Attribute</span></span>|<span data-ttu-id="7c04a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c04a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c04a-112">value</span><span class="sxs-lookup"><span data-stu-id="7c04a-112">value</span></span>|<span data-ttu-id="7c04a-113">İstemcinin bir hizmetin örneğini benzersiz olarak tanımladığı ad.</span><span class="sxs-lookup"><span data-stu-id="7c04a-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="7c04a-114">Bir ormanın tamamında bulunan bilgisayarlara bir hizmetin birden çok örneğini yüklerseniz, her örneğin kendi SPN 'si olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c04a-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="7c04a-115">İstemcilerin kimlik doğrulaması için kullanabileceği birden çok ad varsa, belirli bir hizmet örneği birden çok SPN içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7c04a-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c04a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c04a-116">Child Elements</span></span>  
 <span data-ttu-id="7c04a-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7c04a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c04a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c04a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7c04a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c04a-119">Element</span></span>|<span data-ttu-id="7c04a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c04a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c04a-121">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="7c04a-121">\<identity></span></span>](identity.md)|<span data-ttu-id="7c04a-122">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c04a-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c04a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c04a-123">Remarks</span></span>  
 <span data-ttu-id="7c04a-124">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken SPN 'YI kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c04a-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c04a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c04a-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="7c04a-126">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="7c04a-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7c04a-127">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="7c04a-127">\<identity></span></span>](identity.md)
