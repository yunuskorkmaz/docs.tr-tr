---
title: Null yapılabilir başvuru türleriyle tasarım
description: Bu gelişmiş öğretici, null yapılabilir başvuru türlerine giriş sağlar. Başvuru değerleri null olduğunda ve derleyicinin null olmadıklarında zorunlu olmadığı durumlarda tasarım amacınızı ifade etmek için bilgi edineceksiniz.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 0c95065e6c380fab6ba33432a32b3297e78027a3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926622"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Öğretici: Mevcut kodu Nullable başvuru türleriyle geçirin

C#8, null olabilen değer türleri için aynı şekilde, başvuru türlerini tamamlayan **null yapılabilir başvuru türlerini**tanıtır. Bir`?` değişkeni türüne ekleyerek **null atanabilir bir başvuru türü** olarak bildirirsiniz. Örneğin, `string?` null yapılabilen bir değeri `string`temsil eder. Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir. Bir başvuru türünün varolan değişkenleri, null olamayan bir başvuru türü olarak yorumlanır. 

Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
>
> - Kodla çalışırken null başvuru denetimlerini etkinleştirin.
> - Null değerlerle ilgili farklı uyarıları tanılayın ve düzeltin.
> - Null yapılabilir etkin ve null yapılabilir devre dışı bağlamların arabirimini yönetin.
> - Null yapılabilir ek açıklama bağlamlarını denetleyin.

## <a name="prerequisites"></a>Önkoşullar

C# 8,0 Beta derleyicisi dahil olmak üzere, makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8 Beta derleyicisi, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya en son [.NET Core 3,0 Önizleme](https://dotnet.microsoft.com/download/dotnet-core/3.0)sürümü ile kullanılabilir.

Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="explore-the-sample-application"></a>Örnek uygulamayı keşfet

Geçirilecek örnek uygulama bir RSS Akış okuyucusu web uygulamasıdır. Tek bir RSS akışından okur ve en son makalelerin özetlerini görüntüler. Siteyi ziyaret etmek için makalelerden birine tıklayabilirsiniz. Uygulama nispeten yenidir ancak null yapılabilir başvuru türleri kullanılabilir olmadan önce yazılmıştır. Uygulama için gösterilen ve bu önemli dil özelliğinden yararlanmamak için sunulan tasarım kararları.

Örnek uygulama, uygulamanın ana işlevlerini doğrulayan bir birim testi kitaplığı içerir. Oluşturulan uyarılara göre herhangi bir uygulamayı değiştirirseniz, bu proje güvenli bir şekilde yükseltmeyi daha kolay hale getirir. Başlangıç kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub deposundan indirebilirsiniz.

Bir projeyi geçirme hedefiniz yeni dil özelliklerinden faydalanmak için olmalıdır. böylece, amacınızı null olabilir ve bu nedenle, null yapılabilir ek açıklama bağlamına sahip olduğunuzda derleyicinin uyarı üretmemesi ve null yapılabilir uyarı bağlamı olarak `enabled`ayarlanır.

## <a name="upgrade-the-projects-to-c-8"></a>Projeleri 8 ' e C# yükseltin

Geçiş görevinin kapsamını belirlemekte iyi bir ilk adım vardır. Projeyi C# 8,0 (veya daha yeni) sürümüne yükselterek başlayın. `LangVersion` Öğeyi Web projesi ve birim test projesi için her iki csproj dosyasına ekleyin:

```xml
<LangVersion>8.0</LangVersion>
```

Dil sürümünü yükseltmek 8,0 seçer C# , ancak null yapılabilir ek açıklama bağlamını veya null yapılabilir uyarı bağlamını etkinleştirmez. Uyarı vermeden oluşturulduğundan emin olmak için projeyi yeniden derleyin.

İyi bir sonraki adım, null yapılabilir ek açıklama bağlamını açıp kaç uyarı oluşturulduğunu görmenizde yarar vardır. Çözümdeki her iki csproj dosyasına ve doğrudan `LangVersion` öğesinin altına aşağıdaki öğeyi ekleyin:

