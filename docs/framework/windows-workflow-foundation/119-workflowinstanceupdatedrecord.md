---
title: 119 - WorkflowInstanceUpdatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f58a7c0e3b3122962e79f7f39f0c0f89f374bd10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="119---workflowinstanceupdatedrecord"></a><span data-ttu-id="fd7a7-102">119 - WorkflowInstanceUpdatedRecord</span><span class="sxs-lookup"><span data-stu-id="fd7a7-102">119 - WorkflowInstanceUpdatedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="fd7a7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fd7a7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd7a7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="fd7a7-104">ID</span></span>|<span data-ttu-id="fd7a7-105">119</span><span class="sxs-lookup"><span data-stu-id="fd7a7-105">119</span></span>|  
|<span data-ttu-id="fd7a7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="fd7a7-106">Keywords</span></span>|<span data-ttu-id="fd7a7-107">Ögesi, WFTracking</span><span class="sxs-lookup"><span data-stu-id="fd7a7-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="fd7a7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="fd7a7-108">Level</span></span>|<span data-ttu-id="fd7a7-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="fd7a7-109">Information</span></span>|  
|<span data-ttu-id="fd7a7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="fd7a7-110">Channel</span></span>|<span data-ttu-id="fd7a7-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="fd7a7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fd7a7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd7a7-112">Description</span></span>  
 <span data-ttu-id="fd7a7-113">Bu olay, bir iş akışı örneği güncelleştirildiğinde ETW İzleme katılımcı tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-113">This event is emitted by the ETW tracking participant when a workflow instance is updated.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fd7a7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="fd7a7-114">Message</span></span>  
 <span data-ttu-id="fd7a7-115">TrackRecord WorkflowInstanceUpdatedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, durum = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = % 7 ' ye ek açıklamaları = %8, ProfileName %9 =</span><span class="sxs-lookup"><span data-stu-id="fd7a7-115">TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9</span></span>  
  
## <a name="details"></a><span data-ttu-id="fd7a7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fd7a7-116">Details</span></span>  
  
|<span data-ttu-id="fd7a7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="fd7a7-117">Data Item Name</span></span>|<span data-ttu-id="fd7a7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="fd7a7-118">Data Item Type</span></span>|<span data-ttu-id="fd7a7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd7a7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fd7a7-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="fd7a7-120">InstanceId</span></span>|<span data-ttu-id="fd7a7-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="fd7a7-121">xs:GUID</span></span>|<span data-ttu-id="fd7a7-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="fd7a7-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="fd7a7-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="fd7a7-123">RecordNumber</span></span>|<span data-ttu-id="fd7a7-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="fd7a7-124">xs:long</span></span>|<span data-ttu-id="fd7a7-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="fd7a7-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="fd7a7-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="fd7a7-126">EventTime</span></span>|<span data-ttu-id="fd7a7-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="fd7a7-127">xs:dateTime</span></span>|<span data-ttu-id="fd7a7-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="fd7a7-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="fd7a7-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="fd7a7-129">ActivityDefinitionId</span></span>|<span data-ttu-id="fd7a7-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-130">xs:string</span></span>|<span data-ttu-id="fd7a7-131">İş akışı Kök etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="fd7a7-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="fd7a7-132">Durum</span><span class="sxs-lookup"><span data-stu-id="fd7a7-132">State</span></span>|<span data-ttu-id="fd7a7-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-133">xs:string</span></span>|<span data-ttu-id="fd7a7-134">İş akışının geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="fd7a7-135">OriginalDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="fd7a7-135">OriginalDefinitionIdentity</span></span>|<span data-ttu-id="fd7a7-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-136">xs:string</span></span>|<span data-ttu-id="fd7a7-137">Özgün iş akışı tanımı kimliği</span><span class="sxs-lookup"><span data-stu-id="fd7a7-137">The original workflow definition id</span></span>|  
|<span data-ttu-id="fd7a7-138">UpdatedDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="fd7a7-138">UpdatedDefinitionIdentity</span></span>|<span data-ttu-id="fd7a7-139">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-139">xs:string</span></span>|<span data-ttu-id="fd7a7-140">Güncelleştirilmiş iş akışı tanımı kimliği</span><span class="sxs-lookup"><span data-stu-id="fd7a7-140">The updated workflow definition id</span></span>|  
|<span data-ttu-id="fd7a7-141">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd7a7-141">Annotations</span></span>|<span data-ttu-id="fd7a7-142">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-142">xs:string</span></span>|<span data-ttu-id="fd7a7-143">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-143">The annotations that were added to this event.</span></span> <span data-ttu-id="fd7a7-144">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-144">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="fd7a7-145">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-145">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="fd7a7-146">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-146">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="fd7a7-147">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-147">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="fd7a7-148">ProfileName</span><span class="sxs-lookup"><span data-stu-id="fd7a7-148">ProfileName</span></span>|<span data-ttu-id="fd7a7-149">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-149">xs:string</span></span>|<span data-ttu-id="fd7a7-150">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="fd7a7-150">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="fd7a7-151">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="fd7a7-151">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="fd7a7-152">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-152">xs:string</span></span>|<span data-ttu-id="fd7a7-153">İş akışı tanımı kimliği</span><span class="sxs-lookup"><span data-stu-id="fd7a7-153">The workflow definition id</span></span>|  
|<span data-ttu-id="fd7a7-154">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fd7a7-154">AppDomain</span></span>|<span data-ttu-id="fd7a7-155">xs: String</span><span class="sxs-lookup"><span data-stu-id="fd7a7-155">xs:string</span></span>|<span data-ttu-id="fd7a7-156">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-156">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
