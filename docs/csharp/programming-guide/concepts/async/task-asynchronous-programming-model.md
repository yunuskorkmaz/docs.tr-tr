---
title: Async ve await (C#) Ile görev zaman uyumsuz programlama MODELI (TAP)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 8f88ecc05fd21a3526478cf564dc4fa97f309f7e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969961"
---
# <a name="task-asynchronous-programming-model"></a>Zaman uyumsuz görev programlama modeli

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.

5, .NET Framework 4,5 ve üzeri, .NET Core ve Windows çalışma zamanı zaman uyumsuz destekten yararlanan, zaman uyumsuz programlama ile basitleştirilmiş bir yaklaşım getirmiştir. [ C# ](../../../whats-new/csharp-version-history.md#c-version-50) Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.

Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.

## <a name="BKMK_WhentoUseAsynchrony"></a>Zaman uyumsuz, yanıt hızını geliştirir

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

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Zaman uyumsuz yöntemlerin yazılması daha kolaydır

' Deki C# [Async](../../../language-reference/keywords/async.md) ve [await](../../../language-reference/operators/await.md) anahtar sözcükleri zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak, bir zaman uyumlu Yöntem oluştururken neredeyse kolayca zaman uyumsuz bir yöntem oluşturmak için .NET Framework, .NET Core veya Windows Çalışma Zamanı kaynaklarını kullanabilirsiniz. `async` anahtar sözcüğünü kullanarak tanımladığınız zaman uyumsuz yöntemler, *zaman uyumsuz yöntemler*olarak adlandırılır.

Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır.

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

Yukarıdaki örnekten birkaç uygulama öğrenebilirsiniz. Yöntem imzasıyla başlayın. `async` değiştiricisini içerir. Dönüş türü `Task<int>` (daha fazla seçenek için bkz. "dönüş türleri" bölümü). Yöntem adı `Async`biter. Yönteminin gövdesinde, `GetStringAsync` `Task<string>`döndürür. Bu, görevi `await` `string` (`urlContents`) alacağınız anlamına gelir.  Görevi beklerken önce, `GetStringAsync``string` kullanmayan çalışmayı yapabilirsiniz.

`await` işlecine yakın bir ilgi ödeyin. `AccessTheWebAsync`askıya alır;

- `getStringTask` tamamlanana kadar `AccessTheWebAsync` devam edemiyor.
- Bu arada, denetim `AccessTheWebAsync`çağırana döner.
- `getStringTask` tamamlandığında Denetim burada sürdürülür.
- `await` işleci daha sonra `getStringTask``string` sonucunu alır.

Return ifadesinde bir tamsayı sonucu belirtilir. `AccessTheWebAsync` bekleyen Yöntemler uzunluk değerini alır.

`AccessTheWebAsync`, çağırma `GetStringAsync` arasında yapamazsa ve tamamlanmasını beklerken, aşağıdaki tek deyime çağırarak ve bekleyen kodunuzu basitleştirebilirsiniz.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Aşağıdaki özellikler, önceki örneği nasıl zaman uyumsuz bir yöntem yaptığını özetler:

- Yöntem imzası bir `async` değiştiricisi içerir.
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - yönteminizin `TResult`tür olan bir return ifadesine sahipseniz <xref:System.Threading.Tasks.Task%601>.
  - yönteminizin Return bildirisi yoksa veya işleneni olmayan bir return ifadesine sahipse <xref:System.Threading.Tasks.Task>.
  - zaman uyumsuz bir olay işleyicisi yazıyorsanız `void`.
  - `GetAwaiter` yöntemi olan diğer herhangi bir tür (7,0 ile C# başlayarak).

  Daha fazla bilgi için bkz. [dönüş türleri ve parametreleri](#BKMK_ReturnTypesandParameters) bölümü.

- Yöntemi genellikle, beklenen zaman uyumsuz işlem tamamlanana kadar yöntemin devam edemediği bir noktayı işaretleyen en az bir `await` ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.

.NET Framework önceki sürümlerinde zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Zaman uyumsuz bir yöntemde ne olur?

Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagramda süreç boyunca size yol gösterir:

![Zaman uyumsuz bir programı izleme](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "NavigationTrace")

Diyagramdaki sayılar, Kullanıcı "Başlat" düğmesine tıkladığında başlatılan aşağıdaki adımlara karşılık gelir.

1. Bir olay işleyicisi, `AccessTheWebAsync` zaman uyumsuz yöntemini çağırır ve bekler.

2. `AccessTheWebAsync` bir <xref:System.Net.Http.HttpClient> örneği oluşturur ve bir Web sitesinin içeriğini bir dize olarak indirmek için <xref:System.Net.Http.HttpClient.GetStringAsync%2A> zaman uyumsuz yöntemini çağırır.

3. `GetStringAsync` ilerleme durumunu askıya alan bir sorun oluşur. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemeyi önlemek için `GetStringAsync`, `AccessTheWebAsync` çağıranına denetim verir.

     `GetStringAsync`, `TResult` bir dize olduğu ve `AccessTheWebAsync` görevi `getStringTask` değişkenine atayan bir <xref:System.Threading.Tasks.Task%601>döndürür. Görev, iş tamamlandığında gerçek bir dize değeri üretme taahhüdünde `GetStringAsync`çağrısı için devam eden işlemi temsil eder.

4. `getStringTask` henüz beklenmediği için, `AccessTheWebAsync` `GetStringAsync`son sonucuna bağlı olmayan diğer çalışmalarla devam edebilir. Bu iş, zaman uyumlu Yöntem `DoIndependentWork`çağrısıyla temsil edilir.

5. `DoIndependentWork`, işini yapan ve çağırana döndüren zaman uyumlu bir yöntemdir.

6. `AccessTheWebAsync`, `getStringTask`bir sonuç olmadan yapabilmeden iş dışında çalışıyor. `AccessTheWebAsync`, indirilen dizenin uzunluğunu hesaplamak ve döndürmek istiyor, ancak yöntem dizeye gelinceye kadar bu değeri hesaplayamaz.

     Bu nedenle, `AccessTheWebAsync` ilerlemesini askıya almak ve denetimi `AccessTheWebAsync`çağıran yönteme bırakmak için bir Await işleci kullanır. `AccessTheWebAsync`, çağırana bir `Task<int>` döndürür. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.

    > [!NOTE]
    > `GetStringAsync` (ve bu nedenle `getStringTask`) `AccessTheWebAsync` önünde bekleden önce tamamlanırsa denetim `AccessTheWebAsync`kalır. Çağrılan zaman uyumsuz işlem (`getStringTask`) zaten tamamlanmışsa ve `AccessTheWebAsync` nihai sonucu beklemek zorunda değilse, `AccessTheWebAsync` askıya alma ve sonra geri dönme gideri harcanacaktır.

     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Çağıran, sonucu beklemeden önce `AccessTheWebAsync` sonucu üzerinde bağlı olmayan başka işler, veya arayanın anında bekleme yapması istenebilir.   Olay işleyicisi `AccessTheWebAsync`bekliyor ve `AccessTheWebAsync` `GetStringAsync`bekliyor.

7. `GetStringAsync` tamamlanır ve bir dize sonucu üretir. Dize sonucu, `GetStringAsync` çağrısı tarafından, bekleneceğiniz şekilde döndürülmedi. (Metodun adım 3 ' te bir görevi zaten döndürdüğünü unutmayın.) Bunun yerine, dize sonucu, yönteminin tamamlandığını temsil eden görevde saklanır `getStringTask`. Await işleci `getStringTask`sonucu alır. Atama ekstresi, alınan sonucu `urlContents`atar.

8. `AccessTheWebAsync` dize sonucu olduğunda, yöntemi dizenin uzunluğunu hesaplayabilir. `AccessTheWebAsync` çalışması da tamamlanır ve bekleyen olay işleyicisi de sürdürülür. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.
Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışıC#()](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>API zaman uyumsuz yöntemleri

Zaman uyumsuz programlamayı destekleyen `GetStringAsync` gibi yöntemlerin nerede bulunacağını merak ediyor olabilirsiniz. .NET Framework 4,5 veya üzeri ve .NET Core `async` ve `await`birlikte çalışan birçok üye içerir. Bunları, üye adına eklenen "Async" sonekiyle ve <xref:System.Threading.Tasks.Task> ya da <xref:System.Threading.Tasks.Task%601>dönüş türlerine göre tanıyabilirsiniz. Örneğin `System.IO.Stream` sınıfı, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>ve <xref:System.IO.Stream.WriteAsync%2A> zaman uyumlu yöntemler <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>ve <xref:System.IO.Stream.Write%2A>gibi yöntemleri içerir.

Windows Çalışma Zamanı ayrıca Windows uygulamalarında `async` ve `await` ile kullanabileceğiniz birçok yöntem içerir. Daha fazla bilgi için bkz. UWP geliştirme için [Iş parçacığı ve zaman uyumsuz programlama](/windows/uwp/threading-async/) ve [zaman uyumsuz programlama (Windows Mağazası uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) ve hızlı başlangıç: Windows çalışma zamanı önceki sürümlerini kullanıyorsanız, [ C# veya Visual Basic zaman uyumsuz API 'leri çağırma](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) .

## <a name="BKMK_Threads"></a>Akışları

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Zaman uyumsuz bir yöntemde `await` ifadesi, beklenen görev çalışırken geçerli iş parçacığını engellemez. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.

`async` ve `await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. CPU 'ya bağlanan işi arka plan iş parçacığına taşımak için <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> kullanabilirsiniz, ancak arka plan iş parçacığı yalnızca sonuçların kullanılabilir hale gelmesini bekleyen bir işlem konusunda yardımcı olmaz.

Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Özellikle, bu yaklaşım, kod daha basit olduğundan ve yarış koşullarına karşı koruma sağlamak zorunda olmadığınızdan g/ç 'ye bağlanacak işlemler için <xref:System.ComponentModel.BackgroundWorker> sınıfından daha iyidir. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi ile birlikte zaman uyumsuz programlama, CPU 'ya bağlanan işlemler için <xref:System.ComponentModel.BackgroundWorker> daha iyidir, çünkü zaman uyumsuz programlama, kodunuzun iş parçacığı temelli olarak `Task.Run` aktardığı işten kod çalıştırmanın koordinasyon ayrıntılarını ayırır.

## <a name="BKMK_AsyncandAwait"></a>Async ve await

[Zaman](../../../language-reference/keywords/async.md) uyumsuz değiştirici kullanarak bir yöntemin zaman uyumsuz bir yöntem olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirirsiniz.

- İşaretlenen zaman uyumsuz yöntem, askıya alma noktaları belirlemek için [await](../../../language-reference/operators/await.md) kullanabilir. `await` işleci derleyiciye zaman uyumsuz yöntemin, zaman uyumsuz işlem tamamlanana kadar bu noktanın ötesine devam edemeyeceğini söyler. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.

     Bir `await` ifadesinde zaman uyumsuz bir yöntemin askıya alınması yöntemden bir çıkış oluşturmaz ve `finally` blokları çalışmaz.

- İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.

Zaman uyumsuz bir yöntem, genellikle bir `await` işlecinin bir veya daha fazla örneğini içerir, ancak `await` ifadelerinin yokluğu bir derleyici hatasına neden olmaz. Zaman uyumsuz bir yöntem, askıya alma noktasını işaretlemek için `await` işleci kullanmıyorsa, yöntem, `async` değiştiriciye rağmen zaman uyumlu bir yöntem olarak yürütülür. Derleyici bu tür yöntemler için bir uyarı verir.

`async` ve `await` bağlamsal anahtar sözcüklerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Dönüş türleri ve parametreleri

Zaman uyumsuz bir yöntem genellikle bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>döndürür. Zaman uyumsuz bir yöntem içinde, başka bir zaman uyumsuz metoda yapılan çağrıdan döndürülen bir göreve `await` işleci uygulanır.

Yöntem `TResult`türünde bir işleneni belirten bir [`return`](../../../language-reference/keywords/return.md) bildirisini içeriyorsa, dönüş türü olarak <xref:System.Threading.Tasks.Task%601> belirtirsiniz.

Metodun Return ifadesine sahip olmaması veya bir işleneni döndürmeyen bir return ifadesine sahip olması durumunda dönüş türü olarak <xref:System.Threading.Tasks.Task> kullanırsınız.

7,0 ile C# başlayarak, türün bir `GetAwaiter` yöntemi içermesi şartıyla, başka bir dönüş türü de belirtebilirsiniz. <xref:System.Threading.Tasks.ValueTask%601> bu tür bir örnektir. [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketinde kullanılabilir.

Aşağıdaki örnek, bir <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>döndüren bir yöntemi nasıl bildirmenizi ve çağırakullanacağınızı gösterir:

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

Zaman uyumsuz bir yöntem `void` dönüş türüne de sahip olabilir. Bu dönüş türü, öncelikle `void` dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.

`void` dönüş türüne sahip bir zaman uyumsuz yöntem beklenemez ve void döndüren bir yöntemi çağıran yöntemin aldığı özel durumları yakalayabilir.

Zaman uyumsuz bir yöntem [içinde](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) veya [Out](../../../language-reference/keywords/out-parameter-modifier.md) parametrelerini bildiremez, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir. Benzer şekilde, zaman uyumsuz bir yöntem başvuruya göre değer döndüremez, ancak başvuru dönüş değerleri içeren yöntemler çağırabilir.

Daha fazla bilgi ve örnek için bkz. [Async Return TypesC#()](./async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [try-catch](../../../language-reference/keywords/try-catch.md).

Windows Çalışma Zamanı programlamadaki zaman uyumsuz API 'Ler, görevlerle benzer olan aşağıdaki dönüş türlerinden birine sahiptir:

- <xref:System.Threading.Tasks.Task%601> karşılık gelen <xref:Windows.Foundation.IAsyncOperation%601>
- <xref:System.Threading.Tasks.Task> karşılık gelen <xref:Windows.Foundation.IAsyncAction>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Kural gereği, genellikle zaman uyumsuz türler (örn. `Task`, `Task<T>`, `ValueTask`, `ValueTask<T>`) döndüren yöntemler "Async" ile biten adlara sahip olmalıdır. Zaman uyumsuz bir işlem Başlatan ancak bir awasever türü döndürmeyen Yöntemler, "Async" ile biten adlara sahip olmamalıdır, ancak bu yöntemin işlemin sonucunu döndürmeyeceğini veya oluşturmadığını önermek için "BEGIN", "Start" ya da başka bir fiil ile başlayabilir.

Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, `Button1_Click`gibi yaygın olay işleyicilerini yeniden adlandırmamanız gerekir.

## <a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örnek: Web 'e erişme yolu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Önceki izlenecek yolu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ekler. `WhenAll` kullanımı, tüm indirmeleri aynı anda başlatır.||
|[Async ve await (C#) kullanarak birden çok web isteğini paralel hale getirme](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örnek: birden çok Web Isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Zaman uyumsuz dönüş türleriC#()](./async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||
|[Zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Async örneği: zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> [zaman uyumsuz bir görevi veya görev listesini Iptal etme - (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)<br />zaman [uyumsuz görevleri bir süre sonra iptal - (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [tamamlandıktan sonra kalan zaman uyumsuz görevleri Iptal et (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa (C#) işleyin](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)](./handling-reentrancy-in-async-apps.md)|Çalışırken etkin bir zaman uyumsuz işlemin yeniden başlatılma durumlarının nasıl işleneceğini gösterir.||
|[WhenAny: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.Tasks.Task.WhenAny%2A> kullanabilmeniz için, Windows Çalışma Zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ile Windows Çalışma Zamanı arasında köprü oluşturma (AsTask ve WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Zaman Uyumsuz İptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.CancellationTokenSource> kullanabilmeniz için, Windows Çalışma Zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ve Windows Çalışma Zamanı arasında köprü oluşturma (AsTask & Iptali)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya erişimi için Async Kullanma (C#)](./using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Desenler <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> türlerini temel alır.||
|[Channel 9 ' da zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="BKMK_CompleteExample"></a>Örnek Tamam

Aşağıdaki kod, bu makalede ele alınan WPF uygulamasından gelen *MainWindow.xaml.cs* dosyasıdır. Örneği zaman uyumsuz [örnek: "Async ve await Ile zaman uyumsuz programlama" kaynağından](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/)indirebilirsiniz.

[!code-csharp[async](~/samples/async/async-and-await/cs/MainWindow.xaml.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Zaman uyumsuz programlama](../../../async.md)
- [Zaman uyumsuz genel bakış](../../../../standard/async.md)
