---
title: Nullable başvuru türlerine yükseltme
description: Bu gelişmiş öğretici, nullable başvuru türleri ile varolan kodun nasıl geçirilen gösterir.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 9767493059623e770cc100b83b9284e8d0bdf0f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156460"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Öğretici: Kullanılabilir başvuru türleri ile varolan kodu geçirin

C# 8, başvuru türlerini, nullable değer türlerinin değer türlerini tamamladığı şekilde tamamlayan **nullable başvuru türlerini**tanır. Bir değişkeni, a **nullable reference type** `?` türünü ekleyerek geçersiz bir başvuru türü olarak beyan elabilirsiniz. Örneğin, `string?` nullable `string`temsil eder. Tasarım amacınızı daha net ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olmalıdır,* diğerleri bir değer eksik *olabilir.* Bir başvuru türünün varolan değişkenleri nullable olmayan bir başvuru türü olarak yorumlanır.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Kodla çalışırken null başvuru denetimlerini etkinleştirin.
> - Null değerleri ile ilgili farklı uyarıları tanıkoyun ve düzeltin.
> - Boşatılabilir etkin ve nullable devre dışı bağlamları arasındaki arabirimi yönetin.
> - Geçersiz ek açıklama bağlamlarını denetle.

## <a name="prerequisites"></a>Önkoşullar

C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir. C# 8 derleyicisi [Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

Bu öğretici, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET'e aşina olduğunuzu varsayar.

## <a name="explore-the-sample-application"></a>Örnek uygulamayı keşfedin

Geçireceğiniz örnek uygulama bir RSS özet akışı okuyucu web uygulamasıdır. Tek bir RSS akışından okur ve en son makalelerin özetlerini görüntüler. Siteyi ziyaret etmek için makalelerden herhangi birini seçebilirsiniz. Uygulama nispeten yenidir, ancak geçersiz başvuru türleri kullanılabilir olmadan önce yazılmıştır. Uygulama nın tasarım kararları sağlam ilkeleri temsil eder, ancak bu önemli dil özelliğinden yararlanamaz.

Örnek uygulama, uygulamanın ana işlevselliğini doğrulayan bir birim test kitaplığı içerir. Oluşturulan uyarılara göre uygulamadan herhangi birini değiştirirseniz, bu proje güvenli bir şekilde yükseltmeyi kolaylaştırır. Başlangıç kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub deposundan indirebilirsiniz.

Bir projeyi geçirme amacınız, değişkenlerin geçersiz liği konusundaki niyetinizi açıkça ifade edebilmeniz için yeni dil özelliklerinden yararlanmak ve bunu, geçersiz ek açıklama bağlamı ve geçersiz uyarı bağlamı `enabled`ayarlanmış olduğunda derleyicinin uyarı oluşturmayacak şekilde yapmak olmalıdır.

## <a name="upgrade-the-projects-to-c-8"></a>Projeleri C# 8'e yükseltin

İyi bir ilk adım geçiş görevinin kapsamını belirlemektir. Projeyi C# 8.0 (veya daha yeni) olarak yükselterek başlayın. Web `LangVersion` projesi ve birim test projesi için hem csproj dosyalarında Özellik Grubu'na öğeyi ekleyin:

```xml
<LangVersion>8.0</LangVersion>
```

Dil sürümünü yükseltmek C# 8.0'ı seçer, ancak geçersiz ek açıklama bağlamını veya nullable uyarı bağlamını etkinleştirmez. Uyarı olmadan oluşturduğundan emin olmak için projeyi yeniden oluşturun.

İyi bir sonraki adım, geçersiz ek açıklama bağlamını açmak ve kaç uyarı oluşturulduğunu görmektir. Çözümdeki her iki csproj dosyasına doğrudan öğenin altına aşağıdaki öğeyi `LangVersion` ekleyin:

```xml
<Nullable>enable</Nullable>
```

