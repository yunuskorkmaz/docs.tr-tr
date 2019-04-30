---
title: 'Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea5db2ba1060479f55bbd7f67266d36085a2535f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754381"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="78c35-102">Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="78c35-102">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="78c35-103"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları almak ve bu iletileri işleyen dinleyicileri adlı nesnelere iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="78c35-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="78c35-104">Tür bir dinleyici <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, otomatik olarak oluşturulur ve izleme ya da hata ayıklama etkin olduğunda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="78c35-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="78c35-105">İsterseniz <xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.Debug> herhangi bir ek kaynaklar için yönlendirilmesine çıktısını oluşturmalı ve ek izleme dinleyicileri başlatır.</span><span class="sxs-lookup"><span data-stu-id="78c35-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="78c35-106">Oluşturduğunuz dinleyicileri, uygulamanızın ihtiyaçlarına yansıtmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78c35-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="78c35-107">Örneğin, bir metin kayıt tüm izleme çıkışı istiyorsanız, oluşturun bir <xref:System.Diagnostics.TextWriterTraceListener> dinleyicisi etkinleştirildiğinde, tüm çıktı yeni bir metin dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="78c35-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="78c35-108">Öte yandan, yalnızca uygulama yürütme sırasında çıkış görüntülemek istiyorsanız, oluşturun bir <xref:System.Diagnostics.ConsoleTraceListener> dinleyici, tüm çıkış için bir konsol penceresi yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="78c35-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="78c35-109"><xref:System.Diagnostics.EventLogTraceListener> Bir olay günlüğüne izleme çıkış yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="78c35-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="78c35-110">Daha fazla bilgi için [izleme dinleyicilerine](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="78c35-110">For more information, see [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span></span>

<span data-ttu-id="78c35-111">İzleme dinleyicilerine içinde oluşturduğunuz bir [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) ya da kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="78c35-111">You can create trace listeners in an [application configuration file](../../../docs/framework/configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="78c35-112">Ekleme, değiştirme veya kodunuzu değiştirmek zorunda kalmadan izleme dinleyicilerine kaldırmanıza olanak tanıdığı uygulama yapılandırma dosyaları, kullanılmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="78c35-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="78c35-113">Oluşturma ve yapılandırma dosyası kullanarak izleme dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="78c35-113">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="78c35-114">Uygulama yapılandırma dosyasında, İzleme dinleyicisi bildirin.</span><span class="sxs-lookup"><span data-stu-id="78c35-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="78c35-115">Oluşturmakta olduğunuz dinleyici diğer nesneler gerektiriyorsa, bunları da bildirin.</span><span class="sxs-lookup"><span data-stu-id="78c35-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="78c35-116">Aşağıdaki örnekte adlı bir dinleyici oluşturma işlemi gösterilmektedir `myListener` metin dosyasına yazar `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="78c35-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

    ```xml
    <configuration>
      <system.diagnostics>
        <trace autoflush="false" indentsize="4">
          <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />
            <remove name="Default" />
          </listeners>
        </trace>
      </system.diagnostics>
    </configuration>
    ```

2. <span data-ttu-id="78c35-117">Kullanım <xref:System.Diagnostics.Trace> izleme dinleyicilerine ileti yazmak için kodunuzda sınıfı.</span><span class="sxs-lookup"><span data-stu-id="78c35-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

    ```vb
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="78c35-118">Oluşturma ve İzleme dinleyicisi kodda kullanma</span><span class="sxs-lookup"><span data-stu-id="78c35-118">To create and use a trace listener in code</span></span>

- <span data-ttu-id="78c35-119">İzleme dinleyicisi için ekleme <xref:System.Diagnostics.Trace.Listeners%2A> izleme dinleyicilerine bilgi toplama ve Gönder.</span><span class="sxs-lookup"><span data-stu-id="78c35-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

    ```vb
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

    <span data-ttu-id="78c35-120">\- veya -</span><span class="sxs-lookup"><span data-stu-id="78c35-120">\- or -</span></span>

- <span data-ttu-id="78c35-121">Dinleyicinize izleme çıkışını almak istemiyorsanız, kendisine eklemeyin <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="78c35-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="78c35-122">Bağımsız bir dinleyici çıkışını yayar <xref:System.Diagnostics.Trace.Listeners%2A> dinleyicinin kendi çağırarak koleksiyon çıkış yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="78c35-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="78c35-123">Aşağıdaki örnek, bir çizgi olmayan bir dinleyici için yazma işlemi gösterilmektedir <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="78c35-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

    ```vb
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")
    myListener.WriteLine("Test message.")
    ' You must close or flush the trace listener to empty the output buffer.
    myListener.Flush()
    ```

    ```csharp
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");
    myListener.WriteLine("Test message.");
    // You must close or flush the trace listener to empty the output buffer.
    myListener.Flush();
    ```

## <a name="see-also"></a><span data-ttu-id="78c35-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78c35-124">See also</span></span>

- [<span data-ttu-id="78c35-125">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="78c35-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="78c35-126">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="78c35-126">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="78c35-127">Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="78c35-127">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="78c35-128">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="78c35-128">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
