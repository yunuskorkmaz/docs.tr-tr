---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919108"
---
# <a name="enablewebscript"></a><span data-ttu-id="e4f0c-101">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="e4f0c-101">\<enableWebScript></span></span>
<span data-ttu-id="e4f0c-102">Bu öğe, hizmeti ASP.NET AJAX web sayfalarından kullanmasını olanaklı kılan uç nokta davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="e4f0c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4f0c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4f0c-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="e4f0c-104">\<behaviors></span></span>  
<span data-ttu-id="e4f0c-105">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="e4f0c-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="e4f0c-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="e4f0c-106">\<behavior></span></span>  
<span data-ttu-id="e4f0c-107">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="e4f0c-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f0c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4f0c-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4f0c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4f0c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e4f0c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4f0c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4f0c-111">Attributes</span></span>  
 <span data-ttu-id="e4f0c-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4f0c-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4f0c-113">Child Elements</span></span>  
 <span data-ttu-id="e4f0c-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4f0c-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4f0c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e4f0c-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4f0c-116">Element</span></span>|<span data-ttu-id="e4f0c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4f0c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4f0c-118">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="e4f0c-118">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e4f0c-119">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f0c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4f0c-120">Remarks</span></span>  
 <span data-ttu-id="e4f0c-121">Bu davranış yalnızca [ \<WebHttpBinding >](webhttpbinding.md) standart [ \<bağlaması veya webMessageEncoding >](webmessageencoding.md) Binding öğesi ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="e4f0c-122">Bu davranış hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f0c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f0c-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="e4f0c-124">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="e4f0c-124">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="e4f0c-125">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="e4f0c-125">\<webHttp></span></span>](webhttp.md)
