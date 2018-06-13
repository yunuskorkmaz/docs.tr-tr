---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 855f579241dfd495e7f8603ce3bd57aa2556ca2d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753475"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="1d7ea-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="1d7ea-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="1d7ea-103">Etkinleştirme ve devre dışı uçtan uca izleme bir hizmet uygulaması çalışması sırasında farklı yönlerini olanak sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="1d7ea-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1d7ea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d7ea-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="1d7ea-105">\<diagnostic></span></span>  
<span data-ttu-id="1d7ea-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="1d7ea-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d7ea-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d7ea-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d7ea-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d7ea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d7ea-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d7ea-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d7ea-110">Attributes</span></span>  
  
|<span data-ttu-id="1d7ea-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1d7ea-111">Attribute</span></span>|<span data-ttu-id="1d7ea-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d7ea-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="1d7ea-113">Etkinlik izlemenin etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="1d7ea-114">İleti akışı içinde izleme etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="1d7ea-115">Propagate özniteliği ayarlanmış olup olmadığını belirten bir Boole değeri true.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d7ea-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d7ea-116">Child Elements</span></span>  
 <span data-ttu-id="1d7ea-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d7ea-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d7ea-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1d7ea-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d7ea-119">Element</span></span>|<span data-ttu-id="1d7ea-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d7ea-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d7ea-121">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="1d7ea-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="1d7ea-122">Çalışma zamanı İnceleme için WCF ayarlarını ve yönetici için Denetim tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d7ea-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d7ea-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="1d7ea-124">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="1d7ea-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
