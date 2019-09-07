---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400071"
---
# <a name="persistenceprovider"></a><span data-ttu-id="c77b2-101">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="c77b2-101">\<persistenceProvider></span></span>
<span data-ttu-id="c77b2-102">Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
<span data-ttu-id="c77b2-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c77b2-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c77b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c77b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c77b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c77b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistenceProvider >**</span><span class="sxs-lookup"><span data-stu-id="c77b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c77b2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c77b2-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c77b2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c77b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c77b2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c77b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c77b2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c77b2-112">Attributes</span></span>  
  
|<span data-ttu-id="c77b2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c77b2-113">Attribute</span></span>|<span data-ttu-id="c77b2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c77b2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c77b2-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="c77b2-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="c77b2-116">Kalıcılık <xref:System.TimeSpan> işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c77b2-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="c77b2-117">Varsayılan değer "00:00:30" dır.</span><span class="sxs-lookup"><span data-stu-id="c77b2-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="c77b2-118">türü</span><span class="sxs-lookup"><span data-stu-id="c77b2-118">type</span></span>|<span data-ttu-id="c77b2-119">Kullanılacak kalıcılık sağlayıcısı fabrikası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c77b2-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c77b2-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c77b2-120">Child Elements</span></span>  
 <span data-ttu-id="c77b2-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="c77b2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c77b2-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c77b2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c77b2-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c77b2-123">Element</span></span>|<span data-ttu-id="c77b2-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c77b2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c77b2-125">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c77b2-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c77b2-126">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c77b2-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c77b2-127">Remarks</span></span>  
 <span data-ttu-id="c77b2-128">Bu öğe, bir WCF hizmetinin durumunu seri hale getirmek için kullanılacak Kalıcılık sağlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="c77b2-129">HTTP üst bilgilerinde durum bilgilerini geçiren ile `wsHttpContextBinding` birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c77b2-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77b2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c77b2-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