```xml
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> Öğe daha önce adlandırılmıştı `NullableContextOptions`. `Nullable` Yeniden adlandırma, Visual Studio 2019, 16,2-P1 ile birlikte gönderilir. 3\.0.100-preview5-011568 .NET Core SDK bu değişikliğe sahip değil. .NET Core CLI kullanıyorsanız, sonraki önizleme kullanılabilir olana kadar kullanmanız `NullableContextOptions` gerekir.

Bir test derlemesi yapın ve uyarı listesine dikkat edin. Bu küçük uygulamada, derleyici beş uyarı üretir, bu nedenle null yapılabilir ek açıklama bağlamını etkin bırakıp tüm proje için uyarıları düzeltmeye başlayabilirsiniz.

Bu strateji yalnızca daha küçük projeler için geçerlidir. Daha büyük projeler için, tüm kod tabanı için Nullable ek açıklama bağlamını etkinleştirerek oluşturulan uyarı sayısı, uyarıları sistematik olarak gidermeyi zorlaştırır. Daha büyük kurumsal projelerde, genellikle bir projeyi tek seferde geçirmek isteyeceksiniz. Her projede, tek bir sınıf veya dosyayı aynı anda geçirin.

## <a name="warnings-help-discover-original-design-intent"></a>Uyarılar özgün tasarım amacını bulmaya yardımcı olur

Birden çok uyarı oluşturan iki sınıf vardır. `NewsStoryViewModel` Sınıfıyla başlayın. Uyarı kapsamını çalıştığınız kodun bölümleriyle sınırlayabilmeniz için her iki csproj dosyasından öğeyikaldırın.`Nullable` *NewsStoryViewModel.cs* dosyasını açın ve için `NewsStoryViewModel` null yapılabilir ek açıklama bağlamını etkinleştirmek üzere aşağıdaki yönergeleri ekleyin ve bu sınıf tanımını izleyerek geri yükleyin:

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

Bu iki yönergeler, geçiş çabalarınıza odaklanmaya yardımcı olur. Üzerinde etkin olarak çalışmakta olduğunuz kod alanı için null yapılabilir uyarılar oluşturulur. Projenin tamamına yönelik uyarıları açmaya hazırsanız, bunları açık bırakmalısınız. Projenin tamamına yönelik null `restore` yapılabilir ek `disable` açıklamaları açtığınızda bağlamı yanlışlıkla devre dışı bırakmamanızı sağlamak için yerine, bu değeri kullanın. Tüm proje için Nullable ek açıklama bağlamını etkinleştirdikten sonra, bu projeden tüm `#nullable` pragmaları kaldırabilirsiniz.

