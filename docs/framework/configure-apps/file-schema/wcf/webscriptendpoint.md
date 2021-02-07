---
description: 'Hakkında daha fazla bilgi edinin: <webScriptEndpoint>'
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: eef4eb8e8e7345492f967c85b6245f733a4c824f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682507"
---
# \<webScriptEndpoint>

<span data-ttu-id="75ff8-102">Bu yapılandırma öğesi [\<webHttpBinding>](webhttpbinding.md) , otomatik olarak davranışını ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<enableWebScript>](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="75ff8-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="75ff8-103">Bir ASP.NET AJAX uygulamasından çağrılan bir hizmet yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ff8-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="75ff8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="75ff8-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75ff8-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75ff8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="75ff8-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75ff8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75ff8-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75ff8-107">Attributes</span></span>  
  
|<span data-ttu-id="75ff8-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75ff8-108">Attribute</span></span>|<span data-ttu-id="75ff8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75ff8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75ff8-110">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="75ff8-110">webEndpointType</span></span>|<span data-ttu-id="75ff8-111">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="75ff8-111">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75ff8-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75ff8-112">Child Elements</span></span>  

 <span data-ttu-id="75ff8-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="75ff8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75ff8-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75ff8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="75ff8-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="75ff8-115">Element</span></span>|<span data-ttu-id="75ff8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75ff8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="75ff8-117">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="75ff8-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75ff8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75ff8-118">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
