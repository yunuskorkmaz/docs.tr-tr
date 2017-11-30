---
title: 117 - WorkflowInstanceTerminatedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c8b2bc6325ec6f5cf1c3af8b7748a45ad21809cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a><span data-ttu-id="71b81-102">117 - WorkflowInstanceTerminatedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="71b81-102">117 - WorkflowInstanceTerminatedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="71b81-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="71b81-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71b81-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="71b81-104">ID</span></span>|<span data-ttu-id="71b81-105">117</span><span class="sxs-lookup"><span data-stu-id="71b81-105">117</span></span>|  
|<span data-ttu-id="71b81-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="71b81-106">Keywords</span></span>|<span data-ttu-id="71b81-107">Ögesi, WFTracking</span><span class="sxs-lookup"><span data-stu-id="71b81-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="71b81-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="71b81-108">Level</span></span>|<span data-ttu-id="71b81-109">Hata</span><span class="sxs-lookup"><span data-stu-id="71b81-109">Error</span></span>|  
|<span data-ttu-id="71b81-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="71b81-110">Channel</span></span>|<span data-ttu-id="71b81-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="71b81-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="71b81-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71b81-112">Description</span></span>  
 <span data-ttu-id="71b81-113">Bir iş akışı örneği WorkflowInstanceTerminatedRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="71b81-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceTerminatedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="71b81-114">İleti</span><span class="sxs-lookup"><span data-stu-id="71b81-114">Message</span></span>  
 <span data-ttu-id="71b81-115">TrackRecord WorkflowInstanceTerminatedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamaları = %6, ProfileName = % 7 ' ye WorkflowDefinitionIdentity %8 =</span><span class="sxs-lookup"><span data-stu-id="71b81-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="71b81-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="71b81-116">Details</span></span>  
  
|<span data-ttu-id="71b81-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="71b81-117">Data Item Name</span></span>|<span data-ttu-id="71b81-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="71b81-118">Data Item Type</span></span>|<span data-ttu-id="71b81-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71b81-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="71b81-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="71b81-120">InstanceId</span></span>|<span data-ttu-id="71b81-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="71b81-121">xs:GUID</span></span>|<span data-ttu-id="71b81-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="71b81-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="71b81-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="71b81-123">RecordNumber</span></span>|<span data-ttu-id="71b81-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="71b81-124">xs:long</span></span>|<span data-ttu-id="71b81-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="71b81-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="71b81-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="71b81-126">EventTime</span></span>|<span data-ttu-id="71b81-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="71b81-127">xs:dateTime</span></span>|<span data-ttu-id="71b81-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="71b81-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="71b81-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="71b81-129">ActivityDefinitionId</span></span>|<span data-ttu-id="71b81-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="71b81-130">xs:string</span></span>|<span data-ttu-id="71b81-131">İş akışı Kök etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="71b81-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="71b81-132">Durum</span><span class="sxs-lookup"><span data-stu-id="71b81-132">State</span></span>|<span data-ttu-id="71b81-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="71b81-133">xs:string</span></span>|<span data-ttu-id="71b81-134">İş akışının geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="71b81-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="71b81-135">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71b81-135">Annotations</span></span>|<span data-ttu-id="71b81-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="71b81-136">xs:string</span></span>|<span data-ttu-id="71b81-137">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="71b81-137">The annotations that were added to this event.</span></span> <span data-ttu-id="71b81-138">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="71b81-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="71b81-139">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="71b81-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="71b81-140">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="71b81-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="71b81-141">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="71b81-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="71b81-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="71b81-142">ProfileName</span></span>|<span data-ttu-id="71b81-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="71b81-143">xs:string</span></span>|<span data-ttu-id="71b81-144">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="71b81-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="71b81-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="71b81-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="71b81-146">xs: String</span><span class="sxs-lookup"><span data-stu-id="71b81-146">xs:string</span></span>|<span data-ttu-id="71b81-147">İş akışı tanımı kimliği</span><span class="sxs-lookup"><span data-stu-id="71b81-147">The workflow definition id</span></span>|  
|<span data-ttu-id="71b81-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="71b81-148">AppDomain</span></span>|<span data-ttu-id="71b81-149">xs: String</span><span class="sxs-lookup"><span data-stu-id="71b81-149">xs:string</span></span>|<span data-ttu-id="71b81-150">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="71b81-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
