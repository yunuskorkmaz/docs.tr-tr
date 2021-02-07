---
description: 'Hakkında daha fazla bilgi edinin: <workflowControlEndpoint>'
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 5205edf159bd947531231e69fd23f6cdf9c77d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682351"
---
# \<workflowControlEndpoint>

<span data-ttu-id="defa0-102">Bu yapılandırma öğesi, iş akışı örneklerinin yürütülmesini denetlemek için standart bir uç nokta tanımlar (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="defa0-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="defa0-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="defa0-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="defa0-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="defa0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="defa0-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="defa0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="defa0-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="defa0-106">Attributes</span></span>  
  
|<span data-ttu-id="defa0-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="defa0-107">Attribute</span></span>|<span data-ttu-id="defa0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="defa0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="defa0-109">name</span><span class="sxs-lookup"><span data-stu-id="defa0-109">name</span></span>|<span data-ttu-id="defa0-110">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="defa0-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="defa0-111">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="defa0-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="defa0-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="defa0-112">Child Elements</span></span>  

 <span data-ttu-id="defa0-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="defa0-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="defa0-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="defa0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="defa0-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="defa0-115">Element</span></span>|<span data-ttu-id="defa0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="defa0-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="defa0-117">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="defa0-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="defa0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="defa0-118">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
