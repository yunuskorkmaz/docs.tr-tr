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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8371b9180fec9877ac58026c26fb60c8ccdaa752
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="2484f-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="2484f-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="2484f-103">Bu yapılandırma öğesi iş akışı örnekleri yürütülmesini denetlemeye yönelik standart bir uç nokta tanımlar (oluşturmak, çalıştırmak, askıya almak, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="2484f-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="2484f-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2484f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2484f-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2484f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2484f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2484f-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2484f-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2484f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2484f-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2484f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2484f-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2484f-109">Attributes</span></span>  
  
|<span data-ttu-id="2484f-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2484f-110">Attribute</span></span>|<span data-ttu-id="2484f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2484f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2484f-112">name</span><span class="sxs-lookup"><span data-stu-id="2484f-112">name</span></span>|<span data-ttu-id="2484f-113">Standart uç noktasının yapılandırma adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="2484f-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="2484f-114">Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2484f-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2484f-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2484f-115">Child Elements</span></span>  
 <span data-ttu-id="2484f-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="2484f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2484f-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2484f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2484f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="2484f-118">Element</span></span>|<span data-ttu-id="2484f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2484f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2484f-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2484f-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="2484f-121">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="2484f-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2484f-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2484f-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
