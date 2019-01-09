---
title: '&lt;zaman aşımı&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148337"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="7bf5a-102">&lt;zaman aşımı&gt;</span><span class="sxs-lookup"><span data-stu-id="7bf5a-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="7bf5a-103">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7bf5a-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="7bf5a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7bf5a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7bf5a-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="7bf5a-105">\<client></span></span>  
<span data-ttu-id="7bf5a-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="7bf5a-106">\<endpoint></span></span>  
<span data-ttu-id="7bf5a-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="7bf5a-107">\<host></span></span>  
<span data-ttu-id="7bf5a-108">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="7bf5a-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf5a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bf5a-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bf5a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bf5a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7bf5a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bf5a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bf5a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7bf5a-112">Attributes</span></span>  
  
|<span data-ttu-id="7bf5a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7bf5a-113">Attribute</span></span>|<span data-ttu-id="7bf5a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bf5a-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7bf5a-115">A <xref:System.TimeSpan> zaman aralığını belirten bir değer izin verilen hizmet konağı kapatın.</span><span class="sxs-lookup"><span data-stu-id="7bf5a-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="7bf5a-116">A <xref:System.TimeSpan> zaman aralığını belirten bir değer açmak hizmet ana bilgisayarı için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="7bf5a-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bf5a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bf5a-117">Child Elements</span></span>  
 <span data-ttu-id="7bf5a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7bf5a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bf5a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bf5a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7bf5a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="7bf5a-120">Element</span></span>|<span data-ttu-id="7bf5a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bf5a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bf5a-122">\<konak ></span><span class="sxs-lookup"><span data-stu-id="7bf5a-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="7bf5a-123">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="7bf5a-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bf5a-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bf5a-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="7bf5a-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7bf5a-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
