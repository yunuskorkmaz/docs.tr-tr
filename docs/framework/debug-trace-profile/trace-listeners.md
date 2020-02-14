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
ms.openlocfilehash: a51c046a296fbb62d21c7784cf7c1e78b700f3e9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216136"
---
# <a name="trace-listeners"></a>İz Dinleyicileri
**Trace**, **Debug** ve <xref:System.Diagnostics.TraceSource>kullanırken, gönderilen iletileri toplama ve kaydetme mekanizmasına sahip olmanız gerekir. İzleme iletileri *dinleyiciler*tarafından alınır. Bir dinleyicinin amacı, izleme iletilerini toplamak, depolamak ve yönlendirmaktır. Dinleyiciler izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
 Dinleyicileri, her biri **hata ayıklama**, **izleme**ve <xref:System.Diagnostics.TraceSource> sınıflarında kullanılabilir ve bu, çıktısını çeşitli dinleyici nesnelerine gönderebilirler. Aşağıda yaygın olarak kullanılan önceden tanımlanmış dinleyiciler verilmiştir:  
  
- <xref:System.Diagnostics.TextWriterTraceListener>, çıktıyı <xref:System.IO.TextWriter> sınıfının bir örneğine veya <xref:System.IO.Stream> sınıf olan herhangi bir örneğe yönlendirir. Ayrıca, bu <xref:System.IO.Stream> sınıflar olduğundan konsola veya bir dosyaya da yazabilir.  
  
- Bir <xref:System.Diagnostics.EventLogTraceListener> çıkışı bir olay günlüğüne yönlendirir.  
  
- <xref:System.Diagnostics.DefaultTraceListener>, **OutputDebugString** ve **Debugger. log** yöntemine **Write** ve **WriteLine** iletilerini yayar. Visual Studio 'da bu, hata ayıklama iletilerinin çıkış penceresinde görünmesine neden olur. **Başarısız** ve başarısız **onaylama** Iletileri Ayrıca **OutputDebugString** Windows API 'sine ve **hata ayıklayıcı. log** yöntemine de sahiptir ve ayrıca bir ileti kutusunun görüntülenmesine neden olur. Bu davranış, **hata ayıklama** ve **izleme** iletileri için varsayılan davranıştır, çünkü **DefaultTraceListener** her `Listeners` koleksiyonuna otomatik olarak dahildir ve tek dinleyici otomatik olarak eklenir.  
  
- <xref:System.Diagnostics.ConsoleTraceListener>, izleme veya hata ayıklama çıkışını standart çıktıya ya da standart hata akışına yönlendirir.  
  
- <xref:System.Diagnostics.DelimitedListTraceListener>, çıkış veya hata ayıklama çıkışını akış yazıcı gibi bir metin yazıcısına veya dosya akışı gibi bir akışa yönlendirir. İzleme çıktısı, <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> özelliği tarafından belirtilen sınırlayıcıyı kullanan sınırlandırılmış bir metin biçimindedir.  
  
- <xref:System.Diagnostics.XmlWriterTraceListener>, izleme veya hata ayıklama çıkışını XML kodlu veriler olarak bir <xref:System.IO.TextWriter> ya da <xref:System.IO.FileStream>gibi bir <xref:System.IO.Stream>yönlendirir.  
  
 <xref:System.Diagnostics.DefaultTraceListener> **hata ayıklama**, **izleme** ve <xref:System.Diagnostics.TraceSource> çıktısını almak için herhangi bir dinleyici istiyorsanız, `Listeners` koleksiyonuna eklemeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Izleme dinleyicileri oluşturma ve başlatma](how-to-create-and-initialize-trace-listeners.md) ve [nasıl yapılır: Izleme dinleyicileri Ile TraceSource ve filtreler kullanma](how-to-use-tracesource-and-filters-with-trace-listeners.md). **Dinleyiciler** koleksiyonundaki herhangi bir dinleyici, izleme çıkış yöntemlerinden aynı iletileri alır. Örneğin, iki dinleyici ayarladığınızı varsayalım: bir **TextWriterTraceListener** ve bir **EventLogTraceListener**. Her dinleyici aynı iletiyi alır. **TextWriterTraceListener** , çıktısını bir akışa yönlendirebilir ve **EventLogTraceListener** çıkışını bir olay günlüğüne yönlendirebilir.  
  
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
 **TraceListener** temel sınıfından devralarak kendi dinleyicilerini tanımlayabilir ve kendi yöntemlerini özelleştirilmiş yöntemleriniz ile geçersiz kılarak tanımlayabilirsiniz. Geliştirici tanımlı dinleyiciler oluşturma hakkında daha fazla bilgi için .NET Framework başvurusunda <xref:System.Diagnostics.TraceListener> bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
- [İzleme Anahtarları](trace-switches.md)
