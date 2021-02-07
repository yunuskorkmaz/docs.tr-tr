---
description: 'Hakkında daha fazla bilgi edinin: <discoveryClient>'
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: d04eee828bb16e56a65c39059665feb745f3006a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754400"
---
# \<discoveryClient>

<span data-ttu-id="ed3ec-102">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan özel bir bağlama oluşturmak için bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ed3ec-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="ed3ec-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ed3ec-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed3ec-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed3ec-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ed3ec-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed3ec-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed3ec-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed3ec-106">Attributes</span></span>  
  
|<span data-ttu-id="ed3ec-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed3ec-107">Attribute</span></span>|<span data-ttu-id="ed3ec-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3ec-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed3ec-109">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="ed3ec-109">discoveryEndpoint</span></span>|<span data-ttu-id="ed3ec-110">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ed3ec-110">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed3ec-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed3ec-111">Child Elements</span></span>  
  
|<span data-ttu-id="ed3ec-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed3ec-112">Element</span></span>|<span data-ttu-id="ed3ec-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3ec-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="ed3ec-114">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ed3ec-114">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ed3ec-115">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ec-115">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed3ec-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed3ec-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ed3ec-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed3ec-117">Element</span></span>|<span data-ttu-id="ed3ec-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3ec-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="ed3ec-119">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed3ec-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed3ec-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed3ec-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
