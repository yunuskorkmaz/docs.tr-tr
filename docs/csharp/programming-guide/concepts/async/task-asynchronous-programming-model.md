---
title: Async ve await (C#) ile görev zaman uyumsuz programlama (TAP) modeli
description: Görev tabanlı zaman uyumsuz programlamayı ne zaman ve nasıl kullanacağınızı, C# ' de zaman uyumsuz programlamaya basitleştirilmiş bir yaklaşım olduğunu öğrenin.
ms.date: 08/19/2020
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 5e85b99025b31e205c66468d4bd886701cbaea17
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812100"
---
# <a name="task-asynchronous-programming-model"></a>Zaman uyumsuz görev programlama modeli

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.

[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) , .NET Framework 4,5 ve üzeri, .NET Core ve Windows çalışma zamanı zaman uyumsuz destekten yararlanan, zaman uyumsuz programlama ile basitleştirilmiş bir yaklaşım getirmiştir. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.

Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a> Zaman uyumsuz, yanıt hızını geliştirir

Asynchrony, Web erişimi gibi olası engelleme olasılığı olan etkinlikler için gereklidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Bu tür bir etkinlik zaman uyumlu bir işlemde engellenirse, uygulamanın tamamının beklemesi gerekir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.

Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET ve Windows Çalışma Zamanı listelenen API 'Ler, zaman uyumsuz programlamayı destekleyen yöntemler içerir.

| Uygulama alanı | Zaman uyumsuz yöntemleriyle .NET türleri | Zaman uyumsuz yöntemlere sahip Windows Çalışma Zamanı türleri |
|--|--|--|
| Web erişimi | <xref:System.Net.Http.HttpClient> | <xref:Windows.Web.Http.HttpClient?displayProperty=nameWithType> <br> <xref:Windows.Web.Syndication.SyndicationClient> |
| Dosyalarla çalışma | <xref:System.Text.Json.JsonSerializer> <br> <xref:System.IO.StreamReader> <br> <xref:System.IO.StreamWriter> <br> <xref:System.Xml.XmlReader> <br> <xref:System.Xml.XmlWriter> | <xref:Windows.Storage.StorageFile> |
| Görüntülerle çalışma |  | <xref:Windows.Media.Capture.MediaCapture> <br> <xref:Windows.Graphics.Imaging.BitmapEncoder> <br> <xref:Windows.Graphics.Imaging.BitmapDecoder> |
| WCF programlama | [Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md) |  |

Tüm kullanıcı arabirimi ilişkili faaliyetler genellikle tek bir iş parçacığını paylaştığından, zaman uyumsuzluğun kullanıcı arabirimi iş parçacığına erişen uygulamalar için özellikle önem taşıdığı kanıtlanmıştır. Herhangi bir işlem zaman uyumlu bir uygulamada engellenirse, tümü engellenir. Uygulamanız yanıt vermiyordur ve bunu uygulamanın beklediği değil de başarısız olduğu şeklinde yorumlayabilirsiniz.

Zaman uyumsuz yöntemleri kullandığınızda, uygulama arabirime yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da bitmesini beklemek istemiyorsanız kapatabilirsiniz.

Zaman uyumsuz tabanlı yaklaşım otomatik bir iletimin eşdeğerini, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarından yararlanabilirsiniz, buna rağmen geliştiricinin daha az çaba sarf etmesi gerekir.

## <a name="async-methods-are-easy-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a> Zaman uyumsuz yöntemlerin yazılması kolaydır

Async [ve](../../../language-reference/keywords/async.md) [await](../../../language-reference/operators/await.md) anahtar sözcükleri, zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak, bir zaman uyumlu Yöntem oluştururken neredeyse kolayca zaman uyumsuz bir yöntem oluşturmak için .NET Framework, .NET Core veya Windows Çalışma Zamanı içindeki kaynakları kullanabilirsiniz. Anahtar sözcüğünü kullanarak tanımladığınız zaman uyumsuz yöntemler, `async` *zaman uyumsuz yöntemler*olarak adlandırılır.

Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Koddaki neredeyse her şey size tanıdık gelmelidir.

Zaman [uyumsuz programlamayı, C# ' de zaman uyumsuz ve await ile](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs)karşıdan yüklenebilecek bir bütün WINDOWS PRESENTATION FOUNDATION (WPF) örneği bulabilirsiniz.

:::code language="csharp" source="snippets/access-web/Program.cs" id="ControlFlow":::

Yukarıdaki örnekten birkaç uygulama öğrenebilirsiniz. Yöntem imzasıyla başlayın. `async`Değiştiricisini içerir. Dönüş türü `Task<int>` (daha fazla seçenek için "dönüş türleri" bölümüne bakın). Yöntem adı içinde biter `Async` . Yönteminin gövdesinde, `GetStringAsync` bir döndürür `Task<string>` . Yani, `await` bir görev `string` () alacağınız zaman `contents` . Görevi kapatmadan önce, ' a bağımlı olmayan iş yapabilirsiniz `string` `GetStringAsync` .

Operatöre yakın ilgilenilmesi için ödeme yapın `await` . Askıya alınır `GetUrlContentLengthAsync` :

- `GetUrlContentLengthAsync` tamamlanana kadar devam edilemiyor `getStringTask` .
- Bu arada, Denetim çağırana döner `GetUrlContentLengthAsync` .
- Tamamlandığında, Denetim burada sürdürülür `getStringTask` .
- `await`İşleci bundan sonra sonucu alır `string` `getStringTask` .

Return ifadesinde bir tamsayı sonucu belirtilir. Bekleyen tüm yöntemler `GetUrlContentLengthAsync` uzunluk değerini alır.

`GetUrlContentLengthAsync`Çağrısı ve tamamlanmasını bekleme arasında yapabilecek herhangi bir işi yoksa `GetStringAsync` , aşağıdaki tek deyime çağırarak ve bekleyen kodunuzu basitleştirebilirsiniz.

```csharp
string contents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Aşağıdaki özellikler, önceki örneği nasıl zaman uyumsuz bir yöntem yaptığını özetler:

- Yöntem imzası bir değiştirici içerir `async` .
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - <xref:System.Threading.Tasks.Task%601> yönteminizin işlenenin türü olan bir return bildirisi varsa `TResult` .
  - <xref:System.Threading.Tasks.Task> yönteminizin Return bildirisi yoksa veya işleneni olmayan bir return ifadesine sahip.
  - `void` zaman uyumsuz bir olay işleyicisi yazıyorsanız.
  - Metodu olan diğer herhangi bir tür `GetAwaiter` (C# 7,0 ile başlar).

  Daha fazla bilgi için bkz. [dönüş türleri ve parametreleri](#BKMK_ReturnTypesandParameters) bölümü.

- Yöntemi genellikle, `await` beklenen zaman uyumsuz işlem tamamlanana kadar yöntemin devam edemediği bir noktayı işaretleyen en az bir ifade içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.

Önceki .NET Framework sürümlerindeki zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Zaman uyumsuz bir yöntemde ne olur?

Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagramda süreç boyunca size yol gösterir:

:::image type="content" source="media/task-asynchronous-programming-model/navigation-trace-async-program.png" alt-text="Zaman uyumsuz denetim akışının izleme gezintisi" lightbox="media/task-asynchronous-programming-model/navigation-trace-async-program.png":::

Diyagramdaki sayılar, bir çağırma yöntemi zaman uyumsuz yöntemi çağırdığında başlatılan aşağıdaki adımlara karşılık gelir.

1. Çağırma yöntemi, `GetUrlContentLengthAsync` zaman uyumsuz metodu çağırır ve bekler.

1. `GetUrlContentLengthAsync` bir <xref:System.Net.Http.HttpClient> örnek oluşturur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2A> bir Web sitesinin içeriklerini dize olarak indirmek için zaman uyumsuz yöntemi çağırır.

1. İçinde `GetStringAsync` ilerleme durumunu askıya alan bir sorun var. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemeyi önlemek için, `GetStringAsync` kendi çağıranına denetim verir `GetUrlContentLengthAsync` .

     `GetStringAsync` öğesini döndürür <xref:System.Threading.Tasks.Task%601> , burada `TResult` bir dizedir ve `GetUrlContentLengthAsync` görevi `getStringTask` değişkenine atar. Görev, `GetStringAsync` iş tamamlandığında gerçek bir dize değeri üretme taahhüdünde, çağrısı için devam eden işlemi temsil eder.

1. Henüz beklenmediği `getStringTask` `GetUrlContentLengthAsync` için, nihai sonuca bağlı olmayan diğer çalışmalarla devam edebilir `GetStringAsync` . Bu iş, zaman uyumlu yöntem çağrısıyla temsil edilir `DoIndependentWork` .

1. `DoIndependentWork` , işini yapan ve çağırana döndüren zaman uyumlu bir yöntemdir.

1. `GetUrlContentLengthAsync` , uygulamasından bir sonuç olmadan yapabilmeden iş dışında çalışıyor `getStringTask` . `GetUrlContentLengthAsync` ardından, indirilen dizenin uzunluğunu hesaplamak ve döndürmek ister, ancak yöntem dizeye gelinceye kadar bu değeri hesaplayamaz.

    Bu nedenle, `GetUrlContentLengthAsync` ilerleme durumunu askıya almak ve denetimi çağıran yönteme eklemek için bir Await işleci kullanır `GetUrlContentLengthAsync` . `GetUrlContentLengthAsync` çağırana döndürür `Task<int>` . Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.

    > [!NOTE]
    > `GetStringAsync`(Ve bu nedenle `getStringTask` ), bekleden önce tamamlanırsa `GetUrlContentLengthAsync` , denetim içinde kalır `GetUrlContentLengthAsync` . `GetUrlContentLengthAsync`Çağrılan zaman uyumsuz işlem `getStringTask` zaten tamamlanmışsa ve nihai sonucu beklemek zorunda değilse, ' ın askıya alınması ve geri döndürülmesi `GetUrlContentLengthAsync` ücretlidir.

    Çağırma yöntemi içinde işleme deseninin devam ettiği. Çağıran, sonucu beklemeden önce sonucu kendisine bağlı olmayan başka bir iş `GetUrlContentLengthAsync` ya da çağıran hemen bekleme edebilir. Çağırma yöntemi için bekliyor `GetUrlContentLengthAsync` ve `GetUrlContentLengthAsync` bekliyor `GetStringAsync` .

1. `GetStringAsync` tamamlar ve bir dize sonucu üretir. Dize sonucu, bekleneceğiniz şekilde çağrısı tarafından döndürülmedi `GetStringAsync` . (Metodun adım 3 ' te bir görevi zaten döndürdüğünü unutmayın.) Bunun yerine, dize sonucu, yönteminin tamamlandığını temsil eden görevde saklanır `getStringTask` . Await işleci sonucunu alır `getStringTask` . Atama ekstresi alındı sonucunu öğesine atar `contents` .

1. `GetUrlContentLengthAsync`Dize sonucu olduğunda, yöntemi dizenin uzunluğunu hesaplayabilir. Bu durumda, çalışması `GetUrlContentLengthAsync` da tamamlanır ve bekleyen olay işleyicisi sürdürülebilirler. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.
Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a> API zaman uyumsuz yöntemleri

Zaman uyumsuz programlamayı destekleyen gibi yöntemlerin nerede bulunacağını merak ediyor olabilirsiniz `GetStringAsync` . .NET Framework 4,5 veya üzeri ve .NET Core, ve ile çalışan birçok üye `async` içerir `await` . Bunları, üye adına eklenen "Async" sonekine ve ya da dönüş türlerine göre tanıyabilirsiniz <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> . Örneğin, sınıfı,, ve gibi `System.IO.Stream` yöntemleri, <xref:System.IO.Stream.CopyToAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> <xref:System.IO.Stream.WriteAsync%2A> ile zaman uyumlu yöntemleri içerir <xref:System.IO.Stream.CopyTo%2A> <xref:System.IO.Stream.Read%2A> <xref:System.IO.Stream.Write%2A> .

Windows Çalışma Zamanı ayrıca `async` Windows uygulamalarında ve ile kullanabileceğiniz birçok yöntem içerir `await` . Daha fazla bilgi için bkz. UWP geliştirme için [Iş parçacığı ve zaman uyumsuz programlama](/windows/uwp/threading-async/) ve [zaman uyumsuz programlama (Windows Mağazası uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) ve hızlı başlangıç: Windows çalışma zamanı önceki sürümlerini kullanıyorsanız, [C# veya Visual Basic zaman uyumsuz API 'leri çağırma](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) .

## <a name="threads"></a><a name="BKMK_Threads"></a> Akışları

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. `await`Zaman uyumsuz yöntemdeki bir ifade, beklenen görev çalışırken geçerli iş parçacığını engellemez. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.

`async`Ve `await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>CPU 'ya bağlanan işi arka plan iş parçacığına taşımak için kullanabilirsiniz, ancak arka plan iş parçacığı yalnızca sonuçların kullanılabilir hale gelmesini bekleyen bir işlem konusunda yardımcı olmaz.

Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Özellikle, bu yaklaşım, <xref:System.ComponentModel.BackgroundWorker> kod daha basit olduğundan ve yarış koşullarına karşı koruma sağlamak zorunda olmadığınızdan g/ç ile bağlantılı işlemler için olan sınıftan daha iyidir. , Zaman uyumsuz programlama, <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker> `Task.Run` iş parçacığı havuzuna aktarılan çalışmalardan kodunuzu çalıştırmanın koordinasyon ayrıntılarını ayırdığından, zaman uyumsuz programlama, CPU 'ya bağlanan işlemlerden daha iyidir.

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a> Async ve await

[Zaman](../../../language-reference/keywords/async.md) uyumsuz değiştirici kullanarak bir yöntemin zaman uyumsuz bir yöntem olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirirsiniz.

- İşaretlenen zaman uyumsuz yöntem, askıya alma noktaları belirlemek için [await](../../../language-reference/operators/await.md) kullanabilir. İşleci, zaman uyumsuz yöntemin, beklenen `await` zaman uyumsuz işlem tamamlanana kadar bu noktanın ötesine devam edemeyeceğini derleyiciye bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.

     Bir ifadede zaman uyumsuz bir yöntemin askıya alınması `await` yöntemden bir çıkış oluşturmaz ve `finally` bloklar çalıştırılmaz.

- İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.

Zaman uyumsuz bir yöntem, genellikle bir işlecin bir veya daha fazla örneğini içerir `await` , ancak ifadelerin yokluğu `await` bir derleyici hatasına neden olmaz. Zaman uyumsuz bir yöntem, askıya alma `await` noktasını işaretlemek için bir operatör kullanmıyorsa Yöntem, değiştiriciye rağmen zaman uyumlu bir yöntem olarak yürütülür `async` . Derleyici bu tür yöntemler için bir uyarı verir.

`async` ve `await` bağlamsal anahtar sözcüklerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a> Dönüş türleri ve parametreleri

Zaman uyumsuz bir yöntem genellikle bir <xref:System.Threading.Tasks.Task> veya döndürür <xref:System.Threading.Tasks.Task%601> . Zaman uyumsuz bir yöntemde, bir `await` işleç, başka bir zaman uyumsuz metoda yapılan çağrıdan döndürülen bir göreve uygulanır.

Yöntemi, <xref:System.Threading.Tasks.Task%601> [`return`](../../../language-reference/keywords/return.md) türünde bir işleneni belirten bir ifade içeriyorsa, dönüş türü olarak belirtirsiniz `TResult` .

<xref:System.Threading.Tasks.Task>Metodun Return ifadesine sahip olmaması veya bir işleneni döndürmeyen bir return ifadesine sahip olması durumunda dönüş türü olarak kullanırsınız.

C# 7,0 ' den başlayarak, türün bir yöntemi içermesi kaydıyla, başka bir dönüş türü de belirtebilirsiniz `GetAwaiter` . <xref:System.Threading.Tasks.ValueTask%601> Bu tür bir örnektir. [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketinde kullanılabilir.

Aşağıdaki örnek, bir veya döndüren bir yöntemi nasıl bildirmenizi ve çağırakullanacağınızı gösterir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> :

```csharp
async Task<int> GetTaskOfTResultAsync()
{
    int hours = 0;
    await Task.Delay(0);

    return hours;
}


Task<int> returnedTaskTResult = GetTaskOfTResultAsync();
int intResult = await returnedTaskTResult;
// Single line
// int intResult = await GetTaskOfTResultAsync();

async Task GetTaskAsync()
{
    await Task.Delay(0);
    // No return statement needed
}

Task returnedTask = GetTaskAsync();
await returnedTask;
// Single line
await GetTaskAsync();
```

Döndürülmüş her görev, devam eden bir çalışmayı temsil eder. Bir görev, zaman uyumsuz işlemin durumu hakkındaki bilgileri saklar ve sonunda, işlemden alınan nihai sonuca veya başarısız olursa işlemin neden olduğu bir özel duruma ilişkin bilgileri içerir.

Zaman uyumsuz bir yöntemin `void` dönüş türü de olabilir. Bu dönüş türü öncelikle bir dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır `void` . Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.

Dönüş türüne sahip bir zaman uyumsuz yöntem beklenemez `void` ve void döndüren bir yöntem çağıran yöntemin aldığı özel durumları yakalayabilir.

Zaman uyumsuz bir yöntem [içinde](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) veya [Out](../../../language-reference/keywords/out-parameter-modifier.md) parametrelerini bildiremez, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir. Benzer şekilde, zaman uyumsuz bir yöntem başvuruya göre değer döndüremez, ancak başvuru dönüş değerleri içeren yöntemler çağırabilir.

Daha fazla bilgi ve örnek için bkz. [Async Return Types (C#)](async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [try-catch](../../../language-reference/keywords/try-catch.md).

Windows Çalışma Zamanı programlamadaki zaman uyumsuz API 'Ler, görevlerle benzer olan aşağıdaki dönüş türlerinden birine sahiptir:

- <xref:Windows.Foundation.IAsyncOperation%601>öğesine karşılık gelen <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>öğesine karşılık gelen <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a> Adlandırma kuralı

Kurala göre, yaygın olarak kullanılan türleri (örneğin,,,,,,,) döndüren yöntemlerin `Task` `Task<T>` `ValueTask` `ValueTask<T>` "Async" ile biten adları olmalıdır. Zaman uyumsuz bir işlem Başlatan ancak bir awasever türü döndürmeyen Yöntemler, "Async" ile biten adlara sahip olmamalıdır, ancak bu yöntemin işlemin sonucunu döndürmeyeceğini veya oluşturmadığını önermek için "BEGIN", "Start" ya da başka bir fiil ile başlayabilir.

Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, gibi yaygın olay işleyicilerini yeniden adlandırmamanız gerekir `OnButtonClick` .

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a> İlgili konular ve örnekler (Visual Studio)

| Başlık | Açıklama | Örnek |
|--|--|--|
| [Async ve await kullanarak birden çok web isteğini paralel hale getirme (C#)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) | Nasıl aynı anda birkaç görevi başlatacağınızı gösterir. | [Zaman uyumsuz örnek: birden çok Web Isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e) |
| [Zaman uyumsuz dönüş türleri (C#)](async-return-types.md) | Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar. |  |
| Bir iptal belirteci olan görevleri sinyal mekanizması olarak iptal edin. | Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br><br> - [Görev listesini iptal etme (C#)](cancel-an-async-task-or-a-list-of-tasks.md)<br>- [Bir süre sonra görevleri iptal et (C#)](cancel-async-tasks-after-a-period-of-time.md)<br>- [Zaman uyumsuz görevi tamamlandıklarında işle (C#)](start-multiple-async-tasks-and-process-them-as-they-complete.md) |  |
| [Dosya erişimi için Async Kullanma (C#)](using-async-for-file-access.md) | Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir. |  |
| [Görev tabanlı zaman uyumsuz model (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | Zaman uyumsuz bir model tanımlar, model ve türlerini temel alır <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> . |  |
| [Channel 9 ' da zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en) | Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar. |  |

## <a name="see-also"></a>Ayrıca bkz.

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Zaman uyumsuz programlama](../../../async.md)
- [Zaman uyumsuz genel bakış](../../../../standard/async.md)
