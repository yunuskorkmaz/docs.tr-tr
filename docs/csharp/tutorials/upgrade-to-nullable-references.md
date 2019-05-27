---
title: Null başvuru türleri için Tasarım
description: Gelişmiş Bu öğretici, bir null başvuru türlerine giriş sağlar. Tasarımınız ne zaman başvuru değeri null ve boş olamaz yürüttüğünde derleyici sahip hedefi express öğreneceksiniz.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 289b864aaa0380a31e93ef223fb5b5780e35892a
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195843"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Öğretici: Null başvuru türleri ile mevcut kodu geçirme

C#8 tanıtır **null başvuru türleri**, boş değer atanabilen değer türleri tamamlar değer türleri aynı şekilde hangi tamamlayıcı başvuru türleri. Olması için bir değişken bildirmek bir **boş değer atanabilir bir başvuru türü** ekleyerek bir `?` türü. Örneğin, `string?` temsil eden bir boş değer atanabilir `string`. Bu yeni türleri tasarım amacınızla daha net bir şekilde ifade etmek için kullanabilirsiniz: bazı değişkenler *her zaman bir değere sahip olmalıdır*, diğerleri *bir değer eksik*. Var olan herhangi bir başvuru türü değişkenler, bir NULL olmayan bir başvuru türü yorumlanacağını. 

Bu öğreticide şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Kod ile çalışırken null başvuru denetimlerini etkinleştir.
> * Tanılama ve null değerlere ilgili farklı uyarıları düzeltin.
> * Boş değer atanabilir etkin ve boş değer atanabilir devre dışı bağlamları arasında arabirim yönetin.
> * Boş değer atanabilir bir ek açıklama bağlamları denetler.

## <a name="prerequisites"></a>Önkoşullar

.NET Core çalıştırmak için makinenizi ayarlamak ihtiyacınız olacak dahil olmak üzere C# 8.0 beta derleyici. C# 8 beta derleyici, kullanılabilir [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), veya en son [.NET Core 3.0 Önizleme](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Bu öğreticide, aşina olduğunuz varsayılır C# ve .NET, Visual Studio veya .NET Core CLI gibi.

## <a name="explore-the-sample-application"></a>Örnek uygulamayı keşfedin

Geçirdiğiniz örnek bir RSS Okuyucu web uygulaması akışı uygulamasıdır. Tek bir RSS akışı okur ve en son makaleler için özetlerini görüntüler. Herhangi bir siteyi ziyaret etmek için makaleleri üzerinde tıklayabilirsiniz. Uygulama yeni ancak null başvuru türleri kullanılabilir önce yazılmıştır. Ses ilkeleri uygulama tasarım kararlarına temsil edilen, ancak bu önemli dil özelliğin avantajlarından yararlanmak yok.

Örnek uygulamayı, uygulamanın ana işlevleri doğrulayan bir birim testi kitaplığı içerir. Oluşturulan uyarıları tabanlı uygulama değiştirirseniz proje güvenli bir şekilde, yükseltmeyi kolaylaştırır. Başlatıcı kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub deposu.

Bir projeye geçiş amacınız açıkça amacınızla değişkenleri null olabilirliği üzerinde express ve boş değer atanabilir bir ek açıklama içerik varsa, derleyici uyarıları oluşturmaya olmayan bir şekilde bunu yeni dil özelliklerden yararlanmak için olmalıdır ve boş değer atanabilir uyarı bağlamı kümesine `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Projeleri yükseltme C# 8

İyi bir ilk adım, geçiş görevi kapsamını belirlemektir. Başlangıç projesine yükselterek C# 8.0 (veya daha yeni). Ekleme `LangVersion` hem csproj dosyalarına web projesi ve birim testi projesi öğesi:

```xml
<LangVersion>8.0</LangVersion>
```

Dil sürümü yükseltme seçer C# 8.0, ancak boş değer atanabilir bir ek açıklamanın bağlamı veya boş değer atanabilir uyarı bağlamı etkinleştirmez. Uyarılar olmadan derlendiğinden emin olmak için projeyi yeniden derleyin.

Boş değer atanabilir bir ek açıklama bağlama ve kaç uyarıları üretilir görmek için iyi bir sonraki adım var. Doğrudan altında hem csproj dosyalarına çözümünde, şu öğeyi ekleyin `LangVersion` öğesi:

```xml
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> `Nullable` Öğe daha önce adlandırılmıştı `NullableContextOptions`. 16,2 p1, Visual Studio 2019 birlikte yeniden adlandırma verilir. .NET Core SDK'sı 3.0.100-preview5-011568 bu değişiklik yok. .NET Core CLI'yı kullanıyorsanız, kullanmanız gerekecektir `NullableContextOptions` kadar sonraki Önizleme kullanılabilir.