`NewsStoryViewModel` Sınıf bir veri aktarım nesnesidir (DTO) ve özelliklerden ikisi okuma/yazma dizeleridir:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Bu iki özellik neden `CS8618`"Nullable özelliği başlatılmamış" olur. Bu yeterince net: her iki `string` özellik de oluşturulduğunda varsayılan `null` değerine `NewsStoryViewModel` sahiptir. Bulma için önemli olan özellikler, nesnelerin `NewsStoryViewModel` nasıl oluşturulduğunu bir şeydir. Bu sınıfa baktığınızda, `null` değerin tasarımın bir parçası olup olmadığını veya bu nesnelerin her biri oluşturulduğunda null olmayan değerlere ayarlanmış olduğunu söyleyemiyoruz. Haber hikayeleri, `GetNews` `NewsService` sınıfının yönteminde oluşturulur:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Yukarıdaki kod bloğunda oldukça bir bit vardır. Bu uygulama, öğesinden `ISyndicationItem`bir haber öğesi oluşturmak için [automaber](https://automapper.org/) NuGet paketini kullanır. Haber hikayesi öğelerinin oluşturulduğunu ve özellikler söz konusu bir bildirimde ayarlandığını keşfettiniz. Bu, `NewsStoryViewModel` için tasarımının hiçbir `null` şekilde bu özelliklerin değer vermediğini gösterdiği anlamına gelir. Bu özellikler **null atanamaz başvuru türleri**olmalıdır. Bu, özgün tasarım amacını en iyi ifade eder. Aslında, hiçbiri `NewsStoryViewModel` null olmayan değerler ile doğru *şekilde oluşturulur.* Bu, aşağıdaki başlatma kodunu geçerli bir çözüm haline getirir:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

`Title` `default` Türü için olan ve `Uri` için ataması programın çalışma zamanı davranışını değiştirmez. `null` `string` `NewsStoryViewModel` Hala null değerlerle oluşturulmuş, ancak derleyici hiçbir uyarı raporluyor. **Null-forverme işleci**, `!` `default` ifadeden sonraki karakter derleyiciye önceki ifadenin null olmadığını söyler. Bu teknik, diğer değişiklikler bir kod tabanında çok daha büyük değişiklikler yaparken, ancak bu uygulamada görece hızlı ve daha iyi bir çözüm olduğunda, bu teknik bir şekilde etkilenebilir: Oluşturucuda tüm özelliklerin ayarlandığı sabit birtüryapın.`NewsStoryViewModel` Aşağıdaki değişiklikleri `NewsStoryViewModel`yapın:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Bu yapıldıktan sonra, özellikleri ayarlamak yerine, oluşturucuyu kullanması için Automaber 'yi yapılandıran kodu güncelleştirmeniz gerekir. Açın `NewsService.cs` ve dosyanın en altında aşağıdaki kodu bulun:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu kod, `ISyndicationItem` nesnenin `NewsStoryViewModel` özelliklerini özelliklerine eşler. Bunun yerine bir Oluşturucu kullanarak, Automaber 'nin eşleme sağlamasını istersiniz. Yukarıdaki kodu aşağıdaki automaber yapılandırmasıyla değiştirin:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Bu sınıf küçük olduğundan ve dikkatle incelediğiniz için `#nullable enable` , bu sınıf bildiriminin üzerindeki yönergeyi açmanız gerektiğini unutmayın. Kurucudaki değişiklik bir şeyi bozarak, tüm testleri çalıştırmak ve devam etmeden önce uygulamayı test etmek daha fazla olabilir.

İlk değişiklik kümesi, özgün tasarımın değişkenlerin olarak `null`ayarlanmamalıdır ne zaman yapılacağını nasıl keşfedebileceğine ilişkin olduğunu gösterdi. Teknik, **oluşturma tarafından doğru**olarak adlandırılır. Bir nesne ve özellikleri oluşturulduğunda bildiremezsiniz `null` . Derleyicinin akış analizi, bu özelliklerin oluşturma sonrasında olarak `null` ayarlanmamış olduğunu güvence altına almaktadır. Bu oluşturucunun dış kod tarafından çağrıldığını ve kodun **null değer atanabilir yükümlülüğü**olduğunu unutmayın. Yeni sözdizimi çalışma zamanı denetimi sağlamaz. Dış kod derleyicinin akış analizini atlatılabilir. 

Diğer zamanlarda, bir sınıfın yapısı amaç için farklı ipuçları sağlar. *Error.cshtml.cs* dosyasını *Sayfalar* klasöründe açın. , `ErrorViewModel` Aşağıdaki kodu içerir:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Sınıf bildiriminden önce `#nullable restore` `#nullable enable` yönergesini ve sonra bir yönergeyi ekleyin. Başlatılmamış bir uyarı `RequestId` alırsınız. Sınıfına bakarak, bazı durumlarda `RequestId` özelliğin NULL olması gerektiğine karar vermeniz gerekir. `ShowRequestId` Özelliğin varlığı eksik değerlerin mümkün olduğunu gösterir. Geçerli `null` olduğundan, `RequestId` özelliğin *null yapılabilir bir başvuru türü*olduğunu göstermek için `string` türüne öğesini `?` ekleyin. Son sınıf aşağıdaki örneğe benzer şekilde görünür:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Özelliğin kullanımlarını denetleyin ve ilgili sayfada özelliği, biçimlendirme sırasında işlemeden önce, özelliğinin null olarak denetlendiğini görürsünüz. Bu, null olabilen bir başvuru türünün güvenli bir kullanımı olduğundan bu sınıfla işiniz bitti.

## <a name="fixing-nulls-causes-change"></a>Null değerleri düzeltme değişikliğine neden olur

Genellikle, bir uyarı kümesinin düzeltilmesi ilgili kodda yeni uyarılar oluşturur. Ayrıca, `index.cshtml.cs` sınıfını düzelterek uyarıları görelim. `index.cshtml.cs` Dosyasını açın ve kodu inceleyin. Bu dosya dizin sayfası için arkasındaki kodu içerir:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

`#nullable enable` Yönergesini ekleyin ve iki uyarı görürsünüz. `ErrorText` Özellik ne`NewsItems` de özellik başlatılmaz. Bu sınıfın incelenmesi, her iki özellik de null yapılabilir başvuru türleri olması gerektiğini düşünmenize yol açacaktı. Her ikisinin de özel ayarlayıcıları vardır. `OnGet` Yöntemine tam olarak bir atanır. Değişiklik yapmadan önce her iki özelliği de tüketicilere bakın. Sayfanın kendisinde `ErrorText` , herhangi bir hata için biçimlendirme oluşturmadan önce null değeri denetlenir. Koleksiyon öğesine karşı `null`denetlenir ve koleksiyonda öğeler olduğundan emin olmak için denetlenir. `NewsItems` Hızlı bir çözüm, her iki özelliği de null yapılabilir başvuru türlerini yapmak olacaktır. Daha iyi bir çözüm, koleksiyonu null yapılamayan bir başvuru türü yapmak ve haberleri alırken mevcut koleksiyona öğe eklemek olacaktır. İlk düzeltilme `?` `string` türü için türüne `ErrorText`eklemektir:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

`ErrorText` Özelliğe herhangi bir erişim null denetimleri tarafından zaten korunduğu için, bu değişiklik başka bir kod aracılığıyla görünmez olmayacaktır. Sonra, `NewsItems` listeyi başlatın ve özellik ayarlayıcısını kaldırın ve salt okunur bir özellik yapar:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Bu, uyarıyı düzeltti ancak bir hata sunmuştur. Liste artık oluşturma işlemi **tarafından düzeltilir**, ancak içinde `OnGet` listeyi ayarlayan kodun yeni API ile eşleşecek şekilde değiştirilmesi gerekir. `NewsItems` Atama yerine, mevcut listeye haber `AddRange` öğelerini eklemek için çağırın:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Atama `AddRange` yerine kullanmak, `GetNews` yöntemin `IEnumerable` yerine bir `List`olarak dönebileceği anlamına gelir. Bu, bir ayırmayı kaydeder. Aşağıdaki kod örneğinde gösterildiği gibi, yönteminin imzasını değiştirin ve `ToList` çağrıyı kaldırın:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

İmzanın değiştirilmesi, testlerin birini de keser. `NewsServiceTests.cs` Dosyayı projenin`SimpleFeedReader.Tests` klasöründe açın. `Services` Teste gidin ve `result` değişkenin türünü olarak `IEnumerable<NewsItem>`değiştirin. `Returns_News_Stories_Given_Valid_Uri` Türü değiştirmek `Count` özelliğin artık kullanılamadığı anlamına gelir, bu nedenle içindeki `Count` `Assert` özelliğini öğesine `Any()`çağrısıyla değiştirin:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Dosyanın başlangıcına de bir `using System.Linq` ifade eklemeniz gerekecektir.

Bu değişiklik kümesi, genel örneklemeleri içeren kodu güncelleştirirken özel bir değerlendirme vurgulamaktadır. Hem liste hem de öğeler null yapılamayan türler listesinde. Ya da her ikisi de null yapılabilir türler olabilir. Aşağıdaki bildirimlere izin verilir:

- `List<NewsStoryViewModel>`: ullable olmayan görünüm modellerinin null yapılamayan listesi.
- `List<NewsStoryViewModel?>`: null yapılabilir görünüm modellerinin Nullable listesi.
- `List<NewsStoryViewModel>?`: null yapılamayan görünüm modellerinin null yapılabilir listesi.
- `List<NewsStoryViewModel?>?`: null yapılabilir görünüm modellerinin null olabilir listesi.

## <a name="interfaces-with-external-code"></a>Dış kod içeren arabirimler

`NewsService` Sınıfta değişiklikler yaptınız, bu nedenle bu sınıf için `#nullable enable` ek açıklamayı etkinleştirin. Bu, yeni uyarı oluşturmaz. Ancak, sınıfının dikkatle incelenmesi derleyicinin akış analizinin bazı sınırlamalarını göstermeye yardımcı olur. Oluşturucuyu inceleyin:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` Parametre null atanamaz bir başvuru olarak yazılmış. Bu, ASP.NET Core altyapı kodu tarafından çağrılır, bu nedenle derleyici hiçbir şekilde null olacağını gerçekten `IMapper` bilmez. Varsayılan ASP.NET Core bağımlılık ekleme (dı) kapsayıcısı, gerekli bir hizmeti çözümleyemezse, kod doğru olduğunda bir özel durum oluşturur. Kodunuz null yapılabilir ek açıklama bağlamlarıyla derlense bile derleyici ortak API 'lerinize yapılan tüm çağrıları doğrulayamaz. Ayrıca, kitaplıklarınız henüz null yapılabilir başvuru türlerini kullanarak onaylanmamış projeler tarafından tüketilebilir. Bu girdileri null yapılamayan türler olarak bildirseniz bile ortak API 'lere yönelik girişleri doğrulayın.

## <a name="get-the-code"></a>Kodu alın

İlk test derlenmesi sırasında belirlediğiniz uyarıları düzelttiniz, bu nedenle artık her iki proje için de null yapılabilir ek açıklama bağlamını açabilirsiniz. Projeleri yeniden derleyin; Derleyici hiçbir uyarı rapor vermez. [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) GitHub deposundaki tamamlanmış projenin kodunu alabilirsiniz.

Null yapılabilir başvuru türlerini destekleyen yeni özellikler, kodunuzda değerleri nasıl işleyeceğiniz `null` potansiyel hataları bulmanıza ve düzeltmenize yardımcı olur. Null yapılabilir ek açıklama bağlamını etkinleştirmek, tasarım amacınızı ifade etmenizi sağlar: bazı değişkenler hiçbir şekilde null olmamalıdır, diğer değişkenler de null değerler içerebilir. Bu özellikler tasarım amacınızı bildirmenize daha kolay bir hale getirir. Benzer şekilde, null yapılabilir uyarı bağlamı derleyiciye bu amacı ihlal ettiğinizde uyarı vermesini söyler. Bu uyarılar, kodunuzu daha dayanıklı hale getirmek ve yürütme sırasında oluşturma `NullReferenceException` olasılığını azaltır. Geri kalan kod temeli dokunulmamış olsa da, geçirilecek yerel kod alanına odaklanabilmeniz için bu bağlamların kapsamını kontrol edebilirsiniz. Uygulamada, bu geçiş görevini sınıflarınıza düzenli bakımın bir parçası yapabilirsiniz. Bu öğretici, bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirme işlemini göstermiştir. Bu işlemin daha büyük bir gerçek dünya örneğini, null yapılabilir başvuru türlerini [Nodadtime](https://github.com/nodatime/nodatime/pull/1240/commits)ile birleştirmek IÇIN yapılan PR [Jon iskeet](https://github.com/jskeet) 'i inceleyerek inceleyebilirsiniz.
