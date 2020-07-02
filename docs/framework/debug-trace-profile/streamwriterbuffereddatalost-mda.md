---
title: streamWriterBufferedDataLost MDA
description: Bir StreamWriter bir dosyaya son 1 – 4 KB 'lık verileri yazmazsa etkinleştirebileceğiniz streamWriterBufferedDataLost yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: 0c10ea6bb9dc0aaafa2ac1798696579af7592895
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803497"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost`Yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.IO.StreamWriter> öğesine yazıldığında etkinleştirilir, ancak <xref:System.IO.StreamWriter.Flush%2A> ya da <xref:System.IO.StreamWriter.Close%2A> yöntemi daha sonra örneği yok <xref:System.IO.StreamWriter> edildiğinde çağrılır. Bu MDA etkin olduğunda, çalışma zamanı, arabelleğe alınmış verilerin hala içinde varolup olmadığını belirler <xref:System.IO.StreamWriter> . Arabelleğe alınan veriler varsa, MDA etkin olur. <xref:System.GC.Collect%2A>Ve yöntemlerini çağırmak, <xref:System.GC.WaitForPendingFinalizers%2A> sonlandırıcıları çalıştırmaya zorlayabilir. Sonlandırıcılar, normalde Rastgele zamanlarda çalışır ve muhtemelen işlemden çıkılmaz. Bu MDA etkin olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunu daha güvenilir bir şekilde yeniden oluşturmaya yardımcı olur.  
  
## <a name="symptoms"></a>Belirtiler  
 A bir <xref:System.IO.StreamWriter> dosyaya son 1 – 4 KB veri yazmaz.  
  
## <a name="cause"></a>Nedeni  
 <xref:System.IO.StreamWriter>Verileri dahili olarak arabelleğe alır. Bu, <xref:System.IO.StreamWriter.Close%2A> ya da <xref:System.IO.StreamWriter.Flush%2A> yönteminin, arabelleğe alınan verileri temeldeki veri deposuna yazmak üzere çağrılması gerekir. <xref:System.IO.StreamWriter.Close%2A>Ya da <xref:System.IO.StreamWriter.Flush%2A> uygun bir şekilde çağrılmamışsa, örnekte ara belleğe alınan veriler <xref:System.IO.StreamWriter> beklenen şekilde yazılmayabilir.  
  
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
 <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> Bir uygulamayı veya bir örneğine sahip herhangi bir kod bloğunu kapatmadan önce veya ' de ' i çağırdığınızdan emin olun <xref:System.IO.StreamWriter> . Bunu elde etmek için en iyi mekanizmalardan biri, örneğin, `using` `Using` <xref:System.IO.StreamWriter.Dispose%2A> Yazıcı yönteminin çağrılmasını ve örneğin doğru şekilde kapatılmasını sağlamak için bir C# bloğu (Visual Basic) ile örneği oluşturmaktır.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 Aşağıdaki kod, yerine kullanılarak aynı çözümü gösterir `try/finally` `using` .  
  
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
  
 Bu çözümlerin hiçbiri kullanılabilir değilse (örneğin, bir <xref:System.IO.StreamWriter> statik değişkende depolanıyorsa ve yaşam süresinin sonunda kodu kolayca çalıştıramazsınız), <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> son kullanımı bittikten sonra veya <xref:System.IO.StreamWriter.AutoFlush%2A> özelliği `true` ilk kullanılmadan önce olarak ayarlamak için bu sorundan kaçının.  
  
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
