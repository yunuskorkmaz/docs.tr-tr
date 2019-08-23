---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 3dc7fb19c5c7729620a5d9f3df1111b2dbdacf78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925830"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="c3b32-101">\<dynamicEndpoint ></span><span class="sxs-lookup"><span data-stu-id="c3b32-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="c3b32-102">Bu yapılandırma öğesi, bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3b32-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="c3b32-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c3b32-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c3b32-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c3b32-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b32-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3b32-105">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3b32-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3b32-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c3b32-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3b32-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3b32-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3b32-108">Attributes</span></span>  
 <span data-ttu-id="c3b32-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c3b32-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3b32-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3b32-110">Child Elements</span></span>  
  
|<span data-ttu-id="c3b32-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="c3b32-111">Element</span></span>|<span data-ttu-id="c3b32-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3b32-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3b32-113">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="c3b32-113">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="c3b32-114">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="c3b32-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3b32-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3b32-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c3b32-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c3b32-116">Element</span></span>|<span data-ttu-id="c3b32-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3b32-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3b32-118">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c3b32-118">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="c3b32-119">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c3b32-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3b32-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b32-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
