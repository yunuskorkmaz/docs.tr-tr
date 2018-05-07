---
title: streamWriterBufferedDataLost MDA
ms.date: 03/30/2017
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15957ce03925d75021d88bc81d12809c3fe31c2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.IO.StreamWriter> için yazılmış ancak <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntemi sonradan çağrılmaz örneğini önce <xref:System.IO.StreamWriter> yok. Bu MDA etkinleştirildiğinde, çalışma zamanı herhangi bir arabelleğe alınan veri hala içinde var olup olmadığının <xref:System.IO.StreamWriter>. Arabelleğe alınan verileri mevcut değilse MDA etkinleştirilir. Çağırma <xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemleri çalıştırmak için sonlandırıcılar zorlayabilirsiniz. Sonlandırıcılar, aksi halde görünen rasgele zamanlarda ve büyük olasılıkla hiç işlem Çıkışta çalışacaktır. Açıkça sonlandırıcılar etkin bu MDA ile çalışan bu tür sorunlar daha güvenilir bir şekilde oluşturmaya yardımcı olur.  
  
## <a name="symptoms"></a>Belirtiler  
 A <xref:System.IO.StreamWriter> son 1 – 4 KB'lık verinin bir dosyaya yazmaz.  
  
## <a name="cause"></a>Sebep  
 <xref:System.IO.StreamWriter> Dahili olarak, veri arabelleği, gerektiren <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> yöntemi, temel alınan veri deposuna arabelleğe alınan veri yazmak için çağrılabilir. Varsa <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> uygun şekilde çağrılmaz, içinde arabelleğe alınan verileri <xref:System.IO.StreamWriter> örneği değil yazılmaya beklendiği gibi.  
  
 Bu MDA catch kötü yazılmış kodun bir örnek verilmiştir.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Çöp toplama tetiklenen ve sonlandırıcılar bitinceye kadar sonra askıya önceki kod bu MDA daha güvenilir bir şekilde etkinleştirir. Bu tür sorunlar izlemek için hata ayıklama derlemesi içinde önceki yönteminin sonuna aşağıdaki kod ekleyebilirsiniz. Bu, güvenilir bir şekilde MDA etkinleştirmek için yardımcı olur, ancak Elbette sorunun nedenini gideremiyor.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Çözüm  
 Çağırmanız emin olun <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> bir uygulama veya bir örneğine sahip herhangi bir kod bloğuna kapatmadan önce bir <xref:System.IO.StreamWriter>. Bunu elde etmek için en iyi mekanizmalardan biri oluştururken örnek bir C# ile `using` blok (`Using` Visual Basic'te), emin olun <xref:System.IO.StreamWriter.Dispose%2A> yazıcı için yöntem çağrıldığında, doğru kapatılan örneğinde kaynaklanan.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Aşağıdaki kod aynı çözüm gösterir kullanarak `try/finally` yerine `using`.  
  
```csharp
StreamWriter sw;  
try   
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally   
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 Bu çözümlerin hiçbiri kullanılıp kullanılamayacağını (örneğin, bir <xref:System.IO.StreamWriter> statik içinde depolanan değişken ve kolayca çalıştıramaz kodu çalışma süresi sonunda), ardından çağırma <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> son kullanın veya ayar sonra <xref:System.IO.StreamWriter.AutoFlush%2A> özelliğine `true` önce ilk kullanımı bu sorunu kaçınmalısınız.  
  
```csharp
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()   
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA çalışma zamanı üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Bu ihlali oluştuğunu belirten bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StreamWriter>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
