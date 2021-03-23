---
title: Null yapılabilir başvuru türlerine yükselt
description: Bu gelişmiş öğreticide, var olan kodun null yapılabilir başvuru türleriyle nasıl geçirileceği gösterilmektedir.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: dc254e8ca7b9451ab9374bc1ec650b8eaa9da861
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879123"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Öğretici: mevcut kodu Nullable başvuru türleriyle geçirme

C# 8 ' de, başvuru türlerini tamamlayan null olabilen değer türleri olan değer türlerini tamamlayan **null olabilen başvuru türleri** tanıtılmıştır. Bir değişkeni türüne ekleyerek **null atanabilir bir başvuru türü** olarak bildirirsiniz `?` . Örneğin, `string?` null yapılabilen bir değeri temsil eder `string` . Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik* olabilir. Bir başvuru türünün varolan değişkenleri, null olamayan bir başvuru türü olarak yorumlanır.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - Kodla çalışırken null başvuru denetimlerini etkinleştirin.
> - Null değerlerle ilgili farklı uyarıları tanılayın ve düzeltin.
> - Null yapılabilir etkin ve null yapılabilir devre dışı bağlamların arabirimini yönetin.
> - Null yapılabilir ek açıklama bağlamlarını denetleyin.

## <a name="prerequisites"></a>Önkoşullar

C# 8,0 derleyicisi dahil olmak üzere makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8 derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

Bu öğreticide, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="explore-the-sample-application"></a>Örnek uygulamayı keşfet

Geçirilecek örnek uygulama bir RSS Akış okuyucusu web uygulamasıdır. Tek bir RSS akışından okur ve en son makalelerin özetlerini görüntüler. Siteyi ziyaret etmek için makalelerden herhangi birini seçebilirsiniz. Uygulama nispeten yenidir ancak null yapılabilir başvuru türleri kullanılabilir olmadan önce yazılmıştır. Uygulama için gösterilen ve bu önemli dil özelliğinden yararlanmamak için sunulan tasarım kararları.

Örnek uygulama, uygulamanın ana işlevlerini doğrulayan bir birim testi kitaplığı içerir. Oluşturulan uyarılara göre herhangi bir uygulamayı değiştirirseniz, bu proje güvenli bir şekilde yükseltmeyi daha kolay hale getirir. Başlangıç kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/main/csharp/tutorials/nullable-reference-migration/start) GitHub deposundan indirebilirsiniz.

Bir projeyi geçirme hedefiniz yeni dil özelliklerinden faydalanır, böylece amacınızı null olabilir ve bu sayede, null yapılabilir ek açıklama bağlamı ve null yapılabilir uyarı bağlamı ayarlanmış olduğunda derleyicinin uyarı üretmemesi için bunu yapmanız gerekir `enabled` .

## <a name="upgrade-the-projects-to-c-8"></a>Projeleri C# 8 ' e yükseltme

Geçiş görevinin kapsamını belirlemekte iyi bir ilk adım vardır. Projeyi C# 8,0 (veya daha yeni) sürümüne yükselterek başlayın. `LangVersion`Web projesi ve birim test projesi için her iki csproj dosyasında öğesi PropertyGroup öğesine ekleyin:

```xml
<LangVersion>8.0</LangVersion>
```

Dil sürümünü yükseltmek C# 8,0 ' i seçer, ancak Nullable ek açıklama bağlamını veya null yapılabilir uyarı bağlamını etkinleştirmez. Uyarı vermeden oluşturulduğundan emin olmak için projeyi yeniden derleyin.

İyi bir sonraki adım, null yapılabilir ek açıklama bağlamını açıp kaç uyarı oluşturulduğunu görmenizde yarar vardır. Çözümdeki her iki csproj dosyasına ve doğrudan öğesinin altına aşağıdaki öğeyi ekleyin `LangVersion` :

```xml
<Nullable>enable</Nullable>
```

