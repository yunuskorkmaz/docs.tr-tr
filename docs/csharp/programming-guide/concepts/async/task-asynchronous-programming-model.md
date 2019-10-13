---
title: Async ve await (C#) Ile görev zaman uyumsuz programlama MODELI (TAP)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 3ced168bada4167418bf27861c5b8666b02aa70e
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291334"
---
# <a name="task-asynchronous-programming-model"></a>Görev zaman uyumsuz programlama modeli

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verebilirliğini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir, bu da yazma, hata ayıklama ve sürdürme işlemlerini zorlaştırır.

5, .NET Framework 4,5 ve üzeri, .NET Core ve Windows çalışma zamanı zaman uyumsuz destekten yararlanan, zaman uyumsuz programlama ile basitleştirilmiş bir yaklaşım getirmiştir. [ C# ](../../../whats-new/csharp-version-history.md#c-version-50) Derleyici, geliştiricinin yapması için kullandığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlamanın avantajlarından yararlanın ve bu da çabaların bir sonucudur.

Bu konu, zaman uyumsuz programlamanın ne zaman ve nasıl kullanılacağına dair bir genel bakış sağlar ve Ayrıntılar ve örnekler içeren destek konularına bağlantılar içerir.

## <a name="BKMK_WhentoUseAsynchrony"></a>Zaman uyumsuz, yanıt hızını geliştirir

Asynchrony, Web erişimi gibi olası engelleme olasılığı olan etkinlikler için gereklidir. Bir web kaynağına erişim bazen yavaş veya geciktirilebilir. Bu tür bir etkinlik zaman uyumlu bir işlemde engellenirse, uygulamanın tamamının beklemesi gerekir. Zaman uyumsuz bir işlemde, uygulama, olası engelleme görevi tamamlanana kadar web kaynağına bağlı olmayan diğer çalışmalarla devam edebilir.

Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını artıran tipik bölgeler gösterilmektedir. .NET ve Windows Çalışma Zamanı listelenen API 'Ler, zaman uyumsuz programlamayı destekleyen yöntemler içerir.

| Uygulama alanı    | Zaman uyumsuz yöntemleriyle .NET türleri     | Zaman uyumsuz yöntemlere sahip Windows Çalışma Zamanı türleri  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web erişimi|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Dosyalarla çalışma|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|
|Görüntülerle çalışma||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|WCF programlama|[Zaman uyumlu ve zaman uyumsuz Işlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||

Kullanıcı arabirimi ile ilgili tüm etkinlikler genellikle tek bir iş parçacığını paylaştığından, asynchrony, özellikle UI iş parçacığına erişen uygulamalar için değerlidir. Zaman uyumlu bir uygulamada herhangi bir işlem engellenirse, tümü engellenir. Uygulamanız yanıt vermeyi durduruyor ve bunun yerine bekleme süresi sona erdiğinde, bunun başarısız olduğunu de iptal edebilirsiniz.

Zaman uyumsuz yöntemler kullandığınızda, uygulama kullanıcı arabirimine yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da işlemin bitmesini beklemek istemiyorsanız uygulamayı kapatabilirsiniz.

Zaman uyumsuz tabanlı yaklaşım, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine otomatik bir iletimin eşdeğerini ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarını, ancak geliştiriciden çok daha az çaba elde edersiniz.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Zaman uyumsuz yöntemlerin yazılması daha kolaydır

' Deki C# [Async](../../../language-reference/keywords/async.md) ve [await](../../../language-reference/operators/await.md) anahtar sözcükleri zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak, bir zaman uyumlu Yöntem oluştururken neredeyse kolayca zaman uyumsuz bir yöntem oluşturmak için .NET Framework, .NET Core veya Windows Çalışma Zamanı kaynaklarını kullanabilirsiniz. @No__t-0 anahtar sözcüğünü kullanarak tanımladığınız zaman uyumsuz yöntemler, *zaman uyumsuz yöntemler*olarak adlandırılır.

Aşağıdaki örnek bir zaman uyumsuz yöntemi gösterir. Koddaki neredeyse her şey size tamamen tanıdık gelmelidir.

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

Yukarıdaki örnekten birkaç uygulama öğrenebilirsiniz. Yöntem imzasıyla başlayın. @No__t-0 değiştiricisini içerir. Dönüş türü `Task<int>` ' dır (daha fazla seçenek için "dönüş türleri" bölümüne bakın). Yöntem adı `Async` ' da sona erer. Yöntemin gövdesinde, `GetStringAsync`, `Task<string>` döndürür. Yani, `await` `string` (`urlContents`) alacağınız görevi gösterir.  Görevi beklerken önce, `GetStringAsync` ' den `string` ' ı kullanmayan çalışmayı yapabilirsiniz.

@No__t-0 işlecine yakın bir uyarı ödeyin. @No__t askıya alır-0;

- `getStringTask` @no__t, tamamlanana kadar devam edemiyor.
- Bu arada, denetim `AccessTheWebAsync` çağırana döner.
- @No__t-0 tamamlandığında Denetim burada sürdürülür.
- @No__t-0 işleci daha sonra `getStringTask` ' den `string` sonucunu alır.

Return ifadesinde bir tamsayı sonucu belirtilir. @No__t-0 bekleyen Yöntemler uzunluk değerini alır.

@No__t-0 ' ı çağırarak `GetStringAsync` arasında yapamazsa ve tamamlanmasını beklerken, aşağıdaki tek bildirimde çağırarak ve bekleyen kodunuzu basitleştirebilirsiniz.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Aşağıdaki özellikler, önceki örneği nasıl zaman uyumsuz bir yöntem yaptığını özetler:

- Yöntem imzası `async` değiştiricisi içerir.
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - <xref:System.Threading.Tasks.Task%601> ' ın, işleneni `TResult` türünde olan bir return bildirisi varsa.
  - <xref:System.Threading.Tasks.Task> ' ın Return bildirisi yoksa veya işleneni olmayan bir return ifadesine sahipse.
  - zaman uyumsuz bir olay işleyicisi yazıyorsanız `void`.
  - @No__t-0 yöntemine sahip olan diğer herhangi bir tür (7,0 ile C# başlayarak).

  Daha fazla bilgi için bkz. [dönüş türleri ve parametreleri](#BKMK_ReturnTypesandParameters) bölümü.

- Yöntemi genellikle, beklenen zaman uyumsuz işlem tamamlanana kadar yöntemin devam edemediği bir noktayı işaretleyen en az bir `await` ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim metodun çağıranına döner. Bu konunun sonraki bölümünde, askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde, ne yapmak istediğinizi belirtmek için sunulan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına döndüğünde ne olması gerektiğini izlemek de dahil olmak üzere, geri kalanı yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodda işlenmesi zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri, zaman uyumlu bir çözümde yaptığınız kadar çok yazarsınız ve sorun çözülür.

.NET Framework önceki sürümlerinde zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Zaman uyumsuz bir yöntemde ne olur?

Zaman uyumsuz programlamada anlaşılması gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagramda süreç boyunca size yol gösterir:

![Zaman uyumsuz program](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "Navigationtrace") 'i izleme

Diyagramdaki sayılar, Kullanıcı "Başlat" düğmesine tıkladığında başlatılan aşağıdaki adımlara karşılık gelir.

1. Bir olay işleyicisi, `AccessTheWebAsync` zaman uyumsuz yöntemini çağırır ve bekler.

2. `AccessTheWebAsync` bir <xref:System.Net.Http.HttpClient> örneği oluşturur ve bir Web sitesinin içeriğini bir dize olarak indirmek için <xref:System.Net.Http.HttpClient.GetStringAsync%2A> zaman uyumsuz yöntemini çağırır.

3. @No__t-0 ' da, ilerleme durumunu askıya alan bir sorun oluşur. Belki de bir Web sitesinin indirilmesinin veya başka bir engelleme etkinliğinin beklemesi gerekir. @No__t-0, kaynak engellemeyi önlemek için, `AccessTheWebAsync` ' e yönelik denetim verir.

     `GetStringAsync`, `TResult` bir dize olduğu ve `AccessTheWebAsync`, görevi `getStringTask` değişkenine atayan bir <xref:System.Threading.Tasks.Task%601> döndürür. Görev, iş tamamlandığında gerçek bir dize değeri üretme taahhüdünde `GetStringAsync` ' a yapılan çağrı için devam eden işlemi temsil eder.

4. @No__t-0 henüz beklenmediği için, `AccessTheWebAsync` `GetStringAsync` ' den nihai sonuca bağlı olmayan diğer çalışmalarla devam edebilir. Bu iş, zaman uyumlu yöntem çağrısıyla temsil edilir `DoIndependentWork`.

5. `DoIndependentWork`, işini yapan ve çağırana döndüren zaman uyumlu bir yöntemdir.

6. `AccessTheWebAsync`, `getStringTask` ' den bir sonuç olmadan yapabilmeden iş dışında çalışıyor. `AccessTheWebAsync` ' dan sonra indirilen dizenin uzunluğunu hesaplamak ve döndürmek ister, ancak yöntem dizeye gelinceye kadar bu değeri hesaplayamaz.

     Bu nedenle, `AccessTheWebAsync` ' ın ilerlemesini askıya almak ve denetimi `AccessTheWebAsync` ' i çağıran yönteme getirmek için bir Await işleci kullanır. `AccessTheWebAsync`, çağırana bir `Task<int>` döndürür. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu üretmek için bir Promise 'yi temsil eder.

    > [!NOTE]
    > @No__t-0 (ve bu nedenle `getStringTask`) `AccessTheWebAsync` ' den önce tamamlanırsa, denetim `AccessTheWebAsync` ' te kalır. Çağrılan zaman uyumsuz işlem (`getStringTask`) zaten tamamlanmışsa ve `AccessTheWebAsync` ' nin nihai sonucu beklemek zorunda olmaması halinde `AccessTheWebAsync` ' a geri alma ve geri dönme gideri harcanacaktır.

     Çağıranın içinde (Bu örnekteki olay işleyicisi), işleme deseninin devam etmesi gerekir. Çağıran, sonucu beklemeden önce `AccessTheWebAsync` ' dan sonuca bağlı olmayan başka işler, ya da çağıranın anında bekleme yapması istenebilir.   Olay işleyicisi `AccessTheWebAsync` ' ı bekliyor ve `AccessTheWebAsync` `GetStringAsync` ' i bekliyor.

7. `GetStringAsync` tamamlanır ve bir dize sonucu üretir. Dize sonucu, bekleneceğiniz şekilde `GetStringAsync` ' a çağrı tarafından döndürülmedi. (Metodun adım 3 ' te bir görevi zaten döndürdüğünü unutmayın.) Bunun yerine, dize sonucu yöntemin tamamlanmasını temsil eden görevde saklanır, `getStringTask`. Await işleci `getStringTask` ' dan sonucu alır. Atama ekstresi alınan sonucu `urlContents` ' a atar.

8. @No__t-0 ' ın dize sonucu olduğunda, yöntemi dizenin uzunluğunu hesaplayabilir. @No__t-0 ' ın çalışması da tamamlanır ve bekleyen olay işleyicisi sürdürülebilirler. Konunun sonundaki tam örnekte olay işleyicisinin, uzunluk sonucunun değerini aldığını ve yazdırmasını doğrulayabilirsiniz.
Zaman uyumsuz programlama için yeni bir işlem yapıyorsanız, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkı göz önünde bulundurmanız gereken bir dakika bekleyin. Zaman uyumlu bir yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem iş askıya alındığında bir görev değeri döndürür (adım 3 ve 6). Zaman uyumsuz yöntem işini en sonunda tamamladığında, görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışıC#()](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>API zaman uyumsuz yöntemleri

Zaman uyumsuz programlamayı destekleyen `GetStringAsync` gibi yöntemlerin nerede bulunacağını merak ediyor olabilirsiniz. .NET Framework 4,5 veya üzeri ve .NET Core, `async` ve `await` ile çalışan birçok üye içerir. Bunları, üye adına eklenen "Async" sonekiyle ve <xref:System.Threading.Tasks.Task> ya da <xref:System.Threading.Tasks.Task%601> ' in dönüş türüne göre de tanıyabilirsiniz. Örneğin `System.IO.Stream` sınıfı, zaman uyumlu yöntemler <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> ve <xref:System.IO.Stream.Write%2A> gibi <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> ve <xref:System.IO.Stream.WriteAsync%2A> gibi yöntemler içerir.

Windows Çalışma Zamanı Ayrıca, Windows uygulamalarında `async` ve `await` ile kullanabileceğiniz birçok yöntem içerir. Daha fazla bilgi için bkz. UWP geliştirme için [Iş parçacığı ve zaman uyumsuz programlama](/windows/uwp/threading-async/) ve [zaman uyumsuz programlama (Windows Mağazası uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) ve hızlı başlangıç: önceki sürümlerini kullanıyorsanız, [ C# veya Visual Basic zaman uyumsuz API 'leri çağırma](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) Windows Çalışma Zamanı.

## <a name="BKMK_Threads"></a>Akışları

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olması amaçlanmıştır. Zaman uyumsuz bir yöntemde `await` ifadesi, beklenen görev çalışırken geçerli iş parçacığını engellemez. Bunun yerine ifade, yöntemin geri kalanını devam olarak imzalar ve denetimi zaman uyumsuz yöntemi çağırana döndürür.

@No__t-0 ve `await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz metotlar kendi iş parçacığında çalışmadığından zaman uyumsuz yöntemler çoklu iş parçacığı gerektirmez. Yöntemi geçerli eşitleme bağlamında çalışır ve yalnızca Yöntem etkin olduğunda iş parçacığı üzerinde zaman kullanır. CPU 'ya bağlanan işi arka plan iş parçacığına taşımak için <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> ' ı kullanabilirsiniz, ancak arka plan iş parçacığı sonuçların kullanılabilir hale gelmesini bekleyen bir işlemle ilgili yardım etmez.

Zaman uyumsuz programlama için zaman uyumsuz tabanlı yaklaşım neredeyse her durumda varolan yaklaşımlara tercih edilir. Özellikle, kod daha basit olduğundan ve yarış koşullarına karşı koruma yapmanız gerekmiyorsa, bu yaklaşım, g/ç 'ye bağlanacak işlemler için <xref:System.ComponentModel.BackgroundWorker> sınıfından daha iyidir. @No__t-0 yöntemiyle birlikte zaman uyumsuz programlama, CPU 'ya bağlanan işlemler için <xref:System.ComponentModel.BackgroundWorker> ' den daha iyidir, çünkü zaman uyumsuz programlama, kodunuzun iş parçacığı koduna `Task.Run` ' ye aktardığı çalışmalardan kod çalıştırmanın koordinasyon ayrıntılarını ayırır.

## <a name="BKMK_AsyncandAwait"></a>Async ve await

[Zaman](../../../language-reference/keywords/async.md) uyumsuz değiştirici kullanarak bir yöntemin zaman uyumsuz bir yöntem olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirirsiniz.

- İşaretlenen zaman uyumsuz yöntem, askıya alma noktaları belirlemek için [await](../../../language-reference/operators/await.md) kullanabilir. @No__t-0 işleci derleyiciye zaman uyumsuz yöntemin, zaman uyumsuz işlem tamamlanana kadar bu noktanın ötesine devam edemeyeceğini söyler. Bu sırada denetim, zaman uyumsuz yöntemi çağırana döner.

     Bir `await` ifadesinde zaman uyumsuz bir yöntemin askıya alınması yöntemden bir çıkış oluşturmaz ve `finally` blokları çalışmaz.

- İşaretlenen zaman uyumsuz yöntem kendisini çağıran yöntemler tarafından beklemiş olabilir.

Zaman uyumsuz bir yöntem genellikle `await` işlecinin bir veya daha fazla örneğini içerir, ancak `await` ifadelerinin yokluğu bir derleyici hatasına neden olmaz. Zaman uyumsuz bir yöntem, askıya alma noktasını işaretlemek için `await` işleci kullanmıyorsa, yöntem, `async` değiştiricisine rağmen zaman uyumlu bir yöntem olarak yürütülür. Derleyici bu tür yöntemler için bir uyarı verir.

`async` ve `await` bağlamsal anahtar kelimelerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [eş](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Dönüş türleri ve parametreleri

Zaman uyumsuz bir yöntem genellikle <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndürür. Zaman uyumsuz bir yöntemin içinde, başka bir zaman uyumsuz metoda yapılan çağrıdan döndürülen bir göreve `await` işleci uygulanır.

Yöntem `TResult` türünde bir işleneni belirten [`return`](../../../language-reference/keywords/return.md) ifadesini içeriyorsa, dönüş türü olarak <xref:System.Threading.Tasks.Task%601> belirtirsiniz.

Metodun Return ifadesine sahip olmaması veya bir işleneni döndürmeyen bir return ifadesine sahip olması durumunda, dönüş türü olarak <xref:System.Threading.Tasks.Task> kullanırsınız.

7,0 ile C# başlayarak, türün bir `GetAwaiter` yöntemi içermesi kaydıyla, başka bir dönüş türü de belirtebilirsiniz. <xref:System.Threading.Tasks.ValueTask%601> bu tür bir örnektir. [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketinde kullanılabilir.

Aşağıdaki örnek, <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task> döndüren bir yöntemi nasıl bildirmenizi ve çağırakullanacağınızı gösterir:

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

Döndürülen her görev devam eden çalışmayı temsil eder. Bir görev, zaman uyumsuz işlemin durumuyla ilgili bilgileri ve sonunda işlemin son sonucunu ya da işlemin başarılı olmazsa yaptığı özel durumu kapsar.

Zaman uyumsuz bir yöntem `void` dönüş türüne de sahip olabilir. Bu dönüş türü, öncelikle `void` dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri genellikle zaman uyumsuz programlar için başlangıç noktası olarak görev yapar.

@No__t-0 dönüş türüne sahip bir zaman uyumsuz yöntem beklenemez ve void döndüren bir yöntemi çağıran yöntemin aldığı özel durumları yakalayabilir.

Zaman uyumsuz bir yöntem [içinde](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) veya [Out](../../../language-reference/keywords/out-parameter-modifier.md) parametrelerini bildiremez, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir. Benzer şekilde, zaman uyumsuz bir yöntem başvuruya göre değer döndüremez, ancak başvuru dönüş değerleri içeren yöntemler çağırabilir.

Daha fazla bilgi ve örnek için bkz. [Async Return TypesC#()](./async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [try-catch](../../../language-reference/keywords/try-catch.md).

Windows Çalışma Zamanı programlamadaki zaman uyumsuz API 'Ler, görevlerle benzer olan aşağıdaki dönüş türlerinden birine sahiptir:

- <xref:Windows.Foundation.IAsyncOperation%601>, <xref:System.Threading.Tasks.Task%601> ' e karşılık gelir
- <xref:Windows.Foundation.IAsyncAction>, <xref:System.Threading.Tasks.Task> ' e karşılık gelir
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Kurala göre, yaygın olarak kullanılan türleri (örneğin `Task`, `Task<T>`, `ValueTask`, `ValueTask<T>`) döndüren yöntemler "Async" ile biten adlara sahip olmalıdır. Zaman uyumsuz bir işlem Başlatan ancak bir awasever türü döndürmeyen Yöntemler, "Async" ile biten adlara sahip olmamalıdır, ancak bu yöntemin işlemin sonucunu döndürmeyeceğini veya oluşturmadığını önermek için "BEGIN", "Start" ya da başka bir fiil ile başlayabilir.

Bir olay, temel sınıf veya arabirim sözleşmesinin farklı bir ad önerdiği kuralı yoksayabilirsiniz. Örneğin, `Button1_Click` gibi yaygın olay işleyicilerini yeniden adlandırmamanız gerekir.

## <a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünün zaman uyumsuz bir WPF çözümüne nasıl dönüştürüleceğini gösterir. Uygulama bir dizi Web sitesi indirir.|[Zaman uyumsuz örnek: Web 'e erişme yolu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Nasıl yapılır: Task. WhenAll (C#) kullanarak zaman uyumsuz Izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Önceki izlenecek yol için <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ekler. @No__t-0 kullanımı, tüm indirmeleri aynı anda başlatır.||
|[Nasıl yapılır: Async ve await (C#) kullanarak birden çok Web Isteğini paralel hale getirme](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Aynı anda birkaç görevi nasıl başlatabileceğinizi gösterir.|[Zaman uyumsuz örnek: birden çok Web Isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Zaman uyumsuz dönüş türleriC#()](./async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün uygun olduğu zaman bunu açıklar.||
|[Zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md)|Bir zaman uyumsuz programdaki bir bekleme ifadeleriyle denetim akışını ayrıntılı olarak izler.|[Async örneği: zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevlerin nasıl ekleneceğini gösterir:<br /><br /> - [zaman uyumsuz bir görevi veya görev listesini Iptal etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [bir süre sonra zaman uyumsuz görevleri Iptal et (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [bir süre tamamlandıktan sonra kalan zaman uyumsuz görevleri IptalC#et ()](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [birden çok zaman uyumsuz görevi başlatın ve bunları tamamlarsa (C#) işleyin](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)](./handling-reentrancy-in-async-apps.md)|Çalışırken etkin bir zaman uyumsuz işlemin yeniden başlatılma durumlarının nasıl işleneceğini gösterir.||
|[WhenAny: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.Tasks.Task.WhenAny%2A> kullanabilmeniz için, .NET Framework ve ıasyncoWindows çalışma zamanı Perations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ile Windows Çalışma Zamanı arasında köprü oluşturma (AsTask ve WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Zaman uyumsuz Iptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.CancellationTokenSource> kullanabilmeniz için, .NET Framework ve ıasyncoWindows çalışma zamanı Perations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ve Windows Çalışma Zamanı arasında köprü oluşturma (AsTask & Iptali)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya erişimi için Async Kullanma (C#)](./using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz ve await kullanmanın avantajlarını listeler ve gösterir.||
|[Görev tabanlı zaman uyumsuz model (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework zaman uyumsuzluğu için yeni bir model tanımlar. Bu model <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> türlerini temel alır.||
|[Channel 9 ' da zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="BKMK_CompleteExample"></a>Örnek Tamam

Aşağıdaki kod, bu makalede ele alınan WPF uygulamasından gelen *MainWindow.xaml.cs* dosyasıdır. Örneği zaman uyumsuz [örnek: "Async ve await Ile zaman uyumsuz programlama" kaynağından](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/)indirebilirsiniz.

[!code-csharp[async](~/samples/async/async-and-await/cs/MainWindow.xaml.cs)] 

## <a name="see-also"></a>Ayrıca bkz.

- [eş](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Zaman uyumsuz programlama](../../../async.md)
- [Zaman uyumsuz genel bakış](../../../../standard/async.md)
 
