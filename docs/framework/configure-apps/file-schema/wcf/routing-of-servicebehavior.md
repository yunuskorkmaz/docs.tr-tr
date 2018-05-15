---
title: '&lt;serviceBehavior&gt; &lt;yönlendirme&gt;'
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 5fb7febe365f73acf09ba74b07215fe9cc659efb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a><span data-ttu-id="40ace-102">&lt;serviceBehavior&gt; &lt;yönlendirme&gt;</span><span class="sxs-lookup"><span data-stu-id="40ace-102">&lt;routing&gt; of &lt;serviceBehavior&gt;</span></span>
<span data-ttu-id="40ace-103">Dinamik yönlendirme yapılandırması değiştirilmesine izin veren yönlendirme hizmeti çalışma zamanı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="40ace-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="40ace-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40ace-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40ace-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="40ace-105">\<behaviors></span></span>  
<span data-ttu-id="40ace-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="40ace-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="40ace-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="40ace-107">\<behavior></span></span>  
<span data-ttu-id="40ace-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="40ace-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ace-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40ace-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40ace-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40ace-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40ace-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40ace-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40ace-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40ace-112">Attributes</span></span>  
  
|<span data-ttu-id="40ace-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40ace-113">Attribute</span></span>|<span data-ttu-id="40ace-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40ace-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40ace-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="40ace-115">filterTable</span></span>|<span data-ttu-id="40ace-116">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="40ace-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="40ace-117">Bu değer eşleşmelidir `name` özniteliği bir [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) öğesinde [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="40ace-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="40ace-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="40ace-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="40ace-119">Filtre hem ileti gövdesi ve üst bilgi veya yalnızca üstbilgi inceleyin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="40ace-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="40ace-120">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40ace-120">The default is `true`.</span></span>|  
|<span data-ttu-id="40ace-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="40ace-121">soapProcessingEnabled</span></span>|<span data-ttu-id="40ace-122">SOAP işleme gerçekleşip gerçekleşmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="40ace-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40ace-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40ace-123">Child Elements</span></span>  
 <span data-ttu-id="40ace-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="40ace-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40ace-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40ace-125">Parent Elements</span></span>  
  
|<span data-ttu-id="40ace-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="40ace-126">Element</span></span>|<span data-ttu-id="40ace-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40ace-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40ace-128">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="40ace-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="40ace-129">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="40ace-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40ace-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40ace-130">Remarks</span></span>  
 <span data-ttu-id="40ace-131">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi için hizmeti Yönlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="40ace-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="40ace-132">Bu öğe hizmeti tarafından kullanılacak gerçek yönlendirme tablosu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40ace-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="40ace-133">Bu yapılandırma bölümü kullanarak, dağıtım düzeni değiştiğinde yönlendirme ayarlarınızı kolay bir şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40ace-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="40ace-134">Çalışma zamanında yeni yönlendirme ayarlarıyla yönlendirme uzantınızı kaydedebilirsiniz ve yeni iletileri güncelleştirilmiş yapılandırma bilgilerini kullanarak yönlendirme hizmeti başlar ve ne olursa olsun kuralları kullanarak yürütülen iletileri/oturumları bırakarak sırasında oturumlar, bulunduğunuz Bunlar başlatıldığında yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="40ace-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="40ace-135">Bu oturum için güvenli, daha az geri dönüşüm yeniden yapılandırılması yönlendirme hizmeti çalışma zamanı sırasında yeteneği verir.</span><span class="sxs-lookup"><span data-stu-id="40ace-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
  
