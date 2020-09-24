---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 0d03844a58de5b4af93f276de75c88af6efed3f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153800"
---
# \<servicePrincipalName>

<span data-ttu-id="8de10-101">Hizmet sorumlusu adına (SPN) göre bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8de10-101">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="8de10-102">SPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8de10-102">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="8de10-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="8de10-103">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8de10-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8de10-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8de10-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="8de10-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8de10-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8de10-106">Attributes</span></span>  
  
|<span data-ttu-id="8de10-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8de10-107">Attribute</span></span>|<span data-ttu-id="8de10-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8de10-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8de10-109">değer</span><span class="sxs-lookup"><span data-stu-id="8de10-109">value</span></span>|<span data-ttu-id="8de10-110">İstemcinin bir hizmetin örneğini benzersiz olarak tanımladığı ad.</span><span class="sxs-lookup"><span data-stu-id="8de10-110">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="8de10-111">Bir ormanın tamamında bulunan bilgisayarlara bir hizmetin birden çok örneğini yüklerseniz, her örneğin kendi SPN 'si olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8de10-111">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="8de10-112">İstemcilerin kimlik doğrulaması için kullanabileceği birden çok ad varsa, belirli bir hizmet örneği birden çok SPN içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8de10-112">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8de10-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8de10-113">Child Elements</span></span>  

 <span data-ttu-id="8de10-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="8de10-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8de10-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8de10-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8de10-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="8de10-116">Element</span></span>|<span data-ttu-id="8de10-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8de10-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="8de10-118">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8de10-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8de10-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8de10-119">Remarks</span></span>  

 <span data-ttu-id="8de10-120">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken SPN 'YI kullanır.</span><span class="sxs-lookup"><span data-stu-id="8de10-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de10-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8de10-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="8de10-122">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="8de10-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
