---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b2cdd29cda7f82ce555b0f6c1a963567b41ff81b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213005"
---
# <a name="enablewebscript"></a><span data-ttu-id="696a3-101">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="696a3-101">\<enableWebScript></span></span>
<span data-ttu-id="696a3-102">Bu öğe, ASP.NET AJAX web sayfalarından hizmet kullanmayı mümkün kılan uç nokta davranışını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="696a3-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="696a3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="696a3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="696a3-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="696a3-104">\<behaviors></span></span>  
<span data-ttu-id="696a3-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="696a3-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="696a3-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="696a3-106">\<behavior></span></span>  
<span data-ttu-id="696a3-107">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="696a3-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696a3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="696a3-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="696a3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="696a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="696a3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="696a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="696a3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="696a3-111">Attributes</span></span>  
 <span data-ttu-id="696a3-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="696a3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="696a3-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="696a3-113">Child Elements</span></span>  
 <span data-ttu-id="696a3-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="696a3-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="696a3-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="696a3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="696a3-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="696a3-116">Element</span></span>|<span data-ttu-id="696a3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="696a3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="696a3-118">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="696a3-118">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="696a3-119">Uç nokta davranışları kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="696a3-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="696a3-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="696a3-120">Remarks</span></span>  
 <span data-ttu-id="696a3-121">Bu davranış yalnızca ya da birlikte kullanılmalıdır [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama veya [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="696a3-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="696a3-122">Bu davranışı hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="696a3-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696a3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="696a3-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="696a3-124">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="696a3-124">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="696a3-125">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="696a3-125">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
