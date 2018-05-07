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
ms.openlocfilehash: 457310fbf12ef2d6143586116f76df1720b59a6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="trace-listeners"></a>İz Dinleyicileri
Kullanırken **izleme**, **hata ayıklama** ve <xref:System.Diagnostics.TraceSource>, toplama ve gönderilen iletileri kaydetmek için bir mekanizma olması gerekir. İzleme iletileri tarafından alınan *dinleyicileri*. Toplamak, depolamak ve izleme iletilerini yönlendirmek için bir dinleyici amacı budur. Dinleyicileri İzleme çıktısı günlüğü, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
 Dinleyicileri kullanımına **hata ayıklama**, **izleme**, ve <xref:System.Diagnostics.TraceSource> sınıfları, her biri gönderebilir çıktısını çeşitli dinleyici nesneleri. Yaygın olarak kullanılan önceden tanımlanmış dinleyicileri şunlardır:  
  
-   A <xref:System.Diagnostics.TextWriterTraceListener> çıkış örneğine yönlendiren <xref:System.IO.TextWriter> sınıf veya herhangi bir şey için bir <xref:System.IO.Stream> sınıfı. Bunlar için de konsolunu veya bir dosyaya yazabildiğinizi <xref:System.IO.Stream> sınıfları.  
  
-   Bir <xref:System.Diagnostics.EventLogTraceListener> çıkış için bir olay günlüğü yeniden yönlendirir.  
  
-   A <xref:System.Diagnostics.DefaultTraceListener> yayar **yazma** ve **WriteLine** iletileri için **OutputDebugString** ve **Debugger.Log** yöntemi. Visual Studio'da bu çıkış penceresinde görüntülenecek hata ayıklama iletilerini neden olur. **Başarısız** ve başarısız **Assert** iletileri de yayma için **OutputDebugString** Windows API ve **Debugger.Log** yöntemi ve ayrıca bir ileti kutusu olması neden görüntülenir. Bu davranış için varsayılan davranıştır **hata ayıklama** ve **izleme** , çünkü iletileri **DefaultTraceListener** otomatik olarak dahil her `Listeners` Koleksiyon ve tek dinleyicisi otomatik olarak eklenir.  
  
-   A <xref:System.Diagnostics.ConsoleTraceListener> izleme veya hata ayıklama çıkışını standart çıktı veya standart hata akışı yönlendirir.  
  
-   A <xref:System.Diagnostics.DelimitedListTraceListener> izleme veya hata ayıklama çıktı akışı yazıcı gibi bir metin yazıcı veya bir dosya akışı gibi bir akış yönlendirir. İzleme çıkışının tarafından belirtilen sınırlayıcıyı kullanan bir sınırlandırılmış metin biçiminde olduğundan <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> özelliği.  
  
-   Bir <xref:System.Diagnostics.XmlWriterTraceListener> izleme veya XML olarak kodlanmış veriler olarak hata ayıklama çıkışını yönlendiren bir <xref:System.IO.TextWriter> veya bir <xref:System.IO.Stream>, gibi bir <xref:System.IO.FileStream>.  
  
 Tüm dinleyici yanı sıra istiyorsanız <xref:System.Diagnostics.DefaultTraceListener> almak için **hata ayıklama**, **izleme** ve <xref:System.Diagnostics.TraceSource> çıkışı, kendisine eklemelisiniz `Listeners` koleksiyonu. Daha fazla bilgi için bkz: [nasıl yapılır: oluşturma ve izleme dinleyicilerini başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) ve [nasıl yapılır: kullanım TraceSource ve filtreler iz dinleyicileri ile](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md). Tüm dinleyici **dinleyicileri** toplama izlemesinde aynı iletilerini çıktı yöntemlerini alır. Örneğin, iki dinleyicileri ayarladığınız varsayalım: bir **olmalıdır** ve bir **EventLogTraceListener**. Her dinleyicisi aynı iletiyi alır. **Olmalıdır** çıktısını bir akışa yönlendirir ve **EventLogTraceListener** çıktısını bir olay günlüğü için yönlendirir.  
  
 Aşağıdaki örnek çıktıya göndermek nasıl gösterir **dinleyicileri** koleksiyonu.  
  
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
  
 Hata ayıklama ve izleme paylaşmak aynı **dinleyicileri** koleksiyonu, dolayısıyla eklediğiniz bir dinleyici nesnesine bir **Debug.Listeners** koleksiyonu uygulamanızda eklenmesi için **Trace.Listeners** de koleksiyonu.  
  
 Aşağıdaki örnek, bir dinleyici konsola izleme bilgilerini göndermek için nasıl kullanılacağını gösterir:  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Geliştirici tarafından tanımlanan dinleyicileri  
 Devralarak kendi dinleyicileri tanımlayabilirsiniz **TraceListener** temel sınıf ve kendi özelleştirilmiş yöntemlerinizi yöntemleriyle geçersiz kılma. Geliştirici tarafından tanımlanan dinleyicileri oluşturma hakkında daha fazla bilgi için bkz: <xref:System.Diagnostics.TraceListener> .NET Framework başvurusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
