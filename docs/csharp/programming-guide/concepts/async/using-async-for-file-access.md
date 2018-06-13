---
title: Dosya erişimi için (C#) Async kullanma
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 083a9113fc75c9e18646953a144b9e3d1bfd90ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328295"
---
# <a name="using-async-for-file-access-c"></a>Dosya erişimi için (C#) Async kullanma
Async özelliği dosyalara erişmek için kullanabilirsiniz. Async özelliği kullanarak, geri çağrılar kullanarak veya birden çok yöntem veya lambda ifadeleri kodunuzu bölme olmadan zaman uyumsuz yöntemleri çağırabilirsiniz. Zaman uyumlu bir kod zaman uyumsuz hale getirmek için yalnızca zaman uyumlu yöntemi yerine zaman uyumsuz bir yöntem çağrısı ve birkaç anahtar sözcükleri kodu ekleyin.  
  
 Dosya erişim çağrıları asynchrony eklemek için aşağıdaki nedenlerden düşünebilirsiniz:  
  
-   İşlemi başlatan kullanıcı Arabirimi iş parçacığı diğer işlemleri gerçekleştirmesi çünkü asynchrony UI uygulamaları daha esnek hale getirir. Kullanıcı Arabirimi iş parçacığı kod yürütülmelidir, (örneğin, 50'den fazla milisaniye) daha uzun bir zaman alır, UI g/ç tamamlanana ve kullanıcı Arabirimi iş parçacığı, yeniden klavye işlemek ve giriş ve diğer olayları fare kadar donabilir.  
  
-   İş parçacığı gereksinimini azaltarak ASP.NET ölçeklenebilirliğini ve diğer sunucu tabanlı uygulamalar asynchrony artırır. Uygulama yanıt başına adanmış bir iş parçacığı kullanır ve bir bin istekleri aynı anda işlenmekte, binlerce iş parçacığı gereklidir. Zaman uyumsuz işlemleri genellikle bir iş parçacığı bekleme sırasında kullanmanız gerekmez. Varolan g/ç Tamamlama iş parçacığı kısa bir süre sonunda kullanırlar.  
  
-   Dosya erişim işlemi gecikme geçerli koşullar altında çok düşük olabilir, ancak gecikme gelecekte önemli ölçüde artırabilir. Örneğin, bir dosya dünya genelindeki bir sunucuya taşınması.  
  
-   Eklenen Async özelliği kullanılarak yükünü küçük.  
  
-   Zaman uyumsuz görevleri kolayca paralel olarak çalıştırılabilir.  
  
## <a name="running-the-examples"></a>Örnekleri çalıştırma  
 Bu konudaki örnekler çalıştırmak için oluşturabileceğiniz bir **WPF uygulaması** veya **Windows Forms uygulaması** ve ardından ekleyin bir **düğmesini**. Düğmenin içinde `Click` olay, her örnekte ilk yöntemine bir çağrı ekleyin.  
  
 Aşağıdaki örneklerde, aşağıdakiler dahil `using` deyimleri.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>FILESTREAM sınıfının kullanın  
 Bu konuda kullanım örnekleri <xref:System.IO.FileStream> işletim sistemi düzeyinde gerçekleşmesi zaman uyumsuz g/ç neden olan bir seçenek olan sınıf. Bu seçeneği kullanarak, bir iş parçacığı havuzu iş parçacığı birçok durumda engelleme önleyebilirsiniz. Bu seçeneği etkinleştirmek için belirttiğiniz `useAsync=true` veya `options=FileOptions.Asynchronous` oluşturucu çağrısı bağımsız değişkeni.  
  
 Bu seçenek ile kullanamazsınız <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız. Ancak, bunları sağlarsanız, bu seçeneği kullanabilirsiniz bir <xref:System.IO.Stream> , <xref:System.IO.FileStream> açılan sınıfı. İş parçacığı havuzu iş parçacığı engellendi olsa bile, kullanıcı Arabirimi iş parçacığı bekleme sırasında engellenmiş değil çünkü zaman uyumsuz çağrılar UI uygulamalarında daha hızlı olduğunu unutmayın.  
  
## <a name="writing-text"></a>Metin yazma  
 Aşağıdaki örnek metin bir dosyaya yazar. Her deyimi await, yöntem hemen çıkar. Dosya g/ç tamamlandığında yöntemi bekleme deyimi aşağıdaki ifadesine sürdürür. Zaman uyumsuz değiştiricisi bekleme deyimini yöntemleri tanımında olduğuna dikkat edin.  
  
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
  
 Deyim özgün örnek sahip `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, aşağıdaki iki deyimlerinin daraltmaya olduğu:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 İlk ifade bir görev döndürür ve başlatmak dosya işleme neden olur. Bekleme ikinci deyimiyle hemen çıkmak ve farklı bir görev dönmek yöntem neden olur. Dosya daha sonra işleme tamamlandıktan sonra yürütme bekleme aşağıdaki deyim döndürür. Daha fazla bilgi için bkz: [akış denetimi zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Metin okuma  
 Aşağıdaki örnek, bir dosyadan metin okur. Metin arabelleğe ve, bu durumda, içine yerleştirilen bir <xref:System.Text.StringBuilder>. Farklı olarak önceki örnekte bekleme değerlendirmesi bir değer oluşturur. <xref:System.IO.Stream.ReadAsync%2A> Yöntemi döndürür bir <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, bekleme değerlendirmesi üreten bir `Int32` değeri (`numRead`) işlemi tamamlandıktan sonra. Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
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
 Aşağıdaki örnek, 10 metin dosyaları yazarak paralel işleme gösterir. Her bir dosyanın <xref:System.IO.Stream.WriteAsync%2A> yöntemi görevlerin bir listesi için daha sonra eklenen bir görev döndürür. `await Task.WhenAll(tasks);` Deyimi yöntemi çıkar ve sürdürür dosyası işleme yöntemi içinde tüm görevleri tamamlayın.  
  
 Tüm örnek kapatır <xref:System.IO.FileStream> içinde örnekler bir `finally` görevler tamamlandıktan sonra engelleyin. Her varsa `FileStream` yerine oluşturulan bir `using` deyimi, `FileStream` görev tamamlanmadan önce elden.  
  
 Tüm performans artırma neredeyse tamamen paralel işleme ve zaman uyumsuz işleme olduğuna dikkat edin. Asynchrony avantajları şunlardır: birden çok iş parçacıklarını tie değil ve kullanıcı arabirimi iş parçacığını tie değil.  
  
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
  
 Kullanırken <xref:System.IO.Stream.WriteAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> yöntemleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, hangi işlemi Orta akışı iptal etmek için kullanabilirsiniz. Daha fazla bilgi için bkz: [Fine-Tuning zaman uyumsuz uygulamanız (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) ve [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Denetim akışı zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
