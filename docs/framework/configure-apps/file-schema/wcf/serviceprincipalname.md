---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855000"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="b36ff-101">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="b36ff-101">\<servicePrincipalName></span></span>
<span data-ttu-id="b36ff-102">Hizmet sorumlusu adına (SPN) göre bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b36ff-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="b36ff-103">SPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b36ff-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="b36ff-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b36ff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b36ff-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b36ff-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b36ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="b36ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="b36ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<uç nokta >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="b36ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="b36ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kimlik >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="b36ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="b36ff-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<servicePrincipalName >**</span><span class="sxs-lookup"><span data-stu-id="b36ff-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b36ff-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b36ff-110">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b36ff-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b36ff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b36ff-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="b36ff-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b36ff-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b36ff-113">Attributes</span></span>  
  
|<span data-ttu-id="b36ff-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b36ff-114">Attribute</span></span>|<span data-ttu-id="b36ff-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36ff-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b36ff-116">value</span><span class="sxs-lookup"><span data-stu-id="b36ff-116">value</span></span>|<span data-ttu-id="b36ff-117">İstemcinin bir hizmetin örneğini benzersiz olarak tanımladığı ad.</span><span class="sxs-lookup"><span data-stu-id="b36ff-117">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="b36ff-118">Bir ormanın tamamında bulunan bilgisayarlara bir hizmetin birden çok örneğini yüklerseniz, her örneğin kendi SPN 'si olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b36ff-118">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="b36ff-119">İstemcilerin kimlik doğrulaması için kullanabileceği birden çok ad varsa, belirli bir hizmet örneği birden çok SPN içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b36ff-119">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b36ff-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b36ff-120">Child Elements</span></span>  
 <span data-ttu-id="b36ff-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b36ff-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b36ff-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b36ff-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b36ff-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="b36ff-123">Element</span></span>|<span data-ttu-id="b36ff-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36ff-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b36ff-125">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="b36ff-125">\<identity></span></span>](identity.md)|<span data-ttu-id="b36ff-126">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b36ff-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b36ff-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b36ff-127">Remarks</span></span>  
 <span data-ttu-id="b36ff-128">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken SPN 'YI kullanır.</span><span class="sxs-lookup"><span data-stu-id="b36ff-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36ff-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b36ff-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="b36ff-130">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="b36ff-130">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b36ff-131">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="b36ff-131">\<identity></span></span>](identity.md)
