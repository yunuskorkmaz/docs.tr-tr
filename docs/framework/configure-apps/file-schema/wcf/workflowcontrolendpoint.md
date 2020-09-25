---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 572ff7e119828897860944a430e5f51f5d1c3cad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194849"
---
# \<workflowControlEndpoint>

<span data-ttu-id="d8bd6-101">Bu yapılandırma öğesi, iş akışı örneklerinin yürütülmesini denetlemek için standart bir uç nokta tanımlar (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="d8bd6-101">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="d8bd6-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8bd6-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8bd6-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8bd6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d8bd6-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8bd6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8bd6-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8bd6-105">Attributes</span></span>  
  
|<span data-ttu-id="d8bd6-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d8bd6-106">Attribute</span></span>|<span data-ttu-id="d8bd6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8bd6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8bd6-108">name</span><span class="sxs-lookup"><span data-stu-id="d8bd6-108">name</span></span>|<span data-ttu-id="d8bd6-109">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d8bd6-109">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="d8bd6-110">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8bd6-110">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8bd6-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8bd6-111">Child Elements</span></span>  

 <span data-ttu-id="d8bd6-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8bd6-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8bd6-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8bd6-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d8bd6-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8bd6-114">Element</span></span>|<span data-ttu-id="d8bd6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8bd6-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="d8bd6-116">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d8bd6-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8bd6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8bd6-117">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
