---
title: "Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 018aff8dc130bfe7217c861a7d7bc8ae275ccc66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="841f8-102">Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="841f8-102">How to: Write to an Application Event Log (Visual Basic)</span></span>
<span data-ttu-id="841f8-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` , uygulamanızda gerçekleşen olaylar hakkında bilgi yazılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="841f8-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="841f8-104">Bu örnekte bir olay günlüğü dinleyicisi yapılandırmak bunu gösterilmiştir `My.Application.Log` izleme bilgilerini uygulama olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="841f8-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>  
  
 <span data-ttu-id="841f8-105">Güvenlik günlüğüne yazamaz.</span><span class="sxs-lookup"><span data-stu-id="841f8-105">You cannot write to the Security log.</span></span> <span data-ttu-id="841f8-106">Sistem günlüğüne yazmak için LocalSystem veya yönetici hesabının bir üyesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="841f8-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>  
  
 <span data-ttu-id="841f8-107">Olay günlüğünü görüntülemek için kullanabileceğiniz **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="841f8-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="841f8-108">Daha fazla bilgi için bkz: [.NET Framework'te ETW olayları](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span><span class="sxs-lookup"><span data-stu-id="841f8-108">For more information, see [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="841f8-109">Olay günlükleri, Windows 95, Windows 98 veya Windows Millennium Edition desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="841f8-109">Event logs are not supported on Windows 95, Windows 98, or Windows Millennium Edition.</span></span>  
  
### <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="841f8-110">Eklemek ve olay günlüğü dinleyicisi yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="841f8-110">To add and configure the event log listener</span></span>  
  
1.  <span data-ttu-id="841f8-111">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="841f8-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="841f8-112">\-veya -</span><span class="sxs-lookup"><span data-stu-id="841f8-112">\- or -</span></span>  
  
     <span data-ttu-id="841f8-113">App.config dosyası yoksa,</span><span class="sxs-lookup"><span data-stu-id="841f8-113">If there is no app.config file,</span></span>  
  
    1.  <span data-ttu-id="841f8-114">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="841f8-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="841f8-115">Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="841f8-115">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="841f8-116">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="841f8-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="841f8-117">Bulun `<listeners>` uygulama yapılandırma dosyasında bölüm.</span><span class="sxs-lookup"><span data-stu-id="841f8-117">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="841f8-118">Size `<listeners>` bölümüne `<source>` bölümü altında yer alan "DefaultSource" ad özniteliği olan `<system.diagnostics>` altında en üst düzey iç içe bölüm `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="841f8-118">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="841f8-119">Bu öğe için eklemek `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="841f8-119">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  <span data-ttu-id="841f8-120">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="841f8-120">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="841f8-121">Bu öğe için eklemek `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="841f8-121">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     <span data-ttu-id="841f8-122">Değiştir `APPLICATION_NAME` , uygulamanızın adı.</span><span class="sxs-lookup"><span data-stu-id="841f8-122">Replace `APPLICATION_NAME` with the name of your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="841f8-123">Genellikle, uygulamanın yalnızca hataları olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="841f8-123">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="841f8-124">Günlük çıktısını filtreleme hakkında daha fazla bilgi için bkz: [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="841f8-124">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
### <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="841f8-125">Olay günlüğüne olay bilgilerini yazma</span><span class="sxs-lookup"><span data-stu-id="841f8-125">To write event information to the event log</span></span>  
  
-   <span data-ttu-id="841f8-126">Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` yöntemi bilgileri olay günlüğüne yazma.</span><span class="sxs-lookup"><span data-stu-id="841f8-126">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="841f8-127">Daha fazla bilgi için bkz: [nasıl yapılır: günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="841f8-127">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="841f8-128">Derleme için olay günlüğüne dinleyici yapılandırdıktan sonra tüm aldığı iletileri `My.Applcation.Log` bütünleştirilmiş koddan yazar.</span><span class="sxs-lookup"><span data-stu-id="841f8-128">After you configure the event log listener for an assembly, it receives all messages that `My.Applcation.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841f8-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="841f8-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="841f8-130">Uygulama günlükleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="841f8-130">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="841f8-131">Nasıl yapılır: günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="841f8-131">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="841f8-132">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="841f8-132">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
