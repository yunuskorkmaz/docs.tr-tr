---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854970"
---
# <a name="timeouts"></a><span data-ttu-id="45409-101">\<Zaman aşımları ></span><span class="sxs-lookup"><span data-stu-id="45409-101">\<timeOuts></span></span>
<span data-ttu-id="45409-102">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45409-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
<span data-ttu-id="45409-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45409-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45409-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="45409-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="45409-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="45409-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="45409-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<hizmet >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="45409-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="45409-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ana bilgisayar >** ](host.md)</span><span class="sxs-lookup"><span data-stu-id="45409-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="45409-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Zaman aşımları >**</span><span class="sxs-lookup"><span data-stu-id="45409-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45409-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45409-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45409-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45409-110">Attributes and Elements</span></span>  
 <span data-ttu-id="45409-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45409-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45409-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45409-112">Attributes</span></span>  
  
|<span data-ttu-id="45409-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45409-113">Attribute</span></span>|<span data-ttu-id="45409-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45409-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="45409-115">Hizmet <xref:System.TimeSpan> ana bilgisayarının kapanması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="45409-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="45409-116">Hizmet <xref:System.TimeSpan> ana bilgisayarının açması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="45409-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45409-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45409-117">Child Elements</span></span>  
 <span data-ttu-id="45409-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="45409-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45409-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45409-119">Parent Elements</span></span>  
  
|<span data-ttu-id="45409-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="45409-120">Element</span></span>|<span data-ttu-id="45409-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45409-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45409-122">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="45409-122">\<host></span></span>](host.md)|<span data-ttu-id="45409-123">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="45409-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45409-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45409-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="45409-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="45409-125">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
