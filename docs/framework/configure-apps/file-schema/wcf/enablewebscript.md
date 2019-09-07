---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400381"
---
# <a name="enablewebscript"></a><span data-ttu-id="7955a-101">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="7955a-101">\<enableWebScript></span></span>
<span data-ttu-id="7955a-102">Bu öğe, hizmeti ASP.NET AJAX web sayfalarından kullanmasını olanaklı kılan uç nokta davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7955a-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
<span data-ttu-id="7955a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7955a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7955a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7955a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7955a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7955a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7955a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7955a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="7955a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7955a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="7955a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<enableWebScript >**</span><span class="sxs-lookup"><span data-stu-id="7955a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7955a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7955a-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7955a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7955a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7955a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7955a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7955a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7955a-112">Attributes</span></span>  
 <span data-ttu-id="7955a-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="7955a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7955a-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7955a-114">Child Elements</span></span>  
 <span data-ttu-id="7955a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="7955a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7955a-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7955a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7955a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7955a-117">Element</span></span>|<span data-ttu-id="7955a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7955a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7955a-119">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="7955a-119">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7955a-120">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7955a-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7955a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7955a-121">Remarks</span></span>  
 <span data-ttu-id="7955a-122">Bu davranış yalnızca [ \<WebHttpBinding >](webhttpbinding.md) standart [ \<bağlaması veya webMessageEncoding >](webmessageencoding.md) Binding öğesi ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7955a-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="7955a-123">Bu davranış hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7955a-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7955a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7955a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="7955a-125">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="7955a-125">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="7955a-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="7955a-126">\<webHttp></span></span>](webhttp.md)
