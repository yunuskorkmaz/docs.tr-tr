---
title: Async ve await ile görev zaman uyumsuz programlama modeli (TAP) (C#)
description: Görev tabanlı zaman uyumsuz programlamayı nasıl ve ne zaman kullanacağınızı, C# ' de zaman uyumsuz programlamaya basitleştirilmiş bir yaklaşım hakkında bilgi edinin.
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: ddda97e9c77473120ed32b0e224b07d7c4d71b1e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925143"
---
# <a name="task-asynchronous-programming-model"></a>Zaman uyumsuz görev programlama modeli

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.

[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) , .NET Framework 4,5 ve üzeri, .NET Core ve Windows çalışma zamanı zaman uyumsuz destekten yararlanan, zaman uyumsuz programlama ile basitleştirilmiş bir yaklaşım getirmiştir. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.

Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a>Zaman uyumsuz, yanıt hızını geliştirir

Asynchrony, Web erişimi gibi olası engelleme olasılığı olan etkinlikler için gereklidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Bu tür bir etkinlik zaman uyumlu bir işlemde engellenirse, uygulamanın tamamının beklemesi gerekir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.

Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET ve Windows Çalışma Zamanı listelenen API 'Ler, zaman uyumsuz programlamayı destekleyen yöntemler içerir.

| Uygulama alanı    | Zaman uyumsuz yöntemleriyle .NET türleri     | Zaman uyumsuz yöntemlere sahip Windows Çalışma Zamanı türleri  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web erişimi|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Dosyalarla çalışma|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|
|Görüntülerle çalışma||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|WCF programlama|[Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||

Tüm kullanıcı arabirimi ilişkili faaliyetler genellikle tek bir iş parçacığını paylaştığından, zaman uyumsuzluğun kullanıcı arabirimi iş parçacığına erişen uygulamalar için özellikle önem taşıdığı kanıtlanmıştır. Herhangi bir işlem zaman uyumlu bir uygulamada engellenirse, tümü engellenir. Uygulamanız yanıt vermiyordur ve bunu uygulamanın beklediği değil de başarısız olduğu şeklinde yorumlayabilirsiniz.

Zaman uyumsuz yöntemleri kullandığınızda, uygulama arabirime yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da bitmesini beklemek istemiyorsanız kapatabilirsiniz.

Zaman uyumsuz tabanlı yaklaşım otomatik bir iletimin eşdeğerini, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarından yararlanabilirsiniz, buna rağmen geliştiricinin daha az çaba sarf etmesi gerekir.

## <a name="async-methods-are-easier-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a>Zaman uyumsuz yöntemlerin yazılması daha kolaydır

Async [ve](../../../language-reference/keywords/async.md) [await](../../../language-reference/operators/await.md) anahtar sözcükleri, zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak, bir zaman uyumlu Yöntem oluştururken neredeyse kolayca zaman uyumsuz bir yöntem oluşturmak için .NET Framework, .NET Core veya Windows Çalışma Zamanı içindeki kaynakları kullanabilirsiniz. Anahtar sözcüğünü kullanarak tanımladığınız zaman uyumsuz yöntemler, `async` *zaman uyumsuz yöntemler*olarak adlandırılır.

Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Koddaki neredeyse her şey size tanıdık gelmelidir.

Bu konunun sonunda bir Windows Presentation Foundation (WPF) örnek dosyası bulabilirsiniz ve örneği [zaman uyumsuz örnek: "Async ve await Ile zaman uyumsuz programlama" kaynağından](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/)indirebilirsiniz.

```csharp
async Task<int> AccessTheWebAsync()
{
    // You need to add a reference to System.Net.Http to declare client.
    var client = new HttpClient();

    // GetStringAsync returns a Task<string>. That means that when you await the
    // task you'll get a string (urlContents).
    Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com/dotnet");

    // You can do work here that doesn't rely on the string from GetStringAsync.
    DoIndependentWork();

    // The await operator suspends AccessTheWebAsync.
    //  - AccessTheWebAsync can't continue until getStringTask is complete.
    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.
    //  - Control resumes here when getStringTask is complete.
    //  - The await operator then retrieves the string result from getStringTask.
    string urlContents = await getStringTask;

    // The return statement specifies an integer result.
    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.
    return urlContents.Length;
}
```

Yukarıdaki örnekten birkaç uygulama öğrenebilirsiniz. Yöntem imzasıyla başlayın. `async`Değiştiricisini içerir. Dönüş türü `Task<int>` (daha fazla seçenek için "dönüş türleri" bölümüne bakın). Yöntem adı içinde biter `Async` . Yönteminin gövdesinde, `GetStringAsync` bir döndürür `Task<string>` . Yani, `await` bir görev `string` () alacağınız zaman `urlContents` .  Görevi kapatmadan önce, ' a bağımlı olmayan iş yapabilirsiniz `string` `GetStringAsync` .

Operatöre yakın ilgilenilmesi için ödeme yapın `await` . Askıya alır `AccessTheWebAsync` ;

- `AccessTheWebAsync`tamamlanana kadar devam edilemiyor `getStringTask` .
- Bu arada, Denetim çağırana döner `AccessTheWebAsync` .
- Tamamlandığında, Denetim burada sürdürülür `getStringTask` .
- `await`İşleci bundan sonra sonucu alır `string` `getStringTask` .

Return ifadesinde bir tamsayı sonucu belirtilir. Bekleyen tüm yöntemler `AccessTheWebAsync` uzunluk değerini alır.

`AccessTheWebAsync`Çağrısı ve tamamlanmasını bekleme arasında yapabilecek herhangi bir işi yoksa `GetStringAsync` , aşağıdaki tek deyime çağırarak ve bekleyen kodunuzu basitleştirebilirsiniz.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Aşağıdaki özellikler, önceki örneği nasıl zaman uyumsuz bir yöntem yaptığını özetler:

- Yöntem imzası bir değiştirici içerir `async` .
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - <xref:System.Threading.Tasks.Task%601>yönteminizin işlenenin türü olan bir return bildirisi varsa `TResult` .
  - <xref:System.Threading.Tasks.Task>yönteminizin Return bildirisi yoksa veya işleneni olmayan bir return ifadesine sahip.
  - `void`zaman uyumsuz bir olay işleyicisi yazıyorsanız.
  - Metodu olan diğer herhangi bir tür `GetAwaiter` (C# 7,0 ile başlar).

  Daha fazla bilgi için bkz. [dönüş türleri ve parametreleri](#BKMK_ReturnTypesandParameters) bölümü.

- Yöntemi genellikle, `await` beklenen zaman uyumsuz işlem tamamlanana kadar yöntemin devam edemediği bir noktayı işaretleyen en az bir ifade içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.

Önceki .NET Framework sürümlerindeki zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Zaman uyumsuz bir yöntemde ne olur?

Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagramda süreç boyunca size yol gösterir:

![Zaman uyumsuz bir programı izleme](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "NavigationTrace")

Diyagramdaki sayılar, Kullanıcı "Başlat" düğmesine tıkladığında başlatılan aşağıdaki adımlara karşılık gelir.

1. Bir olay işleyicisi, `AccessTheWebAsync` zaman uyumsuz yöntemini çağırır ve bekler.

2. `AccessTheWebAsync`bir <xref:System.Net.Http.HttpClient> örnek oluşturur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2A> bir Web sitesinin içeriklerini dize olarak indirmek için zaman uyumsuz yöntemi çağırır.

3. İçinde `GetStringAsync` ilerleme durumunu askıya alan bir sorun var. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemeyi önlemek için, `GetStringAsync` kendi çağıranına denetim verir `AccessTheWebAsync` .

     `GetStringAsync`öğesini döndürür <xref:System.Threading.Tasks.Task%601> , burada `TResult` bir dizedir ve `AccessTheWebAsync` görevi `getStringTask` değişkenine atar. Görev, `GetStringAsync` iş tamamlandığında gerçek bir dize değeri üretme taahhüdünde, çağrısı için devam eden işlemi temsil eder.

4. Henüz beklenmediği `getStringTask` `AccessTheWebAsync` için, nihai sonuca bağlı olmayan diğer çalışmalarla devam edebilir `GetStringAsync` . Bu iş, zaman uyumlu yöntem çağrısıyla temsil edilir `DoIndependentWork` .

5. `DoIndependentWork`, işini yapan ve çağırana döndüren zaman uyumlu bir yöntemdir.

6. `AccessTheWebAsync`, uygulamasından bir sonuç olmadan yapabilmeden iş dışında çalışıyor `getStringTask` . `AccessTheWebAsync`ardından, indirilen dizenin uzunluğunu hesaplamak ve döndürmek ister, ancak yöntem dizeye gelinceye kadar bu değeri hesaplayamaz.

     Bu nedenle, `AccessTheWebAsync` ilerleme durumunu askıya almak ve denetimi çağıran yönteme eklemek için bir Await işleci kullanır `AccessTheWebAsync` . `AccessTheWebAsync`çağırana döndürür `Task<int>` . Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.

    > [!NOTE]
    > `GetStringAsync`(Ve bu nedenle `getStringTask` ), bekleden önce tamamlanırsa `AccessTheWebAsync` , denetim içinde kalır `AccessTheWebAsync` . `AccessTheWebAsync`Çağrılan zaman uyumsuz işlem ( `getStringTask` ) zaten tamamlanmışsa ve `AccessTheWebAsync` nihai sonucu beklemek zorunda değilse, askıya alma ve daha sonra geri dönme gideri harcanacaktır.

     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Çağıran, sonucu beklemeden önce sonucu kendisine bağlı olmayan başka bir iş `AccessTheWebAsync` ya da çağıran hemen bekleme edebilir.   Olay işleyicisi için bekliyor `AccessTheWebAsync` ve `AccessTheWebAsync` bekliyor `GetStringAsync` .

7. `GetStringAsync`tamamlar ve bir dize sonucu üretir. Dize sonucu, bekleneceğiniz şekilde çağrısı tarafından döndürülmedi `GetStringAsync` . (Metodun adım 3 ' te bir görevi zaten döndürdüğünü unutmayın.) Bunun yerine, dize sonucu, yönteminin tamamlandığını temsil eden görevde saklanır `getStringTask` . Await işleci sonucunu alır `getStringTask` . Atama ekstresi alındı sonucunu öğesine atar `urlContents` .

8. `AccessTheWebAsync`Dize sonucu olduğunda, yöntemi dizenin uzunluğunu hesaplayabilir. Bu durumda, çalışması `AccessTheWebAsync` da tamamlanır ve bekleyen olay işleyicisi sürdürülebilirler. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.
Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışı (C#)](control-flow-in-async-programs.md).

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a>API zaman uyumsuz yöntemleri

Zaman uyumsuz programlamayı destekleyen gibi yöntemlerin nerede bulunacağını merak ediyor olabilirsiniz `GetStringAsync` . .NET Framework 4,5 veya üzeri ve .NET Core, ve ile çalışan birçok üye `async` içerir `await` . Bunları, üye adına eklenen "Async" sonekine ve ya da dönüş türlerine göre tanıyabilirsiniz <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> . Örneğin, sınıfı,, ve gibi `System.IO.Stream` yöntemleri, <xref:System.IO.Stream.CopyToAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> <xref:System.IO.Stream.WriteAsync%2A> ile zaman uyumlu yöntemleri içerir <xref:System.IO.Stream.CopyTo%2A> <xref:System.IO.Stream.Read%2A> <xref:System.IO.Stream.Write%2A> .

Windows Çalışma Zamanı ayrıca `async` Windows uygulamalarında ve ile kullanabileceğiniz birçok yöntem içerir `await` . Daha fazla bilgi için bkz. UWP geliştirme için [Iş parçacığı ve zaman uyumsuz programlama](/windows/uwp/threading-async/) ve [zaman uyumsuz programlama (Windows Mağazası uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) ve hızlı başlangıç: Windows çalışma zamanı önceki sürümlerini kullanıyorsanız, [C# veya Visual Basic zaman uyumsuz API 'leri çağırma](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) .

## <a name="threads"></a><a name="BKMK_Threads"></a>Akışları

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. `await`Zaman uyumsuz yöntemdeki bir ifade, beklenen görev çalışırken geçerli iş parçacığını engellemez. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.

`async`Ve `await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>CPU 'ya bağlanan işi arka plan iş parçacığına taşımak için kullanabilirsiniz, ancak arka plan iş parçacığı yalnızca sonuçların kullanılabilir hale gelmesini bekleyen bir işlem konusunda yardımcı olmaz.

Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Özellikle, bu yaklaşım, <xref:System.ComponentModel.BackgroundWorker> kod daha basit olduğundan ve yarış koşullarına karşı koruma sağlamak zorunda olmadığınızdan g/ç ile bağlantılı işlemler için olan sınıftan daha iyidir. , Zaman uyumsuz programlama, <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker> iş parçacığı havuzuna aktarılan işten kodunuzu çalıştırmanın koordinasyon ayrıntılarını ayırdığından, zaman uyumsuz programlama, CPU 'ya bağlanan işlemlerden daha iyidir `Task.Run` .

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a>Async ve await

[Zaman](../../../language-reference/keywords/async.md) uyumsuz değiştirici kullanarak bir yöntemin zaman uyumsuz bir yöntem olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirirsiniz.

- İşaretlenen zaman uyumsuz yöntem, askıya alma noktaları belirlemek için [await](../../../language-reference/operators/await.md) kullanabilir. İşleci, zaman uyumsuz yöntemin, beklenen `await` zaman uyumsuz işlem tamamlanana kadar bu noktanın ötesine devam edemeyeceğini derleyiciye bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.

     Bir ifadede zaman uyumsuz bir yöntemin askıya alınması `await` yöntemden bir çıkış oluşturmaz ve `finally` bloklar çalıştırılmaz.

- İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.

Zaman uyumsuz bir yöntem, genellikle bir işlecin bir veya daha fazla örneğini içerir `await` , ancak ifadelerin yokluğu `await` bir derleyici hatasına neden olmaz. Zaman uyumsuz bir yöntem, askıya alma `await` noktasını işaretlemek için bir operatör kullanmıyorsa Yöntem, değiştiriciye rağmen zaman uyumlu bir yöntem olarak yürütülür `async` . Derleyici bu tür yöntemler için bir uyarı verir.

`async`ve `await` bağlamsal anahtar sözcüklerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a>Dönüş türleri ve parametreleri

Zaman uyumsuz bir yöntem genellikle bir <xref:System.Threading.Tasks.Task> veya döndürür <xref:System.Threading.Tasks.Task%601> . Zaman uyumsuz bir yöntemde, bir `await` işleç, başka bir zaman uyumsuz metoda yapılan çağrıdan döndürülen bir göreve uygulanır.

Yöntemi, <xref:System.Threading.Tasks.Task%601> [`return`](../../../language-reference/keywords/return.md) türünde bir işleneni belirten bir ifade içeriyorsa, dönüş türü olarak belirtirsiniz `TResult` .

<xref:System.Threading.Tasks.Task>Metodun Return ifadesine sahip olmaması veya bir işleneni döndürmeyen bir return ifadesine sahip olması durumunda dönüş türü olarak kullanırsınız.

C# 7,0 ' den başlayarak, türün bir yöntemi içermesi kaydıyla, başka bir dönüş türü de belirtebilirsiniz `GetAwaiter` . <xref:System.Threading.Tasks.ValueTask%601>Bu tür bir örnektir. [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketinde kullanılabilir.

Aşağıdaki örnek, bir veya döndüren bir yöntemi nasıl bildirmenizi ve çağırakullanacağınızı gösterir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> :

```csharp
// Signature specifies Task<TResult>
async Task<int> GetTaskOfTResultAsync()
{
    int hours = 0;
    await Task.Delay(0);
    // Return statement specifies an integer result.
    return hours;
}

// Calls to GetTaskOfTResultAsync
Task<int> returnedTaskTResult = GetTaskOfTResultAsync();
int intResult = await returnedTaskTResult;
// or, in a single statement
int intResult = await GetTaskOfTResultAsync();

// Signature specifies Task
async Task GetTaskAsync()
{
    await Task.Delay(0);
    // The method has no return statement.
}

// Calls to GetTaskAsync
Task returnedTask = GetTaskAsync();
await returnedTask;
// or, in a single statement
await GetTaskAsync();
```

Döndürülmüş her görev, devam eden bir çalışmayı temsil eder. Bir görev, zaman uyumsuz işlemin durumu hakkındaki bilgileri saklar ve sonunda, işlemden alınan nihai sonuca veya başarısız olursa işlemin neden olduğu bir özel duruma ilişkin bilgileri içerir.

Zaman uyumsuz bir yöntemin `void` dönüş türü de olabilir. Bu dönüş türü öncelikle bir dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır `void` . Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.

Dönüş türüne sahip bir zaman uyumsuz yöntem beklenemez `void` ve void döndüren bir yöntem çağıran yöntemin aldığı özel durumları yakalayabilir.

Zaman uyumsuz bir yöntem [içinde](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) veya [Out](../../../language-reference/keywords/out-parameter-modifier.md) parametrelerini bildiremez, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir. Benzer şekilde, zaman uyumsuz bir yöntem başvuruya göre değer döndüremez, ancak başvuru dönüş değerleri içeren yöntemler çağırabilir.

Daha fazla bilgi ve örnek için bkz. [Async Return Types (C#)](./async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [try-catch](../../../language-reference/keywords/try-catch.md).

Windows Çalışma Zamanı programlamadaki zaman uyumsuz API 'Ler, görevlerle benzer olan aşağıdaki dönüş türlerinden birine sahiptir:

- <xref:Windows.Foundation.IAsyncOperation%601>öğesine karşılık gelen<xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>öğesine karşılık gelen<xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Kurala göre, yaygın olarak kullanılan türleri (örneğin,,,,,,,) döndüren yöntemlerin `Task` `Task<T>` `ValueTask` `ValueTask<T>` "Async" ile biten adları olmalıdır. Zaman uyumsuz bir işlem Başlatan ancak bir awasever türü döndürmeyen Yöntemler, "Async" ile biten adlara sahip olmamalıdır, ancak bu yöntemin işlemin sonucunu döndürmeyeceğini veya oluşturmadığını önermek için "BEGIN", "Start" ya da başka bir fiil ile başlayabilir.

Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, gibi yaygın olay işleyicilerini yeniden adlandırmamanız gerekir `Button1_Click` .

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örnek: Web 'e erişme yolu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>Önceki izlenecek yolu ekler. Öğesinin kullanımı, `WhenAll` tüm indirmeleri aynı anda başlatır.||
|[Async ve await kullanarak birden çok web isteğini paralel hale getirme (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örnek: birden çok Web Isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Zaman uyumsuz dönüş türleri (C#)](./async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||
|[Zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Async örneği: zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> - [Zaman uyumsuz bir görevi veya görev listesini iptal etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [Kalan zaman uyumsuz görevleri bir tane tamamlandıktan sonra iptal etme (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Birden çok zaman uyumsuz görev başlatma ve bunları tamamlarsa Işleme (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)](./handling-reentrancy-in-async-apps.md)|Çalışırken etkin bir zaman uyumsuz işlemin yeniden başlatılma durumlarının nasıl işleneceğini gösterir.||
|[WhenAny: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Bir Windows Çalışma Zamanı yöntemiyle kullanabilmeniz için, Windows Çalışma Zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir <xref:System.Threading.Tasks.Task.WhenAny%2A> .|[Zaman uyumsuz örnek: .NET ile Windows Çalışma Zamanı arasında köprü oluşturma (AsTask ve WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Zaman Uyumsuz İptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Bir Windows Çalışma Zamanı yöntemiyle kullanabilmeniz için, Windows Çalışma Zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir <xref:System.Threading.CancellationTokenSource> .|[Zaman uyumsuz örnek: .NET ve Windows Çalışma Zamanı arasında köprü oluşturma (AsTask & Iptali)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya erişimi için Async Kullanma (C#)](./using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Model <xref:System.Threading.Tasks.Task> ve türlerini temel alır <xref:System.Threading.Tasks.Task%601> .||
|[Channel 9 ' da zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="complete-example"></a><a name="BKMK_CompleteExample"></a>Örnek Tamam

Aşağıdaki kod, bu makalede ele alınan WPF uygulamasından gelen *MainWindow.xaml.cs* dosyasıdır. Örneği zaman uyumsuz [örnek: "Async ve await Ile zaman uyumsuz programlama" kaynağından](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/)indirebilirsiniz.

[!code-csharp[async](~/samples/snippets/standard/async/async-and-await/cs/MainWindow.xaml.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Zaman uyumsuz programlama](../../../async.md)
- [Zaman uyumsuz genel bakış](../../../../standard/async.md)
