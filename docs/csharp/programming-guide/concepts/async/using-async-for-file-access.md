---
title: Dosya Erişimi için Async kullanma (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: e6b0370049d9b9315de6a72d0e84c080aac12481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595538"
---
# <a name="using-async-for-file-access-c"></a>Dosya Erişimi için Async kullanma (C#)
Dosyalara erişmek için async özelliğini kullanabilirsiniz. Async özelliğini kullanarak, geri arama kullanmadan veya kodunuzu birden çok yöntem veya lambda ifadeleri arasında bölmeden eşzamanlı yöntemlere çağırabilirsiniz. Senkron kodu asynchronous yapmak için, eşzamanlı bir yöntem yerine asynchronous yöntemini aramanız ve koda birkaç anahtar kelime eklemeniz gerekir.  
  
 Dosya erişim çağrılarına eşitleme eklemek için aşağıdaki nedenleri düşünebilirsiniz:  
  
- İşleyişi başlatan Kullanıcı Birikintisi iş parçacığı başka işler gerçekleştirebildiği için Kullanıcı Arası Uygulama uygulamalarını daha duyarlı hale getirir. UI iş parçacığıuzun zaman (örneğin, 50 milisaniyeden fazla) gerektiren kodu yürütmek gerekiyorsa, Kullanıcı Arabirimi G/Ç tamamlanana kadar donabilir ve Kullanıcı Arabirimi iş parçacığı klavye ve fare girişini ve diğer olayları yeniden işleyebilir.  
  
- Asynchrony iş parçacığı ihtiyacını azaltarak ASP.NET ve diğer sunucu tabanlı uygulamaların ölçeklenebilirliğini artırır. Uygulama yanıt başına özel bir iş parçacığı kullanıyorsa ve aynı anda binlerce istek işleniyorsa, bin iş parçacığı gerekir. Eşzamanlı işlemler genellikle bekleme sırasında bir iş parçacığı kullanmak gerekmez. Sonunda varolan G/Ç tamamlama iş parçacığıkısaca kullanırlar.  
  
- Dosya erişim işleminin gecikmesi geçerli koşullar altında çok düşük olabilir, ancak gecikme si gelecekte büyük ölçüde artabilir. Örneğin, bir dosya dünyanın dört bir yanındaki bir sunucuya taşınabilir.  
  
- Async özelliğini kullanmanın eklenen ek yükü küçüktür.  
  
- Eşkenar tümleme görevleri paralel olarak kolayca çalıştırılabilir.  
  
## <a name="running-the-examples"></a>Örnekleri Çalıştırma  
 Bu konudaki örnekleri çalıştırmak için bir **WPF Uygulaması** veya **Windows Forms Uygulaması** oluşturabilir ve ardından bir **Düğme**ekleyebilirsiniz. Düğmenin `Click` durumunda, her örnekteki ilk yönteme bir çağrı ekleyin.  
  
 Aşağıdaki örneklerde aşağıdaki `using` ifadeleri içerir.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>FileStream Sınıfının Kullanımı  
 Bu konudaki örnekler, <xref:System.IO.FileStream> işletim sistemi düzeyinde eşzamanlı G/Ç'nin oluşmasına neden olan bir seçenek olan sınıfı kullanır. Bu seçeneği kullanarak, birçok durumda bir ThreadPool iş parçacığı engelleme önleyebilirsiniz. Bu seçeneği etkinleştirmek için, oluşturucu çağrısındaki `useAsync=true` bağımsız `options=FileOptions.Asynchronous` değişkeni belirtirsiniz.  
  
 Bu seçeneği <xref:System.IO.StreamReader> <xref:System.IO.StreamWriter> bir dosya yolu belirterek doğrudan açarsanız kullanamazsınız. Ancak, sınıfın açtığı bir seçeneği <xref:System.IO.Stream> <xref:System.IO.FileStream> sağlarsanız, bu seçeneği kullanabilirsiniz. Kullanıcı Birleşme işi bekleme sırasında engellenmediği için, Bir ThreadPool işi engellenemişolsa bile UI uygulamalarında asynchronous aramalarının daha hızolduğunu unutmayın.  
  
## <a name="writing-text"></a>Metin Yazma  
 Aşağıdaki örnek, bir dosyaya metin yazar. Her bekleyen deyiminde yöntem hemen çıkar. Dosya G/Ç tamamlandığında, yöntem bekleme deyimini izleyen deyimde devam eder. Async değiştirici bekleme deyimini kullanan yöntemlerin tanımında olduğunu unutmayın.  
  
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
  
 Özgün örnekte, `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`aşağıdaki iki ifadenin daralması olan ifade vardır:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 İlk deyim bir görevi döndürür ve dosya işlemenin başlatılmasına neden olur. Bekleme ile ikinci ifade yöntemin hemen çıkmak ve farklı bir görev dönmek için neden olur. Dosya işleme daha sonra tamamlandığında, yürütme bekleme izleyen deyimi döndürür. Daha fazla bilgi için [Async Programlarında Denetim Akışı (C#) 'ye](./control-flow-in-async-programs.md)bakın.  
  
## <a name="reading-text"></a>Okuma Metni  
 Aşağıdaki örnekte bir dosyadaki metin okur. Metin arabelleğe alınarak bu durumda bir <xref:System.Text.StringBuilder>. Önceki örnekte aksine, bekleme nin değerlendirilmesi bir değer üretir. Yöntem <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.Tasks.Task> \< <xref:System.Int32> bir> döndürür, bu nedenle `Int32` beklemenin değerlendirilmesi işlem tamamlandıktan sonra bir değer (`numRead`) üretir. Daha fazla bilgi için [Bkz. Async İade Türleri (C#)](./async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Paralel Asynchronous I/O  
 Aşağıdaki örnek, 10 metin dosyası yazarak paralel işleme gösterir. Her dosya için <xref:System.IO.Stream.WriteAsync%2A> yöntem, görev listesine eklenen bir görevi döndürür. İfade `await Task.WhenAll(tasks);` yöntemden çıkar ve tüm görevler için dosya işleme tamamlandığında yöntem içinde devam eder.  
  
 Örnek, görevler <xref:System.IO.FileStream> tamamlandıktan sonra `finally` bloktaki tüm örnekleri kapatır. Her `FileStream` biri bir `using` deyimde oluşturulduysa, `FileStream` görev tamamlanmadan önce atılabilir.  
  
 Herhangi bir performans artışının neredeyse tamamen paralel işlemeden geldiğini ve eşzamanlı işlemden olmadığını unutmayın. Eşsenkronizasyonun avantajları, birden çok iş parçacığı bağlamaması ve kullanıcı arabirimi iş parçacığı bağlamamasıdır.  
  
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
  
 Ve yöntemleri kullanırken, işlemi <xref:System.Threading.CancellationToken>orta akışta iptal etmek için kullanabileceğiniz bir , belirtebilirsiniz. <xref:System.IO.Stream.ReadAsync%2A> <xref:System.IO.Stream.WriteAsync%2A> Daha fazla bilgi için, Yönetilen İş Parçacıklarında [Async Uygulamanızı (C#) İnce Ayar](./fine-tuning-your-async-application.md) la ve [İptal'e](../../../../standard/threading/cancellation-in-managed-threads.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile Asynchronous Programlama (C#)](./index.md)
- [Async İade Türleri (C#)](./async-return-types.md)
- [Async Programlarında Kontrol Akışı (C#)](./control-flow-in-async-programs.md)