Bir test derlemesi yapın ve uyarı listesine dikkat edin. Bu küçük uygulamada, derleyici beş uyarı üretir, bu nedenle null yapılabilir ek açıklama bağlamını etkin bırakıp tüm proje için uyarıları düzeltmeye başlayabilirsiniz.

Bu strateji yalnızca daha küçük projeler için geçerlidir. Daha büyük projeler için, tüm kod tabanı için Nullable ek açıklama bağlamını etkinleştirerek oluşturulan uyarı sayısı, uyarıları sistematik olarak gidermeyi zorlaştırır. Daha büyük kurumsal projelerde, genellikle bir projeyi tek seferde geçirmek isteyeceksiniz. Her projede, tek bir sınıf veya dosyayı aynı anda geçirin.

## <a name="warnings-help-discover-original-design-intent"></a>Uyarılar özgün tasarım amacını bulmaya yardımcı olur

Birden çok uyarı oluşturan iki sınıf vardır. `NewsStoryViewModel`Sınıfıyla başlayın. `Nullable`Uyarı kapsamını çalıştığınız kodun bölümleriyle sınırlayabilmeniz için her iki csproj dosyasından öğeyi kaldırın. *Newsstoryviewmodel. cs* dosyasını açın ve için null yapılabilir ek açıklama bağlamını etkinleştirmek üzere aşağıdaki yönergeleri ekleyin `NewsStoryViewModel` ve bu sınıf tanımını izleyerek geri yükleyin:

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

Bu iki yönergeler, geçiş çabalarınıza odaklanmaya yardımcı olur. Üzerinde etkin olarak çalışmakta olduğunuz kod alanı için null yapılabilir uyarılar oluşturulur. Projenin tamamına yönelik uyarıları açmaya hazırsanız, bunları açık bırakmalısınız. `restore` `disable` Projenin tamamına yönelik null yapılabilir ek açıklamaları açtığınızda bağlamı yanlışlıkla devre dışı bırakmamanızı sağlamak için yerine, bu değeri kullanın. Tüm proje için Nullable ek açıklama bağlamını etkinleştirdikten sonra, `#nullable` bu projeden tüm pragmaları kaldırabilirsiniz.

`NewsStoryViewModel`Sınıf bir veri aktarım nesnesidir (DTO) ve özelliklerden ikisi okuma/yazma dizeleridir:

