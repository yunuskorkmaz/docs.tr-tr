---
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: b7a9be18395ef8878900d754b5aa5afdeee0cff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783064"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="be936-102">\<Yönlendirme >, \<serviceBehavior ></span><span class="sxs-lookup"><span data-stu-id="be936-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="be936-103">Dinamik yönlendirme yapılandırması değişikliğini izin vermek için yönlendirme hizmeti çalışma zamanı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="be936-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="be936-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be936-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be936-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="be936-105">\<behaviors></span></span>  
<span data-ttu-id="be936-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="be936-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="be936-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="be936-107">\<behavior></span></span>  
<span data-ttu-id="be936-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="be936-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be936-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be936-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be936-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be936-110">Attributes and Elements</span></span>  
 <span data-ttu-id="be936-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be936-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be936-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be936-112">Attributes</span></span>  
  
|<span data-ttu-id="be936-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="be936-113">Attribute</span></span>|<span data-ttu-id="be936-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be936-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be936-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="be936-115">filterTable</span></span>|<span data-ttu-id="be936-116">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="be936-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="be936-117">Bu değer eşleşmelidir `name` özniteliği bir [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) öğesinde [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="be936-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="be936-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="be936-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="be936-119">Filtre hem ileti gövdesi ve üst bilgi veya üst bilgi inceleyin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="be936-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="be936-120">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="be936-120">The default is `true`.</span></span>|  
|<span data-ttu-id="be936-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="be936-121">soapProcessingEnabled</span></span>|<span data-ttu-id="be936-122">SOAP işleme olmamalıdır olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="be936-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be936-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be936-123">Child Elements</span></span>  
 <span data-ttu-id="be936-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="be936-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be936-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be936-125">Parent Elements</span></span>  
  
|<span data-ttu-id="be936-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="be936-126">Element</span></span>|<span data-ttu-id="be936-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be936-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be936-128">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="be936-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="be936-129">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="be936-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be936-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be936-130">Remarks</span></span>  
 <span data-ttu-id="be936-131">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi, hizmet için yönlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="be936-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="be936-132">Bu öğe hizmeti tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be936-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="be936-133">Bu yapılandırma bölümü kullanarak dağıtım desen değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be936-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="be936-134">Çalışma zamanında, yönlendirme yeni ayarlarla yönlendirme uzantınızı kaydedebilir ve yönlendirme hizmeti yeni iletileri için güncelleştirilmiş yapılandırma bilgilerini kullanarak başlar ve oturumlar, hangi kuralları kullanarak uçuşan iletileri/oturumları bırakarak çalışırken bulunduğunuz Bunlar başlatıldığında yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="be936-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="be936-135">Bu oturum için güvenli, geri dönüşüm daha az yeniden yapılandırılmasını yönlendirme hizmeti çalışma zamanı sırasında yapabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="be936-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
