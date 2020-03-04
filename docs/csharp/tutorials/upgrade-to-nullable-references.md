---
title: Null yapılabilir başvuru türlerine yükselt
description: Bu gelişmiş öğreticide, var olan kodun null yapılabilir başvuru türleriyle nasıl geçirileceği gösterilmektedir.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 38619f9efa5da1f9b3264b3d4240103f0869afea
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240034"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Öğretici: mevcut kodu Nullable başvuru türleriyle geçirme

C#8, null olabilen değer türleri için aynı şekilde, başvuru türlerini tamamlayan **null yapılabilir başvuru türlerini**tanıtır. Türe bir `?` ekleyerek **null olabilen bir başvuru türü** olarak bir değişken bildirirsiniz. Örneğin `string?`, null yapılabilir bir `string`temsil eder. Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir. Bir başvuru türünün varolan değişkenleri, null olamayan bir başvuru türü olarak yorumlanır. 

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Kodla çalışırken null başvuru denetimlerini etkinleştirin.
> - Null değerlerle ilgili farklı uyarıları tanılayın ve düzeltin.
> - Null yapılabilir etkin ve null yapılabilir devre dışı bağlamların arabirimini yönetin.
> - Null yapılabilir ek açıklama bağlamlarını denetleyin.

## <a name="prerequisites"></a>Önkoşullar

Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir. 8 C# derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="explore-the-sample-application"></a>Örnek uygulamayı keşfet

Geçirilecek örnek uygulama bir RSS Akış okuyucusu web uygulamasıdır. Tek bir RSS akışından okur ve en son makalelerin özetlerini görüntüler. Siteyi ziyaret etmek için makalelerden herhangi birini seçebilirsiniz. Uygulama nispeten yenidir ancak null yapılabilir başvuru türleri kullanılabilir olmadan önce yazılmıştır. Uygulama için gösterilen ve bu önemli dil özelliğinden yararlanmamak için sunulan tasarım kararları.

Örnek uygulama, uygulamanın ana işlevlerini doğrulayan bir birim testi kitaplığı içerir. Oluşturulan uyarılara göre herhangi bir uygulamayı değiştirirseniz, bu proje güvenli bir şekilde yükseltmeyi daha kolay hale getirir. Başlangıç kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub deposundan indirebilirsiniz.

Bir projeyi geçirme hedefiniz yeni dil özelliklerinden faydalanır, böylece amacınızı null olabilir ve bu sayede, null yapılabilir ek açıklama bağlamı ve null atanabilir uyarı bağlamı `enabled`olarak ayarlanmış olduğunda derleyicinin uyarı üretmemesi gerekir.

## <a name="upgrade-the-projects-to-c-8"></a>Projeleri 8 ' e C# yükseltin

Geçiş görevinin kapsamını belirlemekte iyi bir ilk adım vardır. Projeyi C# 8,0 (veya daha yeni) sürümüne yükselterek başlayın. Web projesi ve birim test projesi için her iki csproj dosyasında bulunan PropertyGroup öğesine `LangVersion` öğesini ekleyin:

```xml
<LangVersion>8.0</LangVersion>
```

Dil sürümünü yükseltmek 8,0 seçer C# , ancak null yapılabilir ek açıklama bağlamını veya null yapılabilir uyarı bağlamını etkinleştirmez. Uyarı vermeden oluşturulduğundan emin olmak için projeyi yeniden derleyin.

İyi bir sonraki adım, null yapılabilir ek açıklama bağlamını açıp kaç uyarı oluşturulduğunu görmenizde yarar vardır. Çözümdeki her iki csproj dosyasına doğrudan `LangVersion` öğesi altında aşağıdaki öğeyi ekleyin:

```xml
<Nullable>enable</Nullable>
```

