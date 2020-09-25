---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: af9cf127652f1e12ae57948f9b4a6a26285af793
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192262"
---
# \<discoveryClient>

<span data-ttu-id="51f1d-101">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan özel bir bağlama oluşturmak için bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="51f1d-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="51f1d-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="51f1d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51f1d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="51f1d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="51f1d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51f1d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51f1d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="51f1d-105">Attributes</span></span>  
  
|<span data-ttu-id="51f1d-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="51f1d-106">Attribute</span></span>|<span data-ttu-id="51f1d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51f1d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51f1d-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="51f1d-108">discoveryEndpoint</span></span>|<span data-ttu-id="51f1d-109">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="51f1d-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51f1d-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="51f1d-110">Child Elements</span></span>  
  
|<span data-ttu-id="51f1d-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="51f1d-111">Element</span></span>|<span data-ttu-id="51f1d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51f1d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="51f1d-113">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="51f1d-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="51f1d-114">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f1d-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51f1d-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="51f1d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="51f1d-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="51f1d-116">Element</span></span>|<span data-ttu-id="51f1d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51f1d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="51f1d-118">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51f1d-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51f1d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51f1d-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
