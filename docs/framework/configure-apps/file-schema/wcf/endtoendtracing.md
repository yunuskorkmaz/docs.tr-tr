---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919010"
---
# <a name="endtoendtracing"></a><span data-ttu-id="d0c8d-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="d0c8d-101">\<endToEndTracing></span></span>
<span data-ttu-id="d0c8d-102">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="d0c8d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0c8d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0c8d-104">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="d0c8d-104">\<diagnostic></span></span>  
<span data-ttu-id="d0c8d-105">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="d0c8d-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0c8d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0c8d-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0c8d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0c8d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d0c8d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0c8d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0c8d-109">Attributes</span></span>  
  
|<span data-ttu-id="d0c8d-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0c8d-110">Attribute</span></span>|<span data-ttu-id="d0c8d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0c8d-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="d0c8d-112">Etkinlik izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="d0c8d-113">İleti akışı izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="d0c8d-114">Yay özniteliğinin true olarak ayarlandığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0c8d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0c8d-115">Child Elements</span></span>  
 <span data-ttu-id="d0c8d-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0c8d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0c8d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d0c8d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0c8d-118">Element</span></span>|<span data-ttu-id="d0c8d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0c8d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0c8d-120">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="d0c8d-120">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="d0c8d-121">Yönetici için çalışma zamanı incelemesi ve denetimi için WCF ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0c8d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0c8d-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="d0c8d-123">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="d0c8d-123">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
