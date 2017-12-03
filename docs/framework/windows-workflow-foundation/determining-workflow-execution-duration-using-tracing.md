---
title: "İzleme kullanarak iş akışı yürütme süresini belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c635dbd551eaba6ce338c38564480d0f5cfae553
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="3d9e1-102">İzleme kullanarak iş akışı yürütme süresini belirleme</span><span class="sxs-lookup"><span data-stu-id="3d9e1-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="3d9e1-103">Bu konuda, iş akışı izleme kullanarak çalıştırmak başarıyla tamamlandı, kendi kendini barındıran bir iş akışı için geçen süreyi belirlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="3d9e1-104">İş akışı izleme kullanarak iş akışı uygulama yürütme süresini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="3d9e1-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="3d9e1-105">Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d9e1-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="3d9e1-106">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="3d9e1-107">Altında **C#**seçin **iş akışı** düğümü.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="3d9e1-108">Seçin **iş akışı konsol uygulaması** şablonları listesinden.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="3d9e1-109">Yeni proje adı `WorkflowDurationTracing` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="3d9e1-110">Workflow1.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="3d9e1-111">Sürükleme bir <xref:System.Activities.Statements.Delay> Tasarımcı yüzeyine etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="3d9e1-112">Değer 00:00:10 (on saniye) etkinlik süresi özelliğine atayın.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="3d9e1-113">Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırmak**ve girerek `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="3d9e1-114">İş akışı izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar** .</span><span class="sxs-lookup"><span data-stu-id="3d9e1-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="3d9e1-115">Seçin **Görünüm**, **Göster Analitik ve hata ayıklama günlüklerini**.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="3d9e1-116">Sağ **hata ayıklama** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="3d9e1-117">Böylece iş akışını çalıştırmak sonra izleri görüntülenebilir Olay Görüntüleyicisi'ni kapatmayın.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="3d9e1-118">CTRL + SHIFT + B tuşuna basarak iş akışı uygulaması yürütün.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="3d9e1-119">Olay Görüntüleyicisi'nde yeni bir Olay Kimliği 1009 ve bir ileti aşağıdakine benzer bulun.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="3d9e1-120">İleti günlüğe kaydedildi süreyi not edin.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="3d9e1-121">**Üst etkinlik '', DisplayName: '', InstanceId: '' zamanlanmış alt etkinlik 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', örnek kimliği: '1'.**</span><span class="sxs-lookup"><span data-stu-id="3d9e1-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="3d9e1-122">Başka bir son olay kimliği 1001 ve bir ileti aşağıdakine benzer bulun.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="3d9e1-123">Önceki süresi yaklaşık 10 saniye olmalıdır iş akışı yürütme süresini belirlemek için bu ileti günlüğe değerinden çıkarın.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="3d9e1-124">**İş akışı örneği kimliği: '1bbac57b-3322-498e-9e27-8833fda3a5bf' kapalı durumda tamamlandı.**</span><span class="sxs-lookup"><span data-stu-id="3d9e1-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9e1-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d9e1-125">See Also</span></span>  
 [<span data-ttu-id="3d9e1-126">İş akışı izleme</span><span class="sxs-lookup"><span data-stu-id="3d9e1-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="3d9e1-127">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="3d9e1-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="3d9e1-128">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="3d9e1-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