Bir test oluşturma yapın ve uyarı listesine dikkat edin. Bu küçük uygulamada, derleyici beş uyarı oluşturur, bu nedenle geçersiz ek açıklama bağlamını etkin bırakmanız ve tüm proje için uyarıları düzeltmeye başlamanız olasıdır.

Bu strateji sadece küçük projeler için çalışır. Daha büyük projelerde, tüm kod tabanı için geçersiz ek açıklama bağlamını etkinleştirerek oluşturulan uyarı sayısı, uyarıların sistematik olarak düzeltilmesini zorlaştırır. Daha büyük kurumsal projeler için, genellikle aynı anda bir projeyi geçirmek isteyebilirsiniz. Her projede, aynı anda bir sınıf veya dosya geçirin.

## <a name="warnings-help-discover-original-design-intent"></a>Uyarılar orijinal tasarım amacını keşfetmeye yardımcı olur

Birden çok uyarı oluşturan iki sınıf vardır. Dersten `NewsStoryViewModel` başla. Uyarıların `Nullable` kapsamını çalıştığınız kod bölümleriyle sınırlamak için öğeyi her iki csproj dosyasından da kaldırın. *NewsStoryViewModel.cs* dosyasını açın ve geçersiz ek açıklama bağlamını etkinleştirmek `NewsStoryViewModel` için aşağıdaki yönergeleri ekleyin ve bu sınıf tanımını takip ederek geri yükleyin:

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

Bu iki yönerge, geçiş çabalarınızı odaklamanıza yardımcı olur. Etkin olarak üzerinde çalıştığınız kod alanı için geçersiz uyarılar oluşturulur. Tüm proje için uyarıları açmaya hazır olana kadar onları alıkonacaksınız. Tüm proje `restore` için `disable` geçersiz ek açıklamaları açtığınızda bağlamı yanlışlıkla devre dışı düşürmemek için değer yerine kullanmalısınız. Tüm proje için geçersiz ek açıklama bağlamını açtıktan sonra, bu `#nullable` projedeki tüm pragmları kaldırabilirsiniz.

Sınıf `NewsStoryViewModel` bir veri aktarım nesnesi (DTO) ve iki özellikleri okuma/yazma dizeleri vardır:

