---
title: 102 - WorkflowInstanceAbortedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bde4378d-4eea-4907-aaf2-c1a2bc770a37
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f47d94f41880e3463df883f94c2ff43e927a1001
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="102---workflowinstanceabortedrecord"></a><span data-ttu-id="e0eac-102">102 - WorkflowInstanceAbortedRecord</span><span class="sxs-lookup"><span data-stu-id="e0eac-102">102 - WorkflowInstanceAbortedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="e0eac-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e0eac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0eac-104">Kimliği</span><span class="sxs-lookup"><span data-stu-id="e0eac-104">Id</span></span>|<span data-ttu-id="e0eac-105">102</span><span class="sxs-lookup"><span data-stu-id="e0eac-105">102</span></span>|  
|<span data-ttu-id="e0eac-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e0eac-106">Keywords</span></span>|<span data-ttu-id="e0eac-107">Sorun giderme, ögesi, WFTracking EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="e0eac-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="e0eac-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e0eac-108">Level</span></span>|<span data-ttu-id="e0eac-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="e0eac-109">Warning</span></span>|  
|<span data-ttu-id="e0eac-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e0eac-110">Channel</span></span>|<span data-ttu-id="e0eac-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="e0eac-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e0eac-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0eac-112">Description</span></span>  
 <span data-ttu-id="e0eac-113">Bir iş akışı örneği WorkflowInstanceAbortedRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="e0eac-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e0eac-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e0eac-114">Message</span></span>  
 <span data-ttu-id="e0eac-115">TrackRecord WorkflowInstanceAbortedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamaları = %6, ProfileName = %7</span><span class="sxs-lookup"><span data-stu-id="e0eac-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span></span>  
  
## <a name="details"></a><span data-ttu-id="e0eac-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e0eac-116">Details</span></span>  
  
|<span data-ttu-id="e0eac-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e0eac-117">Data Item Name</span></span>|<span data-ttu-id="e0eac-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e0eac-118">Data Item Type</span></span>|<span data-ttu-id="e0eac-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0eac-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e0eac-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="e0eac-120">InstanceId</span></span>|<span data-ttu-id="e0eac-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="e0eac-121">xs:GUID</span></span>|<span data-ttu-id="e0eac-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="e0eac-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e0eac-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="e0eac-123">RecordNumber</span></span>|<span data-ttu-id="e0eac-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="e0eac-124">xs:long</span></span>|<span data-ttu-id="e0eac-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="e0eac-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="e0eac-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="e0eac-126">EventTime</span></span>|<span data-ttu-id="e0eac-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="e0eac-127">xs:dateTime</span></span>|<span data-ttu-id="e0eac-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="e0eac-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="e0eac-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="e0eac-129">ActivityDefinitionId</span></span>|<span data-ttu-id="e0eac-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="e0eac-130">xs:string</span></span>|<span data-ttu-id="e0eac-131">İş akışı Kök etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="e0eac-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="e0eac-132">Neden</span><span class="sxs-lookup"><span data-stu-id="e0eac-132">Reason</span></span>|<span data-ttu-id="e0eac-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="e0eac-133">xs:string</span></span>|<span data-ttu-id="e0eac-134">İş akışı neden iptal edildi</span><span class="sxs-lookup"><span data-stu-id="e0eac-134">The reason the workflow was aborted</span></span>|  
|<span data-ttu-id="e0eac-135">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0eac-135">Annotations</span></span>|<span data-ttu-id="e0eac-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="e0eac-136">xs:string</span></span>|<span data-ttu-id="e0eac-137">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="e0eac-137">The annotations that were added to this event.</span></span>  <span data-ttu-id="e0eac-138">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="e0eac-138">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="e0eac-139">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="e0eac-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="e0eac-140">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0eac-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="e0eac-141">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="e0eac-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="e0eac-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="e0eac-142">ProfileName</span></span>|<span data-ttu-id="e0eac-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="e0eac-143">xs:string</span></span>|<span data-ttu-id="e0eac-144">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="e0eac-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="e0eac-145">HostReference</span><span class="sxs-lookup"><span data-stu-id="e0eac-145">HostReference</span></span>|<span data-ttu-id="e0eac-146">xs: String</span><span class="sxs-lookup"><span data-stu-id="e0eac-146">xs:string</span></span>|<span data-ttu-id="e0eac-147">Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0eac-147">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="e0eac-148">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="e0eac-148">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="e0eac-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e0eac-149">AppDomain</span></span>|<span data-ttu-id="e0eac-150">xs: String</span><span class="sxs-lookup"><span data-stu-id="e0eac-150">xs:string</span></span>|<span data-ttu-id="e0eac-151">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e0eac-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
