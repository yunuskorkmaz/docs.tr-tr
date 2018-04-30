---
title: ASP.NET Core MVC uygulamaları geliştirme
description: ASP.NET Core ve Azure ile modern Web uygulamaları mimari | ASP.NET Core MVC uygulamaları geliştirme
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1a97bd393a4df080d9e2f9fc049165e4efbff852
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="develop-aspnet-core-mvc-apps"></a>ASP.NET Core MVC uygulamaları geliştirme

> "Bu ilk kez sağ almak önemli değildir. En son ne zaman sağ almak oldukça önemlidir."  
> _-Barış aramaya ve David Thomas_

## <a name="summary"></a>Özet

ASP.NET Core modern bulut iyileştirilmiş web uygulamaları oluşturmak için platformlar arası, açık kaynaklı bir çerçevedir. ASP.NET Core uygulamaları basit ve modüler, bağımlılık ekleme, büyük sınanabilirlik ve bakımı etkinleştirme için yerleşik destek bulunur. Modern web API'leri görünüm tabanlı uygulamalar yanı sıra oluşturmayı destekleyen, MVC ile birlikte ASP.NET Core bir güçlü Kurumsal web uygulamaları oluşturmak hangi çerçevedir.

## <a name="mapping-requests-to-responses"></a>Eşleme isteklerini yanıtlar

Temelinde, ASP.NET Core uygulamaları giden yanıtlar gelen istekleri eşleyin. Düşük düzeyde, bu Ara yazılımla yapılır ve basit ASP.NET Core uygulamaları ve mikro hizmetler yalnızca özel ara yazılım oluşabilir. ASP.NET Core MVC kullanırken cinsinden düşünüyorum biraz daha yüksek bir düzeyde çalışabilirsiniz *yollar*, *denetleyicileri*, ve *Eylemler*. Her gelen istek uygulamanın yönlendirme tablosu ile karşılaştırılır ve eşleşen bir rota bulunursa, (bir denetleyiciye ait) ilişkili eylem yöntemi isteği işlemek üzere çağrılır. Eşleşen bir rota bulunursa, bir hata işleyicisi (NotFound sonucu döndürerek bu durumda,) adı verilir.

ASP.NET Core MVC uygulamaları geleneksel yolları, öznitelik rotaları veya her ikisini de kullanabilirsiniz. Geleneksel yollar yönlendirme belirtme kodda tanımlanmış *kuralları* aşağıdaki örnekte olduğu gibi sözdizimini kullanarak:

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

Bu örnekte, "varsayılan" adlı bir rota yönlendirme tablosuna eklendi. Bir rota şablonuyla yer tutucular tanımlar *denetleyicisi*, *eylem*, ve *kimliği*. Belirtilen varsayılan denetleyici ve eylem yer tutucuları bulunur ("Home" ve "Dizin" sırasıyla), ve kimliği tutucudur isteğe bağlı (tarafından virtue, bir "?" uygulanan). Kuralı ikinci bölümü eyleme denetleyicinin adı bir isteğin ilk parçası karşılık gelmelidir durumları burada tanımlanan ve ardından gerekirse, üçüncü bir bölümü bir ID parametresi temsil eder. Geleneksel yollar genellikle uygulama için tek bir yerde gibi başlangıç sınıfı yapılandırma yönteminde tanımlanır.

Öznitelik rotaları denetleyicileri ve eylemleri doğrudan uygulanan yerine genel olarak belirtilmiş. Bu, belirli bir yöntem arıyorsanız, ancak yönlendirme bilgilerini uygulamadaki tek bir yerde tutulan değil anlamına gelmez, çok daha bulunabilirlik yapma avantajına sahiptir. Öznitelik rotaları ile kolayca belirli bir eylem için birden çok rotaları belirtin yanı denetleyicileri ve eylemleri arasındaki yolları birleştirin. Örneğin:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

Yollar [HttpGet] üzerinde belirtilebilir ve benzer öznitelikler eklemek için gereken önleme, ayrı [rota\] öznitelikleri. Öznitelik rotaları belirteçleri, denetleyici veya eylem adlarını yinelemek için gereken aşağıda gösterildiği gibi azaltmak için de kullanabilirsiniz:

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

