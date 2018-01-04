---
title: '&lt;workflowControlEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 443d23a3b0f73d2fd0a08112d51f745d1e1874fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="348fb-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="348fb-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="348fb-103">Bu yapılandırma öğesi iş akışı örnekleri yürütülmesini denetlemeye yönelik standart bir uç nokta tanımlar (oluşturmak, çalıştırmak, askıya almak, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="348fb-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="348fb-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="348fb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="348fb-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="348fb-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348fb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="348fb-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="348fb-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="348fb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="348fb-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="348fb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="348fb-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="348fb-109">Attributes</span></span>  
  
|<span data-ttu-id="348fb-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="348fb-110">Attribute</span></span>|<span data-ttu-id="348fb-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="348fb-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="348fb-112">name</span><span class="sxs-lookup"><span data-stu-id="348fb-112">name</span></span>|<span data-ttu-id="348fb-113">Standart uç noktasının yapılandırma adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="348fb-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="348fb-114">Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.</span><span class="sxs-lookup"><span data-stu-id="348fb-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="348fb-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="348fb-115">Child Elements</span></span>  
 <span data-ttu-id="348fb-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="348fb-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="348fb-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="348fb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="348fb-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="348fb-118">Element</span></span>|<span data-ttu-id="348fb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="348fb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="348fb-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="348fb-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="348fb-121">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="348fb-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="348fb-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="348fb-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
