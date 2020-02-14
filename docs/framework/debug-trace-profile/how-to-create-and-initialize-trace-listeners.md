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
ms.openlocfilehash: ce0df0af32d6798c89c8db6761d18febc1c398bb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217436"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="eabb7-102">Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="eabb7-102">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="eabb7-103"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları, bu iletileri alıp işleyen dinleyiciler adlı nesnelere iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="eabb7-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="eabb7-104"><xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>bir dinleyici, izleme veya hata ayıklama etkinleştirildiğinde otomatik olarak oluşturulur ve başlatılır.</span><span class="sxs-lookup"><span data-stu-id="eabb7-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="eabb7-105"><xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.Debug> çıkışının herhangi bir ek kaynağa yönlendirilmesini istiyorsanız, ek izleme dinleyicileri oluşturmanız ve başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="eabb7-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="eabb7-106">Oluşturduğunuz dinleyiciler uygulamanızın ihtiyaçlarını yansıtmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eabb7-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="eabb7-107">Örneğin, tüm izleme çıktılarına ait bir metin kaydı istiyorsanız, etkin olduğunda tüm çıktıyı yeni bir metin dosyasına yazan <xref:System.Diagnostics.TextWriterTraceListener> dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eabb7-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="eabb7-108">Öte yandan, çıktıyı yalnızca uygulama yürütmesi sırasında görüntülemek istiyorsanız, tüm çıktıyı bir konsol penceresine yönlendiren bir <xref:System.Diagnostics.ConsoleTraceListener> dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eabb7-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="eabb7-109"><xref:System.Diagnostics.EventLogTraceListener>, izleme çıkışını bir olay günlüğüne yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="eabb7-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="eabb7-110">Daha fazla bilgi için bkz. [Trace dinleyicileri](trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="eabb7-110">For more information, see [Trace Listeners](trace-listeners.md).</span></span>

<span data-ttu-id="eabb7-111">Bir [uygulama yapılandırma dosyasında](../configure-apps/index.md) veya kodunuzda izleme dinleyicileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eabb7-111">You can create trace listeners in an [application configuration file](../configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="eabb7-112">Kodunuzu değiştirmeye gerek kalmadan izleme dinleyicileri eklemenize, değiştirmenize veya kaldırmanıza izin verdiklerinden, uygulama yapılandırma dosyalarının kullanılmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="eabb7-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="eabb7-113">Bir yapılandırma dosyası kullanarak izleme dinleyicisi oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="eabb7-113">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="eabb7-114">İzleme dinleyicinizi uygulama yapılandırma dosyanızda bildirin.</span><span class="sxs-lookup"><span data-stu-id="eabb7-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="eabb7-115">Oluşturmakta olduğunuz dinleyici başka nesneler gerektiriyorsa, bunları da bildirin.</span><span class="sxs-lookup"><span data-stu-id="eabb7-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="eabb7-116">Aşağıdaki örnek, `TextWriterOutput.log`metin dosyasına yazan `myListener` adlı bir dinleyicinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eabb7-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

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

2. <span data-ttu-id="eabb7-117">İzleme dinleyicilerine bir ileti yazmak için kodunuzda <xref:System.Diagnostics.Trace> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="eabb7-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="eabb7-118">Kodda bir izleme dinleyicisi oluşturmak ve kullanmak için</span><span class="sxs-lookup"><span data-stu-id="eabb7-118">To create and use a trace listener in code</span></span>

- <span data-ttu-id="eabb7-119">İzleme dinleyicisini <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonuna ekleyin ve dinleyicilerine izleme bilgileri gönderin.</span><span class="sxs-lookup"><span data-stu-id="eabb7-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

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

    <span data-ttu-id="eabb7-120">\- veya-</span><span class="sxs-lookup"><span data-stu-id="eabb7-120">\- or -</span></span>

- <span data-ttu-id="eabb7-121">Dinleyicinizin izleme çıkışını almasını istemiyorsanız, <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonuna eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="eabb7-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="eabb7-122">Dinleyicinin kendi çıkış yöntemlerini çağırarak <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonundan bağımsız bir dinleyici aracılığıyla çıktı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eabb7-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="eabb7-123">Aşağıdaki örnek, <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonunda olmayan bir dinleyiciye bir çizgi yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eabb7-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eabb7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eabb7-124">See also</span></span>

- [<span data-ttu-id="eabb7-125">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="eabb7-125">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="eabb7-126">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="eabb7-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="eabb7-127">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="eabb7-127">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="eabb7-128">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="eabb7-128">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