Belirtilen bir isteğin rotayla eşleşen, ancak önce eylem yönteminden sonra ASP.NET Core MVC gerçekleştirecek [model bağlama](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) ve [model doğrulama](https://docs.microsoft.com/aspnet/core/mvc/models/validation) istek. Model bağlama, gelen HTTP veri çağrılacak eylem yönteminin bir parametre olarak belirtilen .NET türlerine dönüştürme için sorumludur. Örneğin, bir eylem yönteminin bir int kimliği parametre bekliyor, isteğin bir parçası sağlanan değer bu parametresinden sağlamak model bağlama deneyecek. Bunu yapmak için model bağlama gönderilen bir formu değerleri, rota değerleri ve sorgu dizesi değerlerini arar. Bir kimlik değeri bulundu varsayıldığında, onu bir tamsayıya eylem yönteminin iletilmeden önce dönüştürülür.

Model bağlama sonra ancak eylem yöntemi çağrılmadan önce model doğrulama oluşur. Model doğrulama, model türü üzerinde isteğe bağlı öznitelik kullanır ve sağlanan model nesnesi belirli veri gereksinimleri uymasını sağlamak yardımcı olabilir. Belirli değerleri olarak belirtilebilir gerekli veya belirli bir uzunlukta veya sayısal aralığı için sınırlı, vb. Doğrulama öznitelikleri belirtildi ancak model kendi gereksinimlerine uygun değil, özellik ModelState.IsValid false olur ve doğrulama kuralları başarısız kümesi istekte istemciye göndermek kullanılabilir olacak.

Model doğrulama kullanıyorsanız, her zaman uygulamanızı geçersiz veriler bozuk değil emin olmak için tüm durum değiştirme komutları gerçekleştirmeden önce model geçerli olup olmadığını denetlediğinizden emin olun. Kullanabileceğiniz bir [filtre](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) kod bu her eylem eklemek için gereksinimini ortadan kaldırmak için. Böylece ortak ilkeleri ve çapraz kesme sorunları hedeflenen temelinde uygulanabilir ASP.NET Core MVC filtreleri isteklerinin grupları kesintiye uğratan bir yol sunar. Filtreler, tek tek Eylemler, tüm denetleyicileri veya genel bir uygulama için uygulanabilir.

ASP.NET Core MVC Web API'leri destekleyen [ *içerik anlaşması*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), istekleri yanıtlar nasıl biçimlendirilmiş belirtmek izin verme. İstekte sağlanan üstbilgileri bağlı olarak, XML, JSON veya başka bir desteklenen biçiminde yanıt veriyor Eylemler biçimlendirir. Bu özellik, farklı veri biçim gereksinimleri ile birden çok istemci tarafından kullanılmak üzere aynı API sağlar.

> ### <a name="references--mapping-requests-to-responses"></a>Başvuruları – isteklerini yanıtlar eşleme
> - **Denetleyici eylemleri için yönlendirme**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Model bağlama** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding
> - **Model doğrulama**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **filtreleri** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters

## <a name="working-with-dependencies"></a>Bağımlılıkları ile çalışma

ASP.NET Core için yerleşik destek varsa ve dahili olarak kullanır olarak bilinen bir tekniği [bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection). Bağımlılık ekleme gevşek bağlantı uygulamanın farklı bölümleri arasında etkin bir tekniktir. Bazı bağlantı arzu çünkü sınama ya da değiştirme için izin vererek uygulama parçalarını yalıtmak üzere kolaylaştırır. Ayrıca, daha az büyük olasılıkla bir değişiklik uygulamanın bir parçası olarak uygulamada başka bir yere beklenmeyen etkisi olduğunu kılar. Bağımlılık ekleme bağımlılık ters çevirmeyi ilkeye dayanarak ve genellikle açık ve kapalı ilkesini ulaşmak için anahtarıdır. Uygulamanızı bağımlılıklarını ile nasıl çalıştığı değerlendirirken, dikkat [statik cling](http://deviq.com/static-cling/) kod kokusu ve aphorism unutmayın "[Birleştirici yeni](https://ardalis.com/new-is-glue)."

Statik cling sınıflarınızı statik yöntemler çağrı yapmak veya yan etkileri veya bağımlılıkları altyapısına sahip statik özelliklerine erişim oluşur. Örneğin, sırayla bir veritabanına yazma, bir statik yöntemini çağıran bir yöntemi varsa yönteminizi sıkı şekilde veritabanına bağlı. Bu veritabanı çağrısı keser herhangi bir şey yönteminizi çalışmamasına neden olur. Bu tür sınamalar statik çağrıları mock için ticari mocking kitaplıkları gerektiren ya da yalnızca bir test veritabanı yerinde ile test edilebilir beri tür yöntem sınama notoriously zor olabilir. Altyapı, özellikle de tamamen durum bilgisiz herhangi bağımlılığı yok statik çağrıları arayıp bağ veya Test Edilebilirlik (ötesinde kod statik çağrısı kendisini Kuplaj) üzerinde hiçbir etkisi ince.

Çoğu geliştirici statik cling ve genel durum risklerini anlamak, ancak kendi kodlarını doğrudan oluşturmada size belirli uygulamaları için hala sıkı bir şekilde eşleştiği. "Birleştirici yenilikler" Bu bağlantı, anımsatıcı ve değil genel condemnation yeni anahtar sözcük kullanımı için tasarlanmıştır. Gibi statik yöntem çağrılarını genellikle dış bağımlılıkları olmayan türleri yeni örneklerini değil sıkı bir şekilde kod uygulama ayrıntılarını eşleştiği veya test daha zor hale. Ancak bir sınıf örneği, her zaman sabit kodlu için belirli Bu örnek, belirli bir konumda mantıklıdır olup olmadığını ya da bu örnek bir bağımlılık olarak istemek için daha iyi bir tasarım olacaksa dikkate alınması gereken yalnızca kısa biraz zaman ayırın.

### <a name="declare-your-dependencies"></a>Bağımlılıklarınız bildirme

ASP.NET Core yöntemleri sahip geçici oluşturulur ve bağımsız değişkenler olarak isteyen bağımlılıklarını sınıfları bildirme. ASP.NET uygulamaları tipik olarak ayarlandığı bir başlangıç sınıfta kendisi bağımlılık ekleme birkaç noktalarda desteklemek üzere yapılandırıldı. Başlangıç sınıfı bir oluşturucu varsa, Oluşturucusu aracılığıyla bağımlılıklar isteyebilir sözlüğüdür:

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

Var olan hiçbir açık tür gereksinimlerin başlangıç sınıfı ilginç olmamasıdır. Bir özel başlangıç temel sınıfından devralmaz veya herhangi belirli arabirimini uygulayan yapar. Ona bir oluşturucu veya verebilirsiniz ve istediğiniz sayıda parametrelere Oluşturucusu belirtebilirsiniz. Uygulamanız için yapılandırdığınız web ana bilgisayar başlatıldığında kullanacak şekilde söylediyse başlangıç sınıfı çağırır ve bağımlılık ekleme başlangıç sınıfı gerektirir bağımlılıkları doldurmak için kullanır. Doğal olarak, ASP.NET Core tarafından kullanılan hizmetler kapsayıcısında yapılandırılmamışlardır parametreleri isterse bir özel durum alırsınız, ancak bağımlılıkları takılıyor sürece kapsayıcı bilir hakkında istediğinizi isteyebilir.

Başlangıç örneği oluşturduğunuzda, bağımlılık ekleme ASP.NET Core uygulamalarınızı sağ başından içinde yerleşiktir. Ayrıca başlangıç sınıfı var. bitmez. Yapılandırma yöntemi bağımlılıkları da isteğinde bulunabilirsiniz:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Bu davranış özel durumu ConfigureServices yöntemdir; IServiceCollection türünde yalnızca bir parametre almalıdır. Ayrıca, bir yandan hizmet kapsayıcı nesneleri eklemek için sorumlu olduğu ve diğer tüm yapılandırılmış hizmetler IServiceCollection parametresi üzerinden erişimi olan bağımlılık ekleme desteklemek gerçekten gerekmez. Bu nedenle, her bir parametre olarak gerekli hizmet isteyen veya IServiceCollection ConfigureServices içinde çalışma başlangıç sınıfı parçası ASP.NET Core services koleksiyonunda içinde tanımlanan bağımlılıklar çalışabilirsiniz.

> [!NOTE]
> Belirli hizmetleri başlatma sınıfınıza kullanılabilir olduğundan emin olun ihtiyacınız varsa, bunları yapılandırabilirsiniz WebHostBuilder ve onun ConfigureServices yöntemini kullanarak.

Başlangıç sınıfı diğer filtreleri kendi hizmetlerine Ara denetleyicilerinden ASP.NET Core uygulamanızın parçalarını nasıl yapılandırdığınızı modelidir. Her durumda, uygulamanız gereken [açık bağımlılıkları ilkesine](http://deviq.com/explicit-dependencies-principle/)bağımlılıklarınızı isteyen yerine doğrudan oluşturarak ve bağımlılık ekleme, uygulama boyunca yararlanarak. Nerede ve nasıl, doğrudan uygulamaları, özellikle Hizmetleri ve altyapı ile çalışma veya yan etkileri olan nesneleri örneği dikkat edin. Uygulama çekirdek içinde tanımlanan ve içinde cmdlet'e kod başvurularını belirli uygulama türleri için bağımsız değişken olarak geçirilen soyutlama ile çalışmayı tercih eder.

## <a name="structuring-the-application"></a>Uygulama yapılandırma

Tek yapılı uygulamalar genellikle tek giriş noktası vardır. Bir ASP.NET Core web uygulaması söz konusu olduğunda, ASP.NET Core web projesi giriş noktası olacaktır. Ancak, bu çözüm yalnızca tek bir projenin oluşmalıdır anlamına gelmez. Sorunları ayrılması takip etmek için farklı katmanlara uygulamayı oluşturan ayırmak yararlıdır. Katmanlara parçalanmış sonra daha iyi kapsülleme elde etmeye yardımcı olabilir projeleri ayırmak için klasörleri gitmek yararlıdır. Bir ASP.NET Core uygulamayla bu hedeflere ulaşmak için en iyi yaklaşımı, temiz 5 bölümde tartışılan mimarisi çeşididir. Bu yaklaşım uygulamanın çözüm ayrı kitaplıklarının UI, altyapı ve ApplicationCore oluşan.

Bu projeler ek olarak, ayrı bir test projeleri de dahil edilen (Bölüm 9'test açıklanmıştır).

Uygulamanın nesne modeli ve arabirimleri ApplicationCore projesinde yerleştirilmelidir. Bu proje mümkün olduğunca az bağımlılıkları olacaktır ve çözümdeki diğer projelerin başvurur. Altyapı üzerinde doğrudan bağlı olmayan hizmetleri olarak kalıcı olmasını gerektiren iş varlıklarını ApplicationCore projesinde tanımlanır.

Kalıcılık nasıl gerçekleştirildiğini veya nasıl bir kullanıcı, bildirimleri gönderilebilir gibi uygulama ayrıntılarını altyapı projesinde tutulur. Bu projenin Entity Framework Çekirdek gibi uygulamaya özel paketleri başvurur, ancak proje dışında bu uygulamaların ayrıntılarını açığa çıkarmamalıdır. Altyapı hizmetleri ve depoları ApplicationCore proje tanımlanan arabirimi uygulamalıdır ve kendi kalıcılığı ApplicationCore içinde tanımlanan varlıklar saklama ve alma için sorumlu uygulamalarıdır.

ASP.NET Core UI proje herhangi bir kullanıcı Arabirimi düzeyi endişelerini sorumlu olduğu, ancak iş mantığı ya da altyapı ayrıntıları içermemesi gerekir. Aslında, ideal olarak, hatta bir bağımlılık iki proje arasında hiçbir bağımlılık yanlışlıkla sunulan sağlamaya yardımcı olur altyapı projede sahip olmamalıdır. Bu kayıt defteri sınıfların her projede dı kuralları tanımlamanıza olanak verir StructureMap gibi üçüncü taraf bir dı kapsayıcı kullanılarak gerçekleştirilebilir.

Uygulama Ayrıntıları uygulamasından kesilmesi için başka bir yaklaşım, tek tek Docker kapsayıcılarında belki de dağıtılan uygulamayı çağrısı mikro sağlamaktır. Bu sorunları ve iki projeleri arasında dı yararlanarak daha kesilmesi daha da büyük ayrımı sağlar, ancak ek karmaşıklık sahiptir.

### <a name="feature-organization"></a>Özellik kuruluş

Varsayılan olarak, ASP.NET Core uygulamaları denetleyicileri ve görünümler ve sık ViewModels dahil olmak üzere kendi klasör yapısı toplayın. Bu sunucu tarafı yapıları desteklemek üzere istemci tarafı kodlar genellikle ayrı olarak wwwroot klasöründe depolanır. Ancak, belirli bir özelliği genellikle çalışma bu klasörler arasında atlama gerektirdiğinden büyük uygulamalar bu kuruluşla sorunlarla karşılaşabilirsiniz. Dosya ve alt her klasördeki sayısı arttıkça, Çözüm Gezgini aracılığıyla kaydırmanın büyük bir bölümünü sonuçta daha zor alır. Bu sorun için bir çözüm olan uygulama kodu tarafından düzenlemek için *özelliği* yerine göre dosya türü. Bu kuruluş stili genellikle için özellik klasörleri veya özellik dilimler olarak adlandırılır (Ayrıca bkz: [dikey dilimler](http://deviq.com/vertical-slices/)).

ASP.NET Core MVC alanları bu amaç için destekler. Alanları kullanarak denetleyicileri ve görünümler klasörleri (aynı zamanda ilişkili tüm modelleri) her alanı klasörde ayrı ayrı kümeleri oluşturabilirsiniz. Şekil 7-1 alanları kullanarak bir örnek klasör yapısını gösterir.

![](./media/image7-1.png)

Şekil 7-1 örnek alanı kuruluş

Alanları kullanırken, ait oldukları alanın adı ile denetleyicilerinizi tasarlamanız öznitelikleri kullanmanız gerekir:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Ayrıca, yolları alan Destek eklemeniz gerekir:

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

Alanlar için yerleşik destek yanı sıra kendi klasör yapısı ve öznitelikler ve özel yollar yerine kuralları de kullanabilirsiniz. Bu ayrı klasörlerini eklemediniz görünümleri, denetleyicileri, tüm ilgili her özellik için tek bir yerde dosyaları görmeyi kolaylaştırır ve hiyerarşi daha düz tutulması vb. için özellik klasörleri yapmanıza olanak tanır.

ASP.NET Core yerleşik kuralı türleri davranışını denetlemek için kullanır. Bu kuralları değiştirmek ya da değiştirin. Örneğin, özellik adı (genellikle denetleyicisi bulunduğu klasörü karşılık gelen), ad göre belirli bir denetleyici için otomatik olarak alırsınız bir kural oluşturabilirsiniz:

```csharp
FeatureConvention : IControllerModelConvention
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

Uygulamanıza ConfigureServices MVC desteği eklediğinizde, isteğe bağlı olarak bu kural belirtin:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC bir kuralı görünümlerini bulmak için de kullanılır. Böylece görünümler (yukarıda FeatureConvention tarafından sağlanan özellik adı kullanarak), özellik klasörlerde bulunan bir özel kuralı geçersiz kılabilirsiniz. Bu yaklaşımı hakkında daha fazla bilgi ve MSDN makalesinden çalışma örnek indirme [ASP.NET Core MVC özelliği dilimleri](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Çapraz kesme sorunları

Uygulamaları arttıkça, çoğaltma ortadan kaldırmak ve tutarlılık sağlamak için çapraz kesme sorunları faktörü giderek önemli hale gelir. Olsa diğer birçok bazı arası kesme sorunları ASP.NET Core uygulamalarında kimlik doğrulama, model doğrulama kuralları, çıktı önbelleği ve hata işleme, gösterilebilir. ASP.NET Core MVC [filtreleri](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) , önce veya sonra istek işleme ardışık düzeninde belirli adımları kodu çalıştırmanızı sağlar. Örneğin, bir filtre önce ve sonra model bağlama, önce ve bir eylem veya önce ve sonra bir eylem sonucu çalıştırabilirsiniz. Bir yetkilendirme filtresi, kalan ardışık düzenini erişimi denetlemek için de kullanabilirsiniz. Şekil 7-2'de gösterildiği nasıl yürütme akış filtreleri yoluyla yapılandırdıysanız isteyin.

![Talep yetkilendirme filtreleri, kaynak filtreleri, Model bağlama, eylem filtreleri, eylem yürütme ve eylem sonucu dönüştürme, özel durum filtreleri, sonuç filtreleri ve sonuç yürütme işlenir. Yolda isteği yalnızca sonuç filtreleri ve kaynak filtreleri tarafından istemciye gönderilen bir yanıt olmadan önce işlenir.](./media/image7-2.png)

Şekil 7-2 İstek Yürütme filtreleri ve istek ardışık düzeni üzerinden.

Bunları denetleyicileri veya Eylemler uygulayabilmek için filtreleri genellikle öznitelik olarak uygulanır. Bu şekilde, eylem düzeyi geçersiz kılma veya denetleyici düzeyinde belirtilen filtreler temel yapı belirtilen filtreler eklendiğinde kendileri genel filtreleri geçersiz kılar. Örneğin, \[rota\] özniteliği denetleyicileri ve eylemleri arasındaki yolları oluşturmak için kullanılabilir. Benzer şekilde, yetkilendirme denetleyici düzeyinde yapılandırılabilir ve aşağıdaki örnek gösterdiği gibi ayrı eylemler tarafından geçersiz kılındı:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

İlk yöntem, oturum açma, AllowAnonymous filtre (özniteliği) Authorize filtresi denetleyici düzeyinde Ayarla geçersiz kılmak için kullanır. Kimliği doğrulanmış bir isteği ForgotPassword eylem (ve AllowAnonymous özniteliğine sahip değil sınıfı içinde herhangi bir işlem) gerektirir.

Filtreler, çoğaltma ortak hata ilkeleri API'ler işleme biçiminde ortadan kaldırmak için kullanılabilir. Örneğin, tipik bir API İlkesi model doğrulama başarısız olursa mevcut anahtarları başvuran isteklerin NotFound yanıt ve bir BadRequest yanıt getirmektir. Aşağıdaki örnek, bu iki ilke uygulamada gösterir:

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

Bu gibi koşullu koduyla kalabalık hale için eylem yöntemlerini izin vermez. Bunun yerine, ilkeleri gerektiği ölçüde temeline göre uygulanabilir filtreleri içine alın. Bu örnekte, bir komut API için gönderilen dilediğiniz zaman gerçekleşeceğini, model doğrulama denetimi aşağıdaki özniteliği tarafından değiştirilebilir:

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

Benzer şekilde, bir filtre, bir kaydı var ve bu denetimleri eylemi gerçekleştirmek için gereksinimini eylem yürütülmeden önce bir 404 dönüş denetlemek için kullanılabilir. Genel kurallar çekilen ve altyapı kodu ve iş mantığı, kullanıcı Arabiriminden ayırmak için çözümünüzün düzenlenmiş sonra MVC eylem yöntemleri son derece ince olmalıdır:

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Daha fazla bilgiyi filtreleri uygulama ve çalışma örnek MSDN makalesinden indirme hakkında [gerçek dünya ASP.NET Core MVC filtreleri](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Başvuruları – uygulamaları yapılandırma
> - **Alanlar**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN – ASP.NET Core MVC özelliği dilimleri**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtreler**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – gerçek dünya ASP.NET Core MVC filtreleri**  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Güvenlik

Web uygulamalarının güvenliğini sağlama birçok göz önünde büyük bir konu ile ilgilidir. En temel düzeyde, belirtilen bir isteğin geldiği ve bu isteği yalnızca gerektiği kaynaklara erişimi olduğundan emin olduktan bildiğiniz sağlayarak güvenlik içerir. Kimlik doğrulama isteği bilinen bir varlıktan geliyormuş gibi değerlendirilip değerlendirilmeyeceğini görmek için bir istek bu güvenilir veri deposunda ile sağlanan kimlik bilgileri karşılaştırma işlemidir. Yetkilendirme kullanıcı kimliğine göre belirli kaynaklara erişimi kısıtlama işlemidir. Üçüncü güvenlik sorunu istekleri için size gereken en az üçüncü taraflar tarafından gizli dinleme koruma [SSL, uygulamanız tarafından kullanıldığından emin olun](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Kimlik doğrulaması

ASP.NET Core, uygulamanız için oturum açma işlevleri desteklemek için kullanabileceğiniz bir üyelik sistemi kimliğidir. Yerel kullanıcı hesapları için destek ve aynı zamanda Microsoft Account, Twitter, Facebook, Google ve daha fazlası gibi sağlayıcılarından dış oturum açma sağlayıcısı destek vardır. ASP.NET Core kimliği ek olarak, windows kimlik doğrulaması, uygulamanızın kullanabilir veya bir üçüncü taraf kimlik sağlayıcısı ister [kimlik sunucusunu](https://github.com/IdentityServer/IdentityServer4).

Bireysel kullanıcı hesapları seçeneği seçili değilse ASP.NET Core kimlik yeni proje şablonlarını dahil edilir. Bu şablon, kayıt, oturum açma, dış oturum açma bilgileri, unutulan parolaları ve ek işlevsellik için destek içerir.

![](./media/image7-3.png)

Şekil 7-3 seçin bireysel kullanıcı kimliği önceden yapılandırılmış olmasını hesaplar.

Kimlik desteği, başlangıç, hem de ConfigureServices ve yapılandırma yapılandırılır:

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
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

UseIdentity yapılandırma yönteminde UseMvc önce görünen önemlidir. Kimlik ConfigureServices içinde yapılandırırken AddDefaultTokenProviders çağrısı fark edeceksiniz. Bu web iletişimin güvenliğini sağlamak için kullanılabilir, ancak bunun yerine SMS veya e-posta için bunları sırayla kimliğini onaylamak için üzerinden kullanıcılara gönderilen istekleri oluşturmak sağlayıcıları başvuruyor belirteçleri ile ilgisi sahiptir.

Hakkında daha fazla bilgiyi [iki faktörlü kimlik doğrulamasını yapılandırma](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) ve [dış oturum açma sağlayıcılarını etkinleştirme](https://docs.microsoft.com/aspnet/core/security/authentication/social/) resmi ASP.NET Core belgeleri gelen.

### <a name="authorization"></a>Yetkilendirme

Yetkilendirme en basit biçimi, anonim kullanıcılar için erişimi kısıtlamak içerir. Bu basitçe uygulayarak sağlanabilir \[Authorize\] özniteliği belirli denetleyicileri veya eylemler. Rolleri kullanılıyorsa gösterildiği gibi belirli rollere ait olan kullanıcılar için erişimi kısıtlamak için daha fazla öznitelik Genişletilebilir:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

Bu durumda, kullanıcılar ya da HRManager veya finans rolleri (veya her ikisi de) ait SalaryController erişimi gerekir. Bir kullanıcı birden çok rol için (yalnızca biri birkaç) ait zorunlu kılmak için her zaman gerekli rol belirten birden çok kez öznitelik uygulayabilirsiniz.

Birçok farklı denetleyicileri ve eylemleri dizelerde istenmeyen yineleme açabilir gibi belirli roller kümesi belirtme. Yetkilendirme kuralları saklayan, yetkilendirme ilkelerini yapılandırın ve ardından ilkeyi bireysel rolleri yerine uygularken belirtin \[Authorize\] özniteliği:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

İlkeleri bu şekilde kullanarak, belirli roller ya da uygulayan kuralları sınırlı kalmayarak Eylemler türlerini ayırabilirsiniz. Belirli kaynaklara erişmesi gereken yeni bir rol oluşturursanız, daha sonra yalnızca üzerinde her rollerin listesini güncelleştirme yerine bir ilke güncelleştirebilirsiniz her \[Authorize\] özniteliği.

#### <a name="claims"></a>Talepleri

Talep Kimliği doğrulanmış bir kullanıcı özelliklerini temsil eden adı değer çiftleridir. Örneğin, kullanıcıların çalışan numarası bir talep depolayabilir. Talep Yetkilendirme İlkeleri bir parçası olarak kullanılabilir. "EmployeeOnly" adında bir ilke oluşturabilirsiniz Bu örnekte gösterildiği gibi "EmployeeNumber" adlı bir talep varlığını gerektirir:

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

Bu ilke ile sonra kullanılabilir \[Authorize\] herhangi bir denetleyici ve/veya eylem, yukarıda açıklandığı gibi korumak için öznitelik.

#### <a name="securing-web-apis"></a>Web API güvenliğini sağlama

Çoğu web API'leri, bir belirteç tabanlı kimlik doğrulama sistemi uygulamanız gerekir. Belirteç kimlik doğrulama, durum bilgisiz ve ölçeklenebilir olacak şekilde tasarlanmıştır. Bir belirteç tabanlı kimlik doğrulama sisteminde istemci ilk ile kimlik doğrulama sağlayıcısını kimliğini doğrulaması gerekir. Başarılı olursa, istemcinin sadece bir şifreleme açısından anlamlı karakter dizesidir bir belirteç verilir. İstemci ardından bir API için bir istek yayınlamasını gerektiğinde bu belirteç isteği başlığındaki olarak ekler. Sunucu, ardından istek tamamlamadan önce istek üstbilgisinde bulunan belirteci doğrular. Şekil 7-4, bu işlemi gösterir.

![TokenAuth](./media/image7-4.png)

**Şekil 7-4.** Belirteç tabanlı kimlik doğrulaması Web API'leri için.

> ### <a name="references--security"></a>Başvuruları – güvenlik
> - **Güvenlik belgeleri genel bakış**  
> https://docs.microsoft.com/aspnet/core/security/
> - **Bir ASP.NET Core uygulamasında SSL zorlama**  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Kimliğe giriş**  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Yetkilendirme giriş**  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Kimlik doğrulama ve yetkilendirme Azure uygulama hizmetinde API uygulamaları için**  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>İstemci iletişimi

Sayfalarını sunmadan ve web API'leri aracılığıyla veri isteklerine yanıt ek olarak, ASP.NET Core uygulamaları doğrudan bağlı istemcileri ile iletişim kurabilir. Bu giden iletişim çeşitli aktarım teknolojiler, en yaygın olma WebSockets kullanabilirsiniz. ASP.NET Core SignalR, uygulamalarınıza gerçek zamanlı sunucu istemci iletişimi işlevselliği eklemek kolaylaştırır bir kitaplıktır. SignalR WebSockets, aktarım teknolojilerini çeşitli destekler ve geliştirici uygulama ayrıntılarından, dışarıda çok soyutlar.

ASP.NET Core SignalR şu anda geliştirilmekte ve ASP.NET Core sonraki sürümde kullanılabilir olacaktır. Ancak, diğer [kaynak WebSockets kitaplıkları açmak](https://github.com/radu-matei/websocket-manager) şu anda kullanılabilir.

Gerçek zamanlı istemci iletişimi, doğrudan WebSockets veya başka teknikler kullanarak olup çeşitli uygulama senaryolarda kullanışlıdır. Bazı örnekler şunlardır:

-   Canlı sohbet odası uygulamaları

-   Uygulamaları izleme

-   İş ilerleme güncelleştirmeleri

-   Bildirimler

-   Etkileşimli forms uygulamaları

İstemci iletişimi, uygulamalara oluştururken da genellikle iki bileşeni vardır:

-   Sunucu tarafı Bağlantı Yöneticisi'ni (SignalR hub'ı, WebSocketManager WebSocketHandler)

-   İstemci-tarafı kitaplığı

İstemcileri tarayıcıları – mobil uygulamaları, konsol uygulamalar, sınırlı değildir ve diğer yerel uygulamalar ayrıca SignalR/WebSockets kullanarak iletişim kurabilir. Aşağıdaki basit programı WebSocketManager örnek bir uygulama bir parçası olarak konsola sohbet uygulamaya gönderilen tüm içeriği görüntülemektedir:

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
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
```

Uygulamalarınızı doğrudan istemci uygulamaları ile iletişim kurmak ve gerçek zamanlı iletişim uygulamanızın kullanıcı artırmak göz önünde bulundurun yolları deneyimi göz önünde bulundurun.

> ### <a name="references--client-communication"></a>Başvuruları – istemci iletişimi
> - **ASP.NET Core SignalR**  
> <https://github.com/aspnet/SignalR>
> - **WebSocket Yöneticisi**  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Etki alanı tabanlı tasarım – bu uygulamalıdır?

Etki alanı tabanlı tasarım (DDD) olan üzerine odaklanan vurgular yazılım oluşturmaya Çevik bir yaklaşım *iş etki alanı*. Ağır indirimlere iletişim ve geliştiricileri için gerçek sisteminin nasıl çalıştığı ilişkilendirebilirsiniz iş etki alanı expert(s) etkileşim yerleştirir. Örneğin, stok ticaret anlaşması işleyen bir sistem oluşturuyorsanız, etki alanı Uzman deneyimli stok Aracısı olabilir. DDD büyük ve karmaşık iş sorunlarını gidermek için tasarlanmıştır ve yatırım anlama ve etki alanı modelleme, olmadığından daha küçük, daha basit uygulamalar için uygun değil genellikle.

Ekibinizin (teknik olmayan paydaşlara ve katkıda bulunanlar dahil) DDD yaklaşımı izleyerek yazılım oluştururken geliştirmelisiniz bir *bulunabilen dil* sorun alanı için. Diğer bir deyişle, aynı terminolojisi Modellenen gerçek kavram, yazılım eşdeğer ve (örneğin, veritabanı tabloları) kavram kalıcı hale getirmek için mevcut olabilecek tüm yapıları için kullanılmalıdır. Bu nedenle, her yerden dilde açıklanan kavramları temelini, *etki alanı modeli*.

Sistem davranışını temsil etmek için birbiriyle etkileşim nesnelerinin, etki alanı modeli oluşur. Bu nesneler, aşağıdaki kategorilere ayrılır:

-   [Varlıkları](http://deviq.com/entity/), bir iş parçacığı kimliği nesneleriyle temsil eder. Varlıklar, genellikle, bunlar daha sonra alınabilir bir anahtarla kalıcı depolanır.

-   [Toplamalar](http://deviq.com/aggregate-pattern/), bir birim olarak kalıcı nesne gruplarını temsil eder.

-   [Değer nesneleri](http://deviq.com/value-object/), özellik değerlerine toplamını temel alarak karşılaştırılabilir kavramları temsil eder. Örneğin, bir başlangıç ve bitiş tarihi oluşan DateRange.

-   [Etki alanı olayları](https://martinfowler.com/eaaDev/DomainEvent.html), sisteminin diğer bölümleriyle ilgi sistem içinde gerçekleştiği şeyler temsil eder.

DDD etki alanı modeli modelindeki karmaşık davranışı kapsülleyen unutmayın. Varlıklar, özellikle, yalnızca özelliklerinin koleksiyonlarından oluşan olmamalıdır. Etki alanı modeli davranışına sahip değil ve yalnızca sistem durumunu temsil eder, bu olarak kabul edilir bir [anemic modeli](http://deviq.com/anemic-model/), GGG istenmeyen olduğu.

Bu model türlerinin yanı sıra DDD genellikle desenleri çeşitli uygular:

-   [Depo](http://deviq.com/repository-pattern/), Kalıcılık ayrıntılarını özetleyen için.

-   [Fabrika](https://en.wikipedia.org/wiki/Factory_method_pattern), karmaşık nesne oluşturma Kapsüllenen için.

-   Davranış tetikleme gelen bağımlı davranışı kesilmesi için etki alanı olaylar.

-   [Hizmetleri](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), kapsülleyerek karmaşık davranışı ve/veya altyapı uygulama ayrıntıları.

-   [Komut](https://en.wikipedia.org/wiki/Command_pattern), ayırma için verme komutları ve komut yürütme.

-   [Belirtimi](http://deviq.com/specification-pattern/), sorgu ayrıntıları Kapsüllenen için.

DDD gevşek bağlantı, kapsülleme ve birim testleri kullanarak kolayca doğrulanabilir kodu için izin verme temiz daha önce ele alınan mimarisi kullanımını da önerir.

### <a name="when-should-you-apply-ddd"></a>DDD uyguladığınızda

DDD (yalnızca teknik) önemli iş karmaşıklık ile büyük uygulamalar için çok uygundur. Uygulama etki alanı uzmanlar bilgisi istemeniz gerekir. İş kuralları ve yalnızca depolama ve veri depolarına çeşitli kayıtları geçerli durumu alma ötesinde etkileşimleri temsil eden etki alanı modeli kendisini önemli davranışı olmalıdır.

### <a name="when-shouldnt-you-apply-ddd"></a>DDD uyguladığınızda döndürmemelidir

DDD modelleme, mimari ve daha küçük uygulamalar veya temelde yalnızca CRUD (oluşturma/okuma/güncelleştirme/silme) olan uygulamalar için garanti değil iletişimi yatırım gerektirir. Uygulamanızı DDD aşağıdaki yaklaşımlardan, ancak etki alanınız yok davranışı anemic bir modelle olduğunu bulmak tercih ederseniz, yaklaşım zorlanıyor gerekebilir. Uygulamanızı DDD ihtiyacınız olmayabilir ya da etki alanı modeli yerine veritabanı ya da kullanıcı arabirimi iş mantığını saklamak için uygulamanızı yeniden düzenleme yardıma ihtiyacınız.

Karma bir yaklaşım, yalnızca GGG uygulamanın işlem ya da daha karmaşık alanlar için ancak daha basit CRUD veya uygulama salt okunur bölümlerini için kullanmak üzere olacaktır. Örneğin, bir raporu görüntülemek için veya bir Pano için görselleştirmek için verileri sorgulama, bir toplama kısıtlama söz konusu gerekmez. Bu tür gereksinimleri için daha basit, ayrı okuma modeline sahip edilebilir.

> ### <a name="references--domain-driven-design"></a>Başvuruları – etki alanı Odaklı Tasarım
> - **Düz İngilizce (StackOverflow yanıt) DDD**  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Dağıtım

Burada barındırılacak bağımsız olarak ASP.NET Core uygulamanızı dağıtma sürecinde ilgili birkaç adım vardır. Yapılabilir uygulamayı yayımlamak için ilk adımdır dotnet kullanarak yayımlamak CLI komutu. Bu uygulamayı derleyin ve atanmış bir klasöre uygulamayı çalıştırmak için gereken tüm dosyaların yerleştirin. Visual Studio'dan dağıttığınızda, bu adımı sizin için otomatik olarak gerçekleştirilir. Yayımlama klasörü .exe ve .dll dosyaları için uygulama ve onun bağımlılıklarını içerir. Kendi başına bir uygulama .NET çalışma zamanı sürümünü de içerir. ASP.NET Core uygulamaları da yapılandırma dosyalarını, statik istemciyi varlıklar ve MVC görünümleri içerir.

ASP.NET Core uygulamaları sunucu önyüklenir ve uygulama (veya sunucu) çökerse yeniden başlatılması gerekir konsol uygulamalardır. Bir işlem yöneticisi, bu işlemi otomatikleştirmek için kullanılabilir. ASP.NET Core en yaygın işlem yöneticilerinden Nginx ve Linux ve IIS üzerinde Apache ya da Windows'da Windows hizmeti ' dir.

İşlem Yöneticisi ek olarak, ASP.NET Core uygulamaları Kestrel web sunucusunda barındırılan bir ters proxy sunucusu kullanmanız gerekir. Ters proxy sunucusu internet'ten HTTP isteklerini alır ve bunları Kestrel için bazı ön işleme sonra iletir. Ters proxy sunucuları uygulama için bir güvenlik katmanı sağlamak ve (trafiğini Internet'ten gösterilen) kenar dağıtımlar için gereklidir. Kestrel görece olarak daha yeni ve henüz belirli saldırılarına karşı savunma sağlamaz. Kestrel aynı zamanda barındırma üstbilgileri gibi teknikler kendisiyle aynı bağlantı noktasını ve IP adresini birden çok uygulamayı barındıran etkinleştirmek için kullanılamaz aynı bağlantı noktasında birden çok uygulamayı barındıran desteklemiyor.

![Internet'e kestrel](./media/image7-5.png)

Şekil 7-5 ters proxy sunucunun arkasında Kestrel içinde barındırılan ASP.NET

Ters proxy yararlı olabilir başka bir SSL/HTTPS kullanarak birden çok uygulama güvenliğini sağlamak için bir senaryodur. Bu durumda, yalnızca ters proxy SSL yapılandırılmış olması gerekir. Ters proxy sunucusu ve Kestrel arasındaki iletişimi yer HTTP üzerinden Şekil 7-6'da gösterildiği gibi ele geçirebilir.

![](./media/image7-6.png)

Şekil 7-6 HTTPS güvenlikli ters proxy sunucunun arkasında barındırılan ASP.NET

Bir giderek popüler ASP.NET Core uygulamanızda ardından yerel olarak barındırılan veya bulut tabanlı barındırmak için Azure'da dağıtılan bir Docker kapsayıcısı barındırmak için bir yaklaşımdır. Docker kapsayıcısı Kestrel üzerinde çalışan uygulama kodunuz içerebilir ve bir ters proxy sunucunun arkasındaki yukarıda gösterildiği gibi dağıtılması.

Uygulamanızı Azure üzerinde koyduysanız birkaç hizmetleri sağlamak için ayrılmış bir sanal gereç olarak Microsoft Azure uygulama ağ geçidi kullanabilirsiniz. Tek tek uygulamalar için ters proxy görevi gören ek olarak, uygulama ağ geçidi aynı zamanda aşağıdaki özellikleri sunmaktadır:

-   HTTP Yük Dengeleme

-   SSL boşaltma (yalnızca Internet'e SSL)

-   Uçtan uca SSL

-   Çok siteli yönlendirme (tek bir uygulama ağ geçidi en fazla 20 sitelerinde birleştirmek)

-   Web uygulaması güvenlik duvarı

-   Websocket desteği

-   Gelişmiş tanılama

*Bölüm 10'daki Azure dağıtım seçenekleri hakkında daha fazla bilgi edinin.*

> ### <a name="references--deployment"></a>Başvuruları – dağıtım
> - **Barındırma ve dağıtımına genel bakış**  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Ters proxy ile Kestrel kullanma zamanı**  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Docker ana ASP.NET Core uygulamaları**  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Azure uygulama ağ geçidi Tanıtımı**  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
[Önceki] (ortak-istemci-tarafı-web-technologies.md) [sonraki] (work-with-data-in-asp-net-core-apps.md)
