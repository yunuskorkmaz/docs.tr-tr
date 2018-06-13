---
title: '&lt;zaman aşımları&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 1f0638f85177d2acb6f61e3246a1a5ee9a4e2f5c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753007"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="cf7cb-102">&lt;zaman aşımları&gt;</span><span class="sxs-lookup"><span data-stu-id="cf7cb-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="cf7cb-103">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf7cb-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="cf7cb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf7cb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf7cb-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="cf7cb-105">\<client></span></span>  
<span data-ttu-id="cf7cb-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="cf7cb-106">\<endpoint></span></span>  
<span data-ttu-id="cf7cb-107">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="cf7cb-107">\<host></span></span>  
<span data-ttu-id="cf7cb-108">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="cf7cb-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf7cb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf7cb-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf7cb-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf7cb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cf7cb-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf7cb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf7cb-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cf7cb-112">Attributes</span></span>  
  
|<span data-ttu-id="cf7cb-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cf7cb-113">Attribute</span></span>|<span data-ttu-id="cf7cb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf7cb-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="cf7cb-115">A <xref:System.TimeSpan> hizmet ana bilgisayarı kapatmak izin verilen zaman aralığını belirtir değer.</span><span class="sxs-lookup"><span data-stu-id="cf7cb-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="cf7cb-116">A <xref:System.TimeSpan> açmak hizmet ana bilgisayarı için izin verilen zaman aralığını belirtir değer.</span><span class="sxs-lookup"><span data-stu-id="cf7cb-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf7cb-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf7cb-117">Child Elements</span></span>  
 <span data-ttu-id="cf7cb-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="cf7cb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf7cb-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf7cb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cf7cb-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf7cb-120">Element</span></span>|<span data-ttu-id="cf7cb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf7cb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf7cb-122">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="cf7cb-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="cf7cb-123">Hizmet ana bilgisayarı ayarlarını belirtir. bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="cf7cb-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf7cb-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf7cb-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="cf7cb-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="cf7cb-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
