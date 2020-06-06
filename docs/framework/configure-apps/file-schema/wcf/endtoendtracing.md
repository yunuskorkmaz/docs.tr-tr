---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855287"
---
# \<endToEndTracing>
<span data-ttu-id="2b376-101">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b376-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="2b376-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b376-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b376-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b376-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2b376-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b376-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b376-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b376-105">Attributes</span></span>  
  
|<span data-ttu-id="2b376-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2b376-106">Attribute</span></span>|<span data-ttu-id="2b376-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b376-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="2b376-108">Etkinlik izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="2b376-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="2b376-109">İleti akışı izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="2b376-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="2b376-110">Yay özniteliğinin true olarak ayarlandığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="2b376-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b376-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b376-111">Child Elements</span></span>  
 <span data-ttu-id="2b376-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b376-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b376-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b376-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2b376-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b376-114">Element</span></span>|<span data-ttu-id="2b376-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b376-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="2b376-116">Yönetici için çalışma zamanı incelemesi ve denetimi için WCF ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b376-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b376-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b376-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="2b376-118">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="2b376-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
