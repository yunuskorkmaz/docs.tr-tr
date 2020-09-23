---
title: Dosya Erişimi için Async Kullanma
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 2e7fa4a78363a08f2ff25e6a961868e85994e200
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077364"
---
# <a name="using-async-for-file-access-visual-basic"></a>Dosya erişimi için Async Kullanma (Visual Basic)

Dosyalara erişmek için zaman uyumsuz özelliği kullanabilirsiniz. Async özelliğini kullanarak, geri çağırmaları kullanmadan veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde bölmeden zaman uyumsuz yöntemlere çağrı yapabilirsiniz. Zaman uyumlu kodu zaman uyumsuz yapmak için, zaman uyumlu bir yöntem yerine zaman uyumsuz bir yöntem çağırır ve koda birkaç anahtar sözcük eklemeniz yeterlidir.  
  
 Dosya erişim çağrılarına zaman uyumsuzluğu eklemek için aşağıdaki nedenleri göz önünde bulundurmanız gerekebilir:  
  
- İşlemi başlatan kullanıcı arabirimi iş parçacığı başka bir iş gerçekleştirebildiğinden, asynchrony UI uygulamalarını daha hızlı hale getirir. UI iş parçacığının uzun zaman alan kodu yürütmesi gerekiyorsa (örneğin, 50 milisaniyeden fazla), g/ç tamamlanana kadar UI dondurabilir ve Kullanıcı arabirimi iş parçacığı klavye ve fare girişini ve diğer olayları yeniden işleyebilir.  
  
- Asynchrony, iş parçacıkları gereksinimini azaltarak ASP.NET ve diğer sunucu tabanlı uygulamaların ölçeklenebilirliğini geliştirir. Uygulama yanıt başına adanmış bir iş parçacığı kullanıyorsa ve bin istek aynı anda işleneiyorsa, bin iş parçacığı gerekir. Zaman uyumsuz işlemlerin genellikle bekleme sırasında bir iş parçacığı kullanması gerekmez. Mevcut g/ç Tamamlama iş parçacığını kısa bir süre içinde kullanırlar.  
  
- Bir dosya erişim işleminin gecikmesi geçerli koşullar altında çok düşük olabilir, ancak gecikme gelecekte büyük ölçüde artabilir. Örneğin, bir dosya dünya genelinde bir sunucuya taşınabilir.  
  
- Zaman uyumsuz özelliği kullanmanın ek yükü küçüktür.  
  
- Zaman uyumsuz görevler, paralel olarak kolayca çalıştırılabilir.  
  
## <a name="running-the-examples"></a>Örnekleri çalıştırma  

 Bu konudaki örnekleri çalıştırmak için bir **WPF uygulaması** veya **Windows Forms uygulaması** oluşturabilir ve sonra bir **düğme**ekleyebilirsiniz. Düğmenin `Click` olayında, her örnekteki ilk yönteme bir çağrı ekleyin.  
  
 Aşağıdaki örneklerde aşağıdaki `Imports` deyimlerini ekleyin.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>FILESTREAM sınıfının kullanımı  

 Bu konudaki örneklerde, <xref:System.IO.FileStream> zaman uyumsuz g/ç 'nin işletim sistemi düzeyinde oluşmasına neden olan bir seçeneğe sahip olan sınıfını kullanın. Bu seçeneği kullanarak, birçok durumda bir ThreadPool iş parçacığını engellemeyi önleyebilirsiniz. Bu seçeneği etkinleştirmek için, `useAsync=true` `options=FileOptions.Asynchronous` Oluşturucu çağrısında veya bağımsız değişkenini belirtirsiniz.  
  
 Bu seçeneği, <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız kullanabilirsiniz. Ancak, bu seçeneği, <xref:System.IO.Stream> sınıfının açık olduğunu bir şekilde sağlarsanız kullanabilirsiniz <xref:System.IO.FileStream> . Bekleme sırasında UI iş parçacığı engellenmediğinden, zaman uyumsuz çağrıların Kullanıcı arabirimi uygulamalarında daha hızlı olduğunu unutmayın.  
  
## <a name="writing-text"></a>Metin yazma  

 Aşağıdaki örnek bir dosyaya metin yazar. Her await ifadesinde, yöntemi hemen çıkar. G/ç dosyası tamamlandığında, yöntemi await ifadesini izleyen deyimde devam eder. Zaman uyumsuz değiştiricinin await ifadesini kullanan yöntemlerin tanımında olduğunu unutmayın.  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 Özgün örnek, `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)` aşağıdaki iki deyimin bir örneği olan ifadesine sahiptir:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 İlk ifade bir görev döndürür ve dosya işlemenin başlatılmasına neden olur. Await ile ikinci ifade, yönteminin hemen çıkmasına ve farklı bir görev döndürmesine neden olur. Dosya işleme daha sonra tamamlandığında, yürütme, await ' ı izleyen ifadeye geri döner. Daha fazla bilgi için bkz.  [zaman uyumsuz programlarda denetim akışı (Visual Basic)](control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Metin okuma  

 Aşağıdaki örnek bir dosyadaki metni okur. Metin, arabelleğe alınmış ve bu durumda bir öğesine yerleştirildi <xref:System.Text.StringBuilder> . Önceki örnekte aksine, await 'ın değerlendirmesi bir değer oluşturur. <xref:System.IO.Stream.ReadAsync%2A>Yöntemi bir> döndürür <xref:System.Threading.Tasks.Task> \<<xref:System.Int32> , bu nedenle await 'ın değerlendirmesi `Int32` işlem tamamlandıktan sonra bir değer ( `numRead` ) oluşturur. Daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](async-return-types.md).  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a>Paralel zaman uyumsuz g/ç  

 Aşağıdaki örnek, 10 metin dosyası yazarak paralel işlemeyi gösterir. Her dosya için, <xref:System.IO.Stream.WriteAsync%2A> yöntemi bir görev listesine eklenen bir görevi döndürür. `Await Task.WhenAll(tasks)`Deyimden çıkılıyor ve tüm görevler için dosya işleme tamamlandığında yöntemi içinde devam eder.  
  
 Örnek, <xref:System.IO.FileStream> `Finally` görevler tamamlandıktan sonra bir bloktaki tüm örnekleri kapatır. Her biri `FileStream` bir bildiriminde oluşturulduysa, `Imports` görev tamamlanmadan önce ' `FileStream` nin atımı bırakılmış olabilir.  
  
 Herhangi bir performans artışının, zaman uyumsuz işlemden değil, paralel işlemden neredeyse tamamen olduğunu unutmayın. Zaman uyumsuzluğu 'nin avantajları birden çok iş parçacığını bağlamaktır ve Kullanıcı arabirimi iş parçacığını bağlamaktır.  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <xref:System.IO.Stream.WriteAsync%2A>Ve yöntemlerini kullanırken, <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.CancellationToken> işlem orta-akış işlemini iptal etmek için kullanabileceğiniz bir belirtebilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında](../../../../standard/threading/cancellation-in-managed-threads.md) [zaman uyumsuz uygulamanıza ince ayar yapma (Visual Basic)](fine-tuning-your-async-application.md) ve iptal etme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](async-return-types.md)
- [Zaman uyumsuz programlarda denetim akışı (Visual Basic)](control-flow-in-async-programs.md)
