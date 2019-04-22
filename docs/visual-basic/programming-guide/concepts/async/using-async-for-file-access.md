---
title: (Visual Basic) dosya erişimi için Async kullanma
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 0b2b95f1e4f9bc120acdad606b0f15503285057a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814555"
---
# <a name="using-async-for-file-access-visual-basic"></a>(Visual Basic) dosya erişimi için Async kullanma
Async özelliği dosyalara erişmek için kullanabilirsiniz. Async özelliği'ni kullanarak geri çağırmaları kullanarak veya birden çok yöntemlerde veya lambda ifadelerinde kodunuzu bölme olmadan zaman uyumsuz yöntemleri çağırabilir. Eş zamanlı kod zaman uyumsuz hale getirmek için yalnızca zaman uyumlu bir yöntem yerine zaman uyumsuz yöntemini çağırın ve birkaç anahtar sözcükler için kodu ekleyin.  
  
 Dosya erişim çağrıları zaman uyumsuzluğu eklemek için aşağıdaki nedenlerden düşünebilirsiniz:  
  
-   İşlemi başlatan kullanıcı Arabirimi iş parçacığı başka işleri gerçekleştirebilirsiniz çünkü faaliyetler UI uygulamaları daha hızlı sağlar. UI iş parçacığı kod yürütülmesi gerekiyorsa (örneğin, 50'den fazla milisaniye) uzun zaman alan, UI ve UI iş parçacığı yeniden klavye işleyebilir ve giriş ve diğer olayları fare g/ç işlemi tamamlanana kadar donabilir.  
  
-   İş parçacıkları gereksinimini azaltarak ASP.NET ölçeklenebilirliğini ve diğer sunucu tabanlı uygulamalar faaliyetler artırır. Binlerce iş parçacıkları, adanmış bir iş parçacığı başına yanıt uygulama kullanıyorsa ve binlerce istekleri aynı anda işlenmekte gereklidir. Zaman uyumsuz işlemler genellikle bir iş parçacığı bekleme sırasında kullanmanız gerekmez. Mevcut g/ç Tamamlama iş parçacığı kısa bir süre sonunda kullanırlar.  
  
-   Bir dosya erişim işlemi gecikme süresini geçerli koşullar altında çok düşük olabilir ancak gecikme süresi gelecekte büyük ölçüde artırabilir. Örneğin, bir dosya dünya genelindeki bir sunucuya taşınabilir.  
  
-   Ek yükü zaman uyumsuz özelliğini kullanarak küçük.  
  
-   Zaman uyumsuz görevleri kolayca paralel olarak çalıştırılabilir.  
  
## <a name="running-the-examples"></a>Örnekleri çalıştırma  
 Bu konudaki örnekleri çalıştırmak için oluşturabileceğiniz bir **WPF uygulaması** veya **Windows Forms uygulaması** ve ardından eklemek bir **düğmesi**. Düğmenin içinde `Click` olay, her örnekte ilk yönteme bir çağrı ekleyin.  
  
 Aşağıdaki örneklerde, aşağıdakiler dahil `Imports` deyimleri.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>FILESTREAM sınıfının kullanımı  
 Bu konuda kullanım örnekleri <xref:System.IO.FileStream> işletim sistemi düzeyinde gerçekleşmesi zaman uyumsuz g/ç neden olan bir seçenek olduğu sınıf. Bu seçeneği kullanarak, çoğu durumda bir iş parçacığı havuzu iş parçacığını engelleme önleyebilirsiniz. Bu seçeneği etkinleştirmek için belirttiğiniz `useAsync=true` veya `options=FileOptions.Asynchronous` Oluşturucusu çağrısında bağımsız değişken.  
  
 Bu seçeneği kullanamazsınız <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız. Ancak, bunları sağlarsanız, bu seçeneği kullanabilirsiniz bir <xref:System.IO.Stream> , <xref:System.IO.FileStream> sınıfı açılır. Bir iş parçacığı havuzu iş parçacığı engellenir bile, UI iş parçacığı, bekleme sırasında bloke değildir çünkü zaman uyumsuz çağrıları UI uygulamaları daha hızlı olduğunu unutmayın.  
  
## <a name="writing-text"></a>Metin yazma  
 Aşağıdaki örnek, bir dosyaya metin yazar. Her deyim await, yöntem hemen çıkar. Dosya g/ç işlemi tamamlandığında, yöntem bekleme ifadesinin izleyen deyime sürdürür. Zaman uyumsuz değiştirici bekleme ifadesinin yöntem tanımında olduğuna dikkat edin.  
  
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
  
 Deyimi özgün örneğe sahip `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, aşağıdaki iki deyimi, bir kısaltma olduğundan:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 İlk deyim, bir görev döndürür ve başlatmak, dosya işleme neden olur. Await ile ikinci deyim, yöntem hemen çıkın ve farklı bir görev döndürür neden olur. Dosya daha sonra işleme tamamlandıktan sonra yürütme bekleme takip eden deyime döndürür. Daha fazla bilgi için [zaman uyumsuz programlarda (Visual Basic) denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Metin okuma  
 Aşağıdaki örnek, bir dosyadan metin okur. Metin arabelleğe alınır ve bu durumda, içine yerleştirilen bir <xref:System.Text.StringBuilder>. Önceki örnekte, farklı bir değer await değerlendirilmesiyle üretir. <xref:System.IO.Stream.ReadAsync%2A> Yöntemi döndürür bir <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, await değerlendirilmesiyle üreten bir `Int32` değeri (`numRead`) işlemi tamamlandıktan sonra. Daha fazla bilgi için [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
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
 Aşağıdaki örnek, 10 metin dosyaları yazma tarafından paralel işleme gösterir. Her dosya için <xref:System.IO.Stream.WriteAsync%2A> yöntemi görevlerinin listesi için daha sonra eklenen bir görev döndürür. `Await Task.WhenAll(tasks)` Deyimi yöntemin çıkar ve sürdürür dosya işleme olduğunda yöntemi içindeki tüm görevlerin tamamlayın.  
  
 Tüm örnek kapatır <xref:System.IO.FileStream> içinde örnekler bir `Finally` görevler tamamlandıktan sonra engelleyin. Her varsa `FileStream` yerine içinde oluşturulmuş bir `Imports` deyimi `FileStream` görev tamamlanmadan önce elden.  
  
 Herhangi bir performans artışının neredeyse tamamen paralel işleme ve olmayan uyumsuz olduğuna dikkat edin. Faaliyetler avantajları şunlardır: birden çok iş parçacıklarını tie değil ve kullanıcı arabirimi iş parçacığı ' tie değil.  
  
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
  
 Kullanırken <xref:System.IO.Stream.WriteAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> yöntemleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, hangi işlemin ortasında akış iptal etmek için kullanabilirsiniz. Daha fazla bilgi için [Fine-Tuning Async uygulamanızda (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) ve [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Zaman uyumsuz programlarda (Visual Basic) denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
