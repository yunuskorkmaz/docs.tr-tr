---
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: cd53b720bad5752189f1c30d9e4acd3a66830396
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150888"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="99e4d-102">\<routing> / \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="99e4d-102">\<routing> of \<serviceBehavior></span></span>

<span data-ttu-id="99e4d-103">Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="99e4d-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="99e4d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="99e4d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99e4d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99e4d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="99e4d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99e4d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99e4d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99e4d-107">Attributes</span></span>  
  
|<span data-ttu-id="99e4d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="99e4d-108">Attribute</span></span>|<span data-ttu-id="99e4d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99e4d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99e4d-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="99e4d-110">filterTable</span></span>|<span data-ttu-id="99e4d-111">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="99e4d-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="99e4d-112">Bu değer `name` , bölümündeki bir öğenin özniteliğiyle eşleşmelidir [\<filterTable>](filtertable.md) [\<filterTables>](filtertables.md) .</span><span class="sxs-lookup"><span data-stu-id="99e4d-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="99e4d-113">yalnızca routeonheader</span><span class="sxs-lookup"><span data-stu-id="99e4d-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="99e4d-114">Filtrenin hem ileti gövdesini hem de üstbilgiyi veya yalnızca üstbilgiyi incelemenizi belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="99e4d-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="99e4d-115">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="99e4d-115">The default is `true`.</span></span>|  
|<span data-ttu-id="99e4d-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="99e4d-116">soapProcessingEnabled</span></span>|<span data-ttu-id="99e4d-117">SOAP işlemenin gerçekleşmesi gerekip gerekmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="99e4d-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99e4d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99e4d-118">Child Elements</span></span>  

 <span data-ttu-id="99e4d-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="99e4d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99e4d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99e4d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="99e4d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="99e4d-121">Element</span></span>|<span data-ttu-id="99e4d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99e4d-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="99e4d-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="99e4d-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99e4d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99e4d-124">Remarks</span></span>  

 <span data-ttu-id="99e4d-125">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi hizmet için yönlendirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="99e4d-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="99e4d-126">Bu öğedeki hizmet tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99e4d-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="99e4d-127">Bu yapılandırma bölümünü kullanarak, dağıtım düzeniniz değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99e4d-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="99e4d-128">Çalışma zamanında, kendi yönlendirme uzantınızı yeni yönlendirme ayarlarıyla kaydedebilirsiniz ve yönlendirme hizmeti, yeni iletiler ve oturumlar için güncelleştirilmiş yapılandırma bilgilerini kullanmaya başlar. böylece, başlatıldıklarında hangi kuralların yerinde olduğunu kullanarak uçuş iletileri/oturumlarından çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="99e4d-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="99e4d-129">Bu sayede, çalışma zamanı sırasında yönlendirme hizmetinin oturum güvenli, geri dönüşüm için daha az yeniden yapılandırılması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99e4d-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
