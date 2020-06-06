---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855350"
---
# \<dynamicEndpoint>
<span data-ttu-id="41a77-101">Bu yapılandırma öğesi, bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="41a77-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="41a77-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41a77-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41a77-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41a77-103">Attributes and Elements</span></span>  
 <span data-ttu-id="41a77-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41a77-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41a77-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41a77-105">Attributes</span></span>  
 <span data-ttu-id="41a77-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="41a77-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41a77-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41a77-107">Child Elements</span></span>  
  
|<span data-ttu-id="41a77-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="41a77-108">Element</span></span>|<span data-ttu-id="41a77-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41a77-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="41a77-110">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="41a77-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41a77-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41a77-111">Parent Elements</span></span>  
  
|<span data-ttu-id="41a77-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="41a77-112">Element</span></span>|<span data-ttu-id="41a77-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41a77-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="41a77-114">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="41a77-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41a77-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41a77-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
