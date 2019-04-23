---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: a9c16d1036a8177120cd152d4ac211ad084d588e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150390"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="b82b7-101">\<workflowControlEndpoint ></span><span class="sxs-lookup"><span data-stu-id="b82b7-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="b82b7-102">Bu yapılandırma öğesi, iş akışı örnekleri yürütülmesini denetlemek için bir standart uç nokta tanımlar. (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="b82b7-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="b82b7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b82b7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b82b7-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b82b7-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b82b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b82b7-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b82b7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b82b7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b82b7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b82b7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b82b7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b82b7-108">Attributes</span></span>  
  
|<span data-ttu-id="b82b7-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b82b7-109">Attribute</span></span>|<span data-ttu-id="b82b7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b82b7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b82b7-111">name</span><span class="sxs-lookup"><span data-stu-id="b82b7-111">name</span></span>|<span data-ttu-id="b82b7-112">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b82b7-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b82b7-113">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="b82b7-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b82b7-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b82b7-114">Child Elements</span></span>  
 <span data-ttu-id="b82b7-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b82b7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b82b7-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b82b7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b82b7-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b82b7-117">Element</span></span>|<span data-ttu-id="b82b7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b82b7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b82b7-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b82b7-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b82b7-120">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="b82b7-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b82b7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b82b7-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
