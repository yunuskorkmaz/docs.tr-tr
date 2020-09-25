---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b50c0c3db644787fe41ee58ced7eb640e7295f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190026"
---
# \<endToEndTracing>

<span data-ttu-id="0e1fe-101">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="0e1fe-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e1fe-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e1fe-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e1fe-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0e1fe-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e1fe-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e1fe-105">Attributes</span></span>  
  
|<span data-ttu-id="0e1fe-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e1fe-106">Attribute</span></span>|<span data-ttu-id="0e1fe-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e1fe-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="0e1fe-108">Etkinlik izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="0e1fe-109">İleti akışı izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="0e1fe-110">Yay özniteliğinin true olarak ayarlandığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e1fe-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e1fe-111">Child Elements</span></span>  

 <span data-ttu-id="0e1fe-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e1fe-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e1fe-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0e1fe-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e1fe-114">Element</span></span>|<span data-ttu-id="0e1fe-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e1fe-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="0e1fe-116">Yönetici için çalışma zamanı incelemesi ve denetimi için WCF ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e1fe-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e1fe-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="0e1fe-118">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="0e1fe-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
