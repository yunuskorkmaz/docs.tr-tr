---
title: 'Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma'
description: .NET içinde System. Diagnostics. DefaultTraceListener gibi sınıfları kullanarak izleme dinleyicileri oluşturmayı ve başlatmayı öğrenin.
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
ms.openlocfilehash: 752306124e41a7fb7458daccc8c2891631eb9616
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051213"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="dc37b-103">Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="dc37b-103">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="dc37b-104"><xref:System.Diagnostics.Debug?displayProperty=nameWithType>Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları, bu iletileri alıp işleyen dinleyiciler adlı nesnelere iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="dc37b-104">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="dc37b-105">Bu tür bir dinleyici, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType> izleme veya hata ayıklama etkinleştirildiğinde otomatik olarak oluşturulur ve başlatılır.</span><span class="sxs-lookup"><span data-stu-id="dc37b-105">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="dc37b-106"><xref:System.Diagnostics.Trace>Ya da <xref:System.Diagnostics.Debug> çıktının herhangi bir ek kaynağa yönlendirilmesini istiyorsanız, ek izleme dinleyicileri oluşturmanız ve bunları başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="dc37b-106">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="dc37b-107">Oluşturduğunuz dinleyiciler uygulamanızın ihtiyaçlarını yansıtmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc37b-107">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="dc37b-108">Örneğin, tüm izleme çıktılarına ait bir metin kaydı istiyorsanız, <xref:System.Diagnostics.TextWriterTraceListener> etkin olduğunda tüm çıktıyı yeni bir metin dosyasına yazan bir dinleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc37b-108">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="dc37b-109">Öte yandan, çıktıyı yalnızca uygulama yürütmesi sırasında görüntülemek istiyorsanız, <xref:System.Diagnostics.ConsoleTraceListener> tüm çıktıyı bir konsol penceresine yönlendiren bir dinleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc37b-109">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="dc37b-110">, <xref:System.Diagnostics.EventLogTraceListener> İzleme çıkışını bir olay günlüğüne yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="dc37b-110">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="dc37b-111">Daha fazla bilgi için bkz. [Trace dinleyicileri](trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="dc37b-111">For more information, see [Trace Listeners](trace-listeners.md).</span></span>

<span data-ttu-id="dc37b-112">Bir [uygulama yapılandırma dosyasında](../configure-apps/index.md) veya kodunuzda izleme dinleyicileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc37b-112">You can create trace listeners in an [application configuration file](../configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="dc37b-113">Kodunuzu değiştirmeye gerek kalmadan izleme dinleyicileri eklemenize, değiştirmenize veya kaldırmanıza izin verdiklerinden, uygulama yapılandırma dosyalarının kullanılmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="dc37b-113">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="dc37b-114">Bir yapılandırma dosyası kullanarak izleme dinleyicisi oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="dc37b-114">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="dc37b-115">İzleme dinleyicinizi uygulama yapılandırma dosyanızda bildirin.</span><span class="sxs-lookup"><span data-stu-id="dc37b-115">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="dc37b-116">Oluşturmakta olduğunuz dinleyici başka nesneler gerektiriyorsa, bunları da bildirin.</span><span class="sxs-lookup"><span data-stu-id="dc37b-116">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="dc37b-117">Aşağıdaki örnek, metin dosyasına yazan adlı bir dinleyicinin nasıl oluşturulacağını gösterir `myListener` `TextWriterOutput.log` .</span><span class="sxs-lookup"><span data-stu-id="dc37b-117">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

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

2. <span data-ttu-id="dc37b-118"><xref:System.Diagnostics.Trace>Trace dinleyicilerine bir ileti yazmak için kodunuzda sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="dc37b-118">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="dc37b-119">Kodda bir izleme dinleyicisi oluşturmak ve kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dc37b-119">To create and use a trace listener in code</span></span>

- <span data-ttu-id="dc37b-120">İzleme dinleyicisini <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyona ekleyin ve dinleyicilerine izleme bilgileri gönderin.</span><span class="sxs-lookup"><span data-stu-id="dc37b-120">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

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

    <span data-ttu-id="dc37b-121">\-veya</span><span class="sxs-lookup"><span data-stu-id="dc37b-121">\- or -</span></span>

- <span data-ttu-id="dc37b-122">Dinleyicinizin izleme çıkışını almasını istemiyorsanız, <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyona eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="dc37b-122">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="dc37b-123">Dinleyicinin kendi çıkış yöntemlerini çağırarak, bir dinleyicinin içinden bir dinleyici aracılığıyla çıkış yapabilirsiniz <xref:System.Diagnostics.Trace.Listeners%2A> .</span><span class="sxs-lookup"><span data-stu-id="dc37b-123">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="dc37b-124">Aşağıdaki örnek, koleksiyonda olmayan bir dinleyicinin bir satırın nasıl yazılacağını gösterir <xref:System.Diagnostics.Trace.Listeners%2A> .</span><span class="sxs-lookup"><span data-stu-id="dc37b-124">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dc37b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc37b-125">See also</span></span>

- [<span data-ttu-id="dc37b-126">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="dc37b-126">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="dc37b-127">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="dc37b-127">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="dc37b-128">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="dc37b-128">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="dc37b-129">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="dc37b-129">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
