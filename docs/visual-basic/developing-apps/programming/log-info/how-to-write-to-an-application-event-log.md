---
title: 'Nasıl yapılır: Uygulama olay günlüğüne (Visual Basic) yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: c3c7d350132ee6c891633141fc5c4b280989e77f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366510"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="3281f-102">Nasıl yapılır: Uygulama olay günlüğüne (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="3281f-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="3281f-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda gerçekleşen olaylar hakkında bilgi yazılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="3281f-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="3281f-104">Bu örnek nasıl bir olay günlüğü dinleyicisini yapılandırmak bunu gösterir `My.Application.Log` izleme bilgileri uygulama olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="3281f-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="3281f-105">Güvenlik günlüğüne yazamaz.</span><span class="sxs-lookup"><span data-stu-id="3281f-105">You cannot write to the Security log.</span></span> <span data-ttu-id="3281f-106">Sistem günlüğüne yazmak için LocalSystem veya yönetici hesabının bir üyesi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3281f-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="3281f-107">Olay günlüğünü görüntülemek için kullanabileceğiniz **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="3281f-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="3281f-108">Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="3281f-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

### <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="3281f-109">Ekleme ve olay günlüğü dinleyici yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3281f-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="3281f-110">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="3281f-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="3281f-111">\- veya -</span><span class="sxs-lookup"><span data-stu-id="3281f-111">\- or -</span></span>

    <span data-ttu-id="3281f-112">Herhangi bir app.config dosyası varsa,</span><span class="sxs-lookup"><span data-stu-id="3281f-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="3281f-113">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="3281f-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="3281f-114">Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="3281f-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="3281f-115">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3281f-115">Click **Add**.</span></span>

2. <span data-ttu-id="3281f-116">Bulun `<listeners>` uygulama yapılandırma dosyasında bölümü.</span><span class="sxs-lookup"><span data-stu-id="3281f-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="3281f-117">Size `<listeners>` konusundaki `<source>` bölümü altında iç içe "DefaultSource" ad özniteliği ile `<system.diagnostics>` üst düzey altında iç içe bölümünde `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="3281f-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="3281f-118">Bu öğe ekleyen `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="3281f-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="3281f-119">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="3281f-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="3281f-120">Bu öğe ekleyen `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="3281f-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="3281f-121">Değiştirin `APPLICATION_NAME` uygulamanızın adı.</span><span class="sxs-lookup"><span data-stu-id="3281f-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3281f-122">Genellikle, uygulamanın yalnızca hataları olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="3281f-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="3281f-123">Günlük çıktısını filtreleme hakkında daha fazla bilgi için bkz: [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="3281f-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

### <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="3281f-124">Olay bilgilerini olay günlüğüne yazmak için</span><span class="sxs-lookup"><span data-stu-id="3281f-124">To write event information to the event log</span></span>

- <span data-ttu-id="3281f-125">Kullanım `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` bilgilerini olay günlüğüne yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3281f-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="3281f-126">Daha fazla bilgi için [nasıl yapılır: Günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="3281f-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

    <span data-ttu-id="3281f-127">Bir derleme için olay günlüğü dinleyici yapılandırdıktan sonra tüm aldığı iletileri `My.Application.Log` Bu bütünleştirilmiş koddan yazar.</span><span class="sxs-lookup"><span data-stu-id="3281f-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="3281f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3281f-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="3281f-129">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="3281f-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="3281f-130">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="3281f-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="3281f-131">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="3281f-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
