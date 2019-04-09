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
ms.openlocfilehash: 3b35e6ab4de699126b4b3b5f74d7a9a8dacfa4a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117397"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.IO.StreamWriter> için yazılmış ancak <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntemi örneği önce sonradan çağrılmaz <xref:System.IO.StreamWriter> yok. Bu MDA etkinleştirildiğinde, çalışma zamanı arabelleğe alınan tüm veriler hala içinde var olup olmadığını belirler <xref:System.IO.StreamWriter>. Arabelleğe alınan verileri varsa, bu MDA etkinleştirilir. Çağırma <xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemleri sonlandırıcılar çalıştırmaya zorlayabilirsiniz. Sonlandırıcılar, aksi halde görünüşte rastgele zamanlarda ve muhtemelen hiçbir işlem çıkışı üzerinde çalışacaktır. Sonlandırıcılar etkin bu MDA ile açıkça çalışan daha güvenilir bir şekilde bu tür bir sorunu yeniden oluşturmak için yardımcı olur.  
  
## <a name="symptoms"></a>Belirtiler  
 A <xref:System.IO.StreamWriter> son 1 ila 4 KB veri bir dosyaya yazmaz.  
  
## <a name="cause"></a>Sebep  
 <xref:System.IO.StreamWriter> Dahili olarak veri arabelleği, gerektiren <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> yöntemi arabelleğe alınan verileri temel alınan veri deposuna yazacak şekilde çağrılabilir. Varsa <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> uygun şekilde çağrılmaz; içinde arabelleğe alınan verileri <xref:System.IO.StreamWriter> örneği, değil beklenen şekilde yazılabilir.  
  
 Bu mda'nın yakalamalısınız kötü yazılmış koduna ilişkin bir örnek verilmiştir.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Bir çöp toplama tetikleyen ve ardından sonlandırıcılar tamamlanana kadar askıya önceki kod bu mda'nın daha güvenilir bir şekilde etkinleştirir. Bu tür bir sorun izlemek için hata ayıklama derlemesinde önceki yönteminin sonuna aşağıdaki kodu ekleyebilirsiniz. Bu MDA güvenilir bir şekilde etkinleştirmeye yardımcı olur, ancak Elbette sorunun nedenini düzeltmez.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Çözüm  
 Çağırmanızı emin <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> bir uygulama ya da bir örneği olduğu herhangi bir kod bloğuna kapatmadan önce bir <xref:System.IO.StreamWriter>. Örneğiyle oluşturduğundan bu ulaşmak için en iyi mekanizmalardan biri bir C# `using` blok (`Using` Visual Basic'te), hangi emin olmanızı <xref:System.IO.StreamWriter.Dispose%2A> yazıcı için yöntemi çağrılır, doğru şekilde kapatıldığından kuşkulanılıyor örneğinde sonuç.  
  
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
  
 Bu çözümlerin hiçbiri kullanılamaması durumunda (örneğin, bir <xref:System.IO.StreamWriter> statik içinde depolanan değişkeni ve kolayca çalıştırılamaz kod ömrü sona), ardından arama <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> son kullanın ya da ayarı <xref:System.IO.StreamWriter.AutoFlush%2A> özelliğini `true` önce bu sorunun ilk kullanımını kaçınmanız gerekir.  
  
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
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın çalışma zamanı üzerinde etkisi yoktur.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
