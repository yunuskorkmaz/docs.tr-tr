---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 6f9cb127deb5651ed27a0ef5802512fb5b6c7b54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190104"
---
# \<dynamicEndpoint>

<span data-ttu-id="d78bc-101">Bu yapılandırma öğesi, bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d78bc-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="d78bc-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="d78bc-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d78bc-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d78bc-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d78bc-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d78bc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d78bc-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d78bc-105">Attributes</span></span>  

 <span data-ttu-id="d78bc-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="d78bc-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d78bc-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d78bc-107">Child Elements</span></span>  
  
|<span data-ttu-id="d78bc-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="d78bc-108">Element</span></span>|<span data-ttu-id="d78bc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d78bc-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="d78bc-110">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d78bc-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d78bc-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d78bc-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d78bc-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d78bc-112">Element</span></span>|<span data-ttu-id="d78bc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d78bc-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="d78bc-114">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d78bc-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d78bc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d78bc-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
