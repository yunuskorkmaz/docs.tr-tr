---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855350"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="30c8d-101">\<dynamicEndpoint ></span><span class="sxs-lookup"><span data-stu-id="30c8d-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="30c8d-102">Bu yapılandırma öğesi, bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30c8d-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="30c8d-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="30c8d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="30c8d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="30c8d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="30c8d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="30c8d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="30c8d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dynamicEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="30c8d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c8d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30c8d-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30c8d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30c8d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="30c8d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30c8d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30c8d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30c8d-110">Attributes</span></span>  
 <span data-ttu-id="30c8d-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="30c8d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="30c8d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30c8d-112">Child Elements</span></span>  
  
|<span data-ttu-id="30c8d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="30c8d-113">Element</span></span>|<span data-ttu-id="30c8d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30c8d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30c8d-115">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="30c8d-115">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="30c8d-116">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="30c8d-116">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30c8d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30c8d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="30c8d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="30c8d-118">Element</span></span>|<span data-ttu-id="30c8d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30c8d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30c8d-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="30c8d-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="30c8d-121">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="30c8d-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30c8d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30c8d-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
