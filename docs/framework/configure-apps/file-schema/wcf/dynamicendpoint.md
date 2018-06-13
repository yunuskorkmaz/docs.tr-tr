---
title: '&lt;DynamicEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 215bc9d8540b2d782a0c63f2f5be96f6fcde6812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746767"
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="40874-102">&lt;DynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="40874-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="40874-103">Bu yapılandırma öğesi uygulama uç noktası adresi çalışma zamanında dinamik olarak bulabilirsiniz bir istemci program olarak çalışmasını etkinleştirmek için bilgileri içeren standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40874-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="40874-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40874-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40874-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="40874-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40874-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40874-106">Syntax</span></span>  
  
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
            <add scope="URI" />
          </scopes>
        </findCriteria>
      </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40874-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40874-107">Attributes and Elements</span></span>  
 <span data-ttu-id="40874-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40874-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40874-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40874-109">Attributes</span></span>  
 <span data-ttu-id="40874-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="40874-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40874-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40874-111">Child Elements</span></span>  
  
|<span data-ttu-id="40874-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="40874-112">Element</span></span>|<span data-ttu-id="40874-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40874-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40874-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="40874-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="40874-115">Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="40874-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40874-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40874-116">Parent Elements</span></span>  
  
|<span data-ttu-id="40874-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="40874-117">Element</span></span>|<span data-ttu-id="40874-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40874-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40874-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="40874-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="40874-120">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="40874-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40874-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40874-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
