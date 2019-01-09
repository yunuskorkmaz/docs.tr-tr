---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 78a69256a391e97ff1962eea923f09115c4ebadd
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150116"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="6c6a5-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="6c6a5-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="6c6a5-103">Enable ve disable uçtan uca izleme hizmet uygulamasının çalışması sırasında farklı yönlerini olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="6c6a5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6c6a5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c6a5-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="6c6a5-105">\<diagnostic></span></span>  
<span data-ttu-id="6c6a5-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="6c6a5-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c6a5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c6a5-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c6a5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c6a5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6c6a5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c6a5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c6a5-110">Attributes</span></span>  
  
|<span data-ttu-id="6c6a5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c6a5-111">Attribute</span></span>|<span data-ttu-id="6c6a5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c6a5-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="6c6a5-113">Aktivite izlemenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="6c6a5-114">İleti akışı izlemenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="6c6a5-115">Yayma özniteliğinin ayarlanmış olup olmadığını belirten bir Boole değeri true.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c6a5-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c6a5-116">Child Elements</span></span>  
 <span data-ttu-id="6c6a5-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c6a5-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c6a5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6c6a5-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c6a5-119">Element</span></span>|<span data-ttu-id="6c6a5-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c6a5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c6a5-121">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="6c6a5-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="6c6a5-122">WCF ayarları için çalışma zamanı incelemesi ve denetimi yöneticisi için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c6a5-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="6c6a5-124">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="6c6a5-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
