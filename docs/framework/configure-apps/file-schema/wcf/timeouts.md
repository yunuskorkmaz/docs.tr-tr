---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758229"
---
# <a name="timeouts"></a><span data-ttu-id="361d8-101">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="361d8-101">\<timeOuts></span></span>
<span data-ttu-id="361d8-102">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="361d8-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="361d8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="361d8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="361d8-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="361d8-104">\<client></span></span>  
<span data-ttu-id="361d8-105">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="361d8-105">\<endpoint></span></span>  
<span data-ttu-id="361d8-106">\<konak ></span><span class="sxs-lookup"><span data-stu-id="361d8-106">\<host></span></span>  
<span data-ttu-id="361d8-107">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="361d8-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="361d8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="361d8-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="361d8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="361d8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="361d8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="361d8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="361d8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="361d8-111">Attributes</span></span>  
  
|<span data-ttu-id="361d8-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="361d8-112">Attribute</span></span>|<span data-ttu-id="361d8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="361d8-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="361d8-114">A <xref:System.TimeSpan> zaman aralığını belirten bir değer izin verilen hizmet konağı kapatın.</span><span class="sxs-lookup"><span data-stu-id="361d8-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="361d8-115">A <xref:System.TimeSpan> zaman aralığını belirten bir değer açmak hizmet ana bilgisayarı için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="361d8-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="361d8-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="361d8-116">Child Elements</span></span>  
 <span data-ttu-id="361d8-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="361d8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="361d8-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="361d8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="361d8-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="361d8-119">Element</span></span>|<span data-ttu-id="361d8-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="361d8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="361d8-121">\<konak ></span><span class="sxs-lookup"><span data-stu-id="361d8-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="361d8-122">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="361d8-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="361d8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="361d8-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="361d8-124">Barındırma</span><span class="sxs-lookup"><span data-stu-id="361d8-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
