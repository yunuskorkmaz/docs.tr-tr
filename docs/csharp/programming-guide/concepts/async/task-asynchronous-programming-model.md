---
title: Görev Asynchronous Programlama Modeli (TAP) async ve bekliyor (C#)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 2700f5bfaa2746c1ea6f4862bee3af60cf83d693
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78848994"
---
# <a name="task-asynchronous-programming-model"></a>Zaman uyumsuz görev programlama modeli

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.

[C# 5,](../../../whats-new/csharp-version-history.md#c-version-50) .NET Framework 4.5 ve üstü,.NET Core ve Windows Runtime'da asynchronous desteğinden yararlanan basitleştirilmiş bir yaklaşım, async programlama getirmiştir. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.

Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.

## <a name="BKMK_WhentoUseAsynchrony"></a>Async yanıt verme yeteneğini artırır

Asynchrony, web erişimi gibi potansiyel olarak engellenen etkinlikler için çok önemlidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Böyle bir etkinlik eşzamanlı bir işlemde engellenirse, tüm uygulamanın beklemesi gerekir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.

Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET ve Windows Runtime'dan listelenen API'ler, async programlamayı destekleyen yöntemler içerir.

| Uygulama alanı    | .NET türleri async yöntemleri ile     | Async yöntemleri ile Windows Runtime türleri  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web erişimi|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Dosyalarla çalışma|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|
|Görüntülerle çalışma||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|WCF programlama|[Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||

Tüm kullanıcı arabirimi ilişkili faaliyetler genellikle tek bir iş parçacığını paylaştığından, zaman uyumsuzluğun kullanıcı arabirimi iş parçacığına erişen uygulamalar için özellikle önem taşıdığı kanıtlanmıştır. Herhangi bir işlem zaman uyumlu bir uygulamada engellenirse, tümü engellenir. Uygulamanız yanıt vermiyordur ve bunu uygulamanın beklediği değil de başarısız olduğu şeklinde yorumlayabilirsiniz.

Zaman uyumsuz yöntemleri kullandığınızda, uygulama arabirime yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da bitmesini beklemek istemiyorsanız kapatabilirsiniz.

Zaman uyumsuz tabanlı yaklaşım otomatik bir iletimin eşdeğerini, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarından yararlanabilirsiniz, buna rağmen geliştiricinin daha az çaba sarf etmesi gerekir.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Async yöntemleri yazmak daha kolaydır

C#'daki [async](../../../language-reference/keywords/async.md) ve [bekleyen](../../../language-reference/operators/await.md) anahtar kelimeler, async programlamanın kalbidir. Bu iki anahtar kelimeyi kullanarak, .NET Framework, .NET Core veya Windows Runtime'daki kaynakları kullanarak eşzamanlı bir yöntem oluşturduğunuz kadar kolay bir eşzamanlı yöntem oluşturabilirsiniz. `async` Anahtar sözcüğü kullanarak tanımladığınız eşzamanlı *yöntemlere eşitleme yöntemleri*denir.

Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır.

Bu konunun sonunda eksiksiz bir Windows Presentation Foundation (WPF) örnek dosyasını bulabilir ve Örneği [Async Sample'dan indirebilirsiniz: "Async ve Await ile Asynchronous Programming" örneğinden.](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/)

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

Önceki örnekten çeşitli uygulamalar öğrenebilirsiniz. Yöntem imzasıyla başlayın. Değiştirici `async` içerir. İade türü `Task<int>` (Daha fazla seçenek için "İade Türleri" bölümüne bakın). Yöntem adı `Async`. Yöntemin gövdesinde, `GetStringAsync` bir `Task<string>`. Bu, görev `await` aldığınızda bir `string` ( )`urlContents`alırsınız anlamına gelir.  Görevi beklemeden önce, `string` 'den `GetStringAsync`güvenmeyen işler yapabilirsiniz.

Operatöre çok `await` dikkat edin. Bu askıya `AccessTheWebAsync`;

- `AccessTheWebAsync`tamamlanana kadar `getStringTask` devam edemez.
- Bu arada, denetim arayan `AccessTheWebAsync`döner .
- Denetim tamamlandığında burada `getStringTask` devam eder.
- İşleç `await` daha `string` sonra `getStringTask`sonucu alır.

İade deyimi bir sonda sonucu belirtir. Bekleyen `AccessTheWebAsync` tüm yöntemler uzunluk değerini alır.

`AccessTheWebAsync` Arama `GetStringAsync` yapmakla tamamlanmasını beklemek arasında yapabileceği herhangi bir iş yoksa, aşağıdaki tek ifadede arayarak ve bekleyerek kodunuzu basitleştirebilirsiniz.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Aşağıdaki özellikler, önceki örneği bir async yöntemi yapan şeyi özetler:

- Yöntem imzası bir `async` değiştirici içerir.
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - <xref:System.Threading.Tasks.Task%601>yönteminizde operand'ın türü `TResult`olan bir iade deyimi varsa.
  - <xref:System.Threading.Tasks.Task>yönteminizde iade beyanı yoksa veya operand'ı olmayan bir iade beyanı varsa.
  - `void`bir async olay işleyicisi yazıyorsanız.
  - Metodu olan `GetAwaiter` diğer herhangi bir tür (C# 7.0 ile başlayarak).

  Daha fazla bilgi için [İade Türleri ve Parametreler](#BKMK_ReturnTypesandParameters) bölümüne bakın.

- Yöntem genellikle, beklenen `await` eşyoknöz işlem tamamlanana kadar yöntemin devam edilemeyecek bir noktayı işaretleyen en az bir ifade içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.

.NET Framework'ün önceki sürümlerinde eşzamanlılık hakkında daha fazla bilgi için [TPL ve Traditional .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md)bölümüne bakın.

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Async yönteminde ne olur?

Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagram işlem boyunca size yol açar:

![Bir async programını izleme](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "Navigasyon İzleme")

Diyagramdaki sayılar, kullanıcı "başlat" düğmesini tıklattığında başlatılan aşağıdaki adımlara karşılık gelir.

1. Bir olay işleyicisi `AccessTheWebAsync` çağırır ve async yöntemini bekler.

2. `AccessTheWebAsync`bir <xref:System.Net.Http.HttpClient> örnek oluşturur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2A> bir web sitesinin içeriğini dize olarak indirmek için eşzamanlı yöntemi çağırır.

3. İlerlemesini `GetStringAsync` askıya alan bir şey olur. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemeyi önlemek `GetStringAsync` için, denetimi arayana verir. `AccessTheWebAsync`

     `GetStringAsync`bir <xref:System.Threading.Tasks.Task%601>, `TResult` nerede bir dize döndürür ve `AccessTheWebAsync` değişkene `getStringTask` görev atar. Görev, çalışma tamamlandığında gerçek bir `GetStringAsync`dize değeri oluşturma taahhüdüyle, çağrı için devam eden işlemi temsil eder.

4. Çünkü `getStringTask` henüz beklenmedi, `AccessTheWebAsync` nihai sonucuna bağlı olmayan diğer çalışmalarla devam `GetStringAsync`edebilir. Bu çalışma senkron yönteme `DoIndependentWork`yapılan bir çağrı yla temsil edilir.

5. `DoIndependentWork`işini yapan ve arayana geri dönen eşzamanlı bir yöntemdir.

6. `AccessTheWebAsync`bir sonuç olmadan yapabileceği iş tükendi `getStringTask`. `AccessTheWebAsync`sonraki, indirilen dize uzunluğunu hesaplamak ve döndürmek istiyor, ancak yöntem dize olana kadar bu değeri hesaplayamaz.

     Bu `AccessTheWebAsync` nedenle, ilerlemesini askıya almak ve '. `AccessTheWebAsync` `AccessTheWebAsync`arayana `Task<int>` bir döndürür. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.

    > [!NOTE]
    > (ve `GetStringAsync` bu `getStringTask`nedenle) `AccessTheWebAsync` beklemeden tamamlanırsa, denetim `AccessTheWebAsync`. Çağrılan eşzamanlı işlem () `AccessTheWebAsync` `getStringTask`zaten tamamlanmışsa ve nihai sonucu beklemek zorunda değilse, `AccessTheWebAsync` askıya alma ve geri dönüş giderleri boşa gider.

     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Arayan, bu sonucu beklemeden önce elde edilen `AccessTheWebAsync` sonuca bağlı olmayan başka işler yapabilir veya arayan hemen bekleyebilir.   Olay işleyicisi `AccessTheWebAsync`bekliyor `AccessTheWebAsync` ve bekliyor. `GetStringAsync`

7. `GetStringAsync`tamamlar ve bir dize sonucu üretir. Dize sonucu, beklediğiniz şekilde `GetStringAsync` çağrıyla döndürülemez. (Yöntemin 3. adımda bir görevi zaten döndürettiğini unutmayın.) Bunun yerine, dize sonucu yöntemin tamamlanmasını temsil eden `getStringTask`görevde depolanır. Bekleme işleci sonucu ' `getStringTask`dan alır. Atama deyimi, alınan sonucu ' `urlContents`ya .

8. Dize sonucu olduğunda, `AccessTheWebAsync` yöntem dize uzunluğunu hesaplayabilirsiniz. Sonra iş `AccessTheWebAsync` de tamamlanır ve bekleyen olay işleyicisi devam edebilirsiniz. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.
Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi için, [Async Programlarında Denetim Akışı (C#)](control-flow-in-async-programs.md)bakın.

## <a name="BKMK_APIAsyncMethods"></a>API async yöntemleri

Bu tür async programlama gibi `GetStringAsync` yöntemleri nerede bulacağınızı merak ediyor olabilirsiniz. .NET Framework 4.5 veya üstü ve .NET Core `async` `await`ile çalışan ve . Bunları üye adına eklenen "Async" soneki yle ve bunların dönüş türüne <xref:System.Threading.Tasks.Task> göre <xref:System.Threading.Tasks.Task%601>tanıyabilirsiniz. `System.IO.Stream` Örneğin, <xref:System.IO.Stream.CopyToAsync%2A>sınıf , , <xref:System.IO.Stream.ReadAsync%2A>ve <xref:System.IO.Stream.WriteAsync%2A> senkron yöntemlerin <xref:System.IO.Stream.CopyTo%2A>yanı sıra <xref:System.IO.Stream.Read%2A>, <xref:System.IO.Stream.Write%2A>ve .

Windows Runtime, Windows uygulamalarında `async` ve `await` windows uygulamalarında kullanabileceğiniz birçok yöntem de içerir. Daha fazla bilgi için, UWP geliştirme için [İş Parçacığı ve async programlama](/windows/uwp/threading-async/) ve [Asynchronous programlama (Windows Mağazası uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) ve Quickstart: Windows Runtime'ın önceki sürümlerini kullanıyorsanız [C# veya Visual Basic'te asynchronous API'leri arama](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) konusuna bakın.

## <a name="BKMK_Threads"></a>Iş parçacığı

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Async `await` yöntemindeki bir ifade, beklenen görev çalışırken geçerli iş parçacığı engellemez. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.

Anahtar `async` `await` kelimeler ek iş parçacıkları oluşturulmasına neden olmaz. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. CPU'ya <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> bağlı çalışmayı arka plan iş parçacığına taşımak için kullanabilirsiniz, ancak arka plan iş parçacığı, sonuçların kullanılabilir olmasını bekleyen bir işleme yardımcı olmaz.

Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Kod daha basit olduğundan ve <xref:System.ComponentModel.BackgroundWorker> yarış koşullarına karşı korumanız gerekmediği için, bu yaklaşım G/Ç'ye bağlı işlemler için sınıftan daha iyidir. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> Yöntemle birlikte, async programlama, kodunuzu çalıştırmanın koordinasyon ayrıntılarını iş parçacığı havuzuna aktaran `Task.Run` işten ayırdığından, cpu'ya bağlı işlemlerden daha <xref:System.ComponentModel.BackgroundWorker> iyidir.

## <a name="BKMK_AsyncandAwait"></a>async ve bekliyor

Bir yöntemin [async](../../../language-reference/keywords/async.md) değiştirici kullanarak bir async yöntemi olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirin.

- İşaretli async yöntemi süspansiyon noktaları belirlemek için [bekliyor](../../../language-reference/operators/await.md) kullanabilirsiniz. İşleç, `await` beklenen asynchronous işlemi tamamlanana kadar async yönteminin bu noktayı geçemeyebileceğini derleyiciye bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.

     Bir `await` ifadede bir async yönteminin askıya alınması yöntemden çıkış `finally` anlamına gelmez ve bloklar çalışmaz.

- İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.

Async yöntemi genellikle bir `await` işleç bir veya daha fazla `await` oluşumları içerir, ancak ifadelerin yokluğu derleyici hatasına neden olmaz. Bir async yöntemi bir süspansiyon `await` noktası işaretlemek için bir işleç kullanmıyorsa, yöntem `async` değiştirici rağmen, senkron bir yöntem olarak yürütür. Derleyici bu tür yöntemler için bir uyarı verir.

`async`ve `await` bağlamsal anahtar kelimelerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>İade türleri ve parametreleri

Async yöntemi genellikle bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>bir . Bir async yöntemi `await` içinde, bir işleç başka bir async yöntemiiçin bir çağrı döndürülen bir göreve uygulanır.

Yöntem, <xref:System.Threading.Tasks.Task%601> bir operand türü `TResult` [`return`](../../../language-reference/keywords/return.md) belirten bir deyim içeriyorsa, iade türü olarak belirtirsiniz.

Yöntemin <xref:System.Threading.Tasks.Task> iade deyimi yoksa veya bir operand döndürmeyen bir iade deyimi varsa, iade türü olarak kullanırsınız.

C# 7.0 ile başlayarak, tür bir yöntem içeriyorsa, `GetAwaiter` başka bir iade türü de belirtebilirsiniz. <xref:System.Threading.Tasks.ValueTask%601>böyle bir tür bir örnektir. [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketinde mevcuttur.

Aşağıdaki örnek, bir veya bir <xref:System.Threading.Tasks.Task%601> yöntemi nasıl beyan <xref:System.Threading.Tasks.Task>ettiğinizi ve çağırdığınızı gösterir:

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

Bir async yöntemi de `void` bir dönüş türü olabilir. Bu iade türü, öncelikle bir `void` dönüş türü gerekli olay işleyicileri tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.

İade türü olan bir `void` async yöntemi beklenebilir ve geçersiz döndüren bir yöntemin arayan ı, yöntemin attığı özel durumları yakalayamaz.

Bir async yöntemi, [ref](../../../language-reference/keywords/ref.md) veya [out](../../../language-reference/keywords/out-parameter-modifier.md) [parametrelerini](../../../language-reference/keywords/in-parameter-modifier.md)bildiremez, ancak yöntem bu tür parametrelere sahip yöntemleri çağırabilir. Benzer şekilde, bir async yöntemi, ref return değerleri ile yöntemleri çağırabilir rağmen, referans tarafından bir değer döndüremez.

Daha fazla bilgi ve örnekler [için, Bkz. Async İade Türleri (C#)](./async-return-types.md). Async yöntemlerindeki özel durumları nasıl yakalayacakları hakkında daha fazla bilgi için [try-catch'e](../../../language-reference/keywords/try-catch.md)bakın.

Windows Runtime programlamadaki eşzamanlı API'ler, görevlere benzer aşağıdaki iade türlerinden birine sahiptir:

- <xref:Windows.Foundation.IAsyncOperation%601>, hangi karşılık gelir<xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, hangi karşılık gelir<xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Sözleşmeye göre, sık karşılaşılan türleri döndüren `Task` `Task<T>`yöntemlerin (örn. , , , `ValueTask`) `ValueTask<T>`"Async" ile biten adları olmalıdır. Eşzamanlı bir işlem başlatan ancak bekleyen bir türü döndürmeyen yöntemlerin "Async" ile biten adları olmamalıdır, ancak "Begin", "Start" veya bu yöntemin işlemin sonucunu döndürmediğini veya atmadığını öne süren başka bir fiille başlayabilir.

Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, '. gibi `Button1_Click`ortak olay işleyicileri yeniden adlandırmamalısınız.

## <a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Async Örnek: Web Walkthrough erişim](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Task.WhenAll (C#) kullanarak async walkthrough nasıl genişletilir](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Önceki <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> gözden geçirimi ekler. Tüm indirmeleri aynı anda başlatır. `WhenAll`||
|[Async ve await (C#) kullanarak paralel olarak birden fazla web istekleri yapmak için nasıl](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Async Örnek: Paralel Olarak Birden Çok Web İsteği Yapma](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Async İade Türleri (C#)](./async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||
|[Async Programlarında Kontrol Akışı (C#)](./control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Async Örnek: Async Programlarında Kontrol Akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Async Uygulamanızda İnce Ayar (C#)](./fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> - [Bir Async Görevi veya Görev Listesini İptal Etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Bir Süre Sonra Async Görevlerini İptal Etme (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Birden Çok Async Görevi Başlatın ve Tamamlanındıkları Gibi İşleyin (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Async Örnek: Uygulamanızı İyi Ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Async Apps'ta Reentrancy'yi Işleme (C#)](./handling-reentrancy-in-async-apps.md)|Etkin bir eşzamanlı işlemin çalışırken yeniden başlatıldığu servis taleplerini gösterir.||
|[WhenAny: .NET Framework ve Windows Runtime arasında köprü kurma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Windows Runtime yöntemiyle kullanabilmeniz <xref:System.Threading.Tasks.Task.WhenAny%2A> için Windows Runtime'daki .NET Framework ve IAsyncOperations'taki Görev türleri arasında nasıl köprü kurkullanılacağını gösterir.|[Async Örnek: .NET ve Windows Runtime (AsTask ve WhenAny) arasında köprüleme](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Zaman Uyumsuz İptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Windows Runtime yöntemiyle kullanabilmeniz <xref:System.Threading.CancellationTokenSource> için Windows Runtime'daki .NET Framework ve IAsyncOperations'taki Görev türleri arasında nasıl köprü kurkullanılacağını gösterir.|[Async Örnek: .NET ve Windows Runtime arasında köprüleme (AsTask & İptal)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya Erişimi için Async kullanma (C#)](./using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Desen ve <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> türleri dayanmaktadır.||
|[Kanal 9'da Async Videoları](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="BKMK_CompleteExample"></a>Tam örnek

Aşağıdaki kod, bu makalenin tartıştığı WPF uygulamasından *gelen MainWindow.xaml.cs* dosyasıdır. Örneği [Async Sample'dan indirebilirsiniz: "Async ve Await ile Asynchronous Programming" örneğinden.](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/)

[!code-csharp[async](~/samples/snippets/standard/async/async-and-await/cs/MainWindow.xaml.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Zaman uyumsuz programlama](../../../async.md)
- [Async genel bakış](../../../../standard/async.md)
