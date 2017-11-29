---
title: 116 - WorkflowInstanceSuspendedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38232c03-6139-4494-a020-79bc83eb9dce
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6dc875721c323a48f5cc0b49e4ef0e7c167622b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="116---workflowinstancesuspendedrecordwithid"></a><span data-ttu-id="b9b6e-102">116 - WorkflowInstanceSuspendedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="b9b6e-102">116 - WorkflowInstanceSuspendedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="b9b6e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b9b6e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9b6e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b9b6e-104">ID</span></span>|<span data-ttu-id="b9b6e-105">116</span><span class="sxs-lookup"><span data-stu-id="b9b6e-105">116</span></span>|  
|<span data-ttu-id="b9b6e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b9b6e-106">Keywords</span></span>|<span data-ttu-id="b9b6e-107">Ögesi, WFTracking</span><span class="sxs-lookup"><span data-stu-id="b9b6e-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="b9b6e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b9b6e-108">Level</span></span>|<span data-ttu-id="b9b6e-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="b9b6e-109">Information</span></span>|  
|<span data-ttu-id="b9b6e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b9b6e-110">Channel</span></span>|<span data-ttu-id="b9b6e-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="b9b6e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b9b6e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9b6e-112">Description</span></span>  
 <span data-ttu-id="b9b6e-113">Bir iş akışı örneği WorkflowInstanceSuspended kaydı yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceSuspended Record.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b9b6e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b9b6e-114">Message</span></span>  
 <span data-ttu-id="b9b6e-115">TrackRecord WorkflowInstanceSuspendedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamaları = %6, ProfileName = % 7 ' ye WorkflowDefinitionIdentity %8 =</span><span class="sxs-lookup"><span data-stu-id="b9b6e-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="b9b6e-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b9b6e-116">Details</span></span>  
  
|<span data-ttu-id="b9b6e-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b9b6e-117">Data Item Name</span></span>|<span data-ttu-id="b9b6e-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b9b6e-118">Data Item Type</span></span>|<span data-ttu-id="b9b6e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9b6e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b9b6e-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="b9b6e-120">InstanceId</span></span>|<span data-ttu-id="b9b6e-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="b9b6e-121">xs:GUID</span></span>|<span data-ttu-id="b9b6e-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="b9b6e-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b9b6e-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="b9b6e-123">RecordNumber</span></span>|<span data-ttu-id="b9b6e-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="b9b6e-124">xs:long</span></span>|<span data-ttu-id="b9b6e-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="b9b6e-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="b9b6e-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="b9b6e-126">EventTime</span></span>|<span data-ttu-id="b9b6e-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="b9b6e-127">xs:dateTime</span></span>|<span data-ttu-id="b9b6e-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="b9b6e-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="b9b6e-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b9b6e-129">ActivityDefinitionId</span></span>|<span data-ttu-id="b9b6e-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="b9b6e-130">xs:string</span></span>|<span data-ttu-id="b9b6e-131">İş akışı Kök etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="b9b6e-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="b9b6e-132">Durum</span><span class="sxs-lookup"><span data-stu-id="b9b6e-132">State</span></span>|<span data-ttu-id="b9b6e-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="b9b6e-133">xs:string</span></span>|<span data-ttu-id="b9b6e-134">İş akışının geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="b9b6e-135">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9b6e-135">Annotations</span></span>|<span data-ttu-id="b9b6e-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="b9b6e-136">xs:string</span></span>|<span data-ttu-id="b9b6e-137">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-137">The annotations that were added to this event.</span></span> <span data-ttu-id="b9b6e-138">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="b9b6e-139">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="b9b6e-140">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="b9b6e-141">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="b9b6e-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="b9b6e-142">ProfileName</span></span>|<span data-ttu-id="b9b6e-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="b9b6e-143">xs:string</span></span>|<span data-ttu-id="b9b6e-144">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="b9b6e-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="b9b6e-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="b9b6e-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="b9b6e-146">xs: String</span><span class="sxs-lookup"><span data-stu-id="b9b6e-146">xs:string</span></span>|<span data-ttu-id="b9b6e-147">İş akışı tanımı kimliği</span><span class="sxs-lookup"><span data-stu-id="b9b6e-147">The workflow definition id</span></span>|  
|<span data-ttu-id="b9b6e-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b9b6e-148">AppDomain</span></span>|<span data-ttu-id="b9b6e-149">xs: String</span><span class="sxs-lookup"><span data-stu-id="b9b6e-149">xs:string</span></span>|<span data-ttu-id="b9b6e-150">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
