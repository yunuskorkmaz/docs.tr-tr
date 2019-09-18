---
title: İz Dinleyicileri
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 752a6a5f9608aa260f192ee3e9e0709b7a10e27e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052282"
---
# <a name="trace-listeners"></a>İz Dinleyicileri
**Trace**, **Debug** ve <xref:System.Diagnostics.TraceSource>kullanırken gönderilen iletileri toplamak ve kaydetmek için bir mekanizmanız olması gerekir. İzleme iletileri *dinleyiciler*tarafından alınır. Bir dinleyicinin amacı, izleme iletilerini toplamak, depolamak ve yönlendirmaktır. Dinleyiciler izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
 Dinleyicileri, her biri **hata ayıklama**, **izleme**ve <xref:System.Diagnostics.TraceSource> sınıflar tarafından kullanılabilir ve bu, çıktısını çeşitli dinleyici nesnelerine gönderebilirler. Aşağıda yaygın olarak kullanılan önceden tanımlanmış dinleyiciler verilmiştir:  
  
- <xref:System.IO.Stream> , <xref:System.Diagnostics.TextWriterTraceListener> Çıktıyısınıfının<xref:System.IO.TextWriter> bir örneğine veya bir sınıf olan herhangi bir örneğe yönlendirir. Ayrıca, bunlar sınıflar olduklarından <xref:System.IO.Stream> konsola veya bir dosyaya da yazabilir.  
  
- Çıktıyı bir olay günlüğüne yönlendirir.<xref:System.Diagnostics.EventLogTraceListener>  
  
- Bir <xref:System.Diagnostics.DefaultTraceListener> **Write** ve **WriteLine** iletilerini **OutputDebugString** ve **Debugger. log** yöntemine yayar. Visual Studio 'da bu, hata ayıklama iletilerinin çıkış penceresinde görünmesine neden olur. **Başarısız** ve başarısız **onaylama** Iletileri Ayrıca **OutputDebugString** Windows API 'sine ve **hata ayıklayıcı. log** yöntemine de sahiptir ve ayrıca bir ileti kutusunun görüntülenmesine neden olur. Bu davranış, **hata ayıklama** ve **izleme** iletilerinde varsayılan davranıştır, çünkü **DefaultTraceListener** her `Listeners` koleksiyona otomatik olarak eklenir ve tek dinleyici otomatik olarak eklenir.  
  
- Bir <xref:System.Diagnostics.ConsoleTraceListener> izleme veya hata ayıklama çıkışını standart çıktıya ya da standart hata akışına yönlendirir.  
  
- Bir <xref:System.Diagnostics.DelimitedListTraceListener> akış yazıcı gibi bir metin yazıcısına veya dosya akışı gibi bir akışa izleme veya hata ayıklama çıktısı yönlendirir. İzleme çıktısı, <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> özelliği tarafından belirtilen sınırlayıcıyı kullanan bir ayrılmış metin biçimindedir.  
  
- , Bir veya gibi bir veya öğesine <xref:System.Diagnostics.XmlWriterTraceListener> XMLkodluveriler<xref:System.IO.TextWriter> olarak izleme veya hata ayıklama çıktısı yönlendirir. <xref:System.IO.FileStream> <xref:System.IO.Stream>  
  
 **Hata ayıklama**, **izleme** <xref:System.Diagnostics.TraceSource> ve çıkış almak <xref:System.Diagnostics.DefaultTraceListener> için öğesine ek olarak herhangi bir dinleyici istiyorsanız, onu `Listeners` koleksiyona eklemeniz gerekir. Daha fazla bilgi için [nasıl yapılır: İzleme dinleyicileri](how-to-create-and-initialize-trace-listeners.md) oluşturun ve başlatın ve [şunları yapın: Izleme dinleyicileri](how-to-use-tracesource-and-filters-with-trace-listeners.md)Ile TraceSource ve filtreler kullanın. **Dinleyiciler** koleksiyonundaki herhangi bir dinleyici, izleme çıkış yöntemlerinden aynı iletileri alır. Örneğin, iki dinleyici ayarladığınızı varsayalım: bir **TextWriterTraceListener** ve bir **EventLogTraceListener**. Her dinleyici aynı iletiyi alır. **TextWriterTraceListener** , çıktısını bir akışa yönlendirebilir ve **EventLogTraceListener** çıkışını bir olay günlüğüne yönlendirebilir.  
  
 Aşağıdaki örnek, bir çıkışın **dinleyici** koleksiyonuna nasıl gönderileceğini gösterir.  
  
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
  
 Hata ayıklama ve izleme aynı **dinleyici** koleksiyonunu paylaşır, bu nedenle uygulamanızdaki bir **Debug. Listeners** koleksiyonuna bir dinleyici nesnesi eklerseniz, **Trace. Listeners** koleksiyonuna de eklenir.  
  
 Aşağıdaki örnek, bir konsola izleme bilgilerini göndermek için bir dinleyicinin nasıl kullanılacağını gösterir:  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Geliştirici tanımlı dinleyiciler  
 **TraceListener** temel sınıfından devralarak kendi dinleyicilerini tanımlayabilir ve kendi yöntemlerini özelleştirilmiş yöntemleriniz ile geçersiz kılarak tanımlayabilirsiniz. Geliştirici tanımlı dinleyiciler oluşturma hakkında daha fazla bilgi için .NET Framework başvuru <xref:System.Diagnostics.TraceListener> içindeki bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
- [İzleme Anahtarları](trace-switches.md)
