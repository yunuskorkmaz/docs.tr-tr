---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: c2f5e33eff4fdc6dfa85bcc10b59a7c1436cabb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519411"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="dada0-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="dada0-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="dada0-103">Enable ve disable uçtan uca izleme hizmet uygulamasının çalışması sırasında farklı yönlerini olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="dada0-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="dada0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dada0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dada0-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="dada0-105">\<diagnostic></span></span>  
<span data-ttu-id="dada0-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="dada0-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dada0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dada0-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dada0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dada0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dada0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dada0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dada0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dada0-110">Attributes</span></span>  
  
|<span data-ttu-id="dada0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dada0-111">Attribute</span></span>|<span data-ttu-id="dada0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dada0-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="dada0-113">Aktivite izlemenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="dada0-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="dada0-114">İleti akışı izlemenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="dada0-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="dada0-115">Yayma özniteliğinin ayarlanmış olup olmadığını belirten bir Boole değeri true.</span><span class="sxs-lookup"><span data-stu-id="dada0-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dada0-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dada0-116">Child Elements</span></span>  
 <span data-ttu-id="dada0-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="dada0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dada0-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dada0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dada0-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="dada0-119">Element</span></span>|<span data-ttu-id="dada0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dada0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dada0-121">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="dada0-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="dada0-122">WCF ayarları için çalışma zamanı incelemesi ve denetimi yöneticisi için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dada0-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dada0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dada0-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="dada0-124">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="dada0-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
