---
title: '&lt;discoveryClientSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d5e7106de716e4f25e649dbbca716ef66dfa496
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="81ec0-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="81ec0-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="81ec0-103">Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="81ec0-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="81ec0-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="81ec0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="81ec0-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="81ec0-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ec0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81ec0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81ec0-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81ec0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="81ec0-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81ec0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81ec0-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81ec0-109">Attributes</span></span>  
  
|<span data-ttu-id="81ec0-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81ec0-110">Attribute</span></span>|<span data-ttu-id="81ec0-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81ec0-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81ec0-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="81ec0-112">discoveryEndpoint</span></span>|<span data-ttu-id="81ec0-113">Otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlayan bulma uç noktanın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="81ec0-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81ec0-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81ec0-114">Child Elements</span></span>  
  
|<span data-ttu-id="81ec0-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="81ec0-115">Element</span></span>|<span data-ttu-id="81ec0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81ec0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81ec0-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="81ec0-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="81ec0-118">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="81ec0-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="81ec0-119">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="81ec0-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81ec0-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81ec0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="81ec0-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="81ec0-121">Element</span></span>|<span data-ttu-id="81ec0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81ec0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81ec0-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="81ec0-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="81ec0-124">Uygulama uç noktası adresi çalışma zamanında dinamik olarak bulabilirsiniz bir istemci program olarak çalışmasını etkinleştirmek için bilgileri içeren standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81ec0-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81ec0-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81ec0-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
