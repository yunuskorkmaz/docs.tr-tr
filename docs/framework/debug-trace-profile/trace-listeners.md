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
ms.openlocfilehash: 35aec3a311680e398d9f2bba94bf4c9a274c8a04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137910"
---
# <a name="trace-listeners"></a>İz Dinleyicileri
Kullanırken **izleme**, **hata ayıklama** ve <xref:System.Diagnostics.TraceSource>, toplama ve gönderilen iletilerin kaydetmek için bir mekanizma olması gerekir. İzleme iletileri tarafından alınan *dinleyicileri*. Toplamak, depolamak ve izleme iletilerini yönlendirmek için bir dinleyici amacı olan. Dinleyiciler bir günlük, pencere veya metin dosyası gibi uygun bir hedef izleme çıkışa doğrudan.  
  
 Dinleyici için kullanılabilir **hata ayıklama**, **izleme**, ve <xref:System.Diagnostics.TraceSource> her biri gönderebilir çıktısını dinleyici nesneleri için çeşitli sınıflar. Yaygın olarak kullanılan önceden tanımlanmış dinleyicileri şunlardır:  
  
-   A <xref:System.Diagnostics.TextWriterTraceListener> çıkış örneğine yeniden yönlendirir <xref:System.IO.TextWriter> sınıfı veya için herhangi bir <xref:System.IO.Stream> sınıfı. Bu olduğundan, ayrıca konsola veya bir dosyaya yazabilirsiniz <xref:System.IO.Stream> sınıfları.  
  
-   Bir <xref:System.Diagnostics.EventLogTraceListener> çıkış için olay günlüğünü yeniden yönlendirir.  
  
-   A <xref:System.Diagnostics.DefaultTraceListener> yayan **yazma** ve **WriteLine** iletileri **OutputDebugString** ve **Debugger.Log** yöntemi. Visual Studio'da bu çıkış penceresinde görüntülenecek hata ayıklama iletilerini neden olur. **Başarısız** ve başarısız **Assert** iletileri de yaymak için **OutputDebugString** Windows API ve **Debugger.Log** yöntemi ve bir ileti kutusunda olmasını nedeni görüntülenir. Bu davranış için varsayılan davranıştır **hata ayıklama** ve **izleme** çünkü iletileri **DefaultTraceListener** otomatik olarak dahil her `Listeners` Koleksiyon ve otomatik olarak dahil yalnızca bir dinleyicisi.  
  
-   A <xref:System.Diagnostics.ConsoleTraceListener> izleme veya hata ayıklama çıkışını standart çıktı veya standart hata akışı yönlendirir.  
  
-   A <xref:System.Diagnostics.DelimitedListTraceListener> izleme veya hata ayıklama çıkışını bir akış yazıcı gibi bir metin yazıcı veya bir dosya akışı gibi bir akışa yönlendirir. İzleme çıktısına tarafından belirtilen bir sınırlayıcı kullanan bir sınırlandırılmış metin biçiminde olduğundan <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> özelliği.  
  
-   Bir <xref:System.Diagnostics.XmlWriterTraceListener> izleme veya XML kodlu veriler olarak hata ayıklama çıkışını yönlendiren bir <xref:System.IO.TextWriter> veya bir <xref:System.IO.Stream>, gibi bir <xref:System.IO.FileStream>.  
  
 Yanı sıra herhangi bir dinleyici istiyorsanız <xref:System.Diagnostics.DefaultTraceListener> almaya **hata ayıklama**, **izleme** ve <xref:System.Diagnostics.TraceSource> çıkışı, kendisine eklemelisiniz `Listeners` koleksiyonu. Daha fazla bilgi için [nasıl yapılır: İzleme dinleyicileri oluşturma ve başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) ve [nasıl yapılır: İzleme dinleyicileri ile TraceSource ve filtreler kullanma](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md). İçinde herhangi bir dinleyici **dinleyicileri** koleksiyon çıktı yöntemlerini izlemesinden aynı iletileri alır. Örneğin, iki dinleyiciden ayarladığınız varsayalım: bir **TextWriterTraceListener** ve **EventLogTraceListener**. Her dinleyici aynı iletiyi alır. **TextWriterTraceListener** çıktısını bir akışa yönlendirmelisiniz ve **EventLogTraceListener** çıktısını bir olay günlüğüne yönlendirir.  
  
 Aşağıdaki örnek için çıkış göndermek nasıl gösterir **dinleyicileri** koleksiyonu.  
  
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
  
 Hata ayıklama ve izleme paylaşmak aynı **dinleyicileri** koleksiyonu, dolayısıyla eklediğiniz bir dinleyici nesnesine bir **Debug.Listeners** koleksiyonu, uygulamanızda bu eklenen **Trace.Listeners** de koleksiyonu.  
  
 Aşağıdaki örnek, konsola izleme bilgilerini göndermek için bir dinleyici kullanmayı gösterir:  
  
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
 Kendi dinleyicileri devralarak tanımlayabileceğiniz **TraceListener** temel sınıf ve kendi özelleştirilmiş yöntemlerinizi yöntemleriyle geçersiz kılma. Geliştirici tarafından tanımlanan dinleyicileri oluşturma ile ilgili daha fazla bilgi için bkz: <xref:System.Diagnostics.TraceListener> .NET Framework başvurusu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [İzleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
