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
# <a name="trace-listeners"></a>İz Dinleyicileri
**Trace**, **Debug** ve kullanırken <xref:System.Diagnostics.TraceSource> gönderilen iletileri toplamak ve kaydetmek için bir mekanizmanız olması gerekir. İzleme iletileri *dinleyiciler*tarafından alınır. Bir dinleyicinin amacı, izleme iletilerini toplamak, depolamak ve yönlendirmaktır. Dinleyiciler izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
 Dinleyicileri, her biri **hata ayıklama**, **izleme**ve sınıflar tarafından kullanılabilir ve <xref:System.Diagnostics.TraceSource> Bu, çıktısını çeşitli dinleyici nesnelerine gönderebilirler. Aşağıda yaygın olarak kullanılan önceden tanımlanmış dinleyiciler verilmiştir:  
  
- <xref:System.Diagnostics.TextWriterTraceListener>, Çıktıyı sınıfının bir örneğine <xref:System.IO.TextWriter> veya bir sınıf olan herhangi bir örneğe yönlendirir <xref:System.IO.Stream> . Ayrıca, bunlar sınıflar olduklarından konsola veya bir dosyaya da yazabilir <xref:System.IO.Stream> .  
  
- <xref:System.Diagnostics.EventLogTraceListener>Çıktıyı bir olay günlüğüne yönlendirir.  
  
- Bir <xref:System.Diagnostics.DefaultTraceListener> **Write** ve **WriteLine** Iletilerini **OutputDebugString** ve **Debugger. log** yöntemine yayar. Visual Studio 'da bu, hata ayıklama iletilerinin çıkış penceresinde görünmesine neden olur. **Başarısız** ve başarısız **onaylama** Iletileri Ayrıca **OutputDebugString** Windows API 'sine ve **hata ayıklayıcı. log** yöntemine de sahiptir ve ayrıca bir ileti kutusunun görüntülenmesine neden olur. Bu davranış, **hata ayıklama** ve **izleme** iletilerinde varsayılan davranıştır, çünkü **DefaultTraceListener** her koleksiyona otomatik olarak eklenir `Listeners` ve tek dinleyici otomatik olarak eklenir.  
  
- Bir <xref:System.Diagnostics.ConsoleTraceListener> izleme veya hata ayıklama çıkışını standart çıktıya ya da standart hata akışına yönlendirir.  
  
- Bir <xref:System.Diagnostics.DelimitedListTraceListener> akış yazıcı gibi bir metin yazıcısına veya dosya akışı gibi bir akışa izleme veya hata ayıklama çıktısı yönlendirir. İzleme çıktısı, özelliği tarafından belirtilen sınırlayıcıyı kullanan bir ayrılmış metin biçimindedir <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> .  
  
- , Bir veya gibi bir <xref:System.Diagnostics.XmlWriterTraceListener> veya ÖĞESINE XML kodlu veriler olarak izleme veya hata ayıklama çıktısı yönlendirir <xref:System.IO.TextWriter> <xref:System.IO.Stream> <xref:System.IO.FileStream> .  
  
 <xref:System.Diagnostics.DefaultTraceListener> **Hata ayıklama**, **izleme** ve çıkış almak için öğesine ek olarak herhangi bir dinleyici istiyorsanız <xref:System.Diagnostics.TraceSource> , onu koleksiyona eklemeniz gerekir `Listeners` . Daha fazla bilgi için bkz. [nasıl yapılır: Izleme dinleyicileri oluşturma ve başlatma](how-to-create-and-initialize-trace-listeners.md) ve [nasıl yapılır: Izleme dinleyicileri Ile TraceSource ve filtreler kullanma](how-to-use-tracesource-and-filters-with-trace-listeners.md). **Dinleyiciler** koleksiyonundaki herhangi bir dinleyici, izleme çıkış yöntemlerinden aynı iletileri alır. Örneğin, iki dinleyici ayarladığınızı varsayalım: bir **TextWriterTraceListener** ve bir **EventLogTraceListener**. Her dinleyici aynı iletiyi alır. **TextWriterTraceListener** , çıktısını bir akışa yönlendirebilir ve **EventLogTraceListener** çıkışını bir olay günlüğüne yönlendirebilir.  
  
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
 **TraceListener** temel sınıfından devralarak kendi dinleyicilerini tanımlayabilir ve kendi yöntemlerini özelleştirilmiş yöntemleriniz ile geçersiz kılarak tanımlayabilirsiniz. Geliştirici tanımlı dinleyiciler oluşturma hakkında daha fazla bilgi için <xref:System.Diagnostics.TraceListener> .NET Framework başvuru içindeki bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
- [İzleme Anahtarları](trace-switches.md)
