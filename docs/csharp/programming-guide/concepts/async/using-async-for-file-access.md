---
title: Zaman uyumsuz dosya erişimi için (C#) kullanma
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: bbaeb14d5c17665308932c26a0630f1e9e5dabdf
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45570333"
---
# <a name="using-async-for-file-access-c"></a>Zaman uyumsuz dosya erişimi için (C#) kullanma
Async özelliği dosyalara erişmek için kullanabilirsiniz. Async özelliği'ni kullanarak geri çağırmaları kullanarak veya birden çok yöntemlerde veya lambda ifadelerinde kodunuzu bölme olmadan zaman uyumsuz yöntemleri çağırabilir. Eş zamanlı kod zaman uyumsuz hale getirmek için yalnızca zaman uyumlu bir yöntem yerine zaman uyumsuz yöntemini çağırın ve birkaç anahtar sözcükler için kodu ekleyin.  
  
 Dosya erişim çağrıları zaman uyumsuzluğu eklemek için aşağıdaki nedenlerden düşünebilirsiniz:  
  
-   İşlemi başlatan kullanıcı Arabirimi iş parçacığı başka işleri gerçekleştirebilirsiniz çünkü faaliyetler UI uygulamaları daha hızlı sağlar. UI iş parçacığı kod yürütülmesi gerekiyorsa (örneğin, 50'den fazla milisaniye) uzun zaman alan, UI ve UI iş parçacığı yeniden klavye işleyebilir ve giriş ve diğer olayları fare g/ç işlemi tamamlanana kadar donabilir.  
  
-   İş parçacıkları gereksinimini azaltarak ASP.NET ölçeklenebilirliğini ve diğer sunucu tabanlı uygulamalar faaliyetler artırır. Binlerce iş parçacıkları, adanmış bir iş parçacığı başına yanıt uygulama kullanıyorsa ve binlerce istekleri aynı anda işlenmekte gereklidir. Zaman uyumsuz işlemler genellikle bir iş parçacığı bekleme sırasında kullanmanız gerekmez. Mevcut g/ç Tamamlama iş parçacığı kısa bir süre sonunda kullanırlar.  
  
-   Bir dosya erişim işlemi gecikme süresini geçerli koşullar altında çok düşük olabilir ancak gecikme süresi gelecekte büyük ölçüde artırabilir. Örneğin, bir dosya dünya genelindeki bir sunucuya taşınabilir.  
  
-   Ek yükü zaman uyumsuz özelliğini kullanarak küçük.  
  
-   Zaman uyumsuz görevleri kolayca paralel olarak çalıştırılabilir.  
  
## <a name="running-the-examples"></a>Örnekleri çalıştırma  
 Bu konudaki örnekleri çalıştırmak için oluşturabileceğiniz bir **WPF uygulaması** veya **Windows Forms uygulaması** ve ardından eklemek bir **düğmesi**. Düğmenin içinde `Click` olay, her örnekte ilk yönteme bir çağrı ekleyin.  
  
 Aşağıdaki örneklerde, aşağıdakiler dahil `using` deyimleri.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>FILESTREAM sınıfının kullanımı  
 Bu konuda kullanım örnekleri <xref:System.IO.FileStream> işletim sistemi düzeyinde gerçekleşmesi zaman uyumsuz g/ç neden olan bir seçenek olduğu sınıf. Bu seçeneği kullanarak, çoğu durumda bir iş parçacığı havuzu iş parçacığını engelleme önleyebilirsiniz. Bu seçeneği etkinleştirmek için belirttiğiniz `useAsync=true` veya `options=FileOptions.Asynchronous` Oluşturucusu çağrısında bağımsız değişken.  
  
 Bu seçeneği kullanamazsınız <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız. Ancak, bunları sağlarsanız, bu seçeneği kullanabilirsiniz bir <xref:System.IO.Stream> , <xref:System.IO.FileStream> sınıfı açılır. Bir iş parçacığı havuzu iş parçacığı engellenir bile, UI iş parçacığı, bekleme sırasında bloke değildir çünkü zaman uyumsuz çağrıları UI uygulamaları daha hızlı olduğunu unutmayın.  
  
## <a name="writing-text"></a>Metin yazma  
 Aşağıdaki örnek, bir dosyaya metin yazar. Her deyim await, yöntem hemen çıkar. Dosya g/ç işlemi tamamlandığında, yöntem bekleme ifadesinin izleyen deyime sürdürür. Zaman uyumsuz değiştirici bekleme ifadesinin yöntem tanımında olduğuna dikkat edin.  
  
```csharp  
public async void ProcessWrite()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 Deyimi özgün örneğe sahip `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, aşağıdaki iki deyimi, bir kısaltma olduğundan:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 İlk deyim, bir görev döndürür ve başlatmak, dosya işleme neden olur. Await ile ikinci deyim, yöntem hemen çıkın ve farklı bir görev döndürür neden olur. Dosya daha sonra işleme tamamlandıktan sonra yürütme bekleme takip eden deyime döndürür. Daha fazla bilgi için [akış denetimi zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Metin okuma  
 Aşağıdaki örnek, bir dosyadan metin okur. Metin arabelleğe alınır ve bu durumda, içine yerleştirilen bir <xref:System.Text.StringBuilder>. Önceki örnekte, farklı bir değer await değerlendirilmesiyle üretir. <xref:System.IO.Stream.ReadAsync%2A> Yöntemi döndürür bir <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, await değerlendirilmesiyle üreten bir `Int32` değeri (`numRead`) işlemi tamamlandıktan sonra. Daha fazla bilgi için [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
```csharp  
public async void ProcessRead()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a>Paralel zaman uyumsuz g/ç  
 Aşağıdaki örnek, 10 metin dosyaları yazma tarafından paralel işleme gösterir. Her dosya için <xref:System.IO.Stream.WriteAsync%2A> yöntemi görevlerinin listesi için daha sonra eklenen bir görev döndürür. `await Task.WhenAll(tasks);` Deyimi yöntemin çıkar ve sürdürür dosya işleme olduğunda yöntemi içindeki tüm görevlerin tamamlayın.  
  
 Tüm örnek kapatır <xref:System.IO.FileStream> içinde örnekler bir `finally` görevler tamamlandıktan sonra engelleyin. Her varsa `FileStream` yerine içinde oluşturulmuş bir `using` deyimi `FileStream` görev tamamlanmadan önce elden.  
  
 Herhangi bir performans artışının neredeyse tamamen paralel işleme ve olmayan uyumsuz olduğuna dikkat edin. Faaliyetler avantajları şunlardır: birden çok iş parçacıklarını tie değil ve kullanıcı arabirimi iş parçacığı ' tie değil.  
  
```csharp  
public async void ProcessWriteMult()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 Kullanırken <xref:System.IO.Stream.WriteAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> yöntemleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, hangi işlemin ortasında akış iptal etmek için kullanabilirsiniz. Daha fazla bilgi için [Fine-Tuning Async uygulamanızda (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) ve [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
- [Zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [Denetim akışı zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
