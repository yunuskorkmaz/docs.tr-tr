---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739041"
---
# \<discoveryClient>
<span data-ttu-id="281a2-101">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan özel bir bağlama oluşturmak için bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="281a2-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="281a2-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="281a2-102">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="281a2-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="281a2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="281a2-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="281a2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="281a2-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="281a2-105">Attributes</span></span>  
  
|<span data-ttu-id="281a2-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="281a2-106">Attribute</span></span>|<span data-ttu-id="281a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="281a2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="281a2-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="281a2-108">discoveryEndpoint</span></span>|<span data-ttu-id="281a2-109">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="281a2-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="281a2-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="281a2-110">Child Elements</span></span>  
  
|<span data-ttu-id="281a2-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="281a2-111">Element</span></span>|<span data-ttu-id="281a2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="281a2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="281a2-113">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="281a2-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="281a2-114">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="281a2-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="281a2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="281a2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="281a2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="281a2-116">Element</span></span>|<span data-ttu-id="281a2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="281a2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="281a2-118">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="281a2-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="281a2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="281a2-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
