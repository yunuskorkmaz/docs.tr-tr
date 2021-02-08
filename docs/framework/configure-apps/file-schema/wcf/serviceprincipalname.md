---
description: 'Hakkında daha fazla bilgi edinin: <servicePrincipalName>'
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 494368f1f47f10aac8009e47a9219966c87e5eda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786700"
---
# \<servicePrincipalName>

<span data-ttu-id="f26b5-102">Hizmet sorumlusu adına (SPN) göre bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f26b5-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="f26b5-103">SPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f26b5-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="f26b5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f26b5-104">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f26b5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f26b5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f26b5-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="f26b5-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f26b5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f26b5-107">Attributes</span></span>  
  
|<span data-ttu-id="f26b5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f26b5-108">Attribute</span></span>|<span data-ttu-id="f26b5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f26b5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f26b5-110">değer</span><span class="sxs-lookup"><span data-stu-id="f26b5-110">value</span></span>|<span data-ttu-id="f26b5-111">İstemcinin bir hizmetin örneğini benzersiz olarak tanımladığı ad.</span><span class="sxs-lookup"><span data-stu-id="f26b5-111">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="f26b5-112">Bir ormanın tamamında bulunan bilgisayarlara bir hizmetin birden çok örneğini yüklerseniz, her örneğin kendi SPN 'si olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f26b5-112">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="f26b5-113">İstemcilerin kimlik doğrulaması için kullanabileceği birden çok ad varsa, belirli bir hizmet örneği birden çok SPN içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f26b5-113">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f26b5-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f26b5-114">Child Elements</span></span>  

 <span data-ttu-id="f26b5-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="f26b5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f26b5-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f26b5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f26b5-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="f26b5-117">Element</span></span>|<span data-ttu-id="f26b5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f26b5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="f26b5-119">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f26b5-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f26b5-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f26b5-120">Remarks</span></span>  

 <span data-ttu-id="f26b5-121">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken SPN 'YI kullanır.</span><span class="sxs-lookup"><span data-stu-id="f26b5-121">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26b5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f26b5-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="f26b5-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="f26b5-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
