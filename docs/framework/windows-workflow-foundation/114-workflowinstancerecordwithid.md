---
title: 114 - WorkflowInstanceRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bd8b4a1-b210-4c07-8156-f19392318c08
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57eab386e8d0486caa98a6e2f3d2f72e9e89fab7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="114---workflowinstancerecordwithid"></a><span data-ttu-id="11a21-102">114 - WorkflowInstanceRecordWithId</span><span class="sxs-lookup"><span data-stu-id="11a21-102">114 - WorkflowInstanceRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="11a21-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="11a21-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11a21-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="11a21-104">ID</span></span>|<span data-ttu-id="11a21-105">114</span><span class="sxs-lookup"><span data-stu-id="11a21-105">114</span></span>|  
|<span data-ttu-id="11a21-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="11a21-106">Keywords</span></span>|<span data-ttu-id="11a21-107">Ögesi, WFTracking</span><span class="sxs-lookup"><span data-stu-id="11a21-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="11a21-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="11a21-108">Level</span></span>|<span data-ttu-id="11a21-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="11a21-109">Information</span></span>|  
|<span data-ttu-id="11a21-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="11a21-110">Channel</span></span>|<span data-ttu-id="11a21-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="11a21-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="11a21-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11a21-112">Description</span></span>  
 <span data-ttu-id="11a21-113">Bir iş akışı örneği iş akışı durumlarını WorkflowInstanceRecord yayar, bu olay ETW İzleme katılımcı tarafından gösterilen: başlatıldı, sürdürüldü, kalıcı, boşta, silinen, tamamlandı, iptal, kaldırıldığında, Unsuspended.</span><span class="sxs-lookup"><span data-stu-id="11a21-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceRecord for workflow states : Started, Resumed, Persisted, Idle, Deleted, Completed, Canceled, Unloaded, Unsuspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="11a21-114">İleti</span><span class="sxs-lookup"><span data-stu-id="11a21-114">Message</span></span>  
 <span data-ttu-id="11a21-115">TrackRecord WorkflowInstanceRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, durum = %5, ek açıklamaları = %6, ProfileName = % 7 ' ye WorkflowDefinitionIdentity %8 =</span><span class="sxs-lookup"><span data-stu-id="11a21-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="11a21-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="11a21-116">Details</span></span>  
  
|<span data-ttu-id="11a21-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="11a21-117">Data Item Name</span></span>|<span data-ttu-id="11a21-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="11a21-118">Data Item Type</span></span>|<span data-ttu-id="11a21-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11a21-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="11a21-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="11a21-120">InstanceId</span></span>|<span data-ttu-id="11a21-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="11a21-121">xs:GUID</span></span>|<span data-ttu-id="11a21-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="11a21-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="11a21-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="11a21-123">RecordNumber</span></span>|<span data-ttu-id="11a21-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="11a21-124">xs:long</span></span>|<span data-ttu-id="11a21-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="11a21-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="11a21-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="11a21-126">EventTime</span></span>|<span data-ttu-id="11a21-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="11a21-127">xs:dateTime</span></span>|<span data-ttu-id="11a21-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="11a21-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="11a21-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="11a21-129">ActivityDefinitionId</span></span>|<span data-ttu-id="11a21-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a21-130">xs:string</span></span>|<span data-ttu-id="11a21-131">İş akışı Kök etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="11a21-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="11a21-132">Durum</span><span class="sxs-lookup"><span data-stu-id="11a21-132">State</span></span>|<span data-ttu-id="11a21-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a21-133">xs:string</span></span>|<span data-ttu-id="11a21-134">İş akışının geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="11a21-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="11a21-135">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11a21-135">Annotations</span></span>|<span data-ttu-id="11a21-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a21-136">xs:string</span></span>|<span data-ttu-id="11a21-137">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="11a21-137">The annotations that were added to this event.</span></span> <span data-ttu-id="11a21-138">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="11a21-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="11a21-139">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="11a21-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="11a21-140">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="11a21-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="11a21-141">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="11a21-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="11a21-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="11a21-142">ProfileName</span></span>|<span data-ttu-id="11a21-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a21-143">xs:string</span></span>|<span data-ttu-id="11a21-144">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="11a21-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="11a21-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="11a21-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="11a21-146">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a21-146">xs:string</span></span>|<span data-ttu-id="11a21-147">İş akışı tanımı kimliği</span><span class="sxs-lookup"><span data-stu-id="11a21-147">The workflow definition id</span></span>|  
|<span data-ttu-id="11a21-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="11a21-148">AppDomain</span></span>|<span data-ttu-id="11a21-149">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a21-149">xs:string</span></span>|<span data-ttu-id="11a21-150">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="11a21-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
