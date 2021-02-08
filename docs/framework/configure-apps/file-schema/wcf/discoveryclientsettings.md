---
description: 'Hakkında daha fazla bilgi edinin: <discoveryClientSettings>'
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: c2fda0dea33ffd6dbca24881eefab2e54e361f92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802300"
---
# \<discoveryClientSettings>

<span data-ttu-id="de204-102">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="de204-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="de204-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="de204-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de204-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de204-104">Attributes and Elements</span></span>  

 <span data-ttu-id="de204-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de204-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de204-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de204-106">Attributes</span></span>  
  
|<span data-ttu-id="de204-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de204-107">Attribute</span></span>|<span data-ttu-id="de204-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de204-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de204-109">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="de204-109">discoveryEndpoint</span></span>|<span data-ttu-id="de204-110">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="de204-110">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de204-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de204-111">Child Elements</span></span>  
  
|<span data-ttu-id="de204-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="de204-112">Element</span></span>|<span data-ttu-id="de204-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de204-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="de204-114">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="de204-114">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="de204-115">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de204-115">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de204-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de204-116">Parent Elements</span></span>  
  
|<span data-ttu-id="de204-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="de204-117">Element</span></span>|<span data-ttu-id="de204-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de204-118">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="de204-119">Bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de204-119">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de204-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de204-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