[!code-csharp[InitialViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Bu iki `CS8618`özellik , "Nullable özellik başlatılamaz" neden olur. Bu yeterince açık: `string` her iki özellik `null` de `NewsStoryViewModel` bir inşa edildiğinde varsayılan değerine sahiptir. Keşfedilmesi gereken şey nesnelerin `NewsStoryViewModel` nasıl oluşturulduredildiğidir. Bu sınıfa baktığınızda, değerin `null` tasarımın bir parçası olup olmadığını veya bu nesnelerin oluşturulduğunda null olmayan değerlere ayarlı olup olmadığını söyleyemezsiniz. Haberler `GetNews` `NewsService` sınıfın yönteminde oluşturulur:

[!code-csharp[StarterCreateNewsItem](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Bir önceki kod bloğunda bir sürü şey oluyor. Bu uygulama bir `ISyndicationItem`haber öğesi oluşturmak için [AutoMapper](https://automapper.org/) NuGet paketini kullanır. Haber öğelerinin oluşturuldurdığını ve özelliklerin bu ifadede ayarlandığını keşfettiniz. Bu, bu özelliklerin hiçbir zaman `NewsStoryViewModel` değere `null` sahip olmaması gerektiğini gösterir için tasarım anlamına gelir. Bu özellikler **nullable olmayan başvuru türleri**olmalıdır. Bu en iyi orijinal tasarım amacı ifade eder. Aslında, herhangi `NewsStoryViewModel` bir doğru olmayan null değerleri ile *anında.* Bu, aşağıdaki başlatma kodunu geçerli bir düzeltme yapar:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

`Title` Tür `Uri` `null` için ve `default` hangi tür `string` için atama programın çalışma zamanı davranışını değiştirmez. Hala `NewsStoryViewModel` null değerleri ile inşa edilir, ancak şimdi derleyici hiçbir uyarı bildirir. **Null-affgiving işleci** `!` , `default` ifadeyi izleyen karakter derleyiciye önceki ifadenin null olmadığını söyler. Diğer değişiklikler bir kod tabanında çok daha büyük değişiklikler zorlamak zaman bu teknik uygun olabilir, ancak bu `NewsStoryViewModel` uygulamada nispeten hızlı ve daha iyi bir çözüm var: Tüm özellikleri oluşturucu ayarlanır değişmez bir tür olun. Aşağıdaki değişiklikleri `NewsStoryViewModel`yapın:

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Bu yapıldıktan sonra, Özellikleri ayarlamak yerine oluşturucuyu kullanabilmesi için AutoMapper'ı yapılandıran kodu güncelleştirmeniz gerekir. Açın `NewsService.cs` ve dosyanın alt kısmında aşağıdaki kodu arayın:

[!code-csharp[StarterAutoMapper](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu kod, nesnenin `ISyndicationItem` özelliklerini `NewsStoryViewModel` özelliklerle eşler. AutoMapper yerine bir oluşturucu kullanarak eşleme sağlamak istiyorum. Yukarıdaki kodu aşağıdaki automapper yapılandırmasıyla değiştirin:

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu sınıf küçük olduğundan ve dikkatle incelediğiniz için, bu `#nullable enable` sınıf bildiriminin üzerindeki yönergeleri açmanız gerektiğine dikkat edin. Oluşturucuya yapılan değişiklik bir şeyi kırmış olabilir, bu yüzden tüm testleri çalıştırmak ve devam etmeden önce uygulamayı test etmek faydalıdır.

İlk değişiklik kümesi, orijinal tasarımın değişkenlerin .'a `null`ayarlanmaması gerektiğini gösterdiğinde nasıl keşfedeceğinizi gösterdi. Teknik inşaat tarafından **doğru**olarak adlandırılır. Bir nesnenin ve özelliklerinin `null` oluşturulduğunda olamayacağını beyan emzebilirsiniz. Derleyicinin akış analizi, bu özelliklerin `null` inşaattan sonra ayarlmamalarına dair güvence sağlar. Bu oluşturucu nun dış kodla çağrıldığını ve bu kodun **geçersiz**olduğunu unutmayın. Yeni sözdizimi çalışma zamanı denetimi sağlamaz. Dış kod derleyicinin akış çözümlemesi atlatmak olabilir.

Diğer zamanlarda, bir sınıfın yapısı niyet için farklı ipuçları sağlar. Error.cshtml.cs *dosyasını* *Sayfalar* klasöründe açın. Aşağıdaki `ErrorViewModel` kodu içerir:

[!code-csharp[StarterErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Yönergeyi `#nullable enable` sınıf bildiriminden önce `#nullable restore` ve ondan sonra bir yönerge ekleyin. Başharfe basılmayan `RequestId` bir uyarı alırsınız. Sınıfa bakarak, özelliğin `RequestId` bazı durumlarda geçersiz olduğuna karar vermelisiniz. Özelliğin `ShowRequestId` varlığı eksik değerlerin mümkün olduğunu gösterir. Geçerli `null` olduğundan, `?` `string` `RequestId` *özelliğin geçersiz bir başvuru türü*olduğunu belirtmek için üzerine türünü ekleyin. Son sınıf aşağıdaki örnek gibi görünür:

[!code-csharp[FinishedErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Özelliğin kullanımlarını denetleyin ve ilişkili sayfada özelliğin biçimlendirmede oluşturmadan önce geçersiz olup olmadığını niçin denetlediğinizi görürsünüz. Bu, boşsayılabilir bir başvuru türünün güvenli bir kullanımıdır, yani bu sınıfla işi bitti.

## <a name="fixing-nulls-causes-change"></a>Nulls sabitleme değişime neden olur

Sık sık, bir uyarı kümesi nin düzeltmesi ilgili kodda yeni uyarılar oluşturur. `index.cshtml.cs` Sınıfı düzelterek uyarıları hareket halinde görelim. Dosyayı `index.cshtml.cs` açın ve kodu inceleyin. Bu dosya dizin sayfasının arkasındaki kodu içerir:

[!code-csharp[StarterIndexModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Yönergeyi `#nullable enable` ekleyin ve iki uyarı görürsünüz. Ne `ErrorText` özellik ne `NewsItems` de özellik paraya yatırılmış. Bu sınıfın incelenmesi, her iki özelliğin de geçersiz başvuru türleri olması gerektiğine inanmanızı sağlar: Her ikisinin de özel ayarlayıcıları vardır. Tam bir `OnGet` yöntemde atanır. Değişiklik yapmadan önce, her iki özelliğin tüketicilerine bakın. Sayfanın kendisinde, `ErrorText` herhangi bir hata için biçimlendirme oluşturmadan önce null'a karşı denetlenir. Koleksiyon `NewsItems` aleyhine `null`denetlenir ve koleksiyonun öğeleri olduğundan emin olmak için denetlenir. Hızlı bir düzeltme her iki özellik geçersiz başvuru türleri yapmak olacaktır. Daha iyi bir düzeltme, koleksiyonu geçersiz bir başvuru türü haline getirmek ve haber alırken varolan koleksiyona öğe eklemek olacaktır. İlk düzeltme için `?` `string` türüne `ErrorText`eklemektir:

[!code-csharp[UpdateErrorText](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Bu değişiklik diğer kodlar arasında dalgalanmaz, `ErrorText` çünkü tesise herhangi bir erişim zaten geçersiz çeklerle korunuyordu. Ardından, listeyi `NewsItems` başlatma ve özellik ayarlayıcısını kaldırarak yalnızca okunan bir özellik haline getirin:

[!code-csharp[InitializeNewsItems](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Bu uyarı sabit ama bir hata tanıttı. Liste `NewsItems` artık **inşaat tarafından doğru,** ancak listeyi `OnGet` ayarlayan kodun yeni API ile eşleşecek şekilde değişmesi gerekir. Atama yerine, haber `AddRange` öğelerini varolan listeye eklemek için arayın:

[!code-csharp[AddRange](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Atama `AddRange` yerine kullanmak, yöntemin `GetNews` bir `IEnumerable` `List`. yerine bir ' yi döndürebileceği anlamına gelir Bu bir ayırma kaydeder. Yöntemin imzasını değiştirin ve `ToList` aşağıdaki kod örneğinde gösterildiği gibi aramayı kaldırın:

[!code-csharp[GetNews](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

İmzayı değiştirmek de testlerden birini bozar. Proje `NewsServiceTests.cs` klasöründeki `Services` dosyayı `SimpleFeedReader.Tests` açın. `Returns_News_Stories_Given_Valid_Uri` Teste gidin ve `result` değişkenin türünü ' e `IEnumerable<NewsItem>`değiştirin. Türü değiştirmek `Count` özelliğin artık kullanılamadığı anlamına `Count` gelir, `Assert` bu nedenle `Any()`aşağıdaki leri arayarak özelliği değiştirin:

[!code-csharp[FixTests](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Dosyanın başına da `using System.Linq` bir deyim eklemeniz gerekir.

Bu değişiklik kümesi, genel anlık özellikleri içeren kodu güncellerken özel bir dikkat çeker. Hem liste hem de nullable olmayan türler listesindeki öğeler. Ya da her ikisi de geçersiz türleri olabilir. Aşağıdaki tüm bildirimlere izin verilir:

- `List<NewsStoryViewModel>`: geçersiz görünüm modellerinin geçersiz listesi.
- `List<NewsStoryViewModel?>`: nullable görünüm modelleri geçersiz listesi.
- `List<NewsStoryViewModel>?`: nullable görünüm modelleri listesi.
- `List<NewsStoryViewModel?>?`: nullable görünüm modelleri geçersiz listesi.

## <a name="interfaces-with-external-code"></a>Harici kodlu arabirimler

`NewsService` Sınıfta değişiklik yaptınız, bu yüzden o `#nullable enable` sınıfın ek açıklamalarını açın. Bu, yeni uyarılar oluşturmaz. Ancak, sınıfın dikkatli bir şekilde incelenmesi derleyicinin akış analizinin bazı sınırlamalarını göstermeye yardımcı olur. Oluşturucuyu inceleyin:

[!code-csharp[ServiceConstructor](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

Parametre `IMapper` geçersiz bir başvuru olarak yazılır. ASP.NET Core altyapı kodu tarafından çağrılır, bu nedenle derleyici `IMapper` asla null olmayacağını bilmez. Varsayılan ASP.NET Çekirdek bağımlılık enjeksiyonu (DI) kapsayıcısı, gerekli bir hizmeti çözemezse bir özel durum oluşturur, bu nedenle kod doğrudur. Derleyici, kodunuz boş ek açıklama bağlamları etkinleştirilmiş olarak derlenmiş olsa bile, herkese açık API'larınıza yapılan tüm çağrıları doğrulayamamaktadır. Ayrıca, kitaplıklarınız henüz geçersiz başvuru türlerini kullanmayı seçmemiş projeler tarafından tüketilebilir. Girdileri, geçersiz türler olarak beyan etmenize rağmen herkese açık API'lere doğrulayın.

## <a name="get-the-code"></a>Kodu alma

İlk test derlemesinde tanımladığınız uyarıları düzelttin, böylece artık her iki proje için de geçersiz ek açıklama bağlamını açabilirsiniz. Projeleri yeniden oluşturma; derleyici hiçbir uyarı bildirir. Tamamlanan projenin kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) GitHub deposundan alabilirsiniz.

Geçersiz başvuru türlerini destekleyen yeni özellikler, kodunuzdaki değerleri `null` işleme şeklinizdeki olası hataları bulmanıza ve düzeltmenize yardımcı olur. Nullable ek açıklama bağlamını etkinleştirmek tasarım amacınızı ifade etmenizi sağlar: bazı değişkenler asla null olmamalıdır, diğer değişkenler null değerleri içerebilir. Bu özellikler, tasarım amacınızı bildirmenizi kolaylaştırır. Benzer şekilde, geçersiz uyarı bağlamı derleyiciye bu amacı ihlal ettiğinizde uyarı lar yayınlamasını bildirir. Bu uyarılar, kodunuzu daha esnek ve yürütme sırasında atma `NullReferenceException` olasılığını azaltan güncelleştirmeler yapmak için size yol gösterin. Kalan kod tabanına dokunulmamışken geçirilebilmek için yerel kod alanlarına odaklanabilmek için bu bağlamların kapsamını denetleyebilirsiniz. Uygulamada, bu geçiş görevini sınıflarınıza düzenli bakımın bir parçası yapabilirsiniz. Bu öğretici, geçersiz başvuru türlerini kullanmak için bir uygulamayı geçirme işlemini göstermiştir. Bu sürecin daha büyük bir gerçek dünya [örneğini, NodaTime'a](https://github.com/nodatime/nodatime/pull/1240/commits)nullable referans türlerini dahil etmek için yapılan PR [Jon Skeet'i](https://github.com/jskeet) inceleyerek keşfedebilirsiniz. Ya da sadece ek olarak, Varlık Framework Core Entity Framework Core ile nullable referans türleri kullanma teknikleri öğrenebilirsiniz [- nullable referans türleri ile çalışma](/ef/core/miscellaneous/nullable-reference-types).
