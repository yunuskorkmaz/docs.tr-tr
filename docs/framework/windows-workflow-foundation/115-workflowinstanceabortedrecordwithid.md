---
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 314f880f1fc2d78efc59f73f37122d03ae30cf72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="115---workflowinstanceabortedrecordwithid"></a><span data-ttu-id="c33df-102">115 - WorkflowInstanceAbortedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="c33df-102">115 - WorkflowInstanceAbortedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="c33df-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c33df-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c33df-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c33df-104">ID</span></span>|<span data-ttu-id="c33df-105">115</span><span class="sxs-lookup"><span data-stu-id="c33df-105">115</span></span>|  
|<span data-ttu-id="c33df-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c33df-106">Keywords</span></span>|<span data-ttu-id="c33df-107">Ögesi, WFTracking</span><span class="sxs-lookup"><span data-stu-id="c33df-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="c33df-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c33df-108">Level</span></span>|<span data-ttu-id="c33df-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="c33df-109">Warning</span></span>|  
|<span data-ttu-id="c33df-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c33df-110">Channel</span></span>|<span data-ttu-id="c33df-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="c33df-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c33df-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c33df-112">Description</span></span>  
 <span data-ttu-id="c33df-113">Bir iş akışı örneği WorkflowInstanceAbortedRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="c33df-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c33df-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c33df-114">Message</span></span>  
 <span data-ttu-id="c33df-115">TrackRecord WorkflowInstanceAbortedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamaları = %6, ProfileName = % 7 ' ye WorkflowDefinitionIdentity %8 =</span><span class="sxs-lookup"><span data-stu-id="c33df-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="c33df-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c33df-116">Details</span></span>  
  
|<span data-ttu-id="c33df-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c33df-117">Data Item Name</span></span>|<span data-ttu-id="c33df-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c33df-118">Data Item Type</span></span>|<span data-ttu-id="c33df-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c33df-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c33df-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="c33df-120">InstanceId</span></span>|<span data-ttu-id="c33df-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="c33df-121">xs:GUID</span></span>|<span data-ttu-id="c33df-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="c33df-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="c33df-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="c33df-123">RecordNumber</span></span>|<span data-ttu-id="c33df-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="c33df-124">xs:long</span></span>|<span data-ttu-id="c33df-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="c33df-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="c33df-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="c33df-126">EventTime</span></span>|<span data-ttu-id="c33df-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="c33df-127">xs:dateTime</span></span>|<span data-ttu-id="c33df-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="c33df-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="c33df-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="c33df-129">ActivityDefinitionId</span></span>|<span data-ttu-id="c33df-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="c33df-130">xs:string</span></span>|<span data-ttu-id="c33df-131">İş akışı Kök etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="c33df-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="c33df-132">Durum</span><span class="sxs-lookup"><span data-stu-id="c33df-132">State</span></span>|<span data-ttu-id="c33df-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="c33df-133">xs:string</span></span>|<span data-ttu-id="c33df-134">İş akışının geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="c33df-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="c33df-135">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c33df-135">Annotations</span></span>|<span data-ttu-id="c33df-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="c33df-136">xs:string</span></span>|<span data-ttu-id="c33df-137">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="c33df-137">The annotations that were added to this event.</span></span> <span data-ttu-id="c33df-138">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="c33df-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="c33df-139">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="c33df-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="c33df-140">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c33df-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="c33df-141">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="c33df-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="c33df-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="c33df-142">ProfileName</span></span>|<span data-ttu-id="c33df-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="c33df-143">xs:string</span></span>|<span data-ttu-id="c33df-144">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="c33df-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="c33df-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="c33df-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="c33df-146">xs: String</span><span class="sxs-lookup"><span data-stu-id="c33df-146">xs:string</span></span>|<span data-ttu-id="c33df-147">İş akışı tanımı kimliği</span><span class="sxs-lookup"><span data-stu-id="c33df-147">The workflow definition id</span></span>|  
|<span data-ttu-id="c33df-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c33df-148">AppDomain</span></span>|<span data-ttu-id="c33df-149">xs: String</span><span class="sxs-lookup"><span data-stu-id="c33df-149">xs:string</span></span>|<span data-ttu-id="c33df-150">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c33df-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
