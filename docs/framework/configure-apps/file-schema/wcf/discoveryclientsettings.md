---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 6e3f273af807eb362f005fef63246013ecc88581
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192249"
---
# \<discoveryClientSettings>

<span data-ttu-id="5f5f7-101">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="5f5f7-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="5f5f7-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f5f7-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f5f7-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f5f7-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5f5f7-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f5f7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f5f7-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f5f7-105">Attributes</span></span>  
  
|<span data-ttu-id="5f5f7-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5f5f7-106">Attribute</span></span>|<span data-ttu-id="5f5f7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f5f7-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f5f7-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="5f5f7-108">discoveryEndpoint</span></span>|<span data-ttu-id="5f5f7-109">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5f5f7-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f5f7-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f5f7-110">Child Elements</span></span>  
  
|<span data-ttu-id="5f5f7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f5f7-111">Element</span></span>|<span data-ttu-id="5f5f7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f5f7-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="5f5f7-113">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="5f5f7-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="5f5f7-114">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f5f7-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f5f7-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f5f7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5f5f7-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f5f7-116">Element</span></span>|<span data-ttu-id="5f5f7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f5f7-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="5f5f7-118">Bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f5f7-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f5f7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f5f7-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
