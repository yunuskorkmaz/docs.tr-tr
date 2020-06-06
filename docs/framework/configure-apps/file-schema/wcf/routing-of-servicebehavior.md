---
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397727"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="c50db-102">\<routing> / \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="c50db-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="c50db-103">Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c50db-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="c50db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c50db-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c50db-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c50db-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c50db-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c50db-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c50db-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c50db-107">Attributes</span></span>  
  
|<span data-ttu-id="c50db-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c50db-108">Attribute</span></span>|<span data-ttu-id="c50db-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c50db-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c50db-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="c50db-110">filterTable</span></span>|<span data-ttu-id="c50db-111">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c50db-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="c50db-112">Bu değer `name` , bölümündeki bir öğenin özniteliğiyle eşleşmelidir [\<filterTable>](filtertable.md) [\<filterTables>](filtertables.md) .</span><span class="sxs-lookup"><span data-stu-id="c50db-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="c50db-113">yalnızca routeonheader</span><span class="sxs-lookup"><span data-stu-id="c50db-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="c50db-114">Filtrenin hem ileti gövdesini hem de üstbilgiyi veya yalnızca üstbilgiyi incelemenizi belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c50db-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="c50db-115">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="c50db-115">The default is `true`.</span></span>|  
|<span data-ttu-id="c50db-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="c50db-116">soapProcessingEnabled</span></span>|<span data-ttu-id="c50db-117">SOAP işlemenin gerçekleşmesi gerekip gerekmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="c50db-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c50db-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c50db-118">Child Elements</span></span>  
 <span data-ttu-id="c50db-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="c50db-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c50db-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c50db-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c50db-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c50db-121">Element</span></span>|<span data-ttu-id="c50db-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c50db-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c50db-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c50db-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c50db-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c50db-124">Remarks</span></span>  
 <span data-ttu-id="c50db-125">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi hizmet için yönlendirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c50db-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="c50db-126">Bu öğedeki hizmet tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c50db-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="c50db-127">Bu yapılandırma bölümünü kullanarak, dağıtım düzeniniz değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c50db-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="c50db-128">Çalışma zamanında, kendi yönlendirme uzantınızı yeni yönlendirme ayarlarıyla kaydedebilirsiniz ve yönlendirme hizmeti, yeni iletiler ve oturumlar için güncelleştirilmiş yapılandırma bilgilerini kullanmaya başlar. böylece, başlatıldıklarında hangi kuralların yerinde olduğunu kullanarak uçuş iletileri/oturumlarından çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="c50db-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="c50db-129">Bu sayede, çalışma zamanı sırasında yönlendirme hizmetinin oturum güvenli, geri dönüşüm için daha az yeniden yapılandırılması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c50db-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
