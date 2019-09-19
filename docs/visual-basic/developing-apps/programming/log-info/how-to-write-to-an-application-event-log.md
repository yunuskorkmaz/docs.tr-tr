---
title: 'Nasıl yapılır: Uygulama olay günlüğüne yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 385a85d956a0de727e3c061ec447a3d53ad6c159
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054143"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="018be-102">Nasıl yapılır: Uygulama olay günlüğüne yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="018be-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="018be-103">Uygulamanızda gerçekleşen olaylar hakkında `My.Application.Log` bilgi `My.Log` yazmak için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="018be-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="018be-104">Bu örnek, bir olay günlüğü dinleyicisinin izleme bilgilerini uygulama `My.Application.Log` olay günlüğü 'ne yazmalarını sağlayacak şekilde nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="018be-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="018be-105">Güvenlik günlüğüne yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="018be-105">You cannot write to the Security log.</span></span> <span data-ttu-id="018be-106">Sistem günlüğüne yazmak için LocalSystem veya Administrator hesabının bir üyesi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="018be-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="018be-107">Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="018be-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="018be-108">Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="018be-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="018be-109">Olay günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="018be-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="018be-110">**Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="018be-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="018be-111">\- veya -</span><span class="sxs-lookup"><span data-stu-id="018be-111">\- or -</span></span>

    <span data-ttu-id="018be-112">App. config dosyası yoksa,</span><span class="sxs-lookup"><span data-stu-id="018be-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="018be-113">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="018be-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="018be-114">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="018be-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="018be-115">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="018be-115">Click **Add**.</span></span>

2. <span data-ttu-id="018be-116">Uygulama yapılandırma dosyasında bölümünü bulun. `<listeners>`</span><span class="sxs-lookup"><span data-stu-id="018be-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="018be-117">Bölümünün, üst düzey `<listeners>` `<system.diagnostics>` `<source>` bölüm`<configuration>` altında iç içe yerleştirilmiş olan bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="018be-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="018be-118">Bu öğeyi `<listeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="018be-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="018be-119">Bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bölümünde bulunan bölümünübulun.`<sharedListeners>`</span><span class="sxs-lookup"><span data-stu-id="018be-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="018be-120">Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="018be-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="018be-121">Uygulamanızın `APPLICATION_NAME` adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="018be-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="018be-122">Genellikle, bir uygulama olay günlüğüne yalnızca hataları yazar.</span><span class="sxs-lookup"><span data-stu-id="018be-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="018be-123">Günlük çıktısını filtreleme hakkında daha fazla bilgi için [bkz. İzlenecek yol: My. Application. log çıktımı](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)filtreleniyor.</span><span class="sxs-lookup"><span data-stu-id="018be-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="018be-124">Olay günlüğüne olay bilgilerini yazmak için</span><span class="sxs-lookup"><span data-stu-id="018be-124">To write event information to the event log</span></span>

<span data-ttu-id="018be-125">Olay günlüğüne bilgi `My.Application.Log.WriteException` yazmak için veyayönteminikullanın.`My.Application.Log.WriteEntry`</span><span class="sxs-lookup"><span data-stu-id="018be-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="018be-126">Daha fazla bilgi için [nasıl yapılır: Yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)durumları.</span><span class="sxs-lookup"><span data-stu-id="018be-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="018be-127">Bir derleme için olay günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden `My.Application.Log` yazan tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="018be-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="018be-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="018be-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="018be-129">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="018be-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="018be-130">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="018be-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="018be-131">İzlenecek yol: My. Application. log bilgisinin nereden yazabileceğini belirleme</span><span class="sxs-lookup"><span data-stu-id="018be-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
