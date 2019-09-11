---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854789"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="cc40e-101">\<workflowControlEndpoint ></span><span class="sxs-lookup"><span data-stu-id="cc40e-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="cc40e-102">Bu yapılandırma öğesi, iş akışı örneklerinin yürütülmesini denetlemek için standart bir uç nokta tanımlar (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="cc40e-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="cc40e-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cc40e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cc40e-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cc40e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cc40e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="cc40e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="cc40e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowControlEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="cc40e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc40e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc40e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc40e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc40e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cc40e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc40e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc40e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc40e-110">Attributes</span></span>  
  
|<span data-ttu-id="cc40e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cc40e-111">Attribute</span></span>|<span data-ttu-id="cc40e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc40e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc40e-113">name</span><span class="sxs-lookup"><span data-stu-id="cc40e-113">name</span></span>|<span data-ttu-id="cc40e-114">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="cc40e-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="cc40e-115">Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc40e-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc40e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc40e-116">Child Elements</span></span>  
 <span data-ttu-id="cc40e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="cc40e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc40e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc40e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cc40e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc40e-119">Element</span></span>|<span data-ttu-id="cc40e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc40e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc40e-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="cc40e-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="cc40e-122">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cc40e-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc40e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc40e-123">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
