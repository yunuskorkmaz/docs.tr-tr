---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: dd02f6bb7674015d1c153b2dce38e7e29181d25f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599926"
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="e3180-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="e3180-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="e3180-103">Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="e3180-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="e3180-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3180-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3180-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e3180-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3180-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3180-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3180-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3180-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e3180-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3180-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3180-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3180-109">Attributes</span></span>  
  
|<span data-ttu-id="e3180-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3180-110">Attribute</span></span>|<span data-ttu-id="e3180-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3180-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3180-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="e3180-112">discoveryEndpoint</span></span>|<span data-ttu-id="e3180-113">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="e3180-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3180-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3180-114">Child Elements</span></span>  
  
|<span data-ttu-id="e3180-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3180-115">Element</span></span>|<span data-ttu-id="e3180-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3180-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3180-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e3180-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e3180-118">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e3180-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="e3180-119">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="e3180-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3180-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3180-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e3180-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3180-121">Element</span></span>|<span data-ttu-id="e3180-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3180-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3180-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e3180-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e3180-124">Çalışma zamanında dinamik olarak uç nokta adresini bulabilirsiniz bir istemci programı olarak çalışması bir uygulamanın işlemesini etkinleştirmek için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3180-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3180-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3180-125">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
