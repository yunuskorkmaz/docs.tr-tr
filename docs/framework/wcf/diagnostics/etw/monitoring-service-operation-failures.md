---
title: Hizmet İşlemi Hatalarını İzleme
ms.date: 03/30/2017
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
ms.openlocfilehash: 3d708b537789c8d0decf75df780300c1e185c4c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="monitoring-service-operation-failures"></a><span data-ttu-id="b714f-102">Hizmet İşlemi Hatalarını İzleme</span><span class="sxs-lookup"><span data-stu-id="b714f-102">Monitoring Service Operation Failures</span></span>
<span data-ttu-id="b714f-103">Bir uygulama için çözümleme izleme etkinleştirilirse, Olay Görüntüleyicisi'nde hizmet hataları kolayca izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b714f-103">If analytic tracing is enabled for an application, service failures can easily be monitored in the event viewer.</span></span>  <span data-ttu-id="b714f-104">Bu konuda, bir hizmet işlemi başarısız olur ve belirlemek nasıl hatasına neden oldu belirleme gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b714f-104">This topic demonstrates how to determine when a service operation fails, and how to determine what caused the failure.</span></span>  
  
### <a name="determining-service-operation-failure-information"></a><span data-ttu-id="b714f-105">Hizmet işlemi hata bilgileri belirleme</span><span class="sxs-lookup"><span data-stu-id="b714f-105">Determining service operation failure information</span></span>  
  
1.  <span data-ttu-id="b714f-106">Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırmak**ve girerek `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="b714f-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="b714f-107">Çözümleme izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar** .</span><span class="sxs-lookup"><span data-stu-id="b714f-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b714f-108">Seçin **Görünüm**, **Göster Analitik ve hata ayıklama günlüklerini**.</span><span class="sxs-lookup"><span data-stu-id="b714f-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="b714f-109">Sağ **analitik** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="b714f-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="b714f-110">Hizmet işlemi başarısız olduktan sonra izleri görüntülenebilir böylece Olay Görüntüleyicisi'ni kapatmayın.</span><span class="sxs-lookup"><span data-stu-id="b714f-110">Leave Event Viewer open so that traces can be viewed after the service operation fails.</span></span>  
  
3.  <span data-ttu-id="b714f-111">Ardından, oluşturulan örnek açmak [başlangıç Öğreticisi](../../../../../docs/framework/wcf/getting-started-tutorial.md) içinde [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] çalıştırmalısınız Not [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] yönetici olarak böylece hizmet oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="b714f-111">Next, open the sample created in the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) in [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Note that you must run [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] as an administrator so that the service can be created.</span></span> <span data-ttu-id="b714f-112">Yüklü WCF örnekleri varsa açabilirsiniz [Başlarken](../../../../../docs/framework/wcf/samples/getting-started-sample.md), öğreticide oluşturulan projeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="b714f-112">If you have the WCF samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="b714f-113">Sunucu projesi Program.cs dosyasında aşağıdaki kod satırını başlangıcına ekleyin `Divide` yönteminde `CalculatorService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b714f-113">In the Program.cs file in the Server project, add the following line of code to the start of the `Divide` method in the `CalculatorService` class:</span></span>  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  <span data-ttu-id="b714f-114">İstemci projesindeki Program.cs dosyasında sıfır value2 atanan değer değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b714f-114">In the Program.cs file in the Client project, change the value assigned to value2 to zero:</span></span>  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  <span data-ttu-id="b714f-115">Sunucu uygulaması tuşlarına basarak hata ayıklama olmadan yürütün **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b714f-115">Execute the server application without debugging by pressing **Ctrl+F5**.</span></span>  
  
7.  <span data-ttu-id="b714f-116">Visual Studio komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b714f-116">Open a Visual Studio command prompt.</span></span>  <span data-ttu-id="b714f-117">İstemci dizine gidin ve istemci komut satırından yürütün.</span><span class="sxs-lookup"><span data-stu-id="b714f-117">Navigate to the client directory and execute the client from the command line.</span></span>  
  
8.  <span data-ttu-id="b714f-118">Olay Görüntüleyicisi'nde devre dışı bırakın ve analitik günlük yenileyin ve olayları olay kimliğine göre sıralama</span><span class="sxs-lookup"><span data-stu-id="b714f-118">In Event Viewer, disable and refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="b714f-119">Olay Kimliği sahip bir olay arayın [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), hizmet hatası açıklar.</span><span class="sxs-lookup"><span data-stu-id="b714f-119">Look for an event with Event ID [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), which describes the service failure.</span></span>  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b714f-120">Olayları için Olay Görüntüleyicisi'ni gönderilmekte olan zaman arabelleğe alınmış; Hata olayı hemen görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="b714f-120">Events are buffered when being sent to the event viewer; the failure event may not appear right away.</span></span>
