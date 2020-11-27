---
title: Hizmet işlemi süresini belirleme
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 2607efe0d469f1235ee3d43d62f5e9781681668d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254837"
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="16cf3-102">Hizmet işlemi süresini belirleme</span><span class="sxs-lookup"><span data-stu-id="16cf3-102">Determining service operation duration</span></span>

<span data-ttu-id="16cf3-103">Analitik izleme bir Windows Communication Foundation (WCF) uygulamasında etkinleştirilmişse, bir hizmet işlemi için yürütme süresi, olay günlüğü incelenerek kolayca belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="16cf3-103">If analytic tracing is enabled in a Windows Communication Foundation (WCF) application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="16cf3-104">Bu konuda, bir hizmet işleminin tamamlanma süresini belirleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16cf3-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="16cf3-105">Hizmet işlemi yürütme süresini belirleme</span><span class="sxs-lookup"><span data-stu-id="16cf3-105">Determining service operation execution duration</span></span>  
  
1. <span data-ttu-id="16cf3-106">**Başlat**, **çalıştır** ve girerek Olay Görüntüleyicisi açın `eventvwr.exe` .</span><span class="sxs-lookup"><span data-stu-id="16cf3-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2. <span data-ttu-id="16cf3-107">Analitik izlemeyi etkinleştirmediyseniz, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="16cf3-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="16cf3-108">**Görünüm**, **analitik ve hata ayıklama günlüklerini göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="16cf3-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="16cf3-109">**Analitik** öğesine sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="16cf3-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="16cf3-110">İzlemelerin, hizmet işlemi çalıştırıldıktan sonra görüntülenebilmesi için Olay Görüntüleyicisi açık bırakın.</span><span class="sxs-lookup"><span data-stu-id="16cf3-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3. <span data-ttu-id="16cf3-111">Ardından, bir hizmet projesi ve bu hizmetle etkileşime sahip bir istemci projesi içeren bir WCF uygulaması açın.</span><span class="sxs-lookup"><span data-stu-id="16cf3-111">Next, open a WCF application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="16cf3-112">[Kullanmaya başlama öğreticisini](../../getting-started-tutorial.md)izleyerek böyle bir uygulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16cf3-112">You can create such an application by following the [Getting Started Tutorial](../../getting-started-tutorial.md).</span></span>  <span data-ttu-id="16cf3-113">WCF örnekleri yüklüyse, öğreticide oluşturulan tamamlanmış projeyi içeren [Başlarken](../../samples/getting-started-sample.md)' i açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16cf3-113">If you have the WCF samples installed, you can open the [Getting Started](../../samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4. <span data-ttu-id="16cf3-114">**F5** tuşuna basarak sunucu uygulamasını yürütün.</span><span class="sxs-lookup"><span data-stu-id="16cf3-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="16cf3-115">İstemci uygulamasını, **istemci** projesine sağ tıklayıp **Hata Ayıkla**, **Yeni örnek Başlat**' ı seçerek yürütün.</span><span class="sxs-lookup"><span data-stu-id="16cf3-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5. <span data-ttu-id="16cf3-116">Olay Görüntüleyicisi, analitik günlüğünü yenileyin ve olayları olay KIMLIĞINE göre sıralayın.</span><span class="sxs-lookup"><span data-stu-id="16cf3-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="16cf3-117">Olay KIMLIĞI 214 olan olayları ara [-OperationCompleted](214-operationcompleted.md).</span><span class="sxs-lookup"><span data-stu-id="16cf3-117">Look for events with Event ID [214 - OperationCompleted](214-operationcompleted.md).</span></span>  <span data-ttu-id="16cf3-118">Bu olaylar hangi işlemlerin tamamlandığını ve işlemin süresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cf3-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="16cf3-119">Aşağıdaki olay bir ekleme işleminin süresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cf3-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
