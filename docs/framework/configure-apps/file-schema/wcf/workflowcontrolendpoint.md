---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 2c9774217b835acdb9ebf7374b964d838497fc9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915328"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="32813-101">\<workflowControlEndpoint ></span><span class="sxs-lookup"><span data-stu-id="32813-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="32813-102">Bu yapılandırma öğesi, iş akışı örneklerinin yürütülmesini denetlemek için standart bir uç nokta tanımlar (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="32813-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="32813-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32813-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="32813-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="32813-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32813-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32813-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32813-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32813-106">Attributes and Elements</span></span>  
 <span data-ttu-id="32813-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32813-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32813-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32813-108">Attributes</span></span>  
  
|<span data-ttu-id="32813-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="32813-109">Attribute</span></span>|<span data-ttu-id="32813-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32813-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32813-111">name</span><span class="sxs-lookup"><span data-stu-id="32813-111">name</span></span>|<span data-ttu-id="32813-112">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="32813-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="32813-113">Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32813-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32813-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32813-114">Child Elements</span></span>  
 <span data-ttu-id="32813-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="32813-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32813-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32813-116">Parent Elements</span></span>  
  
|<span data-ttu-id="32813-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="32813-117">Element</span></span>|<span data-ttu-id="32813-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32813-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32813-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="32813-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="32813-120">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="32813-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32813-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32813-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