Bir test derlemesini ve uyarı listesini dikkat edin. Bu küçük uygulamadaki derleyici beş uyarılar oluşturur, büyük olasılıkla, bırakabilir, bu nedenle boş değer atanabilir bir ek açıklamanın bağlamı etkin ve tüm proje uyarıları düzeltme başlatın.

Bu strateji daha küçük projeler için çalışır. Tüm daha büyük projeler için boş değer atanabilir bir ek açıklama bağlam için kod tabanının tamamına sağlayarak üretilen uyarı sayısı uyarıları gidermek zorlaştırır sistematik olarak. Büyük kuruluş projeleri için genellikle bir proje teker teker geçirmek isteyeceksiniz. Her projede, aynı anda bir sınıf veya dosya geçirin.

## <a name="warnings-help-discover-original-design-intent"></a>Özgün tasarım amacı keşfedin uyarılar Yardımı

Birden çok uyarı üreten iki sınıf vardır. İle başlayan `NewsStoryViewModel` sınıfı. Kaldırma `Nullable` öğesi hem csproj dosyalarının uyarıları ile çalışırken kod bölümlerini kapsamını sınırlayabilirsiniz. Açık *NewsStoryViewModel.cs* dosya ve ekleme için boş değer atanabilir bir ek açıklamanın bağlamı'nı etkinleştirmek için aşağıdaki yönergeleri `NewsStoryViewModel` ve o sınıf tanımına aşağıdaki geri yükleyin:

```csharp
#nullable enable
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; }
    public string Uri { get; set; }
}
#nullable restore
```

Bu iki yönergeler geçiş çalışmalarınızı odaklanmanıza yardımcı olur. Etkin olarak üzerinde çalıştığınız kod alanının boş değer atanabilir uyarıları üretilir. Tüm proje için uyarıları etkinleştirmek hazır oluncaya kadar üzerinde bırakacağız. Kullanmanız gereken `restore` yerine `disable` böylece tüm proje için boş değer atanabilir ek açıklamaları açık yanlışlıkla bağlamı daha sonra devre dışı olmayan değer. Tüm proje için boş değer atanabilir bir ek açıklama bağlamında ayarladıktan sonra tüm kaldırabilirsiniz `#nullable` pragmaları bu projeye ait.

