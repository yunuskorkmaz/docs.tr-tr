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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352041"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="6e0ea-102">Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e0ea-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="6e0ea-103">Uygulamanızda gerçekleşen olaylar hakkında bilgi yazmak için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="6e0ea-104">Bu örnek bir olay günlüğü dinleyicisinin nasıl yapılandırılacağını gösterir. bu nedenle, `My.Application.Log` izleme bilgilerini uygulama olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="6e0ea-105">Güvenlik günlüğüne yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-105">You cannot write to the Security log.</span></span> <span data-ttu-id="6e0ea-106">Sistem günlüğüne yazmak için LocalSystem veya Administrator hesabının bir üyesi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="6e0ea-107">Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="6e0ea-108">Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="6e0ea-109">Olay günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="6e0ea-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="6e0ea-110">**Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="6e0ea-111">\- veya-</span><span class="sxs-lookup"><span data-stu-id="6e0ea-111">\- or -</span></span>

    <span data-ttu-id="6e0ea-112">App. config dosyası yoksa,</span><span class="sxs-lookup"><span data-stu-id="6e0ea-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="6e0ea-113">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="6e0ea-114">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="6e0ea-115">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-115">Click **Add**.</span></span>

2. <span data-ttu-id="6e0ea-116">Uygulama yapılandırma dosyasında `<listeners>` bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="6e0ea-117">En üst düzey `<configuration>` bölümünün altında yer aldığı `<system.diagnostics>` bölümünde iç içe yerleştirilmiş olan "DefaultSource" ad özniteliğiyle birlikte `<source>` bölümünde `<listeners>` bölümünü bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="6e0ea-118">Bu öğeyi bu `<listeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6e0ea-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="6e0ea-119">Üst düzey `<configuration>` bölümündeki `<system.diagnostics>` bölümünde `<sharedListeners>` bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="6e0ea-120">Bu öğeyi bu `<sharedListeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6e0ea-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="6e0ea-121">`APPLICATION_NAME` değerini uygulamanızın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6e0ea-122">Genellikle, bir uygulama olay günlüğüne yalnızca hataları yazar.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="6e0ea-123">Günlük çıkışını filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: filtreleme My. Application. log output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="6e0ea-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="6e0ea-124">Olay günlüğüne olay bilgilerini yazmak için</span><span class="sxs-lookup"><span data-stu-id="6e0ea-124">To write event information to the event log</span></span>

<span data-ttu-id="6e0ea-125">Olay günlüğüne bilgi yazmak için `My.Application.Log.WriteEntry` veya `My.Application.Log.WriteException` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="6e0ea-126">Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="6e0ea-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="6e0ea-127">Bir derleme için olay günlüğü dinleyicisini yapılandırdıktan sonra, bu derlemeden yazma `My.Application.Log` tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e0ea-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e0ea-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="6e0ea-129">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="6e0ea-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="6e0ea-130">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="6e0ea-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="6e0ea-131">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="6e0ea-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
