---
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 73a610056f94efe144705968eaf97c8314c1ae0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934193"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="c1844-102">\<\<ServiceBehavior > yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="c1844-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="c1844-103">Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1844-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="c1844-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c1844-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1844-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c1844-105">\<behaviors></span></span>  
<span data-ttu-id="c1844-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c1844-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c1844-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c1844-107">\<behavior></span></span>  
<span data-ttu-id="c1844-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="c1844-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1844-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1844-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1844-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1844-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c1844-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1844-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1844-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1844-112">Attributes</span></span>  
  
|<span data-ttu-id="c1844-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c1844-113">Attribute</span></span>|<span data-ttu-id="c1844-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1844-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1844-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="c1844-115">filterTable</span></span>|<span data-ttu-id="c1844-116">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c1844-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="c1844-117">Bu değer, `name` [FilterTables > bölümündeki bir FilterTable > öğesinin özniteliğiyle eşleşmelidir. \<](filtertables.md) [ \<](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="c1844-117">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="c1844-118">yalnızca routeonheader</span><span class="sxs-lookup"><span data-stu-id="c1844-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="c1844-119">Filtrenin hem ileti gövdesini hem de üstbilgiyi veya yalnızca üstbilgiyi incelemenizi belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c1844-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="c1844-120">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c1844-120">The default is `true`.</span></span>|  
|<span data-ttu-id="c1844-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="c1844-121">soapProcessingEnabled</span></span>|<span data-ttu-id="c1844-122">SOAP işlemenin gerçekleşmesi gerekip gerekmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="c1844-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1844-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1844-123">Child Elements</span></span>  
 <span data-ttu-id="c1844-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1844-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1844-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1844-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c1844-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1844-126">Element</span></span>|<span data-ttu-id="c1844-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1844-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1844-128">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c1844-128">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c1844-129">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1844-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1844-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1844-130">Remarks</span></span>  
 <span data-ttu-id="c1844-131">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi hizmet için yönlendirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1844-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="c1844-132">Bu öğedeki hizmet tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1844-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="c1844-133">Bu yapılandırma bölümünü kullanarak, dağıtım düzeniniz değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1844-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="c1844-134">Çalışma zamanında, kendi yönlendirme uzantınızı yeni yönlendirme ayarlarıyla kaydedebilir ve yönlendirme hizmeti yeni iletiler ve oturumlar için güncelleştirilmiş yapılandırma bilgilerini kullanmaya başlar ve bu durumda, hangi kuralların kullanıldığı konusunda uçuş iletilerini/oturumlarını bırakır başlatıldıklarında yer.</span><span class="sxs-lookup"><span data-stu-id="c1844-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="c1844-135">Bu sayede, çalışma zamanı sırasında yönlendirme hizmetinin oturum güvenli, geri dönüşüm için daha az yeniden yapılandırılması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1844-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
