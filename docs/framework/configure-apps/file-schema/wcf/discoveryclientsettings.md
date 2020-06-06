---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855405"
---
# \<discoveryClientSettings>
<span data-ttu-id="d19fb-101">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d19fb-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="d19fb-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d19fb-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d19fb-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d19fb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d19fb-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d19fb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d19fb-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d19fb-105">Attributes</span></span>  
  
|<span data-ttu-id="d19fb-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d19fb-106">Attribute</span></span>|<span data-ttu-id="d19fb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d19fb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d19fb-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="d19fb-108">discoveryEndpoint</span></span>|<span data-ttu-id="d19fb-109">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d19fb-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d19fb-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d19fb-110">Child Elements</span></span>  
  
|<span data-ttu-id="d19fb-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="d19fb-111">Element</span></span>|<span data-ttu-id="d19fb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d19fb-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="d19fb-113">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d19fb-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="d19fb-114">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d19fb-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d19fb-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d19fb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d19fb-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d19fb-116">Element</span></span>|<span data-ttu-id="d19fb-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d19fb-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="d19fb-118">Bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d19fb-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d19fb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d19fb-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
