---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="521a4-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="521a4-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="521a4-103">Etkinleştirme ve devre dışı uçtan uca izleme bir hizmet uygulaması çalışması sırasında farklı yönlerini olanak sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="521a4-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="521a4-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="521a4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="521a4-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="521a4-105">\<diagnostic></span></span>  
<span data-ttu-id="521a4-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="521a4-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="521a4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="521a4-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="521a4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="521a4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="521a4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="521a4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="521a4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="521a4-110">Attributes</span></span>  
  
|<span data-ttu-id="521a4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="521a4-111">Attribute</span></span>|<span data-ttu-id="521a4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="521a4-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="521a4-113">Etkinlik izlemenin etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="521a4-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="521a4-114">İleti akışı içinde izleme etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="521a4-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="521a4-115">Propagate özniteliği ayarlanmış olup olmadığını belirten bir Boole değeri true.</span><span class="sxs-lookup"><span data-stu-id="521a4-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="521a4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="521a4-116">Child Elements</span></span>  
 <span data-ttu-id="521a4-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="521a4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="521a4-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="521a4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="521a4-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="521a4-119">Element</span></span>|<span data-ttu-id="521a4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="521a4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="521a4-121">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="521a4-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="521a4-122">Çalışma zamanı İnceleme için WCF ayarlarını ve yönetici için Denetim tanımlar.</span><span class="sxs-lookup"><span data-stu-id="521a4-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="521a4-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="521a4-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="521a4-124">Uçtan uca izleme</span><span class="sxs-lookup"><span data-stu-id="521a4-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
