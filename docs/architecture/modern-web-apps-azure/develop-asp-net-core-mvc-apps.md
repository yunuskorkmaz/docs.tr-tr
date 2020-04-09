---
title: Core MVC uygulamaları ASP.NET geliştirme
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | Core MVC Uygulamaları ASP.NET geliştirme
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 3de70af23206b0ae0525541b3d2cb480dc5bb882
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987913"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Core MVC uygulamaları ASP.NET geliştirin

> "İlk seferinde doğru yapmak önemli değil. Son seferde doğru yapmak hayati önem taşıyor."  
> _- Andrew Hunt ve David Thomas_

ASP.NET Core, modern bulut için optimize edilmiş web uygulamaları oluşturmak için çapraz platform, açık kaynak kodlu bir çerçevedir. ASP.NET Core uygulamaları, bağımlılık enjeksiyonu için yerleşik destekle hafif ve modülerdir ve daha fazla test edilebilirlik ve sürdürülebilirlik sağlar. Görünüm tabanlı uygulamalara ek olarak modern web API'lerinin oluşturulmasını destekleyen MVC ile birlikte, ASP.NET Core kurumsal web uygulamaları oluşturmak için güçlü bir çerçevedir.

## <a name="mvc-and-razor-pages"></a>MVC ve Jilet Sayfaları

ASP.NET Core MVC, web tabanlı API'ler ve uygulamalar oluşturmak için yararlı olan birçok özellik sunar. MVC terimi, kullanıcı isteklerini çeşitli bölümlere ayıran bir kullanıcı arabirimi deseni olan "Model-View-Controller" anlamına gelir. Bu deseni takip etmeye ek olarak, ASP.NET Core uygulamalarınızda Razor Pages olarak özellikler de uygulayabilirsiniz. Razor Pages core mvc ASP.NET yerleşik ve yönlendirme, model bağlama, vb için aynı özellikleri kullanın. Ancak, Denetleyiciler, Görünümler vb. için ayrı klasörlere ve dosyalara sahip olmak ve öznitelik tabanlı yönlendirme kullanmak yerine, Razor Pages bu klasördeki göreceli konumlarına göre tek bir klasöre ("/Sayfalar") yerleştirilir ve denetleyici eylemleri yerine istekleri işleyicilerle işler.

Yeni bir ASP.NET Core Uygulaması oluşturduğunuzda, oluşturmak istediğiniz uygulama türü için aklınızda bir plan olmalıdır. Visual Studio'da çeşitli şablonlar arasından seçim yapacaksınız. En yaygın üç proje şablonu Web API, Web Application ve Web Application (Model-View-Controller) 'dir. Bu kararı yalnızca bir proje yi ilk oluşturduğunuzda verebilirsiniz, ancak bu geri alınamaz bir karar değildir. Web API projesi standart Model-View-Controller denetleyicilerini kullanır – varsayılan olarak Görünümlerden yoksundur. Aynı şekilde, varsayılan Web Uygulaması şablonu Razor Pages kullanır ve böylece bir Görünümler klasörü de yoksundur. Görünüm tabanlı davranışı desteklemek için daha sonra bu projelere görünümler klasörü ekleyebilirsiniz. Web API ve Model-View-Controller projeleri varsayılan olarak bir Sayfa klasörü içermez, ancak daha sonra Razor Pages tabanlı davranışı desteklemek için bir tane ekleyebilirsiniz. Bu üç şablonu üç farklı varsayılan kullanıcı etkileşimini destekleyen olarak düşünebilirsiniz: veri (web API), sayfa tabanlı ve görünüm tabanlı. Ancak, isterseniz tek bir proje içinde bunların herhangi birini veya tümlerini karıştırıp eşleştirebilirsiniz.

### <a name="why-razor-pages"></a>Neden Razor Pages?

Razor Pages Visual Studio yeni web uygulamaları için varsayılan bir yaklaşımdır. Razor Pages, SPA olmayan formlar gibi sayfa tabanlı uygulama özellikleri oluşturmanın daha basit bir yolunu sunar. Denetleyicileri ve görünümleri kullanarak, uygulamaların birçok farklı bağımlılıkla çalışan ve modelleri görüntüleyen ve birçok farklı görünüm döndüren çok büyük denetleyicilere sahip olması yaygındı. Bu daha karmaşık lıkla sonuçlandı ve genellikle Tek Sorumluluk İlkesi veya Açık/Kapalı İlkeler'i etkin bir şekilde takip eden denetleyicilerle sonuçlandı. Razor Pages, jilet biçimlendirmesi ile bir web uygulamasında belirli bir mantıksal "sayfa" için sunucu tarafı mantığını kapsülleyerek bu sorunu gidermektedir. Sunucu tarafı mantığı olmayan bir Razor Page, yalnızca bir Razor dosyasından (örneğin, "Index.cshtml") oluşabilir. Ancak, önemsiz olmayan Jilet Sayfaları'nın çoğu, sözleşmeye göre ".cs" uzantılı Razor dosyasıyla aynı adlandırılmış ilişkili bir sayfa modeli sınıfına sahip olacaktır (örneğin, "Index.cshtml.cs").

Razor Page'in sayfa modeli, Bir MVC denetleyicisinin ve görüntüleme modelinin sorumluluklarını birleştirir. İstekleri denetleyici eylem yöntemleriyle işlemek yerine, "OnGet()" gibi sayfa modeli işleyicileri yürütülür ve ilişkili sayfalarını varsayılan olarak işler. Razor Pages, core MVC'nin tüm mimari özelliklerini sağlarken, ASP.NET Core uygulamasında tek tek sayfalar oluşturma işlemini kolaylaştırır ve aynı zamanda core MVC ASP.NET'nin tüm mimari özelliklerini de sağlar. Yeni sayfa tabanlı işlevsellik için varsayılan seçenektir.

### <a name="when-to-use-mvc"></a>MVC ne zaman kullanılır?

Web API'leri oluşturuyorsanız, MVC deseni Razor Pages'i kullanmaya çalışmaktan daha mantıklıdır. Projeniz yalnızca web API uç noktalarını ortaya çıkaracaksa, ideal olarak Web API proje şablonundan başlamalısınız. Aksi takdirde, herhangi bir ASP.NET Core uygulamasına denetleyicileri ve ilişkili API uç noktalarını eklemek kolaydır. Varolan bir uygulamayı ASP.NET MVC 5'ten veya daha önce ASP.NET Core MVC'ye geçiriyorsanız ve bunu en az çabayla yapmak istiyorsanız, görünüm tabanlı MVC yaklaşımını kullanın. İlk geçişi yaptıktan sonra, Razor Pages'i yeni özellikler için mi yoksa toptan geçiş olarak mı benimsemenin mantıklı olduğunu değerlendirebilirsiniz.

