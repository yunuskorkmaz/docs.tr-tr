---
title: 'Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352041"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="13474-102">Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13474-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="13474-103">Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylar hakkında bilgi yazmak için nesneleri ve nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13474-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="13474-104">Bu örnek, bir olay günlüğü dinleyicisinin `My.Application.Log` nasıl yapılandırılabildiğini gösterir, bu nedenle Uygulama olay günlüğüne izleme bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="13474-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="13474-105">Güvenlik günlüğüne yazamazsınız.</span><span class="sxs-lookup"><span data-stu-id="13474-105">You cannot write to the Security log.</span></span> <span data-ttu-id="13474-106">Sistem günlüğüne yazabilmek için Yerel Sistem veya Yönetici hesabının bir üyesi olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="13474-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="13474-107">Bir olay günlüğünü görüntülemek için **Server Explorer** veya Windows **Event Viewer'ı**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13474-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="13474-108">Daha fazla bilgi için [.NET Framework'deki ETW Olayları'na](../../../../framework/performance/etw-events.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="13474-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="13474-109">Olay günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="13474-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="13474-110">**Solution Explorer'da** app.config'e sağ tıklayın ve **Aç'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="13474-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="13474-111">\-veya -</span><span class="sxs-lookup"><span data-stu-id="13474-111">\- or -</span></span>

    <span data-ttu-id="13474-112">App.config dosyası yoksa,</span><span class="sxs-lookup"><span data-stu-id="13474-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="13474-113">**Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="13474-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="13474-114">Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="13474-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="13474-115">**Ekle**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="13474-115">Click **Add**.</span></span>

2. <span data-ttu-id="13474-116">Uygulama `<listeners>` yapılandırma dosyasındaki bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="13474-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="13474-117">Üst düzey `<configuration>` `<listeners>` bölümün altında iç içe olan `<system.diagnostics>` bölümün altında iç içe olan "DefaultSource" ad özniteliğinin bulunduğu bölümde bulacaksınız. `<source>`</span><span class="sxs-lookup"><span data-stu-id="13474-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="13474-118">Bu öğeyi `<listeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="13474-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="13474-119">`<sharedListeners>` Bölümü, `<system.diagnostics>` bölümü, üst düzey `<configuration>` bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="13474-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="13474-120">Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="13474-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="13474-121">Başvurunuzun adı ile değiştirin. `APPLICATION_NAME`</span><span class="sxs-lookup"><span data-stu-id="13474-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="13474-122">Genellikle, bir uygulama yalnızca olay günlüğüne hatalar yazar.</span><span class="sxs-lookup"><span data-stu-id="13474-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="13474-123">Günlük çıktısını filtreleme hakkında bilgi için [bkz.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)</span><span class="sxs-lookup"><span data-stu-id="13474-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="13474-124">Olay günlüğe olay bilgilerini yazmak için</span><span class="sxs-lookup"><span data-stu-id="13474-124">To write event information to the event log</span></span>

<span data-ttu-id="13474-125">Olay `My.Application.Log.WriteEntry` günlüğüne bilgi yazmak için veya `My.Application.Log.WriteException` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="13474-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="13474-126">Daha fazla bilgi için [bkz: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [Nasıl Yazılır: Özel Durumları Günlüğe Kaydedin.](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)</span><span class="sxs-lookup"><span data-stu-id="13474-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="13474-127">Bir derleme için olay günlüğü dinleyicisini yapılandırıldıktan sonra, `My.Application.Log` bu derlemeden yazan tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="13474-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="13474-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13474-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="13474-129">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="13474-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="13474-130">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="13474-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="13474-131">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="13474-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
