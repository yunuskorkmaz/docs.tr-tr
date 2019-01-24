---
title: '&lt;zaman aşımı&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 42f4db1d954834cbfa3c526328cca45443751506
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629664"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="e3b89-102">&lt;zaman aşımı&gt;</span><span class="sxs-lookup"><span data-stu-id="e3b89-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="e3b89-103">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3b89-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="e3b89-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3b89-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3b89-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="e3b89-105">\<client></span></span>  
<span data-ttu-id="e3b89-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="e3b89-106">\<endpoint></span></span>  
<span data-ttu-id="e3b89-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="e3b89-107">\<host></span></span>  
<span data-ttu-id="e3b89-108">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="e3b89-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b89-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3b89-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3b89-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3b89-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e3b89-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3b89-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3b89-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3b89-112">Attributes</span></span>  
  
|<span data-ttu-id="e3b89-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3b89-113">Attribute</span></span>|<span data-ttu-id="e3b89-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3b89-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e3b89-115">A <xref:System.TimeSpan> zaman aralığını belirten bir değer izin verilen hizmet konağı kapatın.</span><span class="sxs-lookup"><span data-stu-id="e3b89-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="e3b89-116">A <xref:System.TimeSpan> zaman aralığını belirten bir değer açmak hizmet ana bilgisayarı için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e3b89-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3b89-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3b89-117">Child Elements</span></span>  
 <span data-ttu-id="e3b89-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3b89-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3b89-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3b89-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e3b89-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3b89-120">Element</span></span>|<span data-ttu-id="e3b89-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3b89-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3b89-122">\<konak ></span><span class="sxs-lookup"><span data-stu-id="e3b89-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e3b89-123">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e3b89-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3b89-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3b89-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="e3b89-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e3b89-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
