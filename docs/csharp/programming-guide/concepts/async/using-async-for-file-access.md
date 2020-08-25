---
title: Zaman uyumsuz dosya erişimi (C#)
description: Zaman uyumsuz özelliğini C# ' deki dosyalara erişmek için nasıl kullanacağınızı öğrenin. Geri çağırmaları kullanmadan veya kodlarınızı Yöntemler arasında bölmeden zaman uyumsuz yöntemlere çağrı yapabilirsiniz.
ms.date: 08/19/2020
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 9a8db6004e8fff2cb39f0c350b403b56ea619e54
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812048"
---
# <a name="asynchronous-file-access-c"></a>Zaman uyumsuz dosya erişimi (C#)

Dosyalara erişmek için zaman uyumsuz özelliği kullanabilirsiniz. Async özelliğini kullanarak, geri çağırmaları kullanmadan veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde bölmeden zaman uyumsuz yöntemlere çağrı yapabilirsiniz. Zaman uyumlu kodu zaman uyumsuz yapmak için, zaman uyumlu bir yöntem yerine zaman uyumsuz bir yöntem çağırır ve koda birkaç anahtar sözcük eklemeniz yeterlidir.

Dosya erişim çağrılarına zaman uyumsuzluğu eklemek için aşağıdaki nedenleri göz önünde bulundurmanız gerekebilir:

> [!div class="checklist"]
>
> - İşlemi başlatan kullanıcı arabirimi iş parçacığı başka bir iş gerçekleştirebildiğinden, asynchrony UI uygulamalarını daha hızlı hale getirir. UI iş parçacığının uzun zaman alan kodu yürütmesi gerekiyorsa (örneğin, 50 milisaniyeden fazla), g/ç tamamlanana kadar UI dondurabilir ve Kullanıcı arabirimi iş parçacığı klavye ve fare girişini ve diğer olayları yeniden işleyebilir.
> - Asynchrony, iş parçacıkları gereksinimini azaltarak ASP.NET ve diğer sunucu tabanlı uygulamaların ölçeklenebilirliğini geliştirir. Uygulama yanıt başına adanmış bir iş parçacığı kullanıyorsa ve bin istek aynı anda işleneiyorsa, bin iş parçacığı gerekir. Zaman uyumsuz işlemlerin genellikle bekleme sırasında bir iş parçacığı kullanması gerekmez. Mevcut g/ç Tamamlama iş parçacığını kısa bir süre içinde kullanırlar.
> - Bir dosya erişim işleminin gecikmesi geçerli koşullar altında çok düşük olabilir, ancak gecikme gelecekte büyük ölçüde artabilir. Örneğin, bir dosya dünya genelinde bir sunucuya taşınabilir.
> - Zaman uyumsuz özelliği kullanmanın ek yükü küçüktür.
> - Zaman uyumsuz görevler, paralel olarak kolayca çalıştırılabilir.

## <a name="use-appropriate-classes"></a>Uygun sınıfları kullan

Bu konudaki basit örnekler <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> ve gösterir <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType> . Dosya g/ç işlemleri üzerinde sınırlı denetim için, <xref:System.IO.FileStream> işletim sistemi düzeyinde zaman uyumsuz g/ç 'nin oluşmasına neden olan bir seçeneğe sahip sınıfını kullanın. Bu seçeneği kullanarak, birçok durumda bir iş parçacığı havuzu iş parçacığını engellemeyi önleyebilirsiniz. Bu seçeneği etkinleştirmek için, `useAsync=true` `options=FileOptions.Asynchronous` Oluşturucu çağrısında veya bağımsız değişkenini belirtirsiniz.

Bu seçeneği, <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız kullanabilirsiniz. Ancak, bu seçeneği, <xref:System.IO.Stream> sınıfının açık olduğunu bir şekilde sağlarsanız kullanabilirsiniz <xref:System.IO.FileStream> . Zaman uyumsuz çağrılar, kullanıcı ARABIRIMI iş parçacığı bekleme sırasında engellenmediği için, bir iş parçacığı havuzu iş parçacığı engellense bile UI uygulamalarında daha hızlıdır.

## <a name="write-text"></a>Yazma metni

Aşağıdaki örnekler bir dosyaya metin yazar. Her await ifadesinde, yöntemi hemen çıkar. G/ç dosyası tamamlandığında, yöntemi await ifadesini izleyen deyimde devam eder. Zaman uyumsuz değiştirici, await ifadesini kullanan yöntemlerin tanımıdır.

### <a name="simple-example"></a>Basit örnek

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleWrite":::

### <a name="finite-control-example"></a>Sınırlı denetim örneği

:::code language="csharp" source="snippets/file-access/Program.cs" id="WriteText":::

Özgün örnek, `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` aşağıdaki iki deyimin bir örneği olan ifadesine sahiptir:

```csharp
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
await theTask;
```

İlk ifade bir görev döndürür ve dosya işlemenin başlatılmasına neden olur. Await ile ikinci ifade, yönteminin hemen çıkmasına ve farklı bir görev döndürmesine neden olur. Dosya işleme daha sonra tamamlandığında, yürütme, await ' ı izleyen ifadeye geri döner.

## <a name="read-text"></a>Metin oku

Aşağıdaki örneklerde bir dosyadaki metin okunmalıdır.

### <a name="simple-example"></a>Basit örnek

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleRead":::

### <a name="finite-control-example"></a>Sınırlı denetim örneği

Metin, arabelleğe alınmış ve bu durumda bir öğesine yerleştirildi <xref:System.Text.StringBuilder> . Önceki örnekte aksine, await 'ın değerlendirmesi bir değer oluşturur. <xref:System.IO.Stream.ReadAsync%2A>Yöntemi bir> döndürür <xref:System.Threading.Tasks.Task> \<<xref:System.Int32> , bu nedenle await değerlendirmesi `Int32` işlem tamamlandıktan sonra bir değer oluşturur `numRead` . Daha fazla bilgi için bkz. [Async Return Types (C#)](async-return-types.md).

:::code language="csharp" source="snippets/file-access/Program.cs" id="ReadText":::

## <a name="parallel-asynchronous-io"></a>Paralel zaman uyumsuz g/ç

Aşağıdaki örneklerde, 10 metin dosyası yazarak paralel işleme gösterilmektedir.

### <a name="simple-example"></a>Basit örnek

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleParallelWrite":::

### <a name="finite-control-example"></a>Sınırlı denetim örneği

Her dosya için, <xref:System.IO.Stream.WriteAsync%2A> yöntemi bir görev listesine eklenen bir görevi döndürür. `await Task.WhenAll(tasks);`Deyimden çıkılıyor ve tüm görevler için dosya işleme tamamlandığında yöntemi içinde devam eder.

Örnek, <xref:System.IO.FileStream> `finally` görevler tamamlandıktan sonra bir bloktaki tüm örnekleri kapatır. Her biri `FileStream` bir bildiriminde oluşturulduysa, `using` görev tamamlanmadan önce ' `FileStream` nin atımı bırakılmış olabilir.

Herhangi bir performans artışı, zaman uyumsuz işlemden değil, paralel işlemden neredeyse tamamen yapılır. Zaman uyumsuzluğu 'nin avantajları birden çok iş parçacığını bağlamaktır ve Kullanıcı arabirimi iş parçacığını bağlamaktır.

:::code language="csharp" source="snippets/file-access/Program.cs" id="ParallelWriteText":::

<xref:System.IO.Stream.WriteAsync%2A>Ve yöntemlerini kullanırken, <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.CancellationToken> işlem orta-akış işlemini iptal etmek için kullanabileceğiniz bir belirtebilirsiniz. Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (C#)](index.md)
- [Zaman uyumsuz dönüş türleri (C#)](async-return-types.md)
