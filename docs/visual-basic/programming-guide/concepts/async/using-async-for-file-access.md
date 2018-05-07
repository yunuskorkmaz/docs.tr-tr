---
title: (Visual Basic) dosya erişimi için Async kullanma
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: e12eaa57d0f7186e9d281b89ec3abd26280e12ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-async-for-file-access-visual-basic"></a>(Visual Basic) dosya erişimi için Async kullanma
Async özelliği dosyalara erişmek için kullanabilirsiniz. Async özelliği kullanarak, geri çağrılar kullanarak veya birden çok yöntem veya lambda ifadeleri kodunuzu bölme olmadan zaman uyumsuz yöntemleri çağırabilirsiniz. Zaman uyumlu bir kod zaman uyumsuz hale getirmek için yalnızca zaman uyumlu yöntemi yerine zaman uyumsuz bir yöntem çağrısı ve birkaç anahtar sözcükleri kodu ekleyin.  
  
 Dosya erişim çağrıları asynchrony eklemek için aşağıdaki nedenlerden düşünebilirsiniz:  
  
-   İşlemi başlatan kullanıcı Arabirimi iş parçacığı diğer işlemleri gerçekleştirmesi çünkü asynchrony UI uygulamaları daha esnek hale getirir. Kullanıcı Arabirimi iş parçacığı kod yürütülmelidir, (örneğin, 50'den fazla milisaniye) daha uzun bir zaman alır, UI g/ç tamamlanana ve kullanıcı Arabirimi iş parçacığı, yeniden klavye işlemek ve giriş ve diğer olayları fare kadar donabilir.  
  
-   İş parçacığı gereksinimini azaltarak ASP.NET ölçeklenebilirliğini ve diğer sunucu tabanlı uygulamalar asynchrony artırır. Uygulama yanıt başına adanmış bir iş parçacığı kullanır ve bir bin istekleri aynı anda işlenmekte, binlerce iş parçacığı gereklidir. Zaman uyumsuz işlemleri genellikle bir iş parçacığı bekleme sırasında kullanmanız gerekmez. Varolan g/ç Tamamlama iş parçacığı kısa bir süre sonunda kullanırlar.  
  
-   Dosya erişim işlemi gecikme geçerli koşullar altında çok düşük olabilir, ancak gecikme gelecekte önemli ölçüde artırabilir. Örneğin, bir dosya dünya genelindeki bir sunucuya taşınması.  
  
-   Eklenen Async özelliği kullanılarak yükünü küçük.  
  
-   Zaman uyumsuz görevleri kolayca paralel olarak çalıştırılabilir.  
  
## <a name="running-the-examples"></a>Örnekleri çalıştırma  
 Bu konudaki örnekler çalıştırmak için oluşturabileceğiniz bir **WPF uygulaması** veya **Windows Forms uygulaması** ve ardından ekleyin bir **düğmesini**. Düğmenin içinde `Click` olay, her örnekte ilk yöntemine bir çağrı ekleyin.  
  
 Aşağıdaki örneklerde, aşağıdakiler dahil `Imports` deyimleri.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>FILESTREAM sınıfının kullanın  
 Bu konuda kullanım örnekleri <xref:System.IO.FileStream> işletim sistemi düzeyinde gerçekleşmesi zaman uyumsuz g/ç neden olan bir seçenek olan sınıf. Bu seçeneği kullanarak, bir iş parçacığı havuzu iş parçacığı birçok durumda engelleme önleyebilirsiniz. Bu seçeneği etkinleştirmek için belirttiğiniz `useAsync=true` veya `options=FileOptions.Asynchronous` oluşturucu çağrısı bağımsız değişkeni.  
  
 Bu seçenek ile kullanamazsınız <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız. Ancak, bunları sağlarsanız, bu seçeneği kullanabilirsiniz bir <xref:System.IO.Stream> , <xref:System.IO.FileStream> açılan sınıfı. İş parçacığı havuzu iş parçacığı engellendi olsa bile, kullanıcı Arabirimi iş parçacığı bekleme sırasında engellenmiş değil çünkü zaman uyumsuz çağrılar UI uygulamalarında daha hızlı olduğunu unutmayın.  
  
## <a name="writing-text"></a>Metin yazma  
 Aşağıdaki örnek metin bir dosyaya yazar. Her deyimi await, yöntem hemen çıkar. Dosya g/ç tamamlandığında yöntemi bekleme deyimi aşağıdaki ifadesine sürdürür. Zaman uyumsuz değiştiricisi bekleme deyimini yöntemleri tanımında olduğuna dikkat edin.  
  
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
  
 Deyim özgün örnek sahip `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, aşağıdaki iki deyimlerinin daraltmaya olduğu:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 İlk ifade bir görev döndürür ve başlatmak dosya işleme neden olur. Bekleme ikinci deyimiyle hemen çıkmak ve farklı bir görev dönmek yöntem neden olur. Dosya daha sonra işleme tamamlandıktan sonra yürütme bekleme aşağıdaki deyim döndürür. Daha fazla bilgi için bkz: [akış denetimi zaman uyumsuz programlarda (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Metin okuma  
 Aşağıdaki örnek, bir dosyadan metin okur. Metin arabelleğe ve, bu durumda, içine yerleştirilen bir <xref:System.Text.StringBuilder>. Farklı olarak önceki örnekte bekleme değerlendirmesi bir değer oluşturur. <xref:System.IO.Stream.ReadAsync%2A> Yöntemi döndürür bir <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, bekleme değerlendirmesi üreten bir `Int32` değeri (`numRead`) işlemi tamamlandıktan sonra. Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
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
 Aşağıdaki örnek, 10 metin dosyaları yazarak paralel işleme gösterir. Her bir dosyanın <xref:System.IO.Stream.WriteAsync%2A> yöntemi görevlerin bir listesi için daha sonra eklenen bir görev döndürür. `Await Task.WhenAll(tasks)` Deyimi yöntemi çıkar ve sürdürür dosyası işleme yöntemi içinde tüm görevleri tamamlayın.  
  
 Tüm örnek kapatır <xref:System.IO.FileStream> içinde örnekler bir `Finally` görevler tamamlandıktan sonra engelleyin. Her varsa `FileStream` yerine oluşturulan bir `Imports` deyimi, `FileStream` görev tamamlanmadan önce elden.  
  
 Tüm performans artırma neredeyse tamamen paralel işleme ve zaman uyumsuz işleme olduğuna dikkat edin. Asynchrony avantajları şunlardır: birden çok iş parçacıklarını tie değil ve kullanıcı arabirimi iş parçacığını tie değil.  
  
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
  
 Kullanırken <xref:System.IO.Stream.WriteAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> yöntemleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, hangi işlemi Orta akışı iptal etmek için kullanabilirsiniz. Daha fazla bilgi için bkz: [Fine-Tuning zaman uyumsuz uygulamanız (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) ve [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [(Visual Basic) zaman uyumsuz programlarda denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
