---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: e9723aed1aa8fbcbf5c4e84080c0ba991ea3fd60
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746013"
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="a0431-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="a0431-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="a0431-103">Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="a0431-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="a0431-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a0431-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a0431-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a0431-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0431-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0431-106">Syntax</span></span>  
  
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
              <add name="String" namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0431-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0431-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a0431-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0431-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0431-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0431-109">Attributes</span></span>  
  
|<span data-ttu-id="a0431-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0431-110">Attribute</span></span>|<span data-ttu-id="a0431-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0431-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0431-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="a0431-112">discoveryEndpoint</span></span>|<span data-ttu-id="a0431-113">Otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlayan bulma uç noktanın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="a0431-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0431-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0431-114">Child Elements</span></span>  
  
|<span data-ttu-id="a0431-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0431-115">Element</span></span>|<span data-ttu-id="a0431-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0431-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0431-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a0431-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="a0431-118">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0431-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="a0431-119">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="a0431-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0431-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0431-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a0431-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0431-121">Element</span></span>|<span data-ttu-id="a0431-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0431-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0431-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a0431-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="a0431-124">Uygulama uç noktası adresi çalışma zamanında dinamik olarak bulabilirsiniz bir istemci program olarak çalışmasını etkinleştirmek için bilgileri içeren standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a0431-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0431-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0431-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