[!code-csharp[InitialViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Bu iki özellik neden `CS8618` "Nullable özelliği başlatılmamış" olur. Bu yeterince net: her iki `string` özellik de oluşturulduğunda varsayılan değerine sahiptir `null` `NewsStoryViewModel` . Bulma için önemli olan özellikler, nesnelerin nasıl oluşturulduğunu bir şeydir `NewsStoryViewModel` . Bu sınıfa baktığınızda, `null` değerin tasarımın bir parçası olup olmadığını veya bu nesnelerin her biri oluşturulduğunda null olmayan değerlere ayarlanmış olduğunu söyleyemiyoruz. Haber hikayeleri, `GetNews` sınıfının yönteminde oluşturulur `NewsService` :

[!code-csharp[StarterCreateNewsItem](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Yukarıdaki kod bloğunda oldukça bir bit vardır. Bu uygulama, öğesinden bir haber öğesi oluşturmak için [Automaber](https://automapper.org/) NuGet paketini kullanır `ISyndicationItem` . Haber hikayesi öğelerinin oluşturulduğunu ve özellikler söz konusu bir bildirimde ayarlandığını keşfettiniz. Bu, için tasarımının `NewsStoryViewModel` hiçbir şekilde bu özelliklerin değer vermediğini gösterdiği anlamına gelir `null` . Bu özellikler **null atanamaz başvuru türleri** olmalıdır. Bu, özgün tasarım amacını en iyi ifade eder. Aslında, hiçbiri `NewsStoryViewModel`  null olmayan değerler ile doğru şekilde oluşturulur. Bu, aşağıdaki başlatma kodunu geçerli bir çözüm haline getirir:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

`Title`Türü için olan ve `Uri` için ataması `default` `null` `string` programın çalışma zamanı davranışını değiştirmez. `NewsStoryViewModel`Hala null değerlerle oluşturulmuş, ancak derleyici hiçbir uyarı raporluyor. **Null-forverme işleci**, `!` ifadeden sonraki karakter `default` derleyiciye önceki ifadenin null olmadığını söyler. Bu teknik, diğer değişiklikler bir kod tabanında çok daha büyük değişiklikler yaparken, ancak bu uygulamada görece hızlı ve daha iyi bir çözüm varsa, bu durumda, `NewsStoryViewModel` tüm özelliklerin oluşturucuda ayarlandığı sabit bir tür haline gelebilir. Aşağıdaki değişiklikleri yapın `NewsStoryViewModel` :

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Bu yapıldıktan sonra, özellikleri ayarlamak yerine, oluşturucuyu kullanması için Automaber 'yi yapılandıran kodu güncelleştirmeniz gerekir. Açın `NewsService.cs` ve dosyanın en altında aşağıdaki kodu bulun:

[!code-csharp[StarterAutoMapper](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu kod, `ISyndicationItem` nesnenin özelliklerini `NewsStoryViewModel` özelliklerine eşler. Bunun yerine bir Oluşturucu kullanarak, Automaber 'nin eşleme sağlamasını istersiniz. Yukarıdaki kodu aşağıdaki automaber yapılandırmasıyla değiştirin:

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu sınıf küçük olduğundan ve dikkatle incelediğiniz için, `#nullable enable` Bu sınıf bildiriminin üzerindeki yönergeyi açmanız gerektiğini unutmayın. Kurucudaki değişiklik bir şeyi bozarak, tüm testleri çalıştırmak ve devam etmeden önce uygulamayı test etmek daha fazla olabilir.

İlk değişiklik kümesi, özgün tasarımın değişkenlerin olarak ayarlanmamalıdır ne zaman yapılacağını nasıl keşfedebileceğine ilişkin olduğunu gösterdi `null` . Teknik, **oluşturma tarafından doğru** olarak adlandırılır. Bir nesne ve özellikleri oluşturulduğunda bildiremezsiniz `null` . Derleyicinin akış analizi, bu özelliklerin oluşturma sonrasında olarak ayarlanmamış olduğunu güvence altına almaktadır `null` . Bu oluşturucunun dış kod tarafından çağrıldığını ve kodun **null değer atanabilir yükümlülüğü** olduğunu unutmayın. Yeni sözdizimi çalışma zamanı denetimi sağlamaz. Dış kod derleyicinin akış analizini atlatılabilir.

Diğer zamanlarda, bir sınıfın yapısı amaç için farklı ipuçları sağlar. *Sayfalar* klasöründe *Error. cshtml. cs* dosyasını açın. , `ErrorViewModel` Aşağıdaki kodu içerir:

[!code-csharp[StarterErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

`#nullable enable`Sınıf bildiriminden önce yönergesini ve `#nullable restore` sonra bir yönergeyi ekleyin. Başlatılmamış bir uyarı alırsınız `RequestId` . Sınıfına bakarak, `RequestId` bazı durumlarda özelliğin NULL olması gerektiğine karar vermeniz gerekir. `ShowRequestId`Özelliğin varlığı eksik değerlerin mümkün olduğunu gösterir. Geçerli olduğundan, `null` `?` `string` `RequestId` özelliğin *null yapılabilir bir başvuru türü* olduğunu göstermek için türüne öğesini ekleyin. Son sınıf aşağıdaki örneğe benzer şekilde görünür:

[!code-csharp[FinishedErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Özelliğin kullanımlarını denetleyin ve ilgili sayfada özelliği, biçimlendirme sırasında işlemeden önce, özelliğinin null olarak denetlendiğini görürsünüz. Bu, null olabilen bir başvuru türünün güvenli bir kullanımı olduğundan bu sınıfla işiniz bitti.

## <a name="fixing-nulls-causes-change"></a>Null değerleri düzeltme değişikliğine neden olur

Genellikle, bir uyarı kümesinin düzeltilmesi ilgili kodda yeni uyarılar oluşturur. Ayrıca, sınıfını düzelterek uyarıları görelim `index.cshtml.cs` . Dosyasını açın `index.cshtml.cs` ve kodu inceleyin. Bu dosya dizin sayfası için arkasındaki kodu içerir:

[!code-csharp[StarterIndexModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Yönergesini ekleyin `#nullable enable` ve iki uyarı görürsünüz. `ErrorText`Özellik ne de özellik `NewsItems` başlatılmaz. Bu sınıfın incelenmesi, her iki özelliği de null yapılabilir başvuru türleri olması gerektiğini düşünmenize yol açacağından, her Ikisinin de özel ayarlayıcıları vardır. Yöntemine tam olarak bir atanır `OnGet` . Değişiklik yapmadan önce her iki özelliği de tüketicilere bakın. Sayfanın kendisinde, `ErrorText` herhangi bir hata için biçimlendirme oluşturmadan önce null değeri denetlenir. `NewsItems`Koleksiyon öğesine karşı denetlenir `null` ve koleksiyonda öğeler olduğundan emin olmak için denetlenir. Hızlı bir çözüm, her iki özelliği de null yapılabilir başvuru türlerini yapmak olacaktır. Daha iyi bir çözüm, koleksiyonu null yapılamayan bir başvuru türü yapmak ve haberleri alırken mevcut koleksiyona öğe eklemek olacaktır. İlk düzeltilme türü için türüne eklemektir `?` `string` `ErrorText` :

[!code-csharp[UpdateErrorText](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Özelliğe herhangi bir erişim `ErrorText` null denetimleri tarafından zaten korunduğu için, bu değişiklik başka bir kod aracılığıyla görünmez olmayacaktır. Sonra, listeyi başlatın `NewsItems` ve özellik ayarlayıcısını kaldırın ve salt okunur bir özellik yapar:

[!code-csharp[InitializeNewsItems](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Bu, uyarıyı düzeltti ancak bir hata sunmuştur. `NewsItems`Liste artık oluşturma işlemi **tarafından düzeltilir**, ancak içinde listeyi ayarlayan kodun `OnGet` yeni API ile eşleşecek şekilde değiştirilmesi gerekir. Atama yerine, `AddRange` mevcut listeye haber öğelerini eklemek için çağırın:

[!code-csharp[AddRange](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

`AddRange`Atama yerine kullanmak, `GetNews` yöntemin yerine bir olarak dönebileceği anlamına gelir `IEnumerable` `List` . Bu, bir ayırmayı kaydeder. Aşağıdaki kod örneğinde gösterildiği gibi, yönteminin imzasını değiştirin ve `ToList` çağrıyı kaldırın:

[!code-csharp[GetNews](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

İmzanın değiştirilmesi, testlerin birini de keser. `NewsServiceTests.cs`Dosyayı `Services` projenin klasöründe açın `SimpleFeedReader.Tests` . `Returns_News_Stories_Given_Valid_Uri`Teste gidin ve `result` değişkenin türünü olarak değiştirin `IEnumerable<NewsItem>` . Türü değiştirmek `Count` özelliğin artık kullanılamadığı anlamına gelir, bu nedenle `Count` içindeki özelliğini `Assert` öğesine çağrısıyla değiştirin `Any()` :

[!code-csharp[FixTests](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

`using System.Linq`Dosyanın başlangıcına de bir ifade eklemeniz gerekecektir.

Bu değişiklik kümesi, genel örneklemeleri içeren kodu güncelleştirirken özel bir değerlendirme vurgulamaktadır. Hem liste hem de öğeler null yapılamayan türler listesinde. Ya da her ikisi de null yapılabilir türler olabilir. Aşağıdaki bildirimlere izin verilir:

- `List<NewsStoryViewModel>`: ullable olmayan görünüm modellerinin null yapılamayan listesi.
- `List<NewsStoryViewModel?>`: null yapılabilir görünüm modellerinin Nullable listesi.
- `List<NewsStoryViewModel>?`: null yapılamayan görünüm modellerinin null yapılabilir listesi.
- `List<NewsStoryViewModel?>?`: null yapılabilir görünüm modellerinin null olabilir listesi.

## <a name="interfaces-with-external-code"></a>Dış kod içeren arabirimler

Sınıfta değişiklikler yaptınız `NewsService` , `#nullable enable` Bu nedenle bu sınıf için ek açıklamayı etkinleştirin. Bu, yeni uyarı oluşturmaz. Ancak, sınıfının dikkatle incelenmesi derleyicinin akış analizinin bazı sınırlamalarını göstermeye yardımcı olur. Oluşturucuyu inceleyin:

[!code-csharp[ServiceConstructor](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper`Parametre null atanamaz bir başvuru olarak yazılmış. Bu, ASP.NET Core altyapı kodu tarafından çağrılır, bu nedenle derleyici `IMapper` hiçbir şekilde null olacağını gerçekten bilmez. Varsayılan ASP.NET Core bağımlılık ekleme (dı) kapsayıcısı, gerekli bir hizmeti çözümleyemezse, kod doğru olduğunda bir özel durum oluşturur. Kodunuz null yapılabilir ek açıklama bağlamlarıyla derlense bile derleyici ortak API 'lerinize yapılan tüm çağrıları doğrulayamaz. Ayrıca, kitaplıklarınız henüz null yapılabilir başvuru türlerini kullanarak onaylanmamış projeler tarafından tüketilebilir. Bu girdileri null yapılamayan türler olarak bildirseniz bile ortak API 'lere yönelik girişleri doğrulayın.

## <a name="get-the-code"></a>Kodu alma

İlk test derlenmesi sırasında belirlediğiniz uyarıları düzelttiniz, bu nedenle artık her iki proje için de null yapılabilir ek açıklama bağlamını açabilirsiniz. Projeleri yeniden derleyin; Derleyici hiçbir uyarı rapor vermez. [DotNet/Samples](https://github.com/dotnet/samples/tree/main/csharp/tutorials/nullable-reference-migration/finished) GitHub deposundaki tamamlanmış projenin kodunu alabilirsiniz.

Null yapılabilir başvuru türlerini destekleyen yeni özellikler, kodunuzda değerleri nasıl işleyeceğiniz potansiyel hataları bulmanıza ve düzeltmenize yardımcı olur `null` . Null yapılabilir ek açıklama bağlamını etkinleştirmek, tasarım amacınızı ifade etmenizi sağlar: bazı değişkenler hiçbir şekilde null olmamalıdır, diğer değişkenler de null değerler içerebilir. Bu özellikler tasarım amacınızı bildirmenize daha kolay bir hale getirir. Benzer şekilde, null yapılabilir uyarı bağlamı derleyiciye bu amacı ihlal ettiğinizde uyarı vermesini söyler. Bu uyarılar, kodunuzu daha dayanıklı hale getirmek ve yürütme sırasında oluşturma olasılığını azaltır `NullReferenceException` . Geri kalan kod temeli dokunulmamış olsa da, geçirilecek yerel kod alanına odaklanabilmeniz için bu bağlamların kapsamını kontrol edebilirsiniz. Uygulamada, bu geçiş görevini sınıflarınıza düzenli bakımın bir parçası yapabilirsiniz. Bu öğretici, bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirme işlemini göstermiştir. Bu işlemin daha büyük bir gerçek dünya örneğini, null yapılabilir başvuru türlerini [Nodadtime](https://github.com/nodatime/nodatime/pull/1240/commits)ile birleştirmek IÇIN yapılan PR [Jon iskeet](https://github.com/jskeet) 'i inceleyerek inceleyebilirsiniz. Ya da buna ek olarak, null olabilen başvuru türleri [Ile çalışan Entity Framework Core](/ef/core/miscellaneous/nullable-reference-types)Entity Framework Core ile null yapılabilir başvuru türleri kullanmanın tekniklerini öğrenebilirsiniz.
