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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6dc2654b8c51dad53c05a37f5febe15d6d69fd1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="b1f7a-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="b1f7a-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="b1f7a-103">Bu öğe, ASP.NET AJAX web sayfalarından hizmeti kullanmak mümkün kılar uç nokta davranışını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="b1f7a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b1f7a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1f7a-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="b1f7a-105">\<behaviors></span></span>  
<span data-ttu-id="b1f7a-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b1f7a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="b1f7a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b1f7a-107">\<behavior></span></span>  
<span data-ttu-id="b1f7a-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="b1f7a-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f7a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1f7a-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1f7a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1f7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1f7a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1f7a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1f7a-112">Attributes</span></span>  
 <span data-ttu-id="b1f7a-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1f7a-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1f7a-114">Child Elements</span></span>  
 <span data-ttu-id="b1f7a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1f7a-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1f7a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b1f7a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1f7a-117">Element</span></span>|<span data-ttu-id="b1f7a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1f7a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1f7a-119">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b1f7a-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b1f7a-120">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1f7a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1f7a-121">Remarks</span></span>  
 <span data-ttu-id="b1f7a-122">Bu davranış yalnızca ya da ile birlikte kullanılmalıdır [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama veya [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="b1f7a-123">Bu davranış hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f7a-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f7a-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="b1f7a-125">AJAX tümleştirme ve JSON desteği</span><span class="sxs-lookup"><span data-stu-id="b1f7a-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="b1f7a-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="b1f7a-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
