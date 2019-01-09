---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: bb443334e0713464e64ec9297bbab4ad11eda723
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145061"
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="1679f-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="1679f-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="1679f-103">Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="1679f-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="1679f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1679f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1679f-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1679f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1679f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1679f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1679f-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1679f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1679f-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1679f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1679f-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1679f-109">Attributes</span></span>  
  
|<span data-ttu-id="1679f-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1679f-110">Attribute</span></span>|<span data-ttu-id="1679f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1679f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1679f-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="1679f-112">discoveryEndpoint</span></span>|<span data-ttu-id="1679f-113">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="1679f-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1679f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1679f-114">Child Elements</span></span>  
  
|<span data-ttu-id="1679f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1679f-115">Element</span></span>|<span data-ttu-id="1679f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1679f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1679f-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1679f-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1679f-118">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1679f-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="1679f-119">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="1679f-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1679f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1679f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1679f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="1679f-121">Element</span></span>|<span data-ttu-id="1679f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1679f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1679f-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1679f-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1679f-124">Çalışma zamanında dinamik olarak uç nokta adresini bulabilirsiniz bir istemci programı olarak çalışması bir uygulamanın işlemesini etkinleştirmek için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1679f-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1679f-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1679f-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