Web uygulamanızı Razor Pages veya MVC görünümlerini kullanarak oluşturmayı seçseniz de, uygulamanız da benzer bir performansa sahip olacak ve bağımlılık enjeksiyonu, filtreler, model bağlama, doğrulama ve benzeri destek içerecektir.

## <a name="mapping-requests-to-responses"></a>Yanıtları eşleme istekleri

Kalbinde, ASP.NET Core uygulamaları gelen istekleri giden yanıtlara eşler. Düşük bir düzeyde, bu middleware ile yapılır ve basit ASP.NET Core uygulamaları ve microservices sadece özel ara yazılım oluşabilir. Core MVC ASP.NET kullanırken, _rotalar_, _denetleyiciler_ve _eylemler_açısından düşünme, biraz daha yüksek bir düzeyde çalışabilir. Her gelen istek uygulamanın yönlendirme tablosuyla karşılaştırılır ve eşleşen bir yol bulunursa, isteği işlemek için ilişkili eylem yöntemi (bir denetleyiciye ait) çağrılır. Eşleşen bir yol bulunmazsa, bir hata işleyicisi (bu durumda, Bir NotFound sonucu döndürerek) çağrılır.

ASP.NET Core MVC uygulamaları geleneksel rotaları, öznitelik rotalarını veya her ikisini de kullanabilir. Geleneksel yollar kod olarak tanımlanır ve aşağıdaki örnekte olduğu gibi sözdizimi kullanarak yönlendirme _kuralları_ belirtilir:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Bu örnekte, yönlendirme tablosuna "varsayılan" adlı bir rota eklendi. Bu _denetleyici,_ _eylem_ve _id_için yer tutucuları ile bir rota şablonu tanımlar. Denetleyici ve eylem yer tutucuları varsayılan olarak belirtilmiş ("Ev" ve "Dizin", sırasıyla) ve id yer tutucusu isteğe bağlıdır (buna uygulanan bir "." sayesinde). Burada tanımlanan sözleşme, bir isteğin ilk bölümünün denetleyicinin adına, ikinci bölümünün eyleme karşılık vermesi gerektiğini ve gerekirse üçüncü bir bölümün bir kimlik parametresini temsil edeceğini belirtir. Geleneksel yollar genellikle başlangıç sınıfındaki Yapılandırma yöntemi gibi uygulama için tek bir yerde tanımlanır.

Öznitelik yolları denetleyicilere ve eylemlere genel olarak belirtilmez, doğrudan uygulanır. Bu, belirli bir yönteme baktığınızda onları çok daha keşfedilebilir hale getirme avantajına sahiptir, ancak yönlendirme bilgilerinin uygulamada tek bir yerde tutulmadığı anlamına gelir. Öznitelik yollarında, belirli bir eylem için birden çok rotayı kolayca belirtebilir ve denetleyiciler ve eylemler arasındaki yolları birleştirebilirsiniz. Örneğin:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

[HttpGet] ve benzer özniteliklerüzerinde rotalar belirtilebilir ve ayrı [Rota] öznitelikleri ekleme gereksinimini önler. Öznitelik yolları, aşağıda gösterildiği gibi denetleyici veya eylem adlarını yineleme gereksinimini azaltmak için belirteçleri de kullanabilir:

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Razor Pages öznitelik yönlendirme kullanmaz. Bir Razor Page için yönergesinin `@page` bir parçası olarak ek rota şablonu bilgilerini belirtebilirsiniz:

```csharp
@page "{id:int}"
```

Önceki örnekte, söz konusu sayfa bir tamsayı `id` parametresi olan bir rotayla eşleşir. Örneğin, kökünde bulunan *Products.cshtml* sayfası `/Pages` şu rotaya sahip olur:

```csharp
"/Products/123"
```

Belirli bir istek bir rotayla eşleştikten sonra, ancak eylem yöntemi çağrılmadan önce, ASP.NET Core MVC istekte [model bağlama](/aspnet/core/mvc/models/model-binding) ve model [doğrulama gerçekleştirir.](/aspnet/core/mvc/models/validation) Model bağlama, gelen HTTP verilerinin çağrılacak eylem yönteminin parametreleri olarak belirtilen .NET türlerine dönüştürülmesinden sorumludur. Örneğin, eylem yöntemi bir int id parametresi bekliyorsa, model bağlama isteğinin bir parçası olarak sağlanan bir değerden bu parametreyi sağlamaya çalışır. Bunu yapmak için, model bağlama deftere nakledilen bir formdaki değerleri, rotanın kendisindeki değerleri ve sorgu dize değerlerini arar. Bir kimlik değerinin bulunduğu varsayılıyorsa, eylem yöntemine geçirilmeden önce bir karşıcıya dönüştürülür.

Modeli bağladıktan sonra ancak eylem yöntemini çağırmadan önce model doğrulama oluşur. Model doğrulama, model türünde isteğe bağlı öznitelikleri kullanır ve sağlanan model nesnesinin belirli veri gereksinimlerine uygun olmasını sağlamaya yardımcı olabilir. Belirli değerler gerekli olarak belirtilebilir veya belirli bir uzunluk veya sayısal aralık, vb ile sınırlı Doğrulama öznitelikleri belirtilir ancak model gereksinimlerine uygun değilse, özellik ModelState.IsValid yanlış olacaktır ve başarısız doğrulama kuralları kümesi isteği yapan istemciye göndermek için kullanılabilir.

Model doğrulama kullanıyorsanız, uygulamanızın geçersiz veriler tarafından bozulmadığından emin olmak için, durum değiştiren komutları gerçekleştirmeden önce modelin geçerli olup olmadığını her zaman kontrol ettiğinizden emin olmalısınız. Her eylemde bunun için kod ekleme gereksinimini önlemek için bir [filtre](/aspnet/core/mvc/controllers/filters) kullanabilirsiniz. ASP.NET Core MVC filtreleri, ortak politikaların ve çapraz kesme kaygılarının hedeflenen temelde uygulanabilmesi için istek gruplarını engellemenin bir yolunu sunar. Filtreler tek tek eylemlere, tüm denetleyicilere veya bir uygulama için genel olarak uygulanabilir.

Web API'leri için, ASP.NET Core MVC [_içerik anlaşmalarını_](/aspnet/core/mvc/models/formatting)destekler ve isteklerin yanıtların nasıl biçimlendirilmesi gerektiğini belirtmesine olanak sağlar. İstekte sağlanan üstbilgilere bağlı olarak, verileri döndüren eylemler yanıtı XML, JSON veya başka bir desteklenen biçimde biçimlendirecek. Bu özellik, aynı API'nin farklı veri biçimi gereksinimlerine sahip birden çok istemci tarafından kullanılmasını sağlar.

