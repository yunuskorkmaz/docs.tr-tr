---
title: 113 - WorkflowInstanceTerminatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f53204ee-4ea2-45e1-8859-e86d07305efd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a34a49314c71bc5ec0d68388ae8c166d3a9d30d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="113---workflowinstanceterminatedrecord"></a><span data-ttu-id="1bffb-102">113 - WorkflowInstanceTerminatedRecord</span><span class="sxs-lookup"><span data-stu-id="1bffb-102">113 - WorkflowInstanceTerminatedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="1bffb-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1bffb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1bffb-104">Kimliği</span><span class="sxs-lookup"><span data-stu-id="1bffb-104">Id</span></span>|<span data-ttu-id="1bffb-105">113</span><span class="sxs-lookup"><span data-stu-id="1bffb-105">113</span></span>|  
|<span data-ttu-id="1bffb-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1bffb-106">Keywords</span></span>|<span data-ttu-id="1bffb-107">Sorun giderme, ögesi, WFTracking EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="1bffb-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="1bffb-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1bffb-108">Level</span></span>|<span data-ttu-id="1bffb-109">Hata</span><span class="sxs-lookup"><span data-stu-id="1bffb-109">Error</span></span>|  
|<span data-ttu-id="1bffb-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1bffb-110">Channel</span></span>|<span data-ttu-id="1bffb-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="1bffb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1bffb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bffb-112">Description</span></span>  
 <span data-ttu-id="1bffb-113">Bir iş akışı örneği WorkflowInstanceTerminatedRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1bffb-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceTerminatedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1bffb-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1bffb-114">Message</span></span>  
 <span data-ttu-id="1bffb-115">TrackRecord WorkflowInstanceTerminatedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamaları = %6, ProfileName = %7</span><span class="sxs-lookup"><span data-stu-id="1bffb-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span></span>  
  
## <a name="details"></a><span data-ttu-id="1bffb-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1bffb-116">Details</span></span>  
  
|<span data-ttu-id="1bffb-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1bffb-117">Data Item Name</span></span>|<span data-ttu-id="1bffb-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1bffb-118">Data Item Type</span></span>|<span data-ttu-id="1bffb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bffb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1bffb-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="1bffb-120">InstanceId</span></span>|<span data-ttu-id="1bffb-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="1bffb-121">xs:GUID</span></span>|<span data-ttu-id="1bffb-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="1bffb-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="1bffb-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="1bffb-123">RecordNumber</span></span>|<span data-ttu-id="1bffb-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="1bffb-124">xs:long</span></span>|<span data-ttu-id="1bffb-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="1bffb-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="1bffb-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="1bffb-126">EventTime</span></span>|<span data-ttu-id="1bffb-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="1bffb-127">xs:dateTime</span></span>|<span data-ttu-id="1bffb-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="1bffb-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="1bffb-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="1bffb-129">ActivityDefinitionId</span></span>|<span data-ttu-id="1bffb-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bffb-130">xs:string</span></span>|<span data-ttu-id="1bffb-131">İş akışı Kök etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="1bffb-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="1bffb-132">Neden</span><span class="sxs-lookup"><span data-stu-id="1bffb-132">Reason</span></span>|<span data-ttu-id="1bffb-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bffb-133">xs:string</span></span>|<span data-ttu-id="1bffb-134">İş akışı neden sonlandırıldı</span><span class="sxs-lookup"><span data-stu-id="1bffb-134">The reason the workflow was terminated</span></span>|  
|<span data-ttu-id="1bffb-135">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bffb-135">Annotations</span></span>|<span data-ttu-id="1bffb-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bffb-136">xs:string</span></span>|<span data-ttu-id="1bffb-137">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="1bffb-137">The annotations that were added to this event.</span></span>  <span data-ttu-id="1bffb-138">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="1bffb-138">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="1bffb-139">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="1bffb-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="1bffb-140">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bffb-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="1bffb-141">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="1bffb-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="1bffb-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="1bffb-142">ProfileName</span></span>|<span data-ttu-id="1bffb-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bffb-143">xs:string</span></span>|<span data-ttu-id="1bffb-144">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="1bffb-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="1bffb-145">HostReference</span><span class="sxs-lookup"><span data-stu-id="1bffb-145">HostReference</span></span>|<span data-ttu-id="1bffb-146">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bffb-146">xs:string</span></span>|<span data-ttu-id="1bffb-147">Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bffb-147">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="1bffb-148">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="1bffb-148">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="1bffb-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1bffb-149">AppDomain</span></span>|<span data-ttu-id="1bffb-150">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bffb-150">xs:string</span></span>|<span data-ttu-id="1bffb-151">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1bffb-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
