---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854789"
---
# \<workflowControlEndpoint>
<span data-ttu-id="2579b-101">Bu yapılandırma öğesi, iş akışı örneklerinin yürütülmesini denetlemek için standart bir uç nokta tanımlar (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).</span><span class="sxs-lookup"><span data-stu-id="2579b-101">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="2579b-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2579b-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2579b-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2579b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2579b-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2579b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2579b-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2579b-105">Attributes</span></span>  
  
|<span data-ttu-id="2579b-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2579b-106">Attribute</span></span>|<span data-ttu-id="2579b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2579b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2579b-108">name</span><span class="sxs-lookup"><span data-stu-id="2579b-108">name</span></span>|<span data-ttu-id="2579b-109">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2579b-109">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="2579b-110">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2579b-110">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2579b-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2579b-111">Child Elements</span></span>  
 <span data-ttu-id="2579b-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="2579b-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2579b-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2579b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2579b-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="2579b-114">Element</span></span>|<span data-ttu-id="2579b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2579b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="2579b-116">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2579b-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2579b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2579b-117">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
