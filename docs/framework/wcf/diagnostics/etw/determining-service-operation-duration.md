---
title: "Hizmet işlemi süresini belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63a8c92713ee452da2439475ac526229d1e5741c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="e1769-102">Hizmet işlemi süresini belirleme</span><span class="sxs-lookup"><span data-stu-id="e1769-102">Determining service operation duration</span></span>
<span data-ttu-id="e1769-103">Çözümleme izleme de etkinse, bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] uygulama, bir hizmet işlemi için yürütme süresini kolayca belirlenebilir olay günlüğünü inceleyerek.</span><span class="sxs-lookup"><span data-stu-id="e1769-103">If analytic tracing is enabled in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="e1769-104">Bu konuda, bir hizmet işlemi tamamlamak için geçen süreyi belirlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e1769-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="e1769-105">Hizmet işlemi yürütme süresini belirleme</span><span class="sxs-lookup"><span data-stu-id="e1769-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="e1769-106">Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırmak**ve girerek `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="e1769-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="e1769-107">Çözümleme izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar** .</span><span class="sxs-lookup"><span data-stu-id="e1769-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e1769-108">Seçin **Görünüm**, **Göster Analitik ve hata ayıklama günlüklerini**.</span><span class="sxs-lookup"><span data-stu-id="e1769-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="e1769-109">Sağ **analitik** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="e1769-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="e1769-110">Hizmet işlemini çalıştırdıktan sonra izlemeleri görüntülenebilir böylece Olay Görüntüleyicisi'ni kapatmayın.</span><span class="sxs-lookup"><span data-stu-id="e1769-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="e1769-111">Ardından, açık bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet projesi ve bu hizmeti ile etkileşime giren istemci proje içeren uygulama.</span><span class="sxs-lookup"><span data-stu-id="e1769-111">Next, open a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="e1769-112">İzleyerek böyle bir uygulama oluşturabilirsiniz [başlangıç Öğreticisi](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="e1769-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="e1769-113">Varsa [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] yüklü örnekleri açabilirsiniz [Başlarken](../../../../../docs/framework/wcf/samples/getting-started-sample.md), öğreticide oluşturulan projeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="e1769-113">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="e1769-114">Sunucu uygulaması tuşlarına basarak yürütme **F5**.</span><span class="sxs-lookup"><span data-stu-id="e1769-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="e1769-115">Üzerinde sağ tıklayarak ve istemci uygulamanın yürütme **istemci** proje ve seçerek **hata ayıklama**, **Başlat yeni örnek**.</span><span class="sxs-lookup"><span data-stu-id="e1769-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="e1769-116">Olay Görüntüleyicisi'nde analitik günlüğünü yenilemek ve olayları olay kimliğine göre sıralama</span><span class="sxs-lookup"><span data-stu-id="e1769-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="e1769-117">Olay kimliği olan olaylar için Ara [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span><span class="sxs-lookup"><span data-stu-id="e1769-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="e1769-118">Bu olaylar, hangi işlemleri tamamladınız ve işlem süresini neydi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1769-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="e1769-119">Aşağıdaki olay bir ekleme işlemi süresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1769-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