Web API projeleri, `[ApiController]` tek tek denetleyicilere, bir temel denetleyici sınıfına veya tüm derlemeye uygulanabilen özniteliği kullanmayı düşünmelidir. Bu öznitelik otomatik model doğrulama denetimi ekler ve geçersiz bir modele sahip herhangi bir eylem doğrulama hatalarının ayrıntılarıyla bir BadRequest döndürür. Öznitelik ayrıca, tüm eylemlerin geleneksel bir rota kullanmak yerine bir öznitelik rotasına sahip olmasını gerektirir ve hatalara yanıt olarak daha ayrıntılı ProblemAyrıntıları bilgilerini döndürür.

> ### <a name="references--mapping-requests-to-responses"></a>Referanslar – Yanıtlara Başvuruların Eşlemesi
>
> - **Denetleyici Eylemlere Yönlendirme**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Model Bağlama**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Model Doğrulama**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtre**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **ApiController Özniteliği**
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a>Bağımlılıklarla çalışma

ASP.NET Core için yerleşik destek ve dahili [bağımlılık enjeksiyonu](/aspnet/core/fundamentals/dependency-injection)olarak bilinen bir teknik kullanır. Bağımlılık enjeksiyonu, bir uygulamanın farklı bölümleri arasında gevşek bağlantı sağlayan bir tekniktir. Daha gevşek bağlantı, uygulamanın bazı bölümlerini yalıtmayı kolaylaştırdığından ve test veya değiştirmeye olanak sağlayacağından istenir. Ayrıca, uygulamanın bir bölümündeki bir değişikliğin uygulamada başka bir yerde beklenmeyen bir etkisi olma olasılığını da azaltTır. Bağımlılık enjeksiyonu bağımlılık inversiyon ilkesine dayanır ve genellikle açık/kapalı ilkeye ulaşmanın anahtarıdır. Uygulamanızın bağımlılıklarıyla nasıl çalıştığını değerlendirirken, statik [yapışkan](https://deviq.com/static-cling/) kod kokusuna dikkat edin ve["yeni tutkaltır"](https://ardalis.com/new-is-glue)aforizmini hatırlayın.

Statik tutunma, sınıflarınız statik yöntemlere çağrı yaptığında veya altyapıya yan etkileri veya bağımlılıkları olan statik özelliklere erişdiğinde oluşur. Örneğin, statik bir yöntem çağıran ve buna karşılık veritabanına yazan bir yöntemvarsa, yönteminiz veritabanıyla sıkı bir şekilde birleştiğinde. Veritabanı aramasını bozan her şey metodunuzu bozar. Bu tür testler statik çağrılarla alay etmek için ticari alay kitaplıkları gerektirdiğinden veya yalnızca yerinde bir test veritabanıyla test edilebildiği için, bu tür yöntemlerin test edilmesi oldukça zordur. Altyapıya herhangi bir bağımlılığı olmayan statik çağrılar, özellikle tamamen devletsiz olanlar, çağrı da iyidir ve bağlantı veya sınanabilirlik üzerinde hiçbir etkisi yoktur (statik çağrının kendisine bağlantı kodunun ötesinde).

Birçok geliştirici statik tutunma ve küresel devlet risklerini anlamak, ama yine de sıkı doğrudan anlık yoluyla belirli uygulamalara kendi kod çift olacaktır. "Yeni tutkal" bu bağlantı bir hatırlatma değil, `new` anahtar kelime kullanımı genel bir kınama olması gerekiyordu. Statik yöntem çağrılarında olduğu gibi, dış bağlarını olmayan yeni türler genellikle uygulama ayrıntılarıyla sıkı bir şekilde kod çiftleştirir veya sınamayı zorlaştırır. Ancak bir sınıf anlık olarak her zaman, o belirli bir konumda belirli bir örneği sabit kodlamanın mantıklı olup olmadığını veya bu örneği bağımlılık olarak istemek daha iyi bir tasarım olup olmayacağını düşünmek için kısa bir zaman ayırın.

### <a name="declare-your-dependencies"></a>Bağımlılıklarınızı bildirin

ASP.NET Core yöntemleri ve sınıflar bağımsız değişken olarak bunları isteyen, bağımlılıklarını bildirmek sahip üzerine inşa edilmiştir. ASP.NET uygulamaları genellikle, bağımlılık enjeksiyonuna destek olmak üzere birkaç noktada yapılandırılan bir Başlangıç sınıfında ayarlanır. Başlangıç sınıfınızda bir oluşturucu varsa, aşağıdaki gibi, kurucu aracılığıyla bağımlılıklar isteyebilir:

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
            .SetBasePath(env.ContentRootPath)
            .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
            .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

Başlangıç sınıfı, bunun için açık bir tür gereksinimi olmaması açısından ilginçtir. Özel bir Başlangıç taban sınıfından devralmaz ve belirli bir arabirim uygulamaz. Bir oluşturucu verebilir veya veremezsin, ve oluşturucuüzerinde istediğiniz kadar parametre belirtebilirsiniz. Uygulamanız için yapılandırdığınız web barındırma alanı başladığında, kullanmasını söylediğiniz Başlangıç sınıfını arar ve Başlangıç sınıfının gerektirdiği bağımlılıkları doldurmak için bağımlılık enjeksiyonu kullanır. Elbette, ASP.NET Core tarafından kullanılan hizmet kapsayıcısında yapılandırılmamış parametreleri talep ederseniz, bir özel durum alırsınız, ancak kapsayıcının bildiği bağımlılıklara bağlı kaldığınız sürece istediğiniz her şeyi isteyebilirsiniz.

Bağımlılık enjeksiyonu, Başlangıç örneğini oluşturduğunuzda, ASP.NET Core uygulamalarınızda en başından itibaren yerleşiktir. Başlangıç sınıfı için bununla da bitmiyor. Yapılandırma yönteminde bağımlılıklar da isteyebilirsiniz:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

ConfigureServices yöntemi bu davranışın istisnasidir; türü IServiceCollection sadece bir parametre almalıdır. Bir yandan hizmet kapsayıcısına nesne eklemekten sorumlu olduğundan, diğer yandan iServiceCollection parametresi üzerinden şu anda yapılandırılmış tüm hizmetlere erişimi olduğundan, bağımlılık enjeksiyonuna gerçekten ihtiyaç duymaz. Böylece, başlangıç sınıfının her bölümünde ASP.NET Çekirdek hizmetleri koleksiyonunda tanımlanan bağımlılıklarla, gerekli hizmeti parametre olarak isteyerek veya ConfigureServices'teki IServiceCollection ile çalışarak çalışabilirsiniz.

> [!NOTE]
> Belirli hizmetlerin Başlangıç sınıfınız için kullanılabilir olduğundan emin olmanız gerekiyorsa, bunları CreateDefaultBuilder araması içinde bir IWebHostBuilder ve Yapılandırılan Hizmetler yöntemini kullanarak yapılandırabilirsiniz.

Başlangıç sınıfı, denetleyicilerden Middleware'e ve Filtreler'den kendi Hizmetlerinize kadar ASP.NET Çekirdek uygulamanızın diğer bölümlerini nasıl yapılandırmanız gerektiğine yönelik bir modeldir. Her durumda, doğrudan oluşturmak yerine bağımlılıklarınızı isteyen ve uygulamanız boyunca bağımlılık enjeksiyonundan yararlanarak [Açık Bağımlılıklar İlkesi'ni](https://deviq.com/explicit-dependencies-principle/)izlemeniz gerekir. Uygulamaları, özellikle altyapıyla çalışan veya yan etkileri olan hizmetleri ve nesneleri doğrudan nerede ve nasıl anında değerlendirdiğinize dikkat edin. Uygulama çekirdeğinizde tanımlanan ve belirli uygulama türlerine yapılan hardcoding başvurularına bağımsız değişken olarak geçirilen soyutlamalarla çalışmayı tercih edin.

## <a name="structuring-the-application"></a>Uygulamanın yapılandırılması

Monolitik uygulamaların genellikle tek bir giriş noktası vardır. bir ASP.NET Core web uygulaması söz konusu olduğunda, giriş noktası ASP.NET Core web projesi olacaktır. Ancak, bu çözümün tek bir projeden oluşması gerektiği anlamına gelmez. Endişelerin ayrılmasını takip etmek için uygulamayı farklı katmanlara ayırmak yararlıdır. Katmanlara ayrıldıktan sonra, daha iyi kapsülleme elde etmeye yardımcı olabilecek projeleri ayırmak için klasörlerin ötesine geçmek yararlıdır. ASP.NET Core uygulaması ile bu hedeflere ulaşmak için en iyi yaklaşım, bölüm 5'te tartışılan Temiz Mimari'nin bir varyasyonudur. Bu yaklaşımın ardından, uygulamanın çözümü Kullanıcı Arabirimi, Altyapı ve ApplicationCore için ayrı kitaplıklardan oluşacaktır.

Bu projelere ek olarak, ayrı test projeleri de dahildir (Test Bölüm 9'da ele alınmıştır).

Uygulamanın nesne modeli ve arabirimleri ApplicationCore projesine yerleştirilmelidir. Bu proje mümkün olduğunca az bağımlıya sahip olacak ve çözümdeki diğer projeler buna başvurulacaktır. Kalıcı olması gereken iş varlıkları, doğrudan altyapıya bağlı olmayan hizmetler gibi ApplicationCore projesinde tanımlanır.

Kalıcılığın nasıl gerçekleştirildiği veya bildirimlerin kullanıcıya nasıl gönderileceği gibi uygulama ayrıntıları Altyapı projesinde tutulur. Bu proje, Entity Framework Core gibi uygulamaya özgü paketlere başvurulacaktır, ancak proje dışındaki bu uygulamalarla ilgili ayrıntıları ifşa etmemelidir. Altyapı hizmetleri ve depoları ApplicationCore projesinde tanımlanan arabirimleri uygulamalı ve kalıcılık uygulamaları ApplicationCore'da tanımlanan varlıkların alınması ve depolanmasından sorumludur.

ASP.NET Core UI projesi, ui düzeyindeki tüm endişelerden sorumludur, ancak iş mantığı veya altyapı ayrıntılarını içermemelidir. Aslında, ideal olarak, iki proje arasında hiçbir bağımlılığın kazara uygulanmamasını sağlamaya yardımcı olacak Altyapı projesine bile bağımlı olmamalıdır. Bu, her projede Modül sınıflarında DI kurallarını tanımlamanızı sağlayan Autofac gibi üçüncü taraf bir DI kapsayıcısı kullanılarak elde edilebilir.

Uygulama nın uygulama ayrıntılarından ayrılmasına ilişkin bir diğer yaklaşım da, uygulama çağrısının mikro hizmetleri, belki de tek tek Docker konteynerlerinde dağıtılmasıdır. Bu, iki proje arasında DI'den yararlanarak daha fazla endişe ve ayrışma ayrılması sağlar, ancak ek karmaşıklık vardır.

### <a name="feature-organization"></a>Özellik organizasyonu

Varsayılan olarak, ASP.NET Çekirdek uygulamaları klasör yapılarını Denetleyicileri ve Görünümleri ve sık sık Görünüm Modelleri içerecek şekilde düzenler. Bu sunucu tarafı yapılarını desteklemek için istemci tarafı kodu genellikle wwwroot klasöründe ayrı olarak depolanır. Ancak, belirli bir özellik üzerinde çalışmak genellikle bu klasörler arasında atlama gerektirdiğinden, büyük uygulamalar bu kuruluşla ilgili sorunlarla karşılaşabilir. Bu, her klasördeki dosya ve alt klasör sayısı arttıkça daha da zorlaşıyor ve bu da Çözüm Gezgini'nde büyük bir kaydırma yla sonuçlanıyor. Bu sorunun bir çözümü, dosya türü yerine _özelliğine_ göre uygulama kodu düzenlemektir. Bu kuruluş stili genellikle özellik klasörleri veya [özellik dilimleri](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc) olarak adlandırılır (ayrıca bakınız: [Dikey Dilimler).](https://deviq.com/vertical-slices/)

ASP.NET Core MVC bu amaç için Alanları destekler. Alanları kullanarak, her Alan klasöründe ayrı Denetleyiciler ve Görünümler klasörleri (ve ilişkili modeller) kümeleri oluşturabilirsiniz. Şekil 7-1, Alanlar'ı kullanarak örnek klasör yapısını gösterir.

![Örnek Alan Organizasyonu](./media/image7-1.png)

**Şekil 7-1**. Örnek Alan Organizasyonu

Alanları kullanırken, denetleyicilerinizi ait oldukları alanın adıyla dekore etmek için öznitelikleri kullanmanız gerekir:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Ayrıca rotalarınıza alan desteği eklemeniz gerekir:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "areaRoute", pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Alanlar için yerleşik desteğe ek olarak, öznitelikler ve özel yollar yerine kendi klasör yapınızı ve kurallarınızı da kullanabilirsiniz. Bu, hiyerarşiyi düz tutarak ve ilgili tüm dosyaları her özellik için tek bir yerde görmeyi kolaylaştıran Görünümler, Denetleyiciler vb. için ayrı klasörler içermeyen özellik klasörlerine sahip olmak için izin verir.

ASP.NET Core, davranışını denetlemek için yerleşik kural kuralları türlerini kullanır. Bu kuralları değiştirebilir veya değiştirebilirsiniz. Örneğin, ad alanına göre belirli bir denetleyicinin özellik adını otomatik olarak alacak bir kural oluşturabilirsiniz (genellikle denetleyicinin bulunduğu klasörle ilişkilidir):

```csharp
public class FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

Daha sonra ConfigureServices'teki uygulamanıza MVC desteği eklediğinizde bu kuralı bir seçenek olarak belirtirsiniz:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC de görünümleri bulmak için bir kural kullanır. Görünümlerin özellik klasörlerinizde yer alacağı (yukarıdaki Özellik Sözleşmesi tarafından sağlanan özellik adını kullanarak) özel bir kuralla geçersiz kılabilirsiniz. Bu yaklaşım hakkında daha fazla bilgi edinmek ve msdn dergisi makale, [ASP.NET Core MVC için Özellik Dilimleri](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc)bir çalışma örneği indirebilirsiniz.

### <a name="cross-cutting-concerns"></a>Geniş kapsamlı kritik konular

Uygulamalar büyüdükçe, yinelemeyi ortadan kaldırmak ve tutarlılığı korumak için çapraz kesme endişelerini hesaba klaştırmak giderek daha önemli hale gelir. ASP.NET Core uygulamalarında çapraz kesme kaygılarına bazı örnekler kimlik doğrulama, model doğrulama kuralları, çıktı önbelleğe alma ve hata işlemedir, ancak başka ları da vardır. ASP.NET Core MVC [filtreleri,](/aspnet/core/mvc/controllers/filters) istek işleme ardışık ardışık ardışık ardışık ardışık ardışık ardışık ardışık ardışık ardışık ardışık ardışık belirli adımlardan önce veya sonra kod çalıştırmanızı sağlar. Örneğin, bir filtre model bağlamadan önce ve sonra, bir eylemden önce ve sonra veya bir eylemin sonucundan önce ve sonra çalıştırılabilir. Ayrıca, ardışık hattın geri kalanına erişimi denetlemek için bir yetkilendirme filtresi de kullanabilirsiniz. Şekil 7-2, yapılandırılırsa istek yürütmenin filtrelerden nasıl geçtiğini gösterir.

![İstek Yetkilendirme Filtreleri, Kaynak Filtreleri, Model Bağlama, Eylem Filtreleri, Eylem Yürütme ve Eylem Sonucu Dönüştürme, Özel Durum Filtreleri, Sonuç Filtreleri ve Sonuç Yürütme yoluyla işlenir. Çıkarken, istek yalnızca İstemciye gönderilen bir yanıt olmadan önce Sonuç Filtreleri ve Kaynak Filtreleri tarafından işlenir.](./media/image7-2.png)

**Şekil 7-2**. Filtreler aracılığıyla yürütme isteği nde bulunun ve ardışık kaynak isteyin.

Filtreler genellikle öznitelik olarak uygulanır, böylece denetleyicilere veya eylemlere (hatta genel olarak) uygulayabilirsiniz. Bu şekilde eklendiğinde, eylem düzeyinde belirtilen filtreler geçersiz kılınan veya denetleyici düzeyinde belirtilen filtreler üzerine inşa edilen filtreler, kendilerinin de genel filtreleri geçersiz kılar. Örneğin, \[Rota\] özniteliği denetleyiciler ve eylemler arasında yollar oluşturmak için kullanılabilir. Aynı şekilde, yetkilendirme denetleyici düzeyinde yapılandırılabilir ve aşağıdaki örnekte gösterildiği gibi, tek tek eylemler tarafından geçersiz kılınabilir:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

İlk yöntem, Giriş, denetleyici düzeyinde Yetkilendirme filtresi kümesini geçersiz kılmak için İzin Verme filtresini (öznitelik) kullanır. ForgotPassword eylemi (ve sınıfta İzin Verilen Adsız özniteliği olmayan diğer eylemler) kimlik doğrulaması isteği gerektirir.

Filtreler, API'ler için yaygın hata işleme ilkeleri şeklinde yinelemeyi ortadan kaldırmak için kullanılabilir. Örneğin, tipik bir API ilkesi, var olmayan başvuru anahtarlarına Bir NotFound yanıtı ve model doğrulama başarısız olursa BadRequest yanıtı döndürecek. Aşağıdaki örnek, şu iki ilkeyi iş başında gösterir:

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Eylem yöntemlerinizin bu gibi koşullu kodlarla darmadağın olmasına izin verme. Bunun yerine, ilkeleri gerektiği gibi uygulanabilecek filtrelere çekin. Bu örnekte, api'ye bir komut gönderildiğinde gerçekleşmesi gereken model doğrulama denetimi aşağıdaki öznitelik ile değiştirilebilir:

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

`ValidateModelAttribute` [Ardalis.ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) paketini ekleyerek projenize NuGet bağımlılığı olarak ekleyebilirsiniz. API'ler için, `ApiController` ayrı `ValidateModel` bir filtreye gerek kalmadan bu davranışı zorlamak için özniteliği kullanabilirsiniz.

Benzer şekilde, bir filtre, bir kaydın var olup olmadığını denetlemek ve eylem yürütülmeden önce bir 404 döndürmek için kullanılabilir ve bu denetimleri eylemde gerçekleştirme gereksinimini ortadan kaldırır. Ortak sözleşmeleri çıkardıktan ve altyapı kodunu ve iş mantığını UI'nizden ayırmak için çözümünüzü düzenledikten sonra, MVC eylem yöntemleriniz son derece ince olmalıdır:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Filtreleri uygulama hakkında daha fazla bilgi edinebilir ve MSDN Magazine makale, [Real-World ASP.NET Core MVC Filtreler](https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters)çalışma örneği indirebilirsiniz.

> ### <a name="references--structuring-applications"></a>Referanslar – Uygulamaların yapılandırılması
>
> - **Alanlar**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Dergisi – ASP.NET Core MVC için Özellik Dilimleri**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc>
> - **Filtreler**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN Dergisi – Core MVC Filtreler ASP.NET Gerçek Dünya**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters>

## <a name="security"></a>Güvenlik

Web uygulamalarının güvenliğini sağlamak, birçok hususla birlikte büyük bir konudur. En temel düzeyde, güvenlik, belirli bir isteğin kimden geldiğini bilmenizi ve ardından isteğin yalnızca olması gereken kaynaklara erişmesini sağlamayı içerir. Kimlik doğrulaması, isteğin bilinen bir varlıktan geliyor olarak kabul edilip edilmemesi gerektiğini görmek için, bir istekle sağlanan kimlik bilgilerini güvenilir bir veri deposundakikimlik bilgileriyle karşılaştırma işlemidir. Yetkilendirme, kullanıcı kimliğine dayalı belirli kaynaklara erişimi kısıtlama işlemidir. Üçüncü bir güvenlik endişesi, istekleri üçüncü şahısların gizlice dinlemelerine karşı korumaktır ve bunun için en azından [SSL'nin uygulamanız tarafından kullanıldığından emin](/aspnet/core/security/enforcing-ssl)olmalısınız.

### <a name="authentication"></a>Kimlik Doğrulaması

ASP.NET Çekirdek Kimlik, uygulamanız için giriş işlevselliğini desteklemek için kullanabileceğiniz bir üyelik sistemidir. Microsoft Hesabı, Twitter, Facebook, Google ve daha fazlası gibi sağlayıcılardan yerel kullanıcı hesaplarının yanı sıra harici oturum açma sağlayıcısı desteğine de sahiptir. ASP.NET Çekirdek Kimliğine ek olarak, uygulamanız windows kimlik doğrulamasını veya [Identity Server](https://github.com/IdentityServer/IdentityServer4)gibi bir üçüncü taraf kimlik sağlayıcısını kullanabilir.

ASP.NET Bireysel Kullanıcı Hesapları seçeneği seçilirse, Çekirdek Kimlik yeni proje şablonlarına dahil edilir. Bu şablon, kayıt, giriş, harici oturum açma, unutulan parolalar ve ek işlevler için destek içerir.

![Kimliği önceden yapılandırmak için Bireysel Kullanıcı Hesaplarını seçin](./media/image7-3.png)

**Şekil 7-3**. Kimliği önceden yapılandırmak için Bireysel Kullanıcı Hesapları'nı seçin.

Kimlik desteği, Hem Yapılandırma Hizmetleri'nde hem de Yapılandırma'da Başlangıç'ta yapılandırılır:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Configure yönteminde UseIdentity'in UseMvc'den önce görünmesi önemlidir. ConfigureServices'de Kimliği yapılandırırken AddDefaultTokenProviders'a bir çağrı fark edeceksiniz. Bunun web iletişimini güvence altına almak için kullanılabilecek belirteçlerle bir ilgisi yoktur, ancak bunun yerine, kullanıcıların kimliklerini doğrulamaları için SMS veya e-posta yoluyla gönderilebilen istemler oluşturan sağlayıcılar anlamına gelir.

[İki faktörlü kimlik doğrulamayı yapılandırma](/aspnet/core/security/authentication/2fa) ve dış oturum açma sağlayıcılarının resmi ASP.NET Core dokümanlarından [etkinleştirilmesi](/aspnet/core/security/authentication/social/) hakkında daha fazla bilgi edinebilirsiniz.

### <a name="authorization"></a>Yetkilendirme

En basit yetkilendirme biçimi, anonim kullanıcılara erişimi kısıtlamayı içerir. Bu, \[yalnızca belirli denetleyicilere veya\] eylemlere Yetki özniteliği uygulanarak elde edilebilir. Roller kullanılıyorsa, öznitelik, gösterildiği gibi belirli rollere ait kullanıcılara erişimi kısıtlamak için daha da genişletilebilir:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

Bu durumda, HrManager veya Finans rollerine (veya her ikisine) ait kullanıcılar SalaryController'a erişebilir. Bir kullanıcının birden çok role (yalnızca birkaç rolden birine değil) ait olmasını istemek için, özniteliği her seferinde gerekli rolü belirterek birden çok kez uygulayabilirsiniz.

Birçok farklı denetleyicive eylemde dizeleri olarak belirli rol kümeleri belirtilmesi istenmeyen tekrara neden olabilir. \[Yetkilendirme kurallarını kapsayan yetkilendirme ilkelerini yapılandırabilir ve Yetkilendirme\] özniteliğini uygularken tek tek roller yerine ilkeyi belirtebilirsiniz:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

İlkeleri bu şekilde kullanarak, kısıtlanan eylem türlerini, belirli rollerden veya kurallardan ayırabilirsiniz. Daha sonra, belirli kaynaklara erişmesi gereken yeni bir rol oluşturursanız, her \[Yetkilendirme\] özniteliğindeki her rol listesini güncelleştirmek yerine bir ilkeyi güncelleştirmeniz yeterli olur.

#### <a name="claims"></a>Talepler

Talepler, kimlik doğrulaması yapılan bir kullanıcının özelliklerini temsil eden ad değeri çiftleridir. Örneğin, kullanıcıların çalışan numarasını talep olarak depolayabilirsiniz. Talepler daha sonra yetkilendirme ilkelerinin bir parçası olarak kullanılabilir. Bu örnekte gösterildiği gibi, "Çalışan Sayısı" adlı bir talebin varlığını gerektiren "Yalnızca Çalışan" adlı bir ilke oluşturabilirsiniz:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

Bu ilke daha sonra \[yukarıda\] açıklandığı gibi, herhangi bir denetleyiciyi ve/veya eylemi korumak için Yetki özniteliği ile kullanılabilir.

#### <a name="securing-web-apis"></a>Web API'lerini güvence altına alma

Çoğu web API'si bir belirteç tabanlı kimlik doğrulama sistemi uygulamalıdır. Belirteç kimlik doğrulaması durum benzersizdir ve ölçeklenebilir olacak şekilde tasarlanmıştır. Belirteç tabanlı kimlik doğrulama sisteminde, istemcinin önce kimlik doğrulama sağlayıcısıyla kimlik doğrulaması yapması gerekir. Başarılı olursa, istemciye yalnızca şifreleme açısından anlamlı bir karakter dizesi olan bir belirteç verilir. İstemci daha sonra bir API için bir istek sorunu yayımlamak gerektiğinde, bu istek üzerinde bir üstbilgi olarak bu belirteç ekler. Sunucu daha sonra isteği tamamlamadan önce istek üstbilgisinde bulunan belirteci doğrular. Şekil 7-4 bu süreci göstermektedir.

![TokenAuth](./media/image7-4.png)

**Şekil 7-4.** Web API'leri için belirteç tabanlı kimlik doğrulaması.

Kendi kimlik doğrulama hizmetinizi oluşturabilir, Azure AD ve OAuth ile tümleştirebilir veya [IdentityServer](https://github.com/IdentityServer)gibi açık kaynaklı bir aracı kullanarak bir hizmet uygulayabilirsiniz.

#### <a name="custom-security"></a>Özel Güvenlik

Özellikle şifreleme, kullanıcı üyeliği veya belirteç oluşturma sisteminin "kendi" uygulaması hakkında dikkatli olun. Neredeyse kesinlikle özel bir uygulama daha iyi bir güvenlik olacak birçok ticari ve açık kaynak alternatifleri vardır.

> ### <a name="references--security"></a>Referanslar – Güvenlik
>
> - **Güvenlik Dokümanlarına Genel Bakış**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **ASP.NET Core Uygulamasında SSL'yi uygulama**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Kimliğe giriş**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Yetkilendirmeye Giriş**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Azure App Service’te API Apps için Kimlik Doğrulama ve Yetkilendirme**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Kimlik Sunucusu**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Müşteri iletişimi

ASP.NET Core uygulamaları, sayfalara hizmet vermenin ve web API'leri aracılığıyla veri isteklerine yanıt vermenin yanı sıra, bağlı istemcilerle doğrudan iletişim kurabilir. Bu giden iletişim, en yaygın ı WebSockets olmak üzere çeşitli aktarım teknolojilerini kullanabilir. ASP.NET Core SignalR, uygulamalarınız için gerçek zamanlı sunucudan istemciye iletişim işlevselliği eklemeyi kolaylaştıran bir kitaplıktır. SignalR, WebSockets de dahil olmak üzere çeşitli aktarım teknolojilerini destekler ve uygulama ayrıntılarının çoğunu geliştiriciden soyutlar.

İster doğrudan WebSockets'i veya diğer teknikleri kullanarak, gerçek zamanlı istemci iletişimi, çeşitli uygulama senaryolarında yararlıdır. Bazı örnekler:

- Canlı sohbet odası uygulamaları

- Uygulamaların izlenmesi

- İş ilerleme güncelleştirmeleri

- Bildirimler

- Etkileşimli form uygulamaları

Uygulamalarınızda istemci iletişimi kurarken genellikle iki bileşen vardır:

- Sunucu tarafı bağlantı yöneticisi (SignalR Hub, WebSocketManager WebSocketHandler)

- İstemci tarafı kitaplığı

İstemciler tarayıcılarla sınırlı değildir – mobil uygulamalar, konsol uygulamaları ve diğer yerel uygulamalar signalr/websockets kullanarak da iletişim kurabilir. Aşağıdaki basit program, WebSocketManager örnek uygulamasının bir parçası olarak konsola bir sohbet uygulamasına gönderilen tüm içeriği yansıtır:

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>
        {
            Console.WriteLine($"{arguments[0]} said: {arguments[1]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

Uygulamalarınızın istemci uygulamalarıyla doğrudan iletişim kurma yollarını ve gerçek zamanlı iletişimin uygulamanızın kullanıcı deneyimini iyileştirip iyileştirmeyeceğini düşünün.

> ### <a name="references--client-communication"></a>Referanslar – Müşteri İletişimi
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/dotnet/aspnetcore/tree/master/src/SignalR>
> - **WebSocket Yöneticisi**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Etki alanı odaklı tasarım – Uygulamalı mısın?

Etki Alanı Odaklı Tasarım (DDD), _iş alanına_odaklanmayı vurgulayan yazılım oluşturmaya yönelik çevik bir yaklaşımdır. Gerçek dünya sisteminin nasıl işlediğini geliştiricilerle ilişkilendirebilen iş alanı uzmanı(lar) ile iletişim ve etkileşime büyük önem verir. Örneğin, hisse senedi alım saverelerini işleyen bir sistem oluşturuyorsanız, etki alanı uzmanınız deneyimli bir hisse senedi komisyoncusu olabilir. DDD büyük, karmaşık iş sorunlarını gidermek için tasarlanmıştır ve etki alanını anlama ve modelleme yatırımı buna değmez, genellikle daha küçük, daha basit uygulamalar için uygun değildir.

Bir DDD yaklaşımını izleyerek yazılım geliştirirken, ekibiniz (teknik olmayan paydaşlar ve katkıda bulunanlar dahil) sorun alanı için _her yerde bulunan_ bir dil geliştirmelidir. Diğer bir deyişle, aynı terminoloji, modellenen gerçek dünya kavramı, yazılım eşdeğeri ve kavramı sürdürmek için var olabilecek tüm yapılar (örneğin, veritabanı tabloları) için kullanılmalıdır. Bu nedenle, her yerde bulunan dilde açıklanan kavramlar _etki alanı modelinizin_temelini oluşturmalıdır.

Etki alanı modeliniz, sistemin davranışını temsil etmek için birbirleriyle etkileşimedebilen nesnelerden oluşur. Bu nesneler aşağıdaki kategorilere düşebilir:

- Nesneleri kimlik iş parçacığıyla temsil eden [varlıklar.](https://deviq.com/entity/) Varlıklar genellikle daha sonra alınabilecekleri bir anahtarla kalıcı olarak depolanır.

- Bir birim olarak kalıcı olması gereken nesne gruplarını temsil eden [agregalar.](https://deviq.com/aggregate-pattern/)

- [Değer nesneleri](https://deviq.com/value-object/), özellik değerlerinin toplamı temelinde karşılaştırılabilen kavramları temsil eder. Örneğin, başlangıç ve bitiş tarihinden oluşan DateRange.

- [Etki alanı olayları,](https://martinfowler.com/eaaDev/DomainEvent.html)sistemin diğer bölümlerini ilgilendiren sistem içinde meydana gelen şeyleri temsil eder.

Bir DDD etki alanı modeli, model içindeki karmaşık davranışı kapsüllemelidir. Varlıklar, özellikle, sadece özellikleri koleksiyonları olmamalıdır. Etki alanı modeli davranış yoksun ve sadece sistemin durumunu temsil ettiğinde, bir [anemik model](https://deviq.com/anemic-model/)olduğu söyleniyor , DDD istenmeyen.

Bu model türlerine ek olarak, DDD genellikle çeşitli desenler kullanır:

- [Repository](https://deviq.com/repository-pattern/), kalıcılık ayrıntıları soyutlama için.

- [Fabrika](https://en.wikipedia.org/wiki/Factory_method_pattern), karmaşık nesne oluşturma kapsülleme için.

- Etki alanı olayları, bağımlı davranışı tetikleyici davranıştan ayırmak için.

- [Karmaşık](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)davranış ve/veya altyapı uygulama ayrıntılarını kapsülleme hizmetleri.

- [Komut](https://en.wikipedia.org/wiki/Command_pattern), komutları ayırma ve komutun kendisini yürütme için.

- [Belirtim](https://deviq.com/specification-pattern/), sorgu ayrıntılarını kapsülleme için.

DDD ayrıca, birim testleri kullanılarak kolayca doğrulanabilen gevşek bağlantı, kapsülleme ve koda izin vererek, daha önce tartışılan Temiz Mimari'nin kullanılmasını önerir.

### <a name="when-should-you-apply-ddd"></a>DDD'yi ne zaman uygulamanız gerekir?

DDD, önemli iş (sadece teknik) karmaşıklığı ile büyük uygulamalar için uygundur. Uygulama etki alanı uzmanlarının bilgisini gerektirir. Etki alanı modelinin kendisinde, veri depolarından çeşitli kayıtların geçerli durumunu depolamanın ve almanın ötesinde iş kurallarını ve etkileşimlerini temsil eden önemli davranışlar olmalıdır.

### <a name="when-shouldnt-you-apply-ddd"></a>Ne zaman DDD uygulamamalısınız

DDD modelleme, mimari ve iletişim aslında sadece CRUD (oluşturma/ okuma/güncelleme/silme) olan küçük uygulamalar veya uygulamalar için garanti olmayabilir iletişim yatırımları içerir. DDD'den sonra uygulamanıza yaklaşmayı seçerseniz, ancak etki alanınızın hiçbir davranışı olmayan anemik bir modeli olduğunu fark ederseniz, yaklaşımınızı yeniden düşünmeniz gerekebilir. Uygulamanızın DDD'ye ihtiyacı olmayabilir veya veritabanınız veya kullanıcı arabiriminizde değil, iş mantığını etki alanı modelinde kapsüllemek için uygulamanızı yeniden düzenleme konusunda yardıma ihtiyacınız olabilir.

Karma bir yaklaşım yalnızca uygulamanın işlem veya daha karmaşık alanlar için DDD kullanmak olacaktır, ancak basit CRUD veya uygulamanın salt okunur bölümleri için değil. Örneğin, bir raporu görüntülemek veya bir pano için verileri görselleştirmek için verileri sorgulıyorsanız, Bir Agrega'nın kısıtlamalarına sahip olmanız gerekmez. Bu tür gereksinimler için ayrı, basit bir okuma modeli olması son derece kabul edilebilir.

> ### <a name="references--domain-driven-design"></a>Referanslar – Etki Alanı Odaklı Tasarım
>
> - **Düz İngilizce DDD (StackOverflow Cevap)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Dağıtım

ASP.NET Core uygulamanızı nerede barındırılacağına bakılmaksızın dağıtma işleminde yer alan birkaç adım vardır. İlk adım CLI komutu kullanılarak `dotnet publish` yapılabilir uygulama, yayımlamaktır. Bu, uygulamayı derleyecek ve uygulamayı çalıştırmak için gereken tüm dosyaları belirlenmiş bir klasöre yerleştirilecektir. Visual Studio'dan dağıtıladiğinizde, bu adım sizin için otomatik olarak gerçekleştirilir. Yayımlama klasörü, uygulama ve bağımlılıkları için .exe ve .dll dosyaları içerir. Bağımsız bir uygulama da .NET çalışma zamanının bir sürümünü içerir. ASP.NET Core uygulamaları yapılandırma dosyalarını, statik istemci varlıklarını ve MVC görünümlerini de içerir.

ASP.NET Core uygulamaları, sunucu (veya sunucu) çöktürüldüğünde başlatılması gereken konsol uygulamalarıdır. Bu işlemi otomatikleştirmek için bir işlem yöneticisi kullanılabilir. ASP.NET Core için en yaygın işlem yöneticileri Linux ve IIS veya Windows Windows Service üzerinde Nginx ve Apache vardır.

Bir işlem yöneticisine ek olarak, ASP.NET Core uygulamaları ters proxy sunucusu kullanabilir. Ters proxy sunucusu Internet'ten HTTP isteklerini alır ve bazı ön işleme sonra Bunları Kestrel'e ileter. Ters proxy sunucuları uygulama için bir güvenlik katmanı sağlar. Kerkenez aynı bağlantı noktasında birden çok uygulama barındırmayı da desteklemez, bu nedenle ana bilgisayar başlıkları gibi teknikler aynı bağlantı noktası ve IP adresinde birden çok uygulama barındırmayı etkinleştirmek için onunla birlikte kullanılamaz.

![Kerkenez internete](./media/image7-5.png)

**Şekil 7-5**. ASP.NET ters proxy sunucusu arkasında Kestrel barındırılan

Ters proxy yararlı olabilir başka bir senaryo SSL / HTTPS kullanarak birden çok uygulama güvenli etmektir. Bu durumda, yalnızca ters proxy SSL yapılandırılmış olması gerekir. Ters proxy sunucusu ile Kestrel arasındaki iletişim, Şekil 7-6'da gösterildiği gibi HTTP üzerinden gerçekleşebilir.

![ASP.NET, HTTPS güvenli bir ters proxy sunucusunun arkasında barındırılan](./media/image7-6.png)

**Şekil 7-6**. ASP.NET, HTTPS güvenli bir ters proxy sunucusunun arkasında barındırılan

Giderek daha popüler hale gelen bir yaklaşım, ASP.NET Core uygulamanızı, daha sonra yerel olarak barındırılabilen veya bulut tabanlı barındırma için Azure'a dağıtılabilen bir Docker kapsayıcısında barındırmaktır. Docker kapsayıcısı, Kestrel üzerinde çalışan uygulama kodunuzu içerebilir ve yukarıda gösterildiği gibi ters proxy sunucusunun arkasına dağıtılabilir.

Uygulamanızı Azure'da barındırAn bir uygulamaysanız, çeşitli hizmetler sunmak için Microsoft Azure Uygulama Ağ Geçidi'ni özel bir sanal araç olarak kullanabilirsiniz. Uygulama Ağ Geçidi, tek tek uygulamalar için ters proxy olarak hareket etmesinin yanı sıra aşağıdaki özellikleri de sunabilir:

- HTTP yük dengeleme

- SSL boşaltma (SSL sadece Internet için)

- Uçuca SSL

- Çok siteli yönlendirme (tek bir Uygulama Ağ Geçidi'nde en fazla 20 siteyi birleştirir)

- Web uygulaması güvenlik duvarı

- Websocket desteği

- Gelişmiş tanılama

_[Bölüm 10'da](development-process-for-azure.md)Azure dağıtım seçenekleri hakkında daha fazla bilgi edinin._

> ### <a name="references--deployment"></a>Referanslar – Dağıtım
>
> - **Barındırma ve Dağıtıma Genel Bakış**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Ters proxy ile Kerkenez ne zaman kullanılır**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **DockerASP.NET'da Ana bilgisayar ASP.NET**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Azure Uygulama Ağ Geçidi Tanıtımı**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Önceki](common-client-side-web-technologies.md)
>[Sonraki](work-with-data-in-asp-net-core-apps.md)
