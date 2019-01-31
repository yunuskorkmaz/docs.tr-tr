---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 8a8a352380fe6eedb41ead089405e7b79fad29fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272789"
---
# <a name="timeouts"></a><span data-ttu-id="98abf-101">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="98abf-101">\<timeOuts></span></span>
<span data-ttu-id="98abf-102">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98abf-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="98abf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="98abf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="98abf-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="98abf-104">\<client></span></span>  
<span data-ttu-id="98abf-105">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="98abf-105">\<endpoint></span></span>  
<span data-ttu-id="98abf-106">\<konak ></span><span class="sxs-lookup"><span data-stu-id="98abf-106">\<host></span></span>  
<span data-ttu-id="98abf-107">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="98abf-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98abf-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98abf-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98abf-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="98abf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="98abf-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="98abf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98abf-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="98abf-111">Attributes</span></span>  
  
|<span data-ttu-id="98abf-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="98abf-112">Attribute</span></span>|<span data-ttu-id="98abf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98abf-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="98abf-114">A <xref:System.TimeSpan> zaman aralığını belirten bir değer izin verilen hizmet konağı kapatın.</span><span class="sxs-lookup"><span data-stu-id="98abf-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="98abf-115">A <xref:System.TimeSpan> zaman aralığını belirten bir değer açmak hizmet ana bilgisayarı için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="98abf-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98abf-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="98abf-116">Child Elements</span></span>  
 <span data-ttu-id="98abf-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="98abf-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98abf-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="98abf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="98abf-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="98abf-119">Element</span></span>|<span data-ttu-id="98abf-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98abf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98abf-121">\<konak ></span><span class="sxs-lookup"><span data-stu-id="98abf-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="98abf-122">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="98abf-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98abf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98abf-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="98abf-124">Barındırma</span><span class="sxs-lookup"><span data-stu-id="98abf-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
