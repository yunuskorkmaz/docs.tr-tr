---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b159488efa2a80a9dea625e4c6dfe2f215dfc457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939180"
---
# <a name="timeouts"></a><span data-ttu-id="28b59-101">\<Zaman aşımları ></span><span class="sxs-lookup"><span data-stu-id="28b59-101">\<timeOuts></span></span>
<span data-ttu-id="28b59-102">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="28b59-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="28b59-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28b59-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="28b59-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="28b59-104">\<client></span></span>  
<span data-ttu-id="28b59-105">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="28b59-105">\<endpoint></span></span>  
<span data-ttu-id="28b59-106">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="28b59-106">\<host></span></span>  
<span data-ttu-id="28b59-107">\<Zaman aşımları ></span><span class="sxs-lookup"><span data-stu-id="28b59-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b59-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28b59-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28b59-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="28b59-109">Attributes and Elements</span></span>  
 <span data-ttu-id="28b59-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28b59-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28b59-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="28b59-111">Attributes</span></span>  
  
|<span data-ttu-id="28b59-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="28b59-112">Attribute</span></span>|<span data-ttu-id="28b59-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28b59-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="28b59-114">Hizmet <xref:System.TimeSpan> ana bilgisayarının kapanması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="28b59-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="28b59-115">Hizmet <xref:System.TimeSpan> ana bilgisayarının açması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="28b59-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28b59-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="28b59-116">Child Elements</span></span>  
 <span data-ttu-id="28b59-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="28b59-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28b59-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="28b59-118">Parent Elements</span></span>  
  
|<span data-ttu-id="28b59-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="28b59-119">Element</span></span>|<span data-ttu-id="28b59-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28b59-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b59-121">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="28b59-121">\<host></span></span>](host.md)|<span data-ttu-id="28b59-122">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="28b59-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28b59-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28b59-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="28b59-124">Barındırma</span><span class="sxs-lookup"><span data-stu-id="28b59-124">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
