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
ms.openlocfilehash: 82940b40b302f4a928547f2e6a0c285727e13934
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216099"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost` yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.IO.StreamWriter> yazıldığında etkinleştirilir, ancak <xref:System.IO.StreamWriter> örneği yok etmeden önce <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntemi daha sonra çağrılmaz. Bu MDA etkin olduğunda, çalışma zamanı, arabelleğe alınmış verilerin <xref:System.IO.StreamWriter>içinde hala mevcut olup olmadığını belirler. Arabelleğe alınan veriler varsa, MDA etkin olur. <xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemlerinin çağrılması, sonlandırıcıları çalıştırmaya zorlayabilir. Sonlandırıcılar, normalde Rastgele zamanlarda çalışır ve muhtemelen işlemden çıkılmaz. Bu MDA etkin olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunu daha güvenilir bir şekilde yeniden oluşturmaya yardımcı olur.  
  
## <a name="symptoms"></a>Belirtiler  
 <xref:System.IO.StreamWriter>, bir dosyaya son 1 – 4 KB 'lık verileri yazmaz.  
  
## <a name="cause"></a>Nedeni  
 <xref:System.IO.StreamWriter> verileri dahili olarak arabelleğe alır, bu, arabelleğe alınan verileri temeldeki veri deposuna yazmak için <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> yönteminin çağrılması gerekir. <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> uygun şekilde çağrılmamışsa, <xref:System.IO.StreamWriter> örneğinde arabelleğe alınan veriler beklenen şekilde yazılamaz.  
  
 Aşağıda, bu MDA 'ın yakalandığı kötü yazılmış kodun bir örneği verilmiştir.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Önceki kod, bir atık toplama tetikleniyorsa ve sonlandırıcılar bitene kadar askıya alınırsa bu MDA 'ı daha güvenilir bir şekilde etkinleştirir. Bu tür bir sorunu izlemek için aşağıdaki kodu bir hata ayıklama derlemesinde önceki metodun sonuna ekleyebilirsiniz. Bu, MDA ' yi güvenilir bir şekilde etkinleştirmeye yardımcı olur, ancak elbette sorunun nedenini düzelmez.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Çözüm  
 Bir uygulamayı veya bir <xref:System.IO.StreamWriter>örneğine sahip herhangi bir kod bloğunu kapatmadan önce <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> çağırdığınızdan emin olun. Bunu elde etmek için en iyi mekanizmalardan biri, örneğin Visual Basic `using` bir C# blok (`Using`) oluşturarak Örneğin, yazıcı için <xref:System.IO.StreamWriter.Dispose%2A> yönteminin çağrılmasını ve örneğin doğru şekilde kapatılmasını sağlamak olacaktır.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Aşağıdaki kod, `using`yerine `try/finally` kullanarak aynı çözümü gösterir.  
  
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
  
 Bu çözümlerin hiçbiri kullanılabilir (örneğin, bir <xref:System.IO.StreamWriter> statik bir değişkende depolanıyorsa ve yaşam süresinin sonunda kodu kolayca çalıştıramıyorsa), son kullanıldıktan sonra <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Flush%2A> çağırmak veya ilk kullanılmadan önce <xref:System.IO.StreamWriter.AutoFlush%2A> özelliğini `true` olarak ayarlamak bu sorundan kaçınmak zorunda kalmamak.  
  
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
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Bu ihlalin oluştuğunu belirten bir ileti.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
