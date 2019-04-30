---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 266b33e9b0386d0346a86ba8bd82cc65def4f0c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673062"
---
# <a name="endtoendtracing"></a><span data-ttu-id="c37b6-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="c37b6-101">\<endToEndTracing></span></span>
<span data-ttu-id="c37b6-102">Enable ve disable uçtan uca izleme hizmet uygulamasının çalışması sırasında farklı yönlerini olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c37b6-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="c37b6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c37b6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c37b6-104">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="c37b6-104">\<diagnostic></span></span>  
<span data-ttu-id="c37b6-105">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="c37b6-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c37b6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c37b6-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c37b6-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c37b6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c37b6-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c37b6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c37b6-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c37b6-109">Attributes</span></span>  
  
|<span data-ttu-id="c37b6-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c37b6-110">Attribute</span></span>|<span data-ttu-id="c37b6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c37b6-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="c37b6-112">Aktivite izlemenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c37b6-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="c37b6-113">İleti akışı izlemenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c37b6-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="c37b6-114">Yayma özniteliğinin ayarlanmış olup olmadığını belirten bir Boole değeri true.</span><span class="sxs-lookup"><span data-stu-id="c37b6-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c37b6-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c37b6-115">Child Elements</span></span>  
 <span data-ttu-id="c37b6-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c37b6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c37b6-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c37b6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c37b6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c37b6-118">Element</span></span>|<span data-ttu-id="c37b6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c37b6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c37b6-120">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="c37b6-120">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="c37b6-121">WCF ayarları için çalışma zamanı incelemesi ve denetimi yöneticisi için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c37b6-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c37b6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c37b6-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="c37b6-123">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="c37b6-123">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
