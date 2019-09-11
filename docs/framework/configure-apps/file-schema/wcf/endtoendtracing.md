---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855287"
---
# <a name="endtoendtracing"></a><span data-ttu-id="29650-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="29650-101">\<endToEndTracing></span></span>
<span data-ttu-id="29650-102">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="29650-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
<span data-ttu-id="29650-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="29650-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29650-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="29650-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="29650-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Tanılama >** ](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="29650-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="29650-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endToEndTracing >**</span><span class="sxs-lookup"><span data-stu-id="29650-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29650-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29650-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29650-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29650-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29650-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29650-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29650-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29650-110">Attributes</span></span>  
  
|<span data-ttu-id="29650-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="29650-111">Attribute</span></span>|<span data-ttu-id="29650-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29650-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="29650-113">Etkinlik izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="29650-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="29650-114">İleti akışı izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="29650-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="29650-115">Yay özniteliğinin true olarak ayarlandığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="29650-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29650-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29650-116">Child Elements</span></span>  
 <span data-ttu-id="29650-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="29650-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29650-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29650-118">Parent Elements</span></span>  
  
|<span data-ttu-id="29650-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="29650-119">Element</span></span>|<span data-ttu-id="29650-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29650-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29650-121">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="29650-121">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="29650-122">Yönetici için çalışma zamanı incelemesi ve denetimi için WCF ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29650-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29650-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29650-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="29650-124">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="29650-124">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
