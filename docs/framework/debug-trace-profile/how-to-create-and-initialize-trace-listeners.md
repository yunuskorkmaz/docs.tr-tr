---
title: "Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ebc50e4075a5793c344cbc017eb60247c1c8774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="56a87-102">Nasıl yapılır: İz Dinleyicileri Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="56a87-102">How to: Create and Initialize Trace Listeners</span></span>
<span data-ttu-id="56a87-103"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıfları almak ve bu iletileri işleyen dinleyicileri olarak adlandırılan nesnelere ileti gönderme.</span><span class="sxs-lookup"><span data-stu-id="56a87-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="56a87-104">Bu tür bir dinleyici <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, otomatik olarak oluşturulur ve izleme veya hata ayıklama etkinleştirildiğinde başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="56a87-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="56a87-105">İsterseniz <xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.Debug> herhangi bir ek kaynağına yönlendirilmesi için çıktı, oluşturmalı ve ek izleme dinleyicileri başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="56a87-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>  
  
 <span data-ttu-id="56a87-106">Oluşturduğunuz dinleyicileri uygulamanızın gereksinimlerine yansıtmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56a87-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="56a87-107">Örneğin, metin kaydı tüm izleme çıktısını istiyorsanız, oluşturun bir <xref:System.Diagnostics.TextWriterTraceListener> dinleyici etkinleştirildiğinde, tüm çıktı yeni bir metin dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="56a87-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="56a87-108">Diğer taraftan, yalnızca uygulama yürütmesi sırasında çıktı görüntülemek istiyorsanız, oluşturma bir <xref:System.Diagnostics.ConsoleTraceListener> tüm çıkış konsol penceresine yönlendirir dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="56a87-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="56a87-109"><xref:System.Diagnostics.EventLogTraceListener> İzleme çıktısı için bir olay günlüğüne yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56a87-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="56a87-110">Daha fazla bilgi için bkz: [izleme dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="56a87-110">For more information, see [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span></span>  
  
 <span data-ttu-id="56a87-111">İzleme dinleyicileri oluşturabileceğiniz bir [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) ya da kodunuzdaki.</span><span class="sxs-lookup"><span data-stu-id="56a87-111">You can create trace listeners in an [application configuration file](../../../docs/framework/configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="56a87-112">Eklemek, değiştirmek veya iz dinleyicileri kodunuzu değiştirmek zorunda kalmadan kaldırmanıza izin vermek için uygulama yapılandırma dosyaları, kullanılmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="56a87-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="56a87-113">Oluşturma ve yapılandırma dosyası kullanarak bir izleme dinleyicisi kullanma</span><span class="sxs-lookup"><span data-stu-id="56a87-113">To create and use a trace listener by using a configuration file</span></span>  
  
1.  <span data-ttu-id="56a87-114">Uygulama yapılandırma dosyanızda, İzleme dinleyicisi bildirin.</span><span class="sxs-lookup"><span data-stu-id="56a87-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="56a87-115">Oluşturmakta olduğunuz dinleyicisi diğer nesneleri gerektiriyorsa, bunları da bildirin.</span><span class="sxs-lookup"><span data-stu-id="56a87-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="56a87-116">Aşağıdaki örnek olarak adlandırılan bir dinleyici oluşturulacağını gösterir `myListener` metin dosyasına yazar `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="56a87-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>  
  
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
  
2.  <span data-ttu-id="56a87-117">Kullanım <xref:System.Diagnostics.Trace> kodunuzda izleme dinleyicileri bir ileti yazmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="56a87-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>  
  
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
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="56a87-118">Oluşturma ve İzleme dinleyicisi kod içinde kullanma</span><span class="sxs-lookup"><span data-stu-id="56a87-118">To create and use a trace listener in code</span></span>  
  
-   <span data-ttu-id="56a87-119">İzleme dinleyicisi eklemek <xref:System.Diagnostics.Trace.Listeners%2A> izleme dinleyicileri için bilgi toplama ve Gönder.</span><span class="sxs-lookup"><span data-stu-id="56a87-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>  
  
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
  
     - <span data-ttu-id="56a87-120">veya -</span><span class="sxs-lookup"><span data-stu-id="56a87-120">or -</span></span>  
  
-   <span data-ttu-id="56a87-121">İzleme çıktısını almak için dinleyici istemiyorsanız, kendisine eklemeyin <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="56a87-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="56a87-122">Bağımsız bir dinleyici aracılığıyla çıktı yayma <xref:System.Diagnostics.Trace.Listeners%2A> dinleyicisi 's kendi çağırarak koleksiyon yöntemleri çıktı.</span><span class="sxs-lookup"><span data-stu-id="56a87-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="56a87-123">Aşağıdaki örnek, kullanımda olmayan bir dinleyici için bir satır yazmak gösterilmiştir <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="56a87-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56a87-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56a87-124">See Also</span></span>  
 [<span data-ttu-id="56a87-125">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="56a87-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="56a87-126">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="56a87-126">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="56a87-127">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="56a87-127">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="56a87-128">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="56a87-128">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
