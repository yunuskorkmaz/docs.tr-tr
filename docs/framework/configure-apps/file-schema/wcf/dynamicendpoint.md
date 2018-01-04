---
title: '&lt;dynamicEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46fb4f1f4688aede484b177e30b8bc8dfff1ece2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="58652-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="58652-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="58652-103">Bu yapılandırma öğesi uygulama uç noktası adresi çalışma zamanında dinamik olarak bulabilirsiniz bir istemci program olarak çalışmasını etkinleştirmek için bilgileri içeren standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="58652-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="58652-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="58652-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="58652-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="58652-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58652-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58652-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58652-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="58652-107">Attributes and Elements</span></span>  
 <span data-ttu-id="58652-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58652-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58652-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="58652-109">Attributes</span></span>  
 <span data-ttu-id="58652-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="58652-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58652-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="58652-111">Child Elements</span></span>  
  
|<span data-ttu-id="58652-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="58652-112">Element</span></span>|<span data-ttu-id="58652-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58652-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58652-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="58652-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="58652-115">Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="58652-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58652-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="58652-116">Parent Elements</span></span>  
  
|<span data-ttu-id="58652-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="58652-117">Element</span></span>|<span data-ttu-id="58652-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58652-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58652-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="58652-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="58652-120">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="58652-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58652-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58652-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