Bir test derlemesi yapın ve uyarı listesine dikkat edin. Bu küçük uygulamada, derleyici beş uyarı üretir, bu nedenle null yapılabilir ek açıklama bağlamını etkin bırakıp tüm proje için uyarıları düzeltmeye başlayabilirsiniz.

Bu strateji yalnızca daha küçük projeler için geçerlidir. Daha büyük projeler için, tüm kod tabanı için Nullable ek açıklama bağlamını etkinleştirerek oluşturulan uyarı sayısı, uyarıları sistematik olarak gidermeyi zorlaştırır. Daha büyük kurumsal projelerde, genellikle bir projeyi tek seferde geçirmek isteyeceksiniz. Her projede, tek bir sınıf veya dosyayı aynı anda geçirin.

## <a name="warnings-help-discover-original-design-intent"></a>Uyarılar özgün tasarım amacını bulmaya yardımcı olur

Birden çok uyarı oluşturan iki sınıf vardır. `NewsStoryViewModel` sınıfıyla başlayın. Uyarı kapsamını çalıştığınız kodun bölümleriyle sınırlayabilmeniz için her iki csproj dosyasından `Nullable` öğesini kaldırın. *NewsStoryViewModel.cs* dosyasını açın ve aşağıdaki yönergeleri ekleyerek `NewsStoryViewModel` için Nullable ek açıklama bağlamını etkinleştirin ve bu sınıf tanımını izleyerek geri yükleyin:

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

Bu iki yönergeler, geçiş çabalarınıza odaklanmaya yardımcı olur. Üzerinde etkin olarak çalışmakta olduğunuz kod alanı için null yapılabilir uyarılar oluşturulur. Projenin tamamına yönelik uyarıları açmaya hazırsanız, bunları açık bırakmalısınız. Tüm proje için null yapılabilir ek açıklamaları açtığınızda bağlamı yanlışlıkla devre dışı bırakabilmeniz için `disable` değeri yerine `restore` kullanmanız gerekir. Tüm proje için null yapılabilir ek açıklama bağlamını etkinleştirdikten sonra, bu projeden tüm `#nullable` pragmaları kaldırabilirsiniz.

`NewsStoryViewModel` sınıfı bir veri aktarım nesnesidir (DTO) ve özelliklerden ikisi okuma/yazma dizeleridir:

