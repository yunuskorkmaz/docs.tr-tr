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
ms.openlocfilehash: 18b2a5a95756ed125d26b2846c0b1ddc320463ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181735"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
Yönetilen `streamWriterBufferedDataLost` hata ayıklama yardımcısı (MDA) bir <xref:System.IO.StreamWriter> yazıldığında etkinleştirilir, ancak <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntem daha sonra <xref:System.IO.StreamWriter> yok edilmeden önce çağrılmaz. Bu MDA etkinleştirildiğinde, çalışma zamanı arabelleğe alınan verilerin <xref:System.IO.StreamWriter>. Arabelleğe alınan veriler varsa, MDA etkinleştirilir. Arama <xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemleri sonlandırıcılar çalıştırmak için zorlayabilir. Finalizers aksi takdirde görünüşte rasgele zamanlarda çalışacak ve muhtemelen hiç süreç çıkışında değil. Bu MDA etkinleştirilmiş olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunun daha güvenilir bir şekilde yeniden oluşturulmasına yardımcı olacaktır.  
  
## <a name="symptoms"></a>Belirtiler  
 A, <xref:System.IO.StreamWriter> bir dosyaya son 1-4 KB veri yazmaz.  
  
## <a name="cause"></a>Nedeni  
 Arabellekteki <xref:System.IO.StreamWriter> verileri dahili olarak, <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> arabelleğe alınan verileri temel veri deposuna yazmak için çağrılmasını gerektiren arabellekler. Uygun <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> şekilde çağrılmazsa veya çağrılmazsa, <xref:System.IO.StreamWriter> örnekte arabelleğe alınan veriler beklendiği gibi yazılmayabilir.  
  
 Aşağıda, bu MDA'nın yakalaması gereken kötü yazılmış kod örneği verilmiştir.  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Bir çöp toplama tetiklenir ve sonlandırıcılar tamamlanana kadar askıya sonra önceki kod daha güvenilir bu MDA etkinleştirmek. Bu tür bir sorunu izlemek için, hata ayıklama yapısında önceki yöntemin sonuna aşağıdaki kodu ekleyebilirsiniz. Bu güvenilir MDA etkinleştirmek için yardımcı olacaktır, ama tabii ki sorunun nedenini düzeltmek değildir.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Çözüm  
 Bir uygulamayı <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> bir <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter>'nin örneğini olan herhangi bir kod bloğunu kapatmadan önce veya üzerinde arama yaptığınızdan emin olun Bunu başarmak için en iyi mekanizmalardan biri, yazarın `using` yönteminin`Using` <xref:System.IO.StreamWriter.Dispose%2A> çağrılmasını sağlayacak c# bloğu (Visual Basic)'de örneği oluşturmak tır ve bu da örneğin doğru şekilde kapatılmasıyla sonuçlanır.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 Aşağıdaki kod, `try/finally` `using`yerine kullanarak aynı çözümü gösterir.  
  
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
  
 Bu çözümlerden hiçbiri kullanılamıyorsa (örneğin, <xref:System.IO.StreamWriter> a statik bir değişkende depolanıyorsa ve kodu ömrünün <xref:System.IO.StreamWriter.Flush%2A> sonunda <xref:System.IO.StreamWriter> kolayca çalıştıramıyorsanız), <xref:System.IO.StreamWriter.AutoFlush%2A> son `true` kullanımdan sonra gelene çağrı yapmak veya özelliği ilk kullanımdan önce ayarlamak bu sorunu önlemelidir.  
  
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
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Bu MDA'nın çalışma zamanı üzerinde hiçbir etkisi yoktur.  
  
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
