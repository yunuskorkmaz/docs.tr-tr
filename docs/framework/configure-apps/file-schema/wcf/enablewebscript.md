---
title: '&lt;enableWebScript&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfb6981947b457d5fdad59e96bdcd6937b9abd02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="11925-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="11925-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="11925-103">Bu öğe, ASP.NET AJAX web sayfalarından hizmeti kullanmak mümkün kılar uç nokta davranışını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="11925-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="11925-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="11925-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="11925-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="11925-105">\<behaviors></span></span>  
<span data-ttu-id="11925-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="11925-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="11925-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="11925-107">\<behavior></span></span>  
<span data-ttu-id="11925-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="11925-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11925-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11925-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11925-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="11925-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11925-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11925-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11925-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11925-112">Attributes</span></span>  
 <span data-ttu-id="11925-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="11925-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="11925-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="11925-114">Child Elements</span></span>  
 <span data-ttu-id="11925-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="11925-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11925-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="11925-116">Parent Elements</span></span>  
  
|<span data-ttu-id="11925-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="11925-117">Element</span></span>|<span data-ttu-id="11925-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11925-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11925-119">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="11925-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="11925-120">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="11925-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11925-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11925-121">Remarks</span></span>  
 <span data-ttu-id="11925-122">Bu davranış yalnızca ya da ile birlikte kullanılmalıdır [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama veya [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="11925-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="11925-123">Bu davranış hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="11925-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11925-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11925-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="11925-125">AJAX tümleştirme ve JSON desteği</span><span class="sxs-lookup"><span data-stu-id="11925-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="11925-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="11925-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