[!code-csharp[InitialViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Bu iki özellik `CS8618`, "null yapılamayan özelliğin başlatılmamış" olmasına neden olur. Bu yeterince net: her iki `string` özelliği de bir `NewsStoryViewModel` oluşturulduğunda `null` varsayılan değerine sahiptir. Bulma için önemli olan özellikler `NewsStoryViewModel` nesneleri nasıl oluşturulur. Bu sınıfa bakarak, `null` değerinin tasarımın bir parçası olup olmadığını veya bu nesnelerin her biri oluşturulduğunda null olmayan değerlere ayarlanmış olduğunu söyleyebilirsiniz. Haber hikayeleri, `NewsService` sınıfının `GetNews` yönteminde oluşturulur:

[!code-csharp[StarterCreateNewsItem](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Yukarıdaki kod bloğunda oldukça bir bit vardır. Bu uygulama, bir `ISyndicationItem`haber öğesi oluşturmak için [Automaber](https://automapper.org/) NuGet paketini kullanır. Haber hikayesi öğelerinin oluşturulduğunu ve özellikler söz konusu bir bildirimde ayarlandığını keşfettiniz. Bu, `NewsStoryViewModel` tasarımının bu özelliklerin hiçbir durumda `null` değerine sahip olmayacağını gösterir. Bu özellikler **null atanamaz başvuru türleri**olmalıdır. Bu, özgün tasarım amacını en iyi ifade eder. Aslında, hiçbir `NewsStoryViewModel` null olmayan değerler ile doğru *şekilde oluşturulur.* Bu, aşağıdaki başlatma kodunu geçerli bir çözüm haline getirir:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

`string` tür için `null` olan `default` `Title` ve `Uri` ataması programın çalışma zamanı davranışını değiştirmez. `NewsStoryViewModel` hala null değerlerle oluşturulmuş, ancak derleyici hiçbir uyarı raporluyor. **Null-forverme işleci**, `default` ifadesini izleyen `!` karakteri derleyiciye önceki ifadenin null olmadığını söyler. Bu teknik, diğer değişiklikler bir kod tabanında çok daha büyük değişiklikler yaparken, ancak bu uygulamada görece hızlı ve daha iyi bir çözüm olduğu zaman, `NewsStoryViewModel`: tüm özelliklerin oluşturucuda ayarlandığı sabit bir tür haline gelebilir. `NewsStoryViewModel`aşağıdaki değişiklikleri yapın:

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Bu yapıldıktan sonra, özellikleri ayarlamak yerine, oluşturucuyu kullanması için Automaber 'yi yapılandıran kodu güncelleştirmeniz gerekir. `NewsService.cs` açın ve dosyanın en altında aşağıdaki kodu arayın:

[!code-csharp[StarterAutoMapper](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu kod, `ISyndicationItem` nesnesinin özelliklerini `NewsStoryViewModel` özellikleriyle eşler. Bunun yerine bir Oluşturucu kullanarak, Automaber 'nin eşleme sağlamasını istersiniz. Yukarıdaki kodu aşağıdaki automaber yapılandırmasıyla değiştirin:

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu sınıf küçük olduğu ve dikkatle incelediğiniz için, bu sınıf bildiriminin üzerinde `#nullable enable` yönergesini açmanız gerektiğine dikkat edin. Kurucudaki değişiklik bir şeyi bozarak, tüm testleri çalıştırmak ve devam etmeden önce uygulamayı test etmek daha fazla olabilir.

İlk değişiklik kümesi, özgün tasarımın değişkenlerin `null`olarak ayarlanmamalıdır. Teknik, **oluşturma tarafından doğru**olarak adlandırılır. Bir nesne ve özellikleri oluşturulduğunda `null` olduğunu bildirirsiniz. Derleyicinin akış analizi, bu özelliklerin oluşturulduktan sonra `null` olarak ayarlanmadığından emin olmak için güvence sağlar. Bu oluşturucunun dış kod tarafından çağrıldığını ve kodun **null değer atanabilir yükümlülüğü**olduğunu unutmayın. Yeni sözdizimi çalışma zamanı denetimi sağlamaz. Dış kod derleyicinin akış analizini atlatılabilir. 

Diğer zamanlarda, bir sınıfın yapısı amaç için farklı ipuçları sağlar. *Error.cshtml.cs* dosyasını *Sayfalar* klasöründe açın. `ErrorViewModel` aşağıdaki kodu içerir:

[!code-csharp[StarterErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Sınıf bildiriminden önce `#nullable enable` yönergesini ve sonra bir `#nullable restore` yönergesini ekleyin. `RequestId` başlatılmamış bir uyarı alırsınız. Sınıfına bakarak, bazı durumlarda `RequestId` özelliğinin null olması gerektiğine karar vermeniz gerekir. `ShowRequestId` özelliğinin varlığı eksik değerlerin mümkün olduğunu gösterir. `null` geçerli olduğundan, `RequestId` özelliğinin *null yapılabilir bir başvuru türü*olduğunu göstermek için `string` türüne `?` ekleyin. Son sınıf aşağıdaki örneğe benzer şekilde görünür:

[!code-csharp[FinishedErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Özelliğin kullanımlarını denetleyin ve ilgili sayfada özelliği, biçimlendirme sırasında işlemeden önce, özelliğinin null olarak denetlendiğini görürsünüz. Bu, null olabilen bir başvuru türünün güvenli bir kullanımı olduğundan bu sınıfla işiniz bitti.

## <a name="fixing-nulls-causes-change"></a>Null değerleri düzeltme değişikliğine neden olur

Genellikle, bir uyarı kümesinin düzeltilmesi ilgili kodda yeni uyarılar oluşturur. `index.cshtml.cs` sınıfını düzelterek, uyarıları eylemde görelim. `index.cshtml.cs` dosyasını açın ve kodu inceleyin. Bu dosya dizin sayfası için arkasındaki kodu içerir:

[!code-csharp[StarterIndexModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

`#nullable enable` yönergesini ekleyin ve iki uyarı görürsünüz. `ErrorText` özelliği ne de `NewsItems` özelliği başlatılmaz. Bu sınıfın incelenmesi, her iki özelliği de null yapılabilir başvuru türleri olması gerektiğini düşünmenize yol açacağından, her Ikisinin de özel ayarlayıcıları vardır. `OnGet` yönteminde tam olarak bir atanır. Değişiklik yapmadan önce her iki özelliği de tüketicilere bakın. Sayfanın kendisinde, herhangi bir hata için biçimlendirme oluşturmadan önce `ErrorText` null olarak denetlenir. `NewsItems` koleksiyonu `null`karşı denetlenir ve koleksiyonda öğeler olduğundan emin olmak için denetlenir. Hızlı bir çözüm, her iki özelliği de null yapılabilir başvuru türlerini yapmak olacaktır. Daha iyi bir çözüm, koleksiyonu null yapılamayan bir başvuru türü yapmak ve haberleri alırken mevcut koleksiyona öğe eklemek olacaktır. İlk çözüm, `?` `ErrorText``string` türüne eklemektir:

[!code-csharp[UpdateErrorText](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

`ErrorText` özelliğine herhangi bir erişim null denetimleri tarafından zaten korunduğu için, bu değişiklik diğer kod aracılığıyla görünmez olmayacaktır. Sonra, `NewsItems` listesini başlatın ve özellik ayarlayıcısını kaldırarak salt okunur bir özellik yaparak:

[!code-csharp[InitializeNewsItems](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Bu, uyarıyı düzeltti ancak bir hata sunmuştur. `NewsItems` listesi artık **yapım tarafından düzeltilir**, ancak `OnGet` listesini ayarlayan kod yeni API ile eşleşecek şekilde değişmelidir. Bir atama yerine, mevcut listeye haber öğelerini eklemek için `AddRange` çağırın:

[!code-csharp[AddRange](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Atama yerine `AddRange` kullanmak `GetNews` yönteminin `List`yerine `IEnumerable` döndürebileceği anlamına gelir. Bu, bir ayırmayı kaydeder. Metodun imzasını değiştirin ve aşağıdaki kod örneğinde gösterildiği gibi `ToList` çağrısını kaldırın:

[!code-csharp[GetNews](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

İmzanın değiştirilmesi, testlerin birini de keser. `NewsServiceTests.cs` dosyasını `SimpleFeedReader.Tests` projesinin `Services` klasöründe açın. `Returns_News_Stories_Given_Valid_Uri` testine gidin ve `result` değişkeninin türünü `IEnumerable<NewsItem>`olarak değiştirin. Türü değiştirmek `Count` özelliğinin artık kullanılamadığı anlamına gelir, bu nedenle `Assert` `Count` özelliğini `Any()`çağrısıyla değiştirin:

[!code-csharp[FixTests](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Dosyanın başlangıcına de `using System.Linq` bir ifade eklemeniz gerekecektir.

Bu değişiklik kümesi, genel örneklemeleri içeren kodu güncelleştirirken özel bir değerlendirme vurgulamaktadır. Hem liste hem de öğeler null yapılamayan türler listesinde. Ya da her ikisi de null yapılabilir türler olabilir. Aşağıdaki bildirimlere izin verilir:

- `List<NewsStoryViewModel>`: yinelenmeyen görünüm modellerinin null yapılamayan listesi.
- `List<NewsStoryViewModel?>`: null yapılabilir görünüm modellerinin Nullable listesi.
- `List<NewsStoryViewModel>?`: null yapılamayan görünüm modellerinin null olabilir listesi.
- `List<NewsStoryViewModel?>?`: null yapılabilir görünüm modellerinin null olabilir listesi.

## <a name="interfaces-with-external-code"></a>Dış kod içeren arabirimler

`NewsService` sınıfında değişiklikler yaptınız, bu nedenle söz konusu sınıfın `#nullable enable` ek açıklamasını etkinleştirin. Bu, yeni uyarı oluşturmaz. Ancak, sınıfının dikkatle incelenmesi derleyicinin akış analizinin bazı sınırlamalarını göstermeye yardımcı olur. Oluşturucuyu inceleyin:

[!code-csharp[ServiceConstructor](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` parametresi null atanamaz bir başvuru olarak yazılmış. ASP.NET Core altyapı kodu tarafından çağrılır, bu nedenle derleyici `IMapper` hiçbir şekilde null olmadığını bilmez. Varsayılan ASP.NET Core bağımlılık ekleme (dı) kapsayıcısı, gerekli bir hizmeti çözümleyemezse, kod doğru olduğunda bir özel durum oluşturur. Kodunuz null yapılabilir ek açıklama bağlamlarıyla derlense bile derleyici ortak API 'lerinize yapılan tüm çağrıları doğrulayamaz. Ayrıca, kitaplıklarınız henüz null yapılabilir başvuru türlerini kullanarak onaylanmamış projeler tarafından tüketilebilir. Bu girdileri null yapılamayan türler olarak bildirseniz bile ortak API 'lere yönelik girişleri doğrulayın.

## <a name="get-the-code"></a>Kodu alma

İlk test derlenmesi sırasında belirlediğiniz uyarıları düzelttiniz, bu nedenle artık her iki proje için de null yapılabilir ek açıklama bağlamını açabilirsiniz. Projeleri yeniden derleyin; Derleyici hiçbir uyarı rapor vermez. [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) GitHub deposundaki tamamlanmış projenin kodunu alabilirsiniz.

Null yapılabilir başvuru türlerini destekleyen yeni özellikler, kodunuzda `null` değerleri nasıl işleyeceğinizi bulmanıza ve düzeltmenize yardımcı olur. Null yapılabilir ek açıklama bağlamını etkinleştirmek, tasarım amacınızı ifade etmenizi sağlar: bazı değişkenler hiçbir şekilde null olmamalıdır, diğer değişkenler de null değerler içerebilir. Bu özellikler tasarım amacınızı bildirmenize daha kolay bir hale getirir. Benzer şekilde, null yapılabilir uyarı bağlamı derleyiciye bu amacı ihlal ettiğinizde uyarı vermesini söyler. Bu uyarılar, kodunuzu daha dayanıklı hale getirmek ve yürütme sırasında `NullReferenceException` oluşturması olasılığını azaltır. Geri kalan kod temeli dokunulmamış olsa da, geçirilecek yerel kod alanına odaklanabilmeniz için bu bağlamların kapsamını kontrol edebilirsiniz. Uygulamada, bu geçiş görevini sınıflarınıza düzenli bakımın bir parçası yapabilirsiniz. Bu öğretici, bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirme işlemini göstermiştir. Bu işlemin daha büyük bir gerçek dünya örneğini, null yapılabilir başvuru türlerini [Nodadtime](https://github.com/nodatime/nodatime/pull/1240/commits)ile birleştirmek IÇIN yapılan PR [Jon iskeet](https://github.com/jskeet) 'i inceleyerek inceleyebilirsiniz. Ya da buna ek olarak, null olabilen başvuru türleri [Ile çalışan Entity Framework Core](/ef/core/miscellaneous/nullable-reference-types)Entity Framework Core ile null yapılabilir başvuru türleri kullanmanın tekniklerini öğrenebilirsiniz.
