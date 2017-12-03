---
title: '&lt;webScriptEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c321167eb32535d7b39c3d36cdeefe5c8a218f70
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="29059-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="29059-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="29059-103">Bu yapılandırma öğesi bir sabit ile standart bir uç nokta tanımlayan [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="29059-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="29059-104">Bir ASP.NET AJAX uygulamasından adlı bir hizmet yazarken Bu uç nokta kullanın.</span><span class="sxs-lookup"><span data-stu-id="29059-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="29059-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29059-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="29059-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="29059-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29059-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29059-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29059-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29059-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29059-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29059-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29059-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29059-110">Attributes</span></span>  
  
|<span data-ttu-id="29059-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="29059-111">Attribute</span></span>|<span data-ttu-id="29059-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29059-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29059-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="29059-113">webEndpointType</span></span>|<span data-ttu-id="29059-114">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="29059-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29059-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29059-115">Child Elements</span></span>  
 <span data-ttu-id="29059-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="29059-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29059-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29059-117">Parent Elements</span></span>  
  
|<span data-ttu-id="29059-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="29059-118">Element</span></span>|<span data-ttu-id="29059-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29059-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29059-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="29059-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="29059-121">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="29059-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29059-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29059-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
