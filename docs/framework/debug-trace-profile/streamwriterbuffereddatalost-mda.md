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
ms.openlocfilehash: c3dcdd329318d48efa203d2b9dcbfe3501d94b3e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052275"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
<xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A> Yönetilen hata ayıklama Yardımcısı (MDA), öğesine yazıldığında etkinleştirilir, ancak ya da yöntemi daha sonra örneği yok edildiğinde çağrılır. `streamWriterBufferedDataLost` Bu MDA etkin olduğunda, çalışma zamanı, arabelleğe alınmış verilerin hala içinde <xref:System.IO.StreamWriter>varolup olmadığını belirler. Arabelleğe alınan veriler varsa, MDA etkin olur. <xref:System.GC.Collect%2A> Ve<xref:System.GC.WaitForPendingFinalizers%2A> yöntemlerini çağırmak, sonlandırıcıları çalıştırmaya zorlayabilir. Sonlandırıcılar, normalde Rastgele zamanlarda çalışır ve muhtemelen işlemden çıkılmaz. Bu MDA etkin olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunu daha güvenilir bir şekilde yeniden oluşturmaya yardımcı olur.  
  
## <a name="symptoms"></a>Belirtiler  
 A <xref:System.IO.StreamWriter> bir dosyaya son 1 – 4 KB veri yazmaz.  
  
## <a name="cause"></a>Sebep  
 Verileri dahili olarak arabelleğe <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> alır. Bu, ya da yönteminin, arabelleğe alınan verileri temeldeki veri deposuna yazmak üzere çağrılması gerekir. <xref:System.IO.StreamWriter> Ya da <xref:System.IO.StreamWriter.Flush%2A> uygun bir şekilde çağrılmamışsa <xref:System.IO.StreamWriter> , örnekte ara belleğe alınan veriler beklenen şekilde yazılmayabilir. <xref:System.IO.StreamWriter.Close%2A>  
  
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
 Bir uygulamayı veya bir <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Flush%2A> örneğine<xref:System.IO.StreamWriter>sahip herhangi bir kod bloğunu kapatmadan önce veya ' de ' i çağırdığınızdan emin olun. Bunu elde etmek için en iyi mekanizmalardan biri, örneğin C# `using` , yazıcı <xref:System.IO.StreamWriter.Dispose%2A> yönteminin çağrılmasını ve`Using` örneğin doğru şekilde kapatılmasını sağlamak için bir blok (Visual Basic) ile örneği oluşturmaktır.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Aşağıdaki kod, `try/finally` `using`yerine kullanılarak aynı çözümü gösterir.  
  
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
  
 Bu çözümlerin hiçbiri kullanılabilir değilse <xref:System.IO.StreamWriter> (örneğin, bir statik değişkende depolanıyorsa ve yaşam süresinin sonunda kodu kolayca çalıştıramıyorsa), <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> en son kullanımı veya ayarı <xref:System.IO.StreamWriter.AutoFlush%2A> ilk kullanımı `true` öncesindeki özelliğin bu sorundan kaçınmak gerekir.  
  
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
  
## <a name="output"></a>Çıkış  
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
