---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 0b014a9d797ded61949a374486824ee3ebc34661
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136259"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="1c156-101">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="1c156-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="1c156-102">Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="1c156-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="1c156-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1c156-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c156-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1c156-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c156-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c156-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c156-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c156-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1c156-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c156-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c156-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c156-108">Attributes</span></span>  
  
|<span data-ttu-id="1c156-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c156-109">Attribute</span></span>|<span data-ttu-id="1c156-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c156-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c156-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="1c156-111">discoveryEndpoint</span></span>|<span data-ttu-id="1c156-112">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="1c156-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c156-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c156-113">Child Elements</span></span>  
  
|<span data-ttu-id="1c156-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c156-114">Element</span></span>|<span data-ttu-id="1c156-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c156-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c156-116">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1c156-116">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1c156-117">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1c156-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="1c156-118">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="1c156-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c156-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c156-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1c156-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c156-120">Element</span></span>|<span data-ttu-id="1c156-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c156-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c156-122">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1c156-122">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1c156-123">Çalışma zamanında dinamik olarak uç nokta adresini bulabilirsiniz bir istemci programı olarak çalışması bir uygulamanın işlemesini etkinleştirmek için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c156-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c156-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c156-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
