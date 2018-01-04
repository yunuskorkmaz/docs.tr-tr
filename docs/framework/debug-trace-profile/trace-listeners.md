---
title: "İz Dinleyicileri"
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
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 042b8a6f7c25c34fc06d5d0bfd4ebce6417b920f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="trace-listeners"></a><span data-ttu-id="8ccdc-102">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="8ccdc-102">Trace Listeners</span></span>
<span data-ttu-id="8ccdc-103">Kullanırken **izleme**, **hata ayıklama** ve <xref:System.Diagnostics.TraceSource>, toplama ve gönderilen iletileri kaydetmek için bir mekanizma olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="8ccdc-104">İzleme iletileri tarafından alınan *dinleyicileri*.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="8ccdc-105">Toplamak, depolamak ve izleme iletilerini yönlendirmek için bir dinleyici amacı budur.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="8ccdc-106">Dinleyicileri İzleme çıktısı günlüğü, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="8ccdc-107">Dinleyicileri kullanımına **hata ayıklama**, **izleme**, ve <xref:System.Diagnostics.TraceSource> sınıfları, her biri gönderebilir çıktısını çeşitli dinleyici nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="8ccdc-108">Yaygın olarak kullanılan önceden tanımlanmış dinleyicileri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8ccdc-108">The following are the commonly used predefined listeners:</span></span>  
  
-   <span data-ttu-id="8ccdc-109">A <xref:System.Diagnostics.TextWriterTraceListener> çıkış örneğine yönlendiren <xref:System.IO.TextWriter> sınıf veya herhangi bir şey için bir <xref:System.IO.Stream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="8ccdc-110">Bunlar için de konsolunu veya bir dosyaya yazabildiğinizi <xref:System.IO.Stream> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
-   <span data-ttu-id="8ccdc-111">Bir <xref:System.Diagnostics.EventLogTraceListener> çıkış için bir olay günlüğü yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
-   <span data-ttu-id="8ccdc-112">A <xref:System.Diagnostics.DefaultTraceListener> yayar **yazma** ve **WriteLine** iletileri için **OutputDebugString** ve **Debugger.Log** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="8ccdc-113">Visual Studio'da bu çıkış penceresinde görüntülenecek hata ayıklama iletilerini neden olur.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="8ccdc-114">**Başarısız** ve başarısız **Assert** iletileri de yayma için **OutputDebugString** Windows API ve **Debugger.Log** yöntemi ve ayrıca bir ileti kutusunu nedeni gösterilecek.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="8ccdc-115">Bu davranış için varsayılan davranıştır **hata ayıklama** ve **izleme** , çünkü iletileri **DefaultTraceListener** otomatik olarak dahil her `Listeners` Koleksiyon ve tek dinleyicisi otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
-   <span data-ttu-id="8ccdc-116">A <xref:System.Diagnostics.ConsoleTraceListener> izleme veya hata ayıklama çıkışını standart çıktı veya standart hata akışı yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
-   <span data-ttu-id="8ccdc-117">A <xref:System.Diagnostics.DelimitedListTraceListener> izleme veya hata ayıklama çıktı akışı yazıcı gibi bir metin yazıcı veya bir dosya akışı gibi bir akış yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="8ccdc-118">İzleme çıkışının tarafından belirtilen sınırlayıcıyı kullanan bir sınırlandırılmış metin biçiminde olduğundan <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
-   <span data-ttu-id="8ccdc-119">Bir <xref:System.Diagnostics.XmlWriterTraceListener> izleme veya XML olarak kodlanmış veriler olarak hata ayıklama çıkışını yönlendiren bir <xref:System.IO.TextWriter> veya bir <xref:System.IO.Stream>, gibi bir <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="8ccdc-120">Tüm dinleyici yanı sıra istiyorsanız <xref:System.Diagnostics.DefaultTraceListener> almak için **hata ayıklama**, **izleme** ve <xref:System.Diagnostics.TraceSource> çıkışı, kendisine eklemelisiniz `Listeners` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="8ccdc-121">Daha fazla bilgi için bkz: [nasıl yapılır: oluşturma ve izleme dinleyicilerini başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) ve [nasıl yapılır: kullanım TraceSource ve filtreler iz dinleyicileri ile](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="8ccdc-121">For more information, see [How to: Create and Initialize Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="8ccdc-122">Tüm dinleyici **dinleyicileri** toplama izlemesinde aynı iletilerini çıktı yöntemlerini alır.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="8ccdc-123">Örneğin, iki dinleyicileri ayarladığınız varsayalım: bir **olmalıdır** ve bir **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="8ccdc-124">Her dinleyicisi aynı iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-124">Each listener receives the same message.</span></span> <span data-ttu-id="8ccdc-125">**Olmalıdır** çıktısını bir akışa yönlendirir ve **EventLogTraceListener** çıktısını bir olay günlüğü için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="8ccdc-126">Aşağıdaki örnek çıktıya göndermek nasıl gösterir **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
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
  
 <span data-ttu-id="8ccdc-127">Hata ayıklama ve izleme paylaşmak aynı **dinleyicileri** koleksiyonu, dolayısıyla eklediğiniz bir dinleyici nesnesine bir **Debug.Listeners** koleksiyonu uygulamanızda eklenmesi için **Trace.Listeners** de koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="8ccdc-128">Aşağıdaki örnek, bir dinleyici konsola izleme bilgilerini göndermek için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="8ccdc-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="8ccdc-129">Geliştirici tarafından tanımlanan dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="8ccdc-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="8ccdc-130">Devralarak kendi dinleyicileri tanımlayabilirsiniz **TraceListener** temel sınıf ve kendi özelleştirilmiş yöntemlerinizi yöntemleriyle geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="8ccdc-131">Geliştirici tarafından tanımlanan dinleyicileri oluşturma hakkında daha fazla bilgi için bkz: <xref:System.Diagnostics.TraceListener> .NET Framework başvurusu.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccdc-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ccdc-132">See Also</span></span>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="8ccdc-133">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="8ccdc-133">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="8ccdc-134">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="8ccdc-134">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
