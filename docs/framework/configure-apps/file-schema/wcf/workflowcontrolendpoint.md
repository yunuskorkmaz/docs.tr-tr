---
title: '&lt;workflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 178ccc8ac35b0ac76d74c818dce43dcffc5c0835
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144957"
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="f1ec8-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="f1ec8-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="f1ec8-103">Bu yapılandırma öğesi, iş akışı örnekleri yürütülmesini denetlemek için bir standart uç nokta tanımlar. (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="f1ec8-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="f1ec8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1ec8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1ec8-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f1ec8-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1ec8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1ec8-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1ec8-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1ec8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f1ec8-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1ec8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1ec8-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f1ec8-109">Attributes</span></span>  
  
|<span data-ttu-id="f1ec8-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f1ec8-110">Attribute</span></span>|<span data-ttu-id="f1ec8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1ec8-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1ec8-112">name</span><span class="sxs-lookup"><span data-stu-id="f1ec8-112">name</span></span>|<span data-ttu-id="f1ec8-113">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="f1ec8-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f1ec8-114">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="f1ec8-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1ec8-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1ec8-115">Child Elements</span></span>  
 <span data-ttu-id="f1ec8-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="f1ec8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1ec8-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1ec8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f1ec8-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f1ec8-118">Element</span></span>|<span data-ttu-id="f1ec8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1ec8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1ec8-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f1ec8-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f1ec8-121">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="f1ec8-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1ec8-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1ec8-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