`NewsStoryViewModel` Sınıfı, bir veri aktarım nesnesini (DTO) ve okuma/yazma dizeleri özelliklerinin ikisidir:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Bu iki özellik neden `CS8618`, "atanamayan özelliği başlatılmamış". Yeterli Temizle vardır: her ikisi de `string` özelliklerine sahip varsayılan değerini `null` olduğunda bir `NewsStoryViewModel` oluşturulur. Bulmak önemli olan nasıl `NewsStoryViewModel` nesnelerin oluşturulması. Bu sınıfı baktığımızda, bildiremez, `null` değeri tasarımının parçası olan veya bu nesneler için null olmayan ayarlarsanız değerlerin bir zaman oluşturulur. Haber hikayesi oluşturulan `GetNews` yöntemi `NewsService` sınıfı:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Önceki kod bloğu içinde geçmeden oldukça bit yoktur. Bu uygulamanın kullandığı [AutoMapper](https://automapper.org/) bir haber öğesi oluşturmak için NuGet paketi bir `ISyndicationItem`. Haber hikayesi öğeleri oluşturulur ve özellikler tek bir deyimde ayarlanır keşfettiniz. Tasarımı anlamına `NewsStoryViewModel` bu özellikleri hiç olmayacağını gösterir `null` değeri. Bu özellikler olmalıdır **nonnullable başvuru türleri**. En iyi özgün tasarım hedefi ifade eder. Aslında, hiçbir `NewsStoryViewModel` *olduğu* null olmayan değerler ile doğru şekilde örneği. Bu, geçerli bir düzeltme kod aşağıdaki başlatmaya yapar:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Atamasını `Title` ve `Uri` için `default` olduğu `null` için `string` türü, programın çalışma zamanı davranışını değiştirmez. `NewsStoryViewModel` Boş değerlere sahip, ancak derleyicinin uyarı raporları artık yine de oluşturulur. **Null forgiving işleci**, `!` karakter aşağıdaki `default` ifade derleyiciye önceki ifade null değil. Diğer değişiklikler çok büyük değişiklikleri bir kod tabanına zorlamak, ancak bu uygulamada görece hızlı ve daha iyi bir çözüm yoktur, bu tekniği expedient olabilir: Olun `NewsStoryViewModel` burada tüm özellikleri ayarlanır oluşturucuda bir sabit türü. Aşağıdaki değişiklikleri yapın `NewsStoryViewModel`:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Bu yapıldıktan sonra AutoMapper yapılandırır ve böylece özelliklerini ayarlamak yerine Oluşturucu kullanan kodu güncelleştirmeniz gerekir. Açık `NewsService.cs` ve dosyanın sonuna aşağıdaki kodu bulun:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Kod özelliklerini eşlemeleri `ISyndicationItem` nesnesini `NewsStoryViewModel` özellikleri. Bunun yerine bir kurucu kullanarak eşleme sağlamak üzere AutoMapper kullanmanız gerekir. Yukarıdaki kodu şu automapper yapılandırmayla değiştirin:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Dikkat edin çünkü bu sınıf küçük ve dikkatli bir şekilde incelenmesi açmanız `#nullable enable` Bu sınıf bildiriminin üstüne yönergesi. Tüm testleri çalıştırmak ve geçmeden önce uygulamayı test etmek için bu nedenle, oluşturucuya değişiklik kopuk.

İlk değişiklik kümesini zaman özgün tasarımda değişkenleri ayarlanmamalıdır, belirtilen bulunacak gösterildi `null`. Teknik olarak adlandırılır **yapı tarafından doğru**. Bir nesne ve özelliklerini olamaz bildirdiğiniz `null` bunu ne zaman oluşturulur. Derleyicinin akış analizi özelliklere ayarlanmadığı için güvence sağlayan `null` yapım sonra. Bu Oluşturucu dış kod tarafından çağrılır ve bu kodu Not **boş değer atanabilir oblivious**. Yeni sözdizimi, çalışma zamanı denetimi sağlamaz. Dış kod, derleyicinin akış analizi aşmak. 

Diğer durumlarda, bir sınıf yapısını amaca farklı ipuçları sağlar. Açık *Error.cshtml.cs* dosyası *sayfaları* klasör. `ErrorViewModel` Aşağıdaki kodu içerir:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Ekleme `#nullable enable` sınıf bildiriminden önce yönerge ve `#nullable restore` sonraki yönergesi. Biri, uyarı alırsınız `RequestId` başlatılmadı. Sınıf bakarak, karar `RequestId` özellik bazı durumlarda null olmalıdır. Varlığını `ShowRequestId` özelliği eksik değerleri mümkün olduğunu gösterir. Çünkü `null` geçerli Ekle `?` üzerinde `string` belirtmek için türü `RequestId` özelliği bir *boş değer atanabilir bir başvuru türü*. Son sınıfı aşağıdaki örnekteki gibi görünür:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Özelliğinin kullanımıyla ilgili denetleyin ve ilişkili sayfasında özelliğinin işaretlemede işlemeden önce null için işaretlendiğinden görürsünüz. Bu sınıf ile işiniz için bir null başvuru türünün güvenli bir kullanımı olmasıdır.

## <a name="fixing-nulls-causes-change"></a>Null değerlere düzeltme değişiklik neden olur

Genellikle, bir dizi uyarı düzeltmesini ilgili kodda yeni uyarılar oluşturur. Uygulamada uyarıları düzelterek görelim `index.cshtml.cs` sınıfı. Açık `index.cshtml.cs` dosya ve kodu inceleyin. Bu dosya, dizin sayfası için arka plan kod içerir:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Ekleme `#nullable enable` yönergesi ve iki uyarı göreceksiniz. Ne `ErrorText` özellik ya da `NewsItems` özelliği başlatılır. Bu sınıfın bir inceleme her iki özellik null bir başvuru türü olması gerektiğini düşünüyorsanız yol açar: Her ikisi de, özel ayarlayıcılar sahiptir. Tam olarak bir de atandığı `OnGet` yöntemi. Değişiklik yapmadan önce her iki özellik tüketicilerinin arayın. Sayfanın kendisi içinde `ErrorText` biçimlendirme hataları oluşturmadan önce null karşı denetlenir. `NewsItems` Koleksiyon karşı denetlenir `null`ve işaretli öğeleri koleksiyonu sahip olduğundan emin olmak. Her iki özellikleri null başvuru türleri yapmak için bir hızlı düzeltme olacaktır. Daha iyi bir düzeltme koleksiyonu bir nonnullable sağlamak olacaktır başvuru türüne ve haber alınırken, varolan bir koleksiyona öğeleri ekleyin. Eklenecek ilk düzeltmesidir `?` için `string` yazın `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Tüm erişim nedeniyle değişiklik diğer kodlardan ripple olmaz `ErrorText` özelliği null denetimleri tarafından zaten korumalı. Ardından, başlatma `NewsItems` liste ve salt okunur özelliği yapmadan özellik ayarlayıcısını kaldırın:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Uyarı sabit ancak hata sunmuştur. `NewsItems` Listedir artık **yapı tarafından doğru**, ancak liste ayarlar kod `OnGet` yeni API ile eşleşecek şekilde değiştirmeniz gerekir. Atama yerine çağrı `AddRange` haber öğeleri mevcut listeye eklemek için:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Kullanarak `AddRange` atama yerine anlamına `GetNews` yöntemi döndürebilir bir `IEnumerable` yerine bir `List`. Bir ayırma kaydeder. Metodun imzası değiştirme ve kaldırma `ToList` aşağıdaki kod örneğinde gösterildiği gibi çağrı:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

İmza değiştirmeyi de testleri keser. Açık `NewsServiceTests.cs` dosyası `Services` klasörü `SimpleFeedReader.Tests` proje. Gidin `Returns_News_Stories_Given_Valid_Uri` test ve türünü değiştirme `result` değişkenini `IEnumerable<NewsItem>`. Türü değiştirme anlamına gelir `Count` özelliği artık kullanılabilir, böylece değiştirin `Count` özelliğinde `Assert` çağrısıyla `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Eklemeniz gerekecektir bir `using System.Linq` dosyanın başına bildirimi.

Bu değişiklik kümesini yükseltilmesine genel örnek oluşturma içeren kod güncelleştirilirken vurgular. Liste ve NULL olmayan türleri listesi öğeleri için. Boş değer atanabilir türler ya da olabilir. Aşağıdaki bildirimleri izin verilir:

- `List<NewsStoryViewModel>`: nonullable görünüm modelleri nonnullable listesi.
- `List<NewsStoryViewModel?>`: boş değer atanabilir görünüm modelleri nonnullable listesi.
- `List<NewsStoryViewModel>?`: boş değer atanabilir nonnullable görünümü modellerin listesi.
- `List<NewsStoryViewModel?>?`: boş değer atanabilir görünüm modelleri boş değer atanabilir listesi.

## <a name="interfaces-with-external-code"></a>Dış kod olan arabirimler

Yaptığınız değişiklikleri `NewsService` sınıfı, bu nedenle açma `#nullable enable` o sınıf için ek açıklama. Bu, tüm yeni uyarılar oluştur olmaz. Ancak, sınıf dikkatli incelenmesi, derleyicinin akış analizi sınırlamaları bazılarını göstermeyi yardımcı olur. Oluşturucu inceleyin:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` Nonnullable başvuru olarak parametre türü belirtilmiş. Derleyici, gerçekten bilmez için ASP.NET Core altyapı koduna göre adlandırılır `IMapper` hiçbir zaman null olmaz. ASP.NET Core bağımlılık ekleme (dı) kapsayıcısını varsayılan kod doğru Bu nedenle gerekli bir hizmeti çözümlenemiyor bir özel durum oluşturur. Boş değer atanabilir bir ek açıklama bağlamlarla etkin kod derlenir olsa bile derleyici genel apı'lerinize tüm çağrıları doğrulanamıyor. Ayrıca, Kitaplıklarınızı henüz null başvuru türleri kullanarak geri çevirdiniz olmayan projeleri tarafından tüketilebilir. Nonnullable türleri olarak bildirdikten olsa da, genel API'ler girişleri doğrulayın.

## <a name="get-the-code"></a>Kodu alma

İlk test derleme içinde tanımlanan uyarıları düzelttik bunu şimdi iki proje için boş değer atanabilir bir ek açıklama bağlam etkinleştirebilirsiniz. Projeleri yeniden oluşturun; Derleyici Uyarı bildirir. Tamamlanan proje için kodu alma [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) GitHub deposu.

Null başvuru türleri bulmanıza ve düzeltmenize nasıl işleneceğini olası hataları Yardım destekleyen yeni özellikleri `null` kodunuzda değerleri. Boş değer atanabilir bir ek açıklama bağlam etkinleştirme tasarım amacınızla express olanak tanır: bazı değişkenler hiçbir zaman null olmamalıdır, diğer değişkenler null değerler içerebilir. Bu özellikler, tasarım amacı bildirmek kolaylaştırır. Benzer şekilde, bu hedefi ihlal edildi, boş değer atanabilir uyarı bağlamı sorunu uyarılar için derleyicinin sağlar. Bu uyarılar kodunuz daha dayanıklı ve daha az throw olasılığı yaptığınız güncelleştirmeler yapmak için size yol gösterecek bir `NullReferenceException` yürütme sırasında. Böylece yerel alanlara kalan codebase dokunulmadan olmakla birlikte geçirmek için kod odaklanabilir şu bağlamlarda kapsamını kontrol edebilirsiniz. Uygulamada, bir parçası, sınıflara düzenli bakım görevi bu geçiş yapabilirsiniz. Bu öğreticinin başvuru boş değer atanabilir türleri kullanmak için bir uygulama geçiş süreci gösterilmektedir. Çekme isteği inceleyerek bu işlemin daha büyük bir gerçek örneğin keşfedebilirsiniz [Jon Skeet](https://github.com/jskeet) null başvuru türlerine eklemek için yapılan [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
