---
title: İz Dinleyicileri
description: .NET ' te gönderilen izleme iletilerinin toplanması ve kaydedilmesi için bir mekanizma olan izleme dinleyicilerini keşfedebilirsiniz. Bir dinleyici iletileri toplar, depolar ve yönlendirir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
ms.openlocfilehash: d08f86c782284a296090cf63e4b03c8d446a95fc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803529"
---
# <a name="trace-listeners"></a><span data-ttu-id="ca3d7-104">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="ca3d7-104">Trace Listeners</span></span>
<span data-ttu-id="ca3d7-105">**Trace**, **Debug** ve kullanırken <xref:System.Diagnostics.TraceSource> gönderilen iletileri toplamak ve kaydetmek için bir mekanizmanız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-105">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="ca3d7-106">İzleme iletileri *dinleyiciler*tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-106">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="ca3d7-107">Bir dinleyicinin amacı, izleme iletilerini toplamak, depolamak ve yönlendirmaktır.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-107">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="ca3d7-108">Dinleyiciler izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-108">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="ca3d7-109">Dinleyicileri, her biri **hata ayıklama**, **izleme**ve sınıflar tarafından kullanılabilir ve <xref:System.Diagnostics.TraceSource> Bu, çıktısını çeşitli dinleyici nesnelerine gönderebilirler.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-109">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="ca3d7-110">Aşağıda yaygın olarak kullanılan önceden tanımlanmış dinleyiciler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ca3d7-110">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="ca3d7-111"><xref:System.Diagnostics.TextWriterTraceListener>, Çıktıyı sınıfının bir örneğine <xref:System.IO.TextWriter> veya bir sınıf olan herhangi bir örneğe yönlendirir <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="ca3d7-111">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="ca3d7-112">Ayrıca, bunlar sınıflar olduklarından konsola veya bir dosyaya da yazabilir <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="ca3d7-112">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="ca3d7-113"><xref:System.Diagnostics.EventLogTraceListener>Çıktıyı bir olay günlüğüne yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-113">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="ca3d7-114">Bir <xref:System.Diagnostics.DefaultTraceListener> **Write** ve **WriteLine** Iletilerini **OutputDebugString** ve **Debugger. log** yöntemine yayar.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-114">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="ca3d7-115">Visual Studio 'da bu, hata ayıklama iletilerinin çıkış penceresinde görünmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-115">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="ca3d7-116">**Başarısız** ve başarısız **onaylama** Iletileri Ayrıca **OutputDebugString** Windows API 'sine ve **hata ayıklayıcı. log** yöntemine de sahiptir ve ayrıca bir ileti kutusunun görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-116">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="ca3d7-117">Bu davranış, **hata ayıklama** ve **izleme** iletilerinde varsayılan davranıştır, çünkü **DefaultTraceListener** her koleksiyona otomatik olarak eklenir `Listeners` ve tek dinleyici otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-117">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="ca3d7-118">Bir <xref:System.Diagnostics.ConsoleTraceListener> izleme veya hata ayıklama çıkışını standart çıktıya ya da standart hata akışına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-118">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="ca3d7-119">Bir <xref:System.Diagnostics.DelimitedListTraceListener> akış yazıcı gibi bir metin yazıcısına veya dosya akışı gibi bir akışa izleme veya hata ayıklama çıktısı yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-119">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="ca3d7-120">İzleme çıktısı, özelliği tarafından belirtilen sınırlayıcıyı kullanan bir ayrılmış metin biçimindedir <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca3d7-120">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="ca3d7-121">, Bir veya gibi bir <xref:System.Diagnostics.XmlWriterTraceListener> veya ÖĞESINE XML kodlu veriler olarak izleme veya hata ayıklama çıktısı yönlendirir <xref:System.IO.TextWriter> <xref:System.IO.Stream> <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="ca3d7-121">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="ca3d7-122"><xref:System.Diagnostics.DefaultTraceListener> **Hata ayıklama**, **izleme** ve çıkış almak için öğesine ek olarak herhangi bir dinleyici istiyorsanız <xref:System.Diagnostics.TraceSource> , onu koleksiyona eklemeniz gerekir `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="ca3d7-122">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="ca3d7-123">Daha fazla bilgi için bkz. [nasıl yapılır: Izleme dinleyicileri oluşturma ve başlatma](how-to-create-and-initialize-trace-listeners.md) ve [nasıl yapılır: Izleme dinleyicileri Ile TraceSource ve filtreler kullanma](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="ca3d7-123">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="ca3d7-124">**Dinleyiciler** koleksiyonundaki herhangi bir dinleyici, izleme çıkış yöntemlerinden aynı iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-124">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="ca3d7-125">Örneğin, iki dinleyici ayarladığınızı varsayalım: bir **TextWriterTraceListener** ve bir **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-125">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="ca3d7-126">Her dinleyici aynı iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-126">Each listener receives the same message.</span></span> <span data-ttu-id="ca3d7-127">**TextWriterTraceListener** , çıktısını bir akışa yönlendirebilir ve **EventLogTraceListener** çıkışını bir olay günlüğüne yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-127">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="ca3d7-128">Aşağıdaki örnek, bir çıkışın **dinleyici** koleksiyonuna nasıl gönderileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-128">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="ca3d7-129">Hata ayıklama ve izleme aynı **dinleyici** koleksiyonunu paylaşır, bu nedenle uygulamanızdaki bir **Debug. Listeners** koleksiyonuna bir dinleyici nesnesi eklerseniz, **Trace. Listeners** koleksiyonuna de eklenir.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-129">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="ca3d7-130">Aşağıdaki örnek, bir konsola izleme bilgilerini göndermek için bir dinleyicinin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ca3d7-130">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="ca3d7-131">Geliştirici tanımlı dinleyiciler</span><span class="sxs-lookup"><span data-stu-id="ca3d7-131">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="ca3d7-132">**TraceListener** temel sınıfından devralarak kendi dinleyicilerini tanımlayabilir ve kendi yöntemlerini özelleştirilmiş yöntemleriniz ile geçersiz kılarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-132">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="ca3d7-133">Geliştirici tanımlı dinleyiciler oluşturma hakkında daha fazla bilgi için <xref:System.Diagnostics.TraceListener> .NET Framework başvuru içindeki bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-133">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca3d7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca3d7-134">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ca3d7-135">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="ca3d7-135">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="ca3d7-136">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="ca3d7-136">Trace Switches</span></span>](trace-switches.md)
