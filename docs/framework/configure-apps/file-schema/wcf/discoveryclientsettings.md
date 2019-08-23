---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 2783796166d56be3d4983ab09a60d62491699fe3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925858"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="ecaec-101">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="ecaec-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="ecaec-102">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ecaec-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="ecaec-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ecaec-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ecaec-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ecaec-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecaec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecaec-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecaec-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecaec-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ecaec-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecaec-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecaec-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ecaec-108">Attributes</span></span>  
  
|<span data-ttu-id="ecaec-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ecaec-109">Attribute</span></span>|<span data-ttu-id="ecaec-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecaec-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecaec-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="ecaec-111">discoveryEndpoint</span></span>|<span data-ttu-id="ecaec-112">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ecaec-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecaec-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecaec-113">Child Elements</span></span>  
  
|<span data-ttu-id="ecaec-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecaec-114">Element</span></span>|<span data-ttu-id="ecaec-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecaec-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecaec-116">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ecaec-116">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ecaec-117">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ecaec-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ecaec-118">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaec-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecaec-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecaec-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ecaec-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecaec-120">Element</span></span>|<span data-ttu-id="ecaec-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecaec-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecaec-122">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ecaec-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ecaec-123">Bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ecaec-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecaec-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecaec-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
