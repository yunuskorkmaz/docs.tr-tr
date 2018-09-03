---
title: İzleme kullanarak iş akışı yürütme süresini belirleme
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: c51fdf4543939fc068092b84e02eeb5f52e77d6d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486287"
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="09ec1-102">İzleme kullanarak iş akışı yürütme süresini belirleme</span><span class="sxs-lookup"><span data-stu-id="09ec1-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="09ec1-103">Bu konuda, iş akışı izleme kullanarak çalıştırmak başarıyla tamamlandı, şirket içinde barındırılan bir iş akışı için gereken süreyi belirlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="09ec1-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="09ec1-104">İş akışı izleme kullanarak iş akışı uygulama yürütme süresini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="09ec1-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="09ec1-105">Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09ec1-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="09ec1-106">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="09ec1-107">Altında **C#** seçin **iş akışı** düğümü.</span><span class="sxs-lookup"><span data-stu-id="09ec1-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="09ec1-108">Seçin **iş akışı konsol uygulaması** şablonları listesinden.</span><span class="sxs-lookup"><span data-stu-id="09ec1-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="09ec1-109">Yeni proje adını `WorkflowDurationTracing` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="09ec1-110">Workflow1.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="09ec1-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="09ec1-111">Sürükleme bir <xref:System.Activities.Statements.Delay> Tasarımcı yüzeyine etkinlik.</span><span class="sxs-lookup"><span data-stu-id="09ec1-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="09ec1-112">Değer 00:00:10 (on saniye) etkinlik süresi özelliğine atayın.</span><span class="sxs-lookup"><span data-stu-id="09ec1-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="09ec1-113">Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırma**, girerek `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="09ec1-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="09ec1-114">İş akışı izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucu uygulamaları** .</span><span class="sxs-lookup"><span data-stu-id="09ec1-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="09ec1-115">Seçin **görünümü**, **Göster Analitik ve hata ayıklama günlüklerini**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="09ec1-116">Sağ **hata ayıklama** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="09ec1-117">Olay Görüntüleyicisi, böylece iş akışını çalıştırdığınızda, izlemeleri görüntülenebilir açık bırakın.</span><span class="sxs-lookup"><span data-stu-id="09ec1-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="09ec1-118">İş akışı uygulaması, CTRL + SHIFT + B tuşlarına basarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="09ec1-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="09ec1-119">Olay Görüntüleyicisi'nde yeni bir Olay Kimliği 1009 ve bir ileti aşağıdakine benzer bulun.</span><span class="sxs-lookup"><span data-stu-id="09ec1-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="09ec1-120">İleti günlüğe kaydedildi süreyi not edin.</span><span class="sxs-lookup"><span data-stu-id="09ec1-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="09ec1-121">**Üst etkinlik '', DisplayName: '', InstanceId: '' zamanlanmış alt etkinlik 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span><span class="sxs-lookup"><span data-stu-id="09ec1-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="09ec1-122">Başka bir son olay kimliği 1001 ve bir ileti aşağıdakine benzer bulun.</span><span class="sxs-lookup"><span data-stu-id="09ec1-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="09ec1-123">Önceki ileti süresi yaklaşık 10 saniye olmalıdır iş akışı yürütme süresini belirlemek için bu ileti günlüğe değerinden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="09ec1-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="09ec1-124">**WorkflowInstance ID: kapalı durumda '1bbac57b-3322-498e-9e27-8833fda3a5bf' tamamlandı.**</span><span class="sxs-lookup"><span data-stu-id="09ec1-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ec1-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09ec1-125">See Also</span></span>  
 [<span data-ttu-id="09ec1-126">İş Akışı İzleme</span><span class="sxs-lookup"><span data-stu-id="09ec1-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="09ec1-127">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="09ec1-127">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="09ec1-128">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="09ec1-128">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
