---
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397727"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="74362-102">\<\<ServiceBehavior > yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="74362-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="74362-103">Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="74362-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
<span data-ttu-id="74362-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="74362-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="74362-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="74362-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="74362-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="74362-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="74362-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="74362-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="74362-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="74362-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="74362-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="74362-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74362-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74362-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74362-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="74362-111">Attributes and Elements</span></span>  
 <span data-ttu-id="74362-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74362-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74362-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74362-113">Attributes</span></span>  
  
|<span data-ttu-id="74362-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="74362-114">Attribute</span></span>|<span data-ttu-id="74362-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74362-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74362-116">filterTable</span><span class="sxs-lookup"><span data-stu-id="74362-116">filterTable</span></span>|<span data-ttu-id="74362-117">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="74362-117">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="74362-118">Bu değer, `name` [FilterTables > bölümündeki bir FilterTable > öğesinin özniteliğiyle eşleşmelidir. \<](filtertables.md) [ \<](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="74362-118">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="74362-119">yalnızca routeonheader</span><span class="sxs-lookup"><span data-stu-id="74362-119">routeOnHeaderOnly</span></span>|<span data-ttu-id="74362-120">Filtrenin hem ileti gövdesini hem de üstbilgiyi veya yalnızca üstbilgiyi incelemenizi belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="74362-120">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="74362-121">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="74362-121">The default is `true`.</span></span>|  
|<span data-ttu-id="74362-122">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="74362-122">soapProcessingEnabled</span></span>|<span data-ttu-id="74362-123">SOAP işlemenin gerçekleşmesi gerekip gerekmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="74362-123">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74362-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="74362-124">Child Elements</span></span>  
 <span data-ttu-id="74362-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="74362-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74362-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="74362-126">Parent Elements</span></span>  
  
|<span data-ttu-id="74362-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="74362-127">Element</span></span>|<span data-ttu-id="74362-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74362-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74362-129">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="74362-129">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="74362-130">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="74362-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74362-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74362-131">Remarks</span></span>  
 <span data-ttu-id="74362-132">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi hizmet için yönlendirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="74362-132">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="74362-133">Bu öğedeki hizmet tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74362-133">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="74362-134">Bu yapılandırma bölümünü kullanarak, dağıtım düzeniniz değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74362-134">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="74362-135">Çalışma zamanında, kendi yönlendirme uzantınızı yeni yönlendirme ayarlarıyla kaydedebilir ve yönlendirme hizmeti yeni iletiler ve oturumlar için güncelleştirilmiş yapılandırma bilgilerini kullanmaya başlar ve bu durumda, hangi kuralların kullanıldığı konusunda uçuş iletilerini/oturumlarını bırakır başlatıldıklarında yer.</span><span class="sxs-lookup"><span data-stu-id="74362-135">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="74362-136">Bu sayede, çalışma zamanı sırasında yönlendirme hizmetinin oturum güvenli, geri dönüşüm için daha az yeniden yapılandırılması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74362-136">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
