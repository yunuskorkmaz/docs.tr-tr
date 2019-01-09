---
title: '&lt;serviceBehavior&gt; &lt;yönlendirme&gt;'
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0a007eb33063f8f44098a8c63708255b884b5fdc
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146855"
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a><span data-ttu-id="4e487-102">&lt;serviceBehavior&gt; &lt;yönlendirme&gt;</span><span class="sxs-lookup"><span data-stu-id="4e487-102">&lt;routing&gt; of &lt;serviceBehavior&gt;</span></span>
<span data-ttu-id="4e487-103">Dinamik yönlendirme yapılandırması değişikliğini izin vermek için yönlendirme hizmeti çalışma zamanı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e487-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="4e487-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e487-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e487-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="4e487-105">\<behaviors></span></span>  
<span data-ttu-id="4e487-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4e487-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4e487-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4e487-107">\<behavior></span></span>  
<span data-ttu-id="4e487-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="4e487-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e487-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e487-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e487-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e487-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4e487-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4e487-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e487-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4e487-112">Attributes</span></span>  
  
|<span data-ttu-id="4e487-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4e487-113">Attribute</span></span>|<span data-ttu-id="4e487-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e487-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e487-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="4e487-115">filterTable</span></span>|<span data-ttu-id="4e487-116">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="4e487-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="4e487-117">Bu değer eşleşmelidir `name` özniteliği bir [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) öğesinde [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="4e487-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="4e487-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="4e487-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="4e487-119">Filtre hem ileti gövdesi ve üst bilgi veya üst bilgi inceleyin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4e487-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="4e487-120">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4e487-120">The default is `true`.</span></span>|  
|<span data-ttu-id="4e487-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="4e487-121">soapProcessingEnabled</span></span>|<span data-ttu-id="4e487-122">SOAP işleme olmamalıdır olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4e487-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e487-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e487-123">Child Elements</span></span>  
 <span data-ttu-id="4e487-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e487-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e487-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e487-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4e487-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e487-126">Element</span></span>|<span data-ttu-id="4e487-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e487-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e487-128">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4e487-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4e487-129">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e487-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e487-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e487-130">Remarks</span></span>  
 <span data-ttu-id="4e487-131">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi, hizmet için yönlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e487-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="4e487-132">Bu öğe hizmeti tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e487-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="4e487-133">Bu yapılandırma bölümü kullanarak dağıtım desen değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e487-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="4e487-134">Çalışma zamanında, yönlendirme yeni ayarlarla yönlendirme uzantınızı kaydedebilir ve yönlendirme hizmeti yeni iletileri için güncelleştirilmiş yapılandırma bilgilerini kullanarak başlar ve oturumlar, hangi kuralları kullanarak uçuşan iletileri/oturumları bırakarak çalışırken bulunduğunuz Bunlar başlatıldığında yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="4e487-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="4e487-135">Bu oturum için güvenli, geri dönüşüm daha az yeniden yapılandırılmasını yönlendirme hizmeti çalışma zamanı sırasında yapabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e487-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
  
