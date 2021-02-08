---
description: 'Hakkında daha fazla bilgi <routing> edinin: <serviceBehavior>'
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 1d8a056d708b3c42aeccf3e46a0703b3fc78a17d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786895"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="7a4bb-103">\<routing> / \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="7a4bb-103">\<routing> of \<serviceBehavior></span></span>

<span data-ttu-id="7a4bb-104">Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-104">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="7a4bb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a4bb-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a4bb-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a4bb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7a4bb-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a4bb-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a4bb-108">Attributes</span></span>  
  
|<span data-ttu-id="7a4bb-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7a4bb-109">Attribute</span></span>|<span data-ttu-id="7a4bb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a4bb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a4bb-111">filterTable</span><span class="sxs-lookup"><span data-stu-id="7a4bb-111">filterTable</span></span>|<span data-ttu-id="7a4bb-112">Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-112">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="7a4bb-113">Bu değer `name` , bölümündeki bir öğenin özniteliğiyle eşleşmelidir [\<filterTable>](filtertable.md) [\<filterTables>](filtertables.md) .</span><span class="sxs-lookup"><span data-stu-id="7a4bb-113">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="7a4bb-114">yalnızca routeonheader</span><span class="sxs-lookup"><span data-stu-id="7a4bb-114">routeOnHeaderOnly</span></span>|<span data-ttu-id="7a4bb-115">Filtrenin hem ileti gövdesini hem de üstbilgiyi veya yalnızca üstbilgiyi incelemenizi belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-115">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="7a4bb-116">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-116">The default is `true`.</span></span>|  
|<span data-ttu-id="7a4bb-117">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="7a4bb-117">soapProcessingEnabled</span></span>|<span data-ttu-id="7a4bb-118">SOAP işlemenin gerçekleşmesi gerekip gerekmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-118">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a4bb-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a4bb-119">Child Elements</span></span>  

 <span data-ttu-id="7a4bb-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a4bb-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a4bb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7a4bb-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a4bb-122">Element</span></span>|<span data-ttu-id="7a4bb-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a4bb-123">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7a4bb-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-124">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a4bb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a4bb-125">Remarks</span></span>  

 <span data-ttu-id="7a4bb-126">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi hizmet için yönlendirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-126">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="7a4bb-127">Bu öğedeki hizmet tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-127">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="7a4bb-128">Bu yapılandırma bölümünü kullanarak, dağıtım düzeniniz değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-128">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="7a4bb-129">Çalışma zamanında, kendi yönlendirme uzantınızı yeni yönlendirme ayarlarıyla kaydedebilirsiniz ve yönlendirme hizmeti, yeni iletiler ve oturumlar için güncelleştirilmiş yapılandırma bilgilerini kullanmaya başlar. böylece, başlatıldıklarında hangi kuralların yerinde olduğunu kullanarak uçuş iletileri/oturumlarından çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-129">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="7a4bb-130">Bu sayede, çalışma zamanı sırasında yönlendirme hizmetinin oturum güvenli, geri dönüşüm için daha az yeniden yapılandırılması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-130">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
