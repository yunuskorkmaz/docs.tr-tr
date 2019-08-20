---
title: Dosya erişimi için Async Kullanma (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: e6b0370049d9b9315de6a72d0e84c080aac12481
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595538"
---
# <a name="using-async-for-file-access-c"></a>Dosya erişimi için Async Kullanma (C#)
Dosyalara erişmek için zaman uyumsuz özelliği kullanabilirsiniz. Async özelliğini kullanarak, geri çağırmaları kullanmadan veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde bölmeden zaman uyumsuz yöntemlere çağrı yapabilirsiniz. Zaman uyumlu kodu zaman uyumsuz yapmak için, zaman uyumlu bir yöntem yerine zaman uyumsuz bir yöntem çağırır ve koda birkaç anahtar sözcük eklemeniz yeterlidir.  
  
 Dosya erişim çağrılarına zaman uyumsuzluğu eklemek için aşağıdaki nedenleri göz önünde bulundurmanız gerekebilir:  
  
- İşlemi başlatan kullanıcı arabirimi iş parçacığı başka bir iş gerçekleştirebildiğinden, asynchrony UI uygulamalarını daha hızlı hale getirir. UI iş parçacığının uzun zaman alan kodu yürütmesi gerekiyorsa (örneğin, 50 milisaniyeden fazla), g/ç tamamlanana kadar UI dondurabilir ve Kullanıcı arabirimi iş parçacığı klavye ve fare girişini ve diğer olayları yeniden işleyebilir.  
  
- Asynchrony, iş parçacıkları gereksinimini azaltarak ASP.NET ve diğer sunucu tabanlı uygulamaların ölçeklenebilirliğini geliştirir. Uygulama yanıt başına adanmış bir iş parçacığı kullanıyorsa ve bin istek aynı anda işleneiyorsa, bin iş parçacığı gerekir. Zaman uyumsuz işlemlerin genellikle bekleme sırasında bir iş parçacığı kullanması gerekmez. Mevcut g/ç Tamamlama iş parçacığını kısa bir süre içinde kullanırlar.  
  
- Bir dosya erişim işleminin gecikmesi geçerli koşullar altında çok düşük olabilir, ancak gecikme gelecekte büyük ölçüde artabilir. Örneğin, bir dosya dünya genelinde bir sunucuya taşınabilir.  
  
- Zaman uyumsuz özelliği kullanmanın ek yükü küçüktür.  
  
- Zaman uyumsuz görevler, paralel olarak kolayca çalıştırılabilir.  
  
## <a name="running-the-examples"></a>Örnekleri çalıştırma  
 Bu konudaki örnekleri çalıştırmak için bir **WPF uygulaması** veya **Windows Forms uygulaması** oluşturabilir ve sonra bir **düğme**ekleyebilirsiniz. Düğmenin `Click` olayında, her örnekteki ilk yönteme bir çağrı ekleyin.  
  
 Aşağıdaki örneklerde aşağıdaki `using` deyimlerini ekleyin.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>FILESTREAM sınıfının kullanımı  
 Bu konudaki örneklerde, zaman uyumsuz g <xref:System.IO.FileStream> /ç 'nin işletim sistemi düzeyinde oluşmasına neden olan bir seçeneğe sahip olan sınıfını kullanın. Bu seçeneği kullanarak, birçok durumda bir ThreadPool iş parçacığını engellemeyi önleyebilirsiniz. Bu seçeneği etkinleştirmek için, Oluşturucu çağrısında `useAsync=true` veya `options=FileOptions.Asynchronous` bağımsız değişkenini belirtirsiniz.  
  
 Bu seçeneği <xref:System.IO.StreamReader> , ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız kullanabilirsiniz. Ancak, bu seçeneği, <xref:System.IO.Stream> <xref:System.IO.FileStream> sınıfının açık olduğunu bir şekilde sağlarsanız kullanabilirsiniz. Bekleme sırasında UI iş parçacığı engellenmediğinden, zaman uyumsuz çağrıların Kullanıcı arabirimi uygulamalarında daha hızlı olduğunu unutmayın.  
  
## <a name="writing-text"></a>Metin yazma  
 Aşağıdaki örnek bir dosyaya metin yazar. Her await ifadesinde, yöntemi hemen çıkar. G/ç dosyası tamamlandığında, yöntemi await ifadesini izleyen deyimde devam eder. Zaman uyumsuz değiştiricinin await ifadesini kullanan yöntemlerin tanımında olduğunu unutmayın.  
  
```csharp  
public async Task ProcessWriteAsync()  
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
  
 Özgün örnek, aşağıdaki iki deyimin `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`bir örneği olan ifadesine sahiptir:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 İlk ifade bir görev döndürür ve dosya işlemenin başlatılmasına neden olur. Await ile ikinci ifade, yönteminin hemen çıkmasına ve farklı bir görev döndürmesine neden olur. Dosya işleme daha sonra tamamlandığında, yürütme, await ' ı izleyen ifadeye geri döner. Daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışıC#()](./control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Metin okuma  
 Aşağıdaki örnek bir dosyadaki metni okur. Metin, arabelleğe alınmış ve bu durumda bir <xref:System.Text.StringBuilder>öğesine yerleştirildi. Önceki örnekte aksine, await 'ın değerlendirmesi bir değer oluşturur. Yöntemibir<xref:System.Threading.Tasks.Task>`numRead` >döndürür`Int32` , bu nedenle await 'ın değerlendirmesi işlem tamamlandıktan sonra bir değer () oluşturur. \< <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Int32> Daha fazla bilgi için bkz. [Async Return TypesC#()](./async-return-types.md).  
  
```csharp  
public async Task ProcessReadAsync()  
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
 Aşağıdaki örnek, 10 metin dosyası yazarak paralel işlemeyi gösterir. Her dosya için, <xref:System.IO.Stream.WriteAsync%2A> yöntemi bir görev listesine eklenen bir görevi döndürür. `await Task.WhenAll(tasks);` Deyimden çıkılıyor ve tüm görevler için dosya işleme tamamlandığında yöntemi içinde devam eder.  
  
 Örnek, görevler tamamlandıktan <xref:System.IO.FileStream> sonra bir `finally` bloktaki tüm örnekleri kapatır. Her biri `FileStream` bir `using` bildiriminde oluşturulduysa, görev tamamlanmadan önce ' `FileStream` nin atımı bırakılmış olabilir.  
  
 Herhangi bir performans artışının, zaman uyumsuz işlemden değil, paralel işlemden neredeyse tamamen olduğunu unutmayın. Zaman uyumsuzluğu 'nin avantajları birden çok iş parçacığını bağlamaktır ve Kullanıcı arabirimi iş parçacığını bağlamaktır.  
  
```csharp  
public async Task ProcessWriteMultAsync()  
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
  
 <xref:System.IO.Stream.WriteAsync%2A> <xref:System.Threading.CancellationToken>Ve yöntemlerinikullanırken,işlemorta-akışişleminiiptaletmekiçinkullanabileceğinizbirbelirtebilirsiniz.<xref:System.IO.Stream.ReadAsync%2A> Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında](../../../../standard/threading/cancellation-in-managed-threads.md) [zaman uyumsuzC#uygulamanızı () ve iptali hassas ayarlama](./fine-tuning-your-async-application.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await (C#) ile zaman uyumsuz programlama](./index.md)
- [Zaman uyumsuz dönüş türleriC#()](./async-return-types.md)
- [Zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md)
