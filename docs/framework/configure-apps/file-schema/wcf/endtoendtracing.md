---
description: 'Hakkında daha fazla bilgi edinin: <endToEndTracing>'
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 2ac4a7563d7d7881cdb503e843d34f84fd9c95a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782123"
---
# \<endToEndTracing>

<span data-ttu-id="2abb8-102">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="2abb8-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="2abb8-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="2abb8-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2abb8-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2abb8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2abb8-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2abb8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2abb8-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2abb8-106">Attributes</span></span>  
  
|<span data-ttu-id="2abb8-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2abb8-107">Attribute</span></span>|<span data-ttu-id="2abb8-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2abb8-108">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="2abb8-109">Etkinlik izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="2abb8-109">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="2abb8-110">İleti akışı izlemenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="2abb8-110">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="2abb8-111">Yay özniteliğinin true olarak ayarlandığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="2abb8-111">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2abb8-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2abb8-112">Child Elements</span></span>  

 <span data-ttu-id="2abb8-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2abb8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2abb8-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2abb8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2abb8-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2abb8-115">Element</span></span>|<span data-ttu-id="2abb8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2abb8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="2abb8-117">Yönetici için çalışma zamanı incelemesi ve denetimi için WCF ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2abb8-117">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2abb8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2abb8-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="2abb8-119">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="2abb8-119">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
