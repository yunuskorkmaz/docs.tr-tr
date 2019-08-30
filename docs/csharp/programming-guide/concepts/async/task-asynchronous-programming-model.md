---
title: Async ve await (C#) Ile görev zaman uyumsuz programlama MODELI (TAP)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: abe1ab777a17ba8cba15a27b02d389a9ede3caf0
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167895"
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

' Deki C# [Async](../../../language-reference/keywords/async.md) ve [await](../../../language-reference/operators/await.md) anahtar sözcükleri zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak, bir zaman uyumlu Yöntem oluştururken neredeyse kolayca zaman uyumsuz bir yöntem oluşturmak için .NET Framework, .NET Core veya Windows Çalışma Zamanı kaynaklarını kullanabilirsiniz. `async` Anahtar sözcüğünü kullanarak tanımladığınız zaman uyumsuz yöntemler, *zaman uyumsuz yöntemler*olarak adlandırılır.

Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır.

Bu konunun sonunda bir Windows Presentation Foundation (WPF) örnek dosyası bulabilirsiniz ve örneği [zaman uyumsuz örnekten indirebilirsiniz: "Async ve await ile zaman uyumsuz programlama"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c)örneği.

```csharp
async Task<int> AccessTheWebAsync()
{
    // You need to add a reference to System.Net.Http to declare client.
    using (HttpClient client = new HttpClient())
    {
        Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");

        DoIndependentWork();

        string urlContents = await getStringTask;

        return urlContents.Length;
    }
}
```

Yukarıdaki örnekten birkaç uygulama öğrenebilirsiniz. Yöntem imzasıyla başlayın. `async` Değiştiricisini içerir. Dönüş türü `Task<int>` (daha fazla seçenek için "dönüş türleri" bölümüne bakın). Yöntem adı içinde `Async`biter. Yönteminin gövdesinde, `GetStringAsync` bir `Task<string>`döndürür. Yani, bir `string` görev ( `await` `urlContents`) alacağınız zaman.  Görevi kapatmadan önce, `string` `GetStringAsync`' a bağımlı olmayan iş yapabilirsiniz.

`await` Operatöre yakın ilgilenilmesi için ödeme yapın. Askıya alır `AccessTheWebAsync`;

- `AccessTheWebAsync`tamamlanana kadar `getStringTask` devam edilemiyor.
- Bu arada, Denetim çağırana `AccessTheWebAsync`döner.
- Tamamlandığında `getStringTask` , Denetim burada sürdürülür.
- İşleci bundan sonra `string` sonucu`getStringTask`alır. `await`

Return ifadesinde bir tamsayı sonucu belirtilir. Bekleyen `AccessTheWebAsync` tüm yöntemler uzunluk değerini alır.

`AccessTheWebAsync` Çağrısı`GetStringAsync` ve tamamlanmasını bekleme arasında yapabilecek herhangi bir işi yoksa, aşağıdaki tek deyime çağırarak ve bekleyen kodunuzu basitleştirebilirsiniz.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com");
```

Aşağıdaki özellikler, önceki örneği neyin zaman uyumsuz hale getirdiğini özetler.

- Yöntem imzası bir `async` değiştirici içerir.

- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.

- Dönüş türü aşağıdaki türlerden biridir:

  - <xref:System.Threading.Tasks.Task%601>yönteminizin işlenenin türü `TResult`olan bir return bildirisi varsa.

  - <xref:System.Threading.Tasks.Task>yönteminizin Return bildirisi yoksa veya işleneni olmayan bir return ifadesine sahip.

  - `void`zaman uyumsuz bir olay işleyicisi yazıyorsanız.

  - Yöntemi olan diğer herhangi bir `GetAwaiter` tür (7,0 ile C# başlar).

  Daha fazla bilgi için bkz. [dönüş türleri ve parametreleri](#BKMK_ReturnTypesandParameters) bölümü.

- Yöntemi genellikle, beklenen zaman uyumsuz işlem `await` tamamlanana kadar yöntemin devam edemediği bir noktayı işaretleyen en az bir ifade içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.

.NET Framework önceki sürümlerinde zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Zaman uyumsuz bir yöntemde ne olur?

Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagram işlem boyunca size yol gösterecektir.

![Zaman uyumsuz bir programı izleme](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "Navigationtrace")

Diyagramdaki sayılar, Kullanıcı "Başlat" düğmesine tıkladığında başlatılan aşağıdaki adımlara karşılık gelir.

1. Bir olay işleyicisi, `AccessTheWebAsync` zaman uyumsuz yöntemini çağırır ve bekler.

2. `AccessTheWebAsync`bir örnek oluşturur ve bir Web <xref:System.Net.Http.HttpClient.GetStringAsync%2A> sitesinin içeriklerini dize olarak indirmek için zaman uyumsuz yöntemi çağırır. <xref:System.Net.Http.HttpClient>

3. İçinde `GetStringAsync` ilerleme durumunu askıya alan bir sorun var. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları `GetStringAsync` engellemeyi önlemek için, kendi `AccessTheWebAsync`çağıranına denetim verir.

     `GetStringAsync`öğesini döndürür, burada `TResult` bir dizedir ve `AccessTheWebAsync` görevi `getStringTask` değişkenine atar. <xref:System.Threading.Tasks.Task%601> Görev, iş tamamlandığında gerçek bir dize değeri üretme taahhüdünde `GetStringAsync`, çağrısı için devam eden işlemi temsil eder.

4. Henüz `getStringTask` beklenmediği için, `AccessTheWebAsync` nihai sonuca `GetStringAsync`bağlı olmayan diğer çalışmalarla devam edebilir. Bu iş, zaman uyumlu Yöntem `DoIndependentWork`çağrısıyla temsil edilir.

5. `DoIndependentWork`, işini yapan ve çağırana döndüren zaman uyumlu bir yöntemdir.

6. `AccessTheWebAsync`, uygulamasından `getStringTask`bir sonuç olmadan yapabilmeden iş dışında çalışıyor. `AccessTheWebAsync`ardından, indirilen dizenin uzunluğunu hesaplamak ve döndürmek ister, ancak yöntem dizeye gelinceye kadar bu değeri hesaplayamaz.

     Bu nedenle `AccessTheWebAsync` , ilerleme durumunu askıya almak ve denetimi çağıran `AccessTheWebAsync`yönteme eklemek için bir Await işleci kullanır. `AccessTheWebAsync``Task<int>` çağırana döndürür. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.

    > [!NOTE]
    > (Ve bu nedenle `getStringTask`), bekleden önce `AccessTheWebAsync` tamamlanırsa, denetim içinde `AccessTheWebAsync`kalır. `GetStringAsync` Çağrılan zaman uyumsuz işlem ( `AccessTheWebAsync` `getStringTask`) zaten tamamlanmışsa ve `AccessTheWebAsync` nihai sonucu beklemek zorunda değilse, askıya alma ve daha sonra geri dönme gideri harcanacaktır.

     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Çağıran, sonucu `AccessTheWebAsync` beklemeden önce sonucu kendisine bağlı olmayan başka bir iş ya da çağıran hemen bekleme edebilir.   Olay işleyicisi için `AccessTheWebAsync`bekliyor ve `AccessTheWebAsync` bekliyor `GetStringAsync`.

7. `GetStringAsync`tamamlar ve bir dize sonucu üretir. Dize sonucu, bekleneceğiniz şekilde çağrısı `GetStringAsync` tarafından döndürülmedi. (Metodun adım 3 ' te bir görevi zaten döndürdüğünü unutmayın.) Bunun yerine, dize sonucu, yönteminin `getStringTask`tamamlandığını temsil eden görevde saklanır. Await işleci sonucunu `getStringTask`alır. Atama ekstresi alındı sonucunu öğesine `urlContents`atar.

8. Dize `AccessTheWebAsync` sonucu olduğunda, yöntemi dizenin uzunluğunu hesaplayabilir. Bu `AccessTheWebAsync` durumda, çalışması da tamamlanır ve bekleyen olay işleyicisi sürdürülebilirler. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.
Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışıC#()](./control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>API zaman uyumsuz yöntemleri

Zaman uyumsuz programlamayı destekleyen gibi `GetStringAsync` yöntemlerin nerede bulunacağını merak ediyor olabilirsiniz. .NET Framework 4,5 veya üzeri ve .NET Core, ve `async` `await`ile çalışan birçok üye içerir. Bunları, üye adına eklenen "Async" sonekine ve <xref:System.Threading.Tasks.Task> ya <xref:System.Threading.Tasks.Task%601>da dönüş türlerine göre tanıyabilirsiniz. Örneğin `System.IO.Stream` , <xref:System.IO.Stream.CopyTo%2A>sınıfı <xref:System.IO.Stream.CopyToAsync%2A> <xref:System.IO.Stream.Read%2A>, <xref:System.IO.Stream.ReadAsync%2A>, ve gibi yöntemleri, ve ile<xref:System.IO.Stream.Write%2A>zaman uyumlu yöntemleri içerir. <xref:System.IO.Stream.WriteAsync%2A>

Windows çalışma zamanı ayrıca Windows uygulamalarında ve `async` `await` ile kullanabileceğiniz birçok yöntem içerir. Daha fazla bilgi için bkz. UWP geliştirme ve [zaman uyumsuz programlama (Windows Mağazası uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) ve [hızlı başlangıç için [iş parçacığı oluşturma ve zaman uyumsuz programlama](/windows/uwp/threading-async/) : Windows çalışma zamanı önceki sürümlerini kullanıyorsanız C# , veya](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) Visual Basic zaman uyumsuz API 'leri çağırma.

## <a name="BKMK_Threads"></a>Akışları

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Zaman `await` uyumsuz yöntemdeki bir ifade, beklenen görev çalışırken geçerli iş parçacığını engellemez. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.

`async` Ve`await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. CPU 'ya bağlanan <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> işi arka plan iş parçacığına taşımak için kullanabilirsiniz, ancak arka plan iş parçacığı yalnızca sonuçların kullanılabilir hale gelmesini bekleyen bir işlem konusunda yardımcı olmaz.

Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Özellikle, bu yaklaşım, kod daha basit olduğundan <xref:System.ComponentModel.BackgroundWorker> ve yarış koşullarına karşı koruma sağlamak zorunda olmadığınızdan g/ç ile bağlantılı işlemler için olan sınıftan daha iyidir. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> Yöntemi ile birlikte zaman uyumsuz programlama <xref:System.ComponentModel.BackgroundWorker> , zaman uyumsuz programlama, `Task.Run` kodunuzun çalıştırılmasına ilişkin koordinasyon ayrıntılarını, ' a aktaran iş parçacığı.

## <a name="BKMK_AsyncandAwait"></a>Async ve await

[Zaman](../../../language-reference/keywords/async.md) uyumsuz değiştirici kullanarak bir yöntemin zaman uyumsuz bir yöntem olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirirsiniz.

- İşaretlenen zaman uyumsuz yöntem, askıya alma noktaları belirlemek için [await](../../../language-reference/operators/await.md) kullanabilir. `await` İşleci, zaman uyumsuz yöntemin, beklenen zaman uyumsuz işlem tamamlanana kadar bu noktanın ötesine devam edemeyeceğini derleyiciye bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.

     Bir `await` ifadede zaman uyumsuz bir yöntemin askıya alınması yöntemden bir çıkış oluşturmaz ve `finally` bloklar çalıştırılmaz.

- İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.

Zaman uyumsuz bir yöntem, genellikle bir `await` işlecin bir veya daha fazla örneğini içerir, ancak `await` ifadelerin yokluğu bir derleyici hatasına neden olmaz. Zaman uyumsuz bir yöntem, askıya alma `await` noktasını işaretlemek için bir operatör kullanmıyorsa Yöntem, `async` değiştiriciye rağmen zaman uyumlu bir yöntem olarak yürütülür. Derleyici bu tür yöntemler için bir uyarı verir.

`async`ve `await` bağlamsal anahtar sözcüklerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [async](../../../language-reference/keywords/async.md)

- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Dönüş türleri ve parametreleri

Zaman uyumsuz bir yöntem genellikle bir <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>veya döndürür. Zaman uyumsuz bir yöntemde, bir `await` işleç, başka bir zaman uyumsuz metoda yapılan çağrıdan döndürülen bir göreve uygulanır.

Yöntemi, <xref:System.Threading.Tasks.Task%601> türünde [`return`](../../../language-reference/keywords/return.md) bir`TResult`işleneni belirten bir ifade içeriyorsa, dönüş türü olarak belirtirsiniz.

Metodun Return <xref:System.Threading.Tasks.Task> ifadesine sahip olmaması veya bir işleneni döndürmeyen bir return ifadesine sahip olması durumunda dönüş türü olarak kullanırsınız.

7,0 ile C# başlayarak, türün bir yöntemi içermesi şartıyla, başka bir `GetAwaiter` dönüş türü de belirtebilirsiniz. <xref:System.Threading.Tasks.ValueTask%601>Bu tür bir örnektir. [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketinde kullanılabilir.

Aşağıdaki örnek, bir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task>veya döndüren bir yöntemi nasıl bildirmenizi ve çağırılacağını gösterir.

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

Zaman uyumsuz bir yöntemin `void` dönüş türü de olabilir. Bu dönüş türü öncelikle bir `void` dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.

`void` Dönüş türüne sahip bir zaman uyumsuz yöntem beklenemez ve void döndüren bir yöntem çağıran yöntemin aldığı özel durumları yakalayabilir.

Zaman uyumsuz bir yöntem [içinde](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) veya [Out](../../../language-reference/keywords/out-parameter-modifier.md) parametrelerini bildiremez, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir. Benzer şekilde, zaman uyumsuz bir yöntem başvuruya göre değer döndüremez, ancak başvuru dönüş değerleri içeren yöntemler çağırabilir.

Daha fazla bilgi ve örnek için bkz. [Async Return TypesC#()](./async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [try-catch](../../../language-reference/keywords/try-catch.md).

Windows Çalışma Zamanı programlamadaki zaman uyumsuz API 'Ler, görevlerle benzer olan aşağıdaki dönüş türlerinden birine sahiptir:

- <xref:Windows.Foundation.IAsyncOperation%601>öğesine karşılık gelen<xref:System.Threading.Tasks.Task%601>

- <xref:Windows.Foundation.IAsyncAction>öğesine karşılık gelen<xref:System.Threading.Tasks.Task>

- <xref:Windows.Foundation.IAsyncActionWithProgress%601>

- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Kurala göre, yaygın olarak kullanılan `Task`türleri (ör. `Task<T>` `ValueTask` `ValueTask<T>`,,,) döndüren yöntemlerin "Async" ile biten adları olmalıdır. Zaman uyumsuz bir işlem Başlatan ancak bir awasever türü döndürmeyen Yöntemler, "Async" ile biten adlara sahip olmamalıdır, ancak bu yöntemin işlemin sonucunu döndürmeyeceğini veya oluşturmadığını önermek için "BEGIN", "Start" ya da başka bir fiil ile başlayabilir.

Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, gibi yaygın olay işleyicilerini `Button1_Click`yeniden adlandırmamanız gerekir.

## <a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örnek: Web 'e erişme Kılavuzu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Nasıl yapılır: Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Önceki <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> izlenecek yolu ekler. Öğesinin `WhenAll` kullanımı, tüm indirmeleri aynı anda başlatır.||
|[Nasıl yapılır: Async ve await (C#) kullanarak birden çok web isteğini paralel hale getirme](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örnek: Birden çok Web Isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Zaman uyumsuz dönüş türleriC#()](./async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||
|[Zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Zaman uyumsuz örnek: Zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> - [Zaman uyumsuz bir görevi veya görev listesini iptal etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Zaman uyumsuz görevleri bir süre sonra iptal et (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [Tamamlandıktan sonra kalan zaman uyumsuz görevleri iptal et (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa (C#) işleyin](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: Uygulamanızda ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)](./handling-reentrancy-in-async-apps.md)|Çalıştırıldığı sırada etkin bir zaman uyumsuz işlemin yeniden başlatıldığı durumların nasıl işleneceğini gösterir.||
|[WhenAny .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Bir Windows çalışma zamanı yöntemiyle kullanabilmeniz <xref:System.Threading.Tasks.Task.WhenAny%2A> için, Windows çalışma zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ve Windows Çalışma Zamanı arasında köprü oluşturma (AsTask ve WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Zaman uyumsuz Iptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Bir Windows çalışma zamanı yöntemiyle kullanabilmeniz <xref:System.Threading.CancellationTokenSource> için, Windows çalışma zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ve Windows Çalışma Zamanı arasında köprü oluşturma (AsTask & Iptali)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya erişimi için Async Kullanma (C#)](./using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Model <xref:System.Threading.Tasks.Task> ve<xref:System.Threading.Tasks.Task%601> türlerini temel alır.||
|[Channel 9 ' da zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="BKMK_CompleteExample"></a>Örnek Tamam

Aşağıdaki kod, bu konunun ele aldığı Windows Presentation Foundation (WPF) uygulamasındaki MainWindow.xaml.cs dosyasıdır. Örneği [zaman uyumsuz örnekten indirebilirsiniz: "Async ve await ile zaman uyumsuz programlama"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c)örneği.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http;
using System.Net.Http;

namespace AsyncFirstExample
{
    public partial class MainWindow : Window
    {
        // Mark the event handler with async so you can use await in it.
        private async void StartButton_Click(object sender, RoutedEventArgs e)
        {
            // Call and await separately.
            //Task<int> getLengthTask = AccessTheWebAsync();
            //// You can do independent work here.
            //int contentLength = await getLengthTask;

            int contentLength = await AccessTheWebAsync();

            resultsTextBox.Text +=
                $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }

        // Three things to note in the signature:
        //  - The method has an async modifier.
        //  - The return type is Task or Task<T>. (See "Return Types" section.)
        //    Here, it is Task<int> because the return statement returns an integer.
        //  - The method name ends in "Async."
        async Task<int> AccessTheWebAsync()
        {
            // You need to add a reference to System.Net.Http to declare client.
            using (HttpClient client = new HttpClient())
            {
                    // GetStringAsync returns a Task<string>. That means that when you await the
                    // task you'll get a string (urlContents).
                    Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");

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
        }

        void DoIndependentWork()
        {
            resultsTextBox.Text += "Working . . . . . . .\r\n";
        }
    }
}

// Sample Output:

// Working . . . . . . .

// Length of the downloaded string: 25035.
```

## <a name="see-also"></a>Ayrıca bkz.

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Zaman uyumsuz programlama](../../../async.md)
- [Zaman uyumsuz genel bakış](../../../../standard/async.md)
 