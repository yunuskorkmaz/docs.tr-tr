---
title: ASP.NET Core MVC geliştirme uygulamaları
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | ASP.NET Core MVC uygulamaları geliştirme
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 7459173f21bd5219c2aa7b994ac2b2b44857375f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152791"
---
# <a name="develop-aspnet-core-mvc-apps"></a>ASP.NET Core MVC geliştirme uygulamaları

> "Bunu ilk kez doğru almak önemli değildir. Son doğru almak oldukça önemlidir."  
> _-Andrew Hunt ve David Thomas_

ASP.NET Core, modern bulut için iyileştirilmiş web uygulamaları oluşturmaya yönelik platformlar arası, açık kaynaklı bir çerçevedir. ASP.NET Core uygulamaları, basit ve modüler, bağımlılık ekleme, büyük Test Edilebilirlik ve bakımı etkinleştirmek için yerleşik destek. Görünüm tabanlı uygulamaların yanı sıra modern web API'leri oluşturmaya destekler, MVC ile birleştirilmiş ASP.NET Core, Kurumsal web uygulamaları oluşturmak güçlü bir çerçeve olan.

## <a name="mapping-requests-to-responses"></a>Eşleme isteklerini yanıtlar

Temelinde, ASP.NET Core uygulamaları, gelen istekleri giden yanıtlarını eşleyin. Düşük düzeyde, bu ara yazılım ile gerçekleştirilir ve basit bir ASP.NET Core uygulamaları ve mikro hizmetler, yalnızca özel bir ara yazılım oluşabilir. ASP.NET Core MVC kullanırken açısından düşünmek biraz daha yüksek bir düzeyde çalışabilir _yollar_, _denetleyicileri_, ve _eylemleri_. Her gelen istek uygulamanın yönlendirme tablosu ile karşılaştırılır ve eşleşen bir rota bulunursa (bir denetleyiciye ait) ilişkili eylem yöntemi isteği işlemek için çağrılır. Eşleşen hiçbir yol bulunursa, bir hata işleyicisi (NotFound sonucu döndürerek bu durumda,) çağrılır.

ASP.NET Core MVC uygulamaları, geleneksel yollar, öznitelik rotaları veya her ikisini de kullanabilirsiniz. Geleneksel yollar yönlendirme belirterek kod içinde tanımlanan _kuralları_ aşağıdaki örnekte olduğu gibi bir söz dizimi kullanarak:

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

Bu örnekte, "varsayılan" adlı bir rota yönlendirme tablosuna eklendi. Bir rota şablonu için yer tutucu ile tanımlar _denetleyicisi_, _eylem_, ve _kimliği_. Denetleyici ve eylem yer tutucuları varsayılan belirtilen sahip ("Home" ve "Index", sırasıyla), ve kimliği tutucudur isteğe bağlı (tarafından virtue, bir "?" uygulanmış). Kuralı ikinci bölümü eyleme denetleyicinin adı bir isteğin ilk parçası karşılık gelmelidir durumları burada tanımlanan ve ardından gerekirse üçüncü bölümü bir kimliği parametre temsil eder. Geleneksel yollar genellikle, uygulama için tek bir yerde gibi başlangıç sınıfındaki yapılandırma yöntemi tanımlanır.

Öznitelik rotaları denetleyicileri ve eylemleri doğrudan uygulanan yerine genel olarak belirtildi. Bu, belirli bir yöntem arıyorsanız, ancak yönlendirme bilgileri uygulamada tek bir yerde tutulan değil demektir daha bulunabilir hale getirme avantajına sahiptir. Öznitelik rotaları ile kolayca için belirli bir eylemi birden çok yol belirtmek, yapabilir denetleyicilere ve eylemlere arasında rotaları birleştirin. Örneğin:

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

Yollar [HttpGet] üzerinde belirtilebilir ve eklemek için gereğinden kurtulursunuz benzer öznitelikleri [yol] özniteliğini ayırmak. Öznitelik rotaları da aşağıda gösterildiği gibi denetleyici veya eylem adları yineleyin gereksinimini azaltmak için belirteçleri kullanabilirsiniz:

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Belirtilen bir isteğin bir rota için eşleşen, ancak önce eylem yöntemi çağırıldıktan sonra ASP.NET Core MVC gerçekleştirecek [model bağlama](/aspnet/core/mvc/models/model-binding) ve [model doğrulama](/aspnet/core/mvc/models/validation) istekte. Model bağlama, gelen HTTP veri çağrılacak eylem yönteminin bir parametre olarak belirtilen .NET türlerine dönüştürme için sorumludur. Örneğin, bir eylem yönteminin bir int kimliği parametre bekliyor, bu parametre, isteğin bir parçası sağlanan bir değerden sağlamak model bağlama deneyecek. Bunu yapmak için model bağlama için gönderilen bir formu değerleri, rota değerleri ve sorgu dizesi değerlerini arar. Bir kimlik değeri bulundu varsayıldığında, da bir tamsayıya eylem metodun Metoda geçilen önce dönüştürülür.

Model doğrulama, model bağlama sonra ancak eylem yöntemi çağrılmadan önce gerçekleşir. Model doğrulama, model türü üzerinde isteğe bağlı öznitelikleri kullanır ve belirtilen model nesnesi belirli veri gereksinimlere uymasını sağlamak yardımcı olabilir. Belirli değerleri olarak belirtilebilir gerekli veya belirli bir uzunlukta veya sayısal aralık için sınırlı, vs. Doğrulama öznitelikleri belirtildiğinde, ancak modelin kendi gereksinimlerine uymuyor ModelState.IsValid özelliği false olacak ve başarısız doğrulama kuralları kümesi isteği yapan istemcinin göndermek kullanılabilir.

Model doğrulama kullanıyorsanız, her zaman uygulamanızı geçersiz veriler bozuk olmadığından emin olmak için tüm durum değiştirme komutları gerçekleştirmeden önce model geçerli olduğunu denetleyin. Kullanabileceğiniz bir [filtre](/aspnet/core/mvc/controllers/filters) her eylem için bu kodu eklemek için gereken önlemek için. Ortak ilkelere ve geniş kapsamlı kritik konular hedef temelinde uygulanabilir, ASP.NET Core MVC filtreleri grupları istekleri sızdırılması bir yol sunar. Bireysel işlemlere, tüm denetleyicileri veya genel olarak bir uygulama için filtre uygulanabilir.

ASP.NET Core MVC Web API'lerini destekleyen [ _içerik anlaşması_](/aspnet/core/mvc/models/formatting), istekleri yanıtlar nasıl biçimlendirilmesi gerektiğini belirtmek izin verme. İstekte sağlanan üstbilgileri bağlı olarak, XML, JSON veya desteklenen başka bir biçimde yanıt veriyor eylemleri biçimlendirir. Bu özellik, farklı veri biçimi gereksinimlerine sahip birden çok istemci tarafından kullanılmak üzere aynı API sağlar.

> ### <a name="references--mapping-requests-to-responses"></a>Başvuruları – isteklerini yanıtlar eşleme
>
> - **Denetleyici eylemlerine yönlendirme**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Model bağlama**
> <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Model doğrulama**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtreleri**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>

## <a name="working-with-dependencies"></a>Bağımlılıkları ile çalışma

ASP.NET Core için yerleşik desteği vardır ve dahili olarak bilinen bir tekniğin kullanır [bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection). Bağımlılık ekleme, bir uygulamanın farklı kısımlarını arasındaki bu sıkı bağ sağlayan bir tekniktir. Bazı bağlantı arzu çünkü test ya da değiştirme için uygulamanın parçalarını yalıtmak üzere kolaylaştırır. Ayrıca, bir uygulamanın bir bölümünde değişiklik uygulamada başka bir yere beklenmeyen bir etkisi olacağını düşürür. Bağımlılık ekleme bağımlılık tersine çevirme ilkeye dayanarak ve genellikle açık/kapalı ilkesini ulaşmak için anahtardır. Uygulamanızın çalışma şeklinden bağımlılıklarını değerlendirirken dikkat [statik cling](https://deviq.com/static-cling/) kod kokusu ve aphorism unutmayın "[Birleştirici yeni](https://ardalis.com/new-is-glue)."

Statik cling sınıflarınızı statik yöntemler çağrı yapmak veya yan etkileri veya bağımlılıkları altyapıya sahip statik özelliklerine erişim oluşur. Örneğin, sırasıyla bir veritabanına yazan, statik bir yöntemi çağıran bir yöntemi varsa, yöntemi sıkı şekilde veritabanına bağlı. Bu veritabanı çağrısı keser herhangi bir şey yönteminizi çalışmamasına neden olur. Bu tür testler statik çağrıları sahte ticari sahte kitaplıkları gerektiren ya da bir test veritabanı yerinde yalnızca test edilebilir olduğundan bu tür yöntemler test öğesinin kolay değildir. Altyapı, özellikle de tamamen durum bilgisi olmayan herhangi bir bağımlılığa sahip olmayan statik çağrıları çağrı ve bağ veya (ötesinde kodu statik çağrısı kendisini eşlenmesiyle) Test Edilebilirlik üzerinde hiçbir etkisi bir sakınca yoktur.

Birçok geliştiricinin statik cling ve genel durum risklerini anlayın, ancak kendi kod aracılığıyla doğrudan belirli uygulamalar için yine de sıkı bir şekilde birleştirin. "Bağlantılı yeni bir" Bu eşleştirmeye bir anımsatıcı ve değil bir genel condemnation kullanımını olacak şekilde tasarlanmış `new` anahtar sözcüğü. Gibi statik yöntem çağrılarını türleri genellikle dış bağımlılıkları olmayan yeni örneklerini değil sıkı bir şekilde kod uygulama ayrıntılarını birleştirin veya test daha zor hale. Ancak, bir sınıf örneği, her zaman sabit kodlamak için o belirli örnekte ilgili belirli bir konumda mantıklıdır veya bağımlılık olarak bu örneğe istemek için daha iyi bir tasarım olacaksa, dikkate alınması gereken yalnızca bir kısa dakikanızı ayırın.

### <a name="declare-your-dependencies"></a>Bağımlılıklarınızı bildirme

ASP.NET Core yöntemleri sahip etrafında oluşturulmuştur ve bunları bağımsız değişken olarak isteyen bağımlılıklarını sınıfları bildirme. ASP.NET uygulamalarının tipik olarak ayarlandığı bir başlangıç sınıfta kendisi çeşitli noktalarda bağımlılık eklemeyi desteklemek için yapılandırılır. Başlangıç sınıfınızın bir oluşturucusu yoksa, oluşturucu aracılığıyla bağımlılıklar isteyebilir şu şekilde:

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

Başlangıç sınıfı hiçbir açık tür gereksinimlerin olduğuna açısından ilginçtir. Özel başlangıç temel sınıftan devralmaz ya da herhangi bir belirli arabirimini uygulamıyor. Ona bir oluşturucu veya verebilirsiniz ve istediğiniz sayıda parametre oluşturucuda belirtebilirsiniz. Uygulamanız için yapılandırdığınız web ana bilgisayarı başlatıldığında kullanacak şekilde söylediğiniz başlangıç sınıfı çağıracak ve bağımlılık ekleme, başlangıç sınıfı gerektirdiği tüm bağımlılıkların doldurmak için kullanır. Elbette, ASP.NET Core tarafından kullanılan hizmet kapsayıcı yapılandırılmamışlardır parametreleri istek, bir özel durum alırsınız, ancak bağımlılıklarını takılıyor sürece kapsayıcı bilir hakkında istediğinizi isteyebilir.

Başlangıç örneği oluşturduğunuzda, ASP.NET Core uygulamalarınızı sağ başından bağımlılık ekleme yerleşiktir. Ayrıca, başlangıç sınıfı için yok bitmez. Yapılandırma yönteminin bağımlılıkları da isteyebilirsiniz:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Bu davranışı özel durumu Createservicereplicalisteners() yöntemdir; Bunu IServiceCollection türünde tek bir parametre almalıdır. Ayrıca, bir yandan Hizmetleri kapsayıcıya nesneleri eklemek için sorumlu olduğundan ve diğer tüm yapılandırılmış hizmetlerini IServiceCollection parametresi üzerinden erişimi olan bağımlılık eklemeyi desteklemek gerçekten gerekmiyor. Bu nedenle, her parçasını başlangıç sınıfı, bir parametre olarak gerekli hizmet isteyen veya IServiceCollection Createservicereplicalisteners() içinde çalışan ASP.NET Core Hizmetleri koleksiyonda tanımlanan bağımlılıklar çalışabilirsiniz.

> [!NOTE]
> Belirli hizmetleri başlatma sınıfınıza kullanılabilir olduğundan emin olmak ihtiyacınız varsa, bunları yapılandırabilirsiniz WebHostBuilder ve kendi Createservicereplicalisteners() yöntemi kullanarak.

Başlangıç sınıfı diğer bölümlerine kendi hizmetlerine filtreleri için Ara yazılıma denetleyicilerinden ASP.NET Core uygulamanızı nasıl yapılandırmanız gerektiği bir modeldir. Her durumda, uygulamanız gereken [açık bağımlılıkları İlkesi](https://deviq.com/explicit-dependencies-principle/)bağımlılıklarınızı isteyen yerine doğrudan oluşturarak ve bağımlılık ekleme uygulamanızda kullanma. Nerede ve nasıl doğrudan uygulamaları, özellikle hizmetler ve altyapı ile çalışır veya yan etkileri olan nesneleri örneği dikkat edin. Uygulama çekirdek içinde tanımlanan ve bağımsız değişkenler olarak belirli uygulama türlerini runbook'a kod başvurularına geçirilen soyutlama ile çalışmayı tercih eder.

## <a name="structuring-the-application"></a>Uygulama yapılandırma

Tek yapılı uygulamalar genellikle tek giriş noktası vardır. Bir ASP.NET Core web uygulaması söz konusu olduğunda, ASP.NET Core web projesi giriş noktası olacaktır. Ancak, bu çözüm yalnızca tek bir projenin oluşmalıdır anlamına gelmez. Görev ayrımı nettir takip etmek için uygulamayı farklı katmanlara ayırmak kullanışlıdır. Katmanlara parçalanmış sonra daha iyi saklama elde etmeye yardımcı olabilir projeleri ayırmak için klasörleri gitmek yararlıdır. Bir ASP.NET Core uygulaması ile bu hedeflere ulaşmak için en iyi yaklaşım temiz 5. bölümde tartışılan mimari bir çeşididir. Bu yaklaşım uygulamanın çözüm ayrı kitaplıklarını kullanıcı Arabirimi, altyapı ve ApplicationCore oluşur.

Bu projeler ek olarak, ayrı bir test projeleri de dahil edilir (Bölüm 9'da test açıklanmıştır).

Uygulamanın nesne modeli ve arabirimleri ApplicationCore projede yerleştirilmelidir. Bu proje mümkün olduğu kadar az bağımlılıklar sahiptir ve çözümdeki diğer projelerin başvurur. Altyapısında doğrudan bağlı olmayan hizmetler olarak kalıcı gereken iş varlıkları ApplicationCore projesinde tanımlanmıştır.

Kalıcılık nasıl gerçekleştirildiğini veya nasıl bir kullanıcı, bildirimleri gönderilebilir gibi uygulama ayrıntılarını altyapı projede tutulur. Bu proje, Entity Framework Core gibi uygulamaya özel paketler başvurur, ancak proje dışında bu uygulamaların ayrıntılarını kullanıma sunmamalıdır. Altyapı hizmetleri ve depoları ApplicationCore projede tanımlanan arabirimi uygulamalıdır ve bunun Kalıcılık uygulamalarını alma ve varlıkları ApplicationCore içinde tanımlanan depolama sorumludur.

ASP.NET Core UI projesi herhangi bir kullanıcı Arabirimi düzeyi sorunları için sorumlu olan, ancak iş mantığı ya da altyapı ayrıntıları içermemelidir. Aslında, ideal olarak, hatta bir bağımlılık iki projeler arasında hiçbir bağımlılık yanlışlıkla sunulan olmanıza yardımcı olur altyapısı projesi hakkında sahip olmamalıdır. Bu, bir üçüncü taraf DI kapsayıcı kayıt defteri sınıflar her projede DI kuralları tanımlamak olanak tanıyan StructureMap gibi kullanarak gerçekleştirilebilir.

Uygulama Ayrıntıları uygulamadan ayırma başka bir yaklaşım, uygulamanın çağrı belki de tek bir Docker kapsayıcılarında dağıtılmış mikro hizmetler, sahip olmaktır. Bu sorunları ve iki projeler arasında DI yararlanarak daha ayırma daha da fazla ayrımı sağlar, ancak ek karmaşıklığa sahiptir.

### <a name="feature-organization"></a>Özellik kuruluş

Varsayılan olarak, ASP.NET Core uygulamaları bunların klasör yapılarını denetleyicileri ve görünümler ve Viewmodel'lar sık içerecek şekilde düzenleyin. Bu sunucu tarafı yapılarını desteklemek üzere istemci tarafı kod, genellikle wwwroot klasörü içinde ayrı olarak depolanır. Ancak, genellikle herhangi belirli bir özellik üzerinde çalışan bu klasör arasında atlama gerektirdiğinden büyük uygulamalar bu kuruluşun sorunlarla karşılaşabilirsiniz. Bu dosyaları ve alt klasörlerdeki her klasör sayısı arttıkça, çözüm Gezginine kaydırma büyük ölçüde sonuçta daha zor alır. Bu soruna bir çözüm ise uygulama kodu tarafından düzenlemek için _özellik_ bunun yerine dosya türü. Bu kuruluş stili genellikle özellik klasörler veya özellik dilim adlandırılır (Ayrıca bkz: [Dikey dilimleri](https://deviq.com/vertical-slices/)).

ASP.NET Core MVC, bu amaçla alanlarını destekler. Alanlara kullanarak denetleyicileri ve görünümleri klasörleri (aynı zamanda ilişkili herhangi bir model) her alan klasördeki ayrı kümeleri oluşturabilirsiniz. Şekil 7-1 alanlara kullanarak bir örnek klasör yapısını gösterir.

![](./media/image7-1.png)

Şekil 7-1 örnek alanı kuruluş

Alanları kullanırken, ait oldukları alanın adı ile denetleyicilerinizi donatmak için öznitelikleri kullanmanız gerekir:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Alan desteği eklemek için yollarınızı gerekir:

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

Alanlar için yerleşik destek ek olarak kendi klasör yapısını ve öznitelikler ve özel yollar yerine kuralları da kullanabilirsiniz. Bu ayrı klasörlerini eklemediğiniz görünümleri, denetleyicileri, hiyerarşi düzleştiren tutulması ve tüm ilgili dosyalar tek bir yerde her bir özellik görmek kolaylaştırarak vb. için özellik klasörleri olmasını çalıştırmasına olanak tanır.

ASP.NET Core yerleşik kuralı türleri davranışını denetlemek için kullanır. Bu kuralları değiştirmek ya da değiştirin. Örneğin, özellik adı, ad alanı (Bu genellikle, denetleyici bulunduğu klasöre ilişkilendirir) göre belirli bir denetleyici için otomatik olarak alacak bir kural oluşturabilirsiniz:

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

Uygulamanıza Createservicereplicalisteners() MVC için destek eklediğinizde bir seçenek olarak bu kural belirtin:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC bir kuralı görünümlerini bulmak için de kullanılır. Böylece görünümleri (yukarıda FeatureConvention tarafından sağlanan özellik adı kullanarak) özellik klasörlerde bulunan bir özel kuralı geçersiz kılabilirsiniz. Bu yaklaşımı hakkında daha fazla bilgi edinin ve MSDN makalesi, bir çalışma örneği indirin [ASP.NET Core MVC özellik dilimleri](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Geniş kapsamlı kritik konular

Uygulamaları büyüdükçe, çoğaltma ortadan kaldırabilir ve tutarlılık sağlamak için geniş kapsamlı kritik konular etkimesi giderek daha önemli hale gelir. Vardır ancak diğer birçok bazı geniş kapsamlı kritik konular ASP.NET Core uygulamalarında kimlik doğrulama, model doğrulama kuralları, çıktı önbelleği ve hata işleme örnekleridir. ASP.NET Core MVC [filtreleri](/aspnet/core/mvc/controllers/filters) önce veya sonra bazı adımlar istek işleme ardışık düzeninde kod çalıştırmanıza olanak tanır. Örneğin, bir filtre önce ve sonra model bağlama, önce ve sonra bir eylem veya önce ve sonra bir eylem sonucu çalıştırabilirsiniz. Bir yetkilendirme filtresi, kalan ardışık düzenini erişimi denetlemek için de kullanabilirsiniz. Şekil 7-2'de gösterildiği nasıl yürütme akışları, yapılandırılmış istek filtreleri.

![İstek, yetkilendirme filtreleri, kaynak filtreleri, Model bağlama, eylem filtreleri, eylem yürütme ve eylem sonucu dönüştürme, özel durum filtreleri, sonuç filtreleri ve sonuç yürütme işlenir. Biçimi üzerinde istek yalnızca sonuç filtreleri ve kaynak filtreler tarafından istemciye gönderilen bir yanıt olmadan önce işlenir.](./media/image7-2.png)

Şekil 7-2 İstek Yürütme filtreleri ve istek ardışık düzeni üzerinden.

Bunları denetleyicileri veya Eylemler uygulayabilirsiniz böylece filtreleri genellikle öznitelik olarak uygulanır. Bu şekilde düzeyinde geçersiz kılma eylem veya denetleyici düzeyinde belirtilen filtreleri temel yapı belirtilen filtreler eklendiğinde kendileri genel filtreleri geçersiz kılar. Örneğin, \[rota\] özniteliği derleme denetleyicileri ve eylemleri arasındaki yolları'kurmak için kullanılabilir. Benzer şekilde, yetkilendirme denetleyici düzeyinde yapılandırılabilir ve aşağıdaki örnekte gösterildiği gibi bireysel eylemleri tarafından geçersiz kılınmış:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

İlk yöntem, oturum açma, denetleyici düzeyinde Authorize filtre geçersiz kılmak için AllowAnonymous filtre (öznitelik) kullanır. Kimliği doğrulanmış bir isteği ForgotPassword eylemi (ve herhangi bir işlem AllowAnonymous özniteliğine sahip değil sınıfında) gerektirir.

Filtreler, çoğaltma ilkeleri için API'leri işleme yaygın hata biçiminde ortadan kaldırmak için kullanılabilir. Örneğin, tipik bir API İlkesi mevcut anahtarlar başvuran isteklerin NotFound yanıt ve bir BadRequest yanıt model doğrulama başarısız olursa geri döndürmektir. Aşağıdaki örnek, bu iki ilke uygulamada gösterir:

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

Bu gibi koşullu kodla dağınık hale, eylem yöntemlerine izin vermez. Bunun yerine, gerektiğinde bir temelinde uygulanabilen filtreleri içine ilkeleri çekin. Bu örnekte, bir komut, API'ye gönderilen dilediğiniz zaman gerçekleşmesi gerektiğini, model doğrulama denetimi aşağıdaki özniteliği tarafından değiştirilebilir:

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

Benzer şekilde, bir filtre, bir kaydı var ve bu denetimleri eylemi gerçekleştirmek için gereksinimini ortadan kaldırır eylem yürütülmeden önce bir 404 döndüren denetlemek için kullanılabilir. Genel kurallar çekilen ve altyapı kod ve iş mantığı, kullanıcı Arabiriminden ayırmak için çözümünüzün düzenlenmiş sonra MVC eylemi yöntemlerinizi son derece basit olması gerekir:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Daha fazla uygulama filtreleri ve MSDN makalesi, bir çalışma örneği indirin hakkında [gerçek dünya ASP.NET Core MVC filtreleri](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Başvuruları – uygulamaları yapılandırma
>
> - **Alanlar**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine – ASP.NET Core MVC özellik dilimleri**  
 > <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtreler**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – gerçek ASP.NET Core MVC filtreleri**  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Güvenlik

Web uygulamalarının güvenliğini sağlama, birçok konuları ile büyük bir konu olduğu. En temel düzeyde güvenlik, belirtilen bir isteğin geldiği ve ardından istek yalnızca olması gerektiği kaynaklarına erişimi olduğundan emin bildiğiniz gelmelerini sağlamak anlamına gelir. Kimlik doğrulama isteği bilinen bir varlıktan yakında olarak değerlendirilip değerlendirilmeyeceğini görmek için bir istek bu güvenilir veri deposunda sağlanan kimlik bilgileri karşılaştırma işlemidir. Yetkilendirme, belirli kaynaklara kullanıcı kimliğine göre erişimi kısıtlama işlemidir. Üçüncü bir güvenlik sorunu için size gereken en az üçüncü taraflarca gizlice gelen istekleri koruduğu [uygulamanız için SSL kullanıldığından emin olun](/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Kimlik doğrulaması

ASP.NET Core, uygulamanız için oturum açma işlevlerini desteklemek için kullanabileceğiniz bir üyelik sistemi kimliğidir. Bunun yanı sıra Microsoft Account, Twitter, Facebook, Google ve daha fazlası gibi sağlayıcılarından dış oturum açma sağlayıcısı destek yerel kullanıcı hesapları için destek de vardır. ASP.NET Core kimliği ek olarak, uygulamanızı windows kimlik doğrulaması kullanabilir veya bir üçüncü taraf kimlik sağlayıcısı ister [kimlik sunucusu](https://github.com/IdentityServer/IdentityServer4).

Bireysel kullanıcı hesapları seçeneğini seçtiyseniz, ASP.NET Core kimliği yeni proje şablonları bulunur. Bu şablon, kaydı, oturum açma, dış oturum açma bilgileri, unutulan parolalar ve ek işlevler için destek içerir.

![](./media/image7-3.png)

Şekil 7-3 tek tek kullanıcı önceden yapılandırılmış bir kimliğe sahip hesapları.

Kimlik desteği hem Createservicereplicalisteners() ve yapılandırma başlangıç yapılandırılır:

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

UseIdentity yapılandırma yöntemi önce UseMvc göründüğünü önemlidir. Kimlik Createservicereplicalisteners() yapılandırırken, bir çağrı AddDefaultTokenProviders fark edeceksiniz. Bu web iletişimin güvenliğini sağlamak için kullanılabilir, ancak bunun yerine SMS veya e-posta edebilmeleri kimliğini onaylamak için aracılığıyla kullanıcılara gönderilen istekleri oluşturma sağlayıcıları başvurduğu belirteçleriyle yapılacak bir şey yok sahiptir.

Daha fazla bilgi edinebilirsiniz [iki öğeli kimlik doğrulamayı yapılandırma](/aspnet/core/security/authentication/2fa) ve [dış oturum açma sağlayıcılarını etkinleştirme](/aspnet/core/security/authentication/social/) resmi ASP.NET Core belgeleri öğesinden.

### <a name="authorization"></a>Yetkilendirme

Anonim kullanıcılar için erişimi kısıtlamak en basit şekliyle yetkilendirme içerir. Bu basitçe uygulayarak gerçekleştirilebilir \[Authorize\] öznitelik belirli denetleyicileri veya eylemler. Rolleri kullanılıyorsa, gösterildiği gibi belirli rollere ait olan kullanıcılar için erişimi kısıtlamak için daha fazla öznitelik Genişletilebilir:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

Bu durumda, kullanıcılar ya da HRManager veya finans rolleri (veya her ikisi de) ait SalaryController erişimi gerekir. Bir kullanıcı birden çok rol için (yalnızca birkaçını) ait zorunlu kılmak için gerekli bir rol her durumda belirtilmesinden öznitelik birden çok kez uygulayabilirsiniz.

Birçok farklı denetleyicileri ve eylemleri dizeleri için istenmeyen yineleme neden olabileceğinden bazı roller kümesi belirtme. Yetkilendirme kuralları yalıtma, yetkilendirme ilkelerini yapılandırabilir ve ardından ilkeyi ayrı roller yerine uygularken belirtin \[Authorize\] özniteliği:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

İlkeleri bu şekilde kullanılması, tür Eylemler belirli roller ya da ona uygulanacak kuralları kısıtlı ayırabilirsiniz. Belirli kaynaklara erişmesi gereken yeni bir rol oluşturursanız, daha sonra yalnızca üzerinde her rollerin listesini güncelleştirmek yerine bir ilke güncelleştirebilirsiniz her \[Authorize\] özniteliği.

#### <a name="claims"></a>Talep

Talep Kimliği doğrulanmış bir kullanıcının özelliklerini temsil eden ad değer çiftleridir. Örneğin, kullanıcıların çalışan numarası bir talep depolayabilir. Talep Yetkilendirme İlkeleri bir parçası olarak kullanılabilir. "EmployeeOnly" adlı bir ilke oluşturabilirsiniz. Bu örnekte gösterildiği gibi "EmployeeNumber" adlı bir talep varlığını gerektirir:

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

Bu ilke ile ardından kullanılabilir \[Authorize\] herhangi bir denetleyici ve/veya eylem, yukarıda açıklanan şekilde korumak için özniteliği.

#### <a name="securing-web-apis"></a>Web API güvenliğini sağlama

Çoğu web API'leri, bir belirteç tabanlı kimlik doğrulama sisteminde uygulamalıdır. Belirteç kimlik doğrulaması, durum bilgisiz ve ölçeklenebilir şekilde tasarlanmıştır. Bir belirteç tabanlı kimlik doğrulama sisteminde, istemci öncelikle kimlik doğrulama sağlayıcısının doğrulaması gerekir. Başarılı olursa, istemci yalnızca şifreleme açısından anlamlı bir dize karakter olan bir belirteç verilir. İstemci ardından API'ye bir isteği yayımlamanız gerektiğinde bu belirteci bir istek başlığında olarak ekler. Sunucu, ardından isteğini tamamlamadan önce istek üstbilgisinde bulunan belirteci doğrular. Şekil 7-4'te, bu işlemi gösterir.

![TokenAuth](./media/image7-4.png)

**Şekil 7-4.** Belirteç tabanlı kimlik doğrulaması için Web API'leri.

> ### <a name="references--security"></a>Başvurular: güvenlik
>
> - **Güvenlik belgeleri genel bakış**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **ASP.NET Core uygulaması olarak SSL'yi zorunlu tutma**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Kimliğe giriş**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Yetkilendirme giriş**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Kimlik doğrulama ve yetkilendirme için Azure App Service'te API Apps**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>İstemci iletişimi

ASP.NET Core uygulamaları, sayfalarını sunmadan ve web API'leri aracılığıyla veri isteklerine yanıt ek olarak, bağlı istemciler ile doğrudan iletişim kurabilir. Bu giden iletişim birçok farklı aktarım teknoloji, en yaygın durdurulmasını WebSockets kullanabilirsiniz. ASP.NET Core SignalR, uygulamalarınıza gerçek zamanlı sunucusu istemci iletişim işlevselliği eklemek basit yapan bir kitaplıktır. SignalR değişik WebSockets, aktarım teknolojilerini destekler ve uygulama Ayrıntıları ' geliştiriciden biri koyma çok soyutlar.

ASP.NET Core SignalR ile ASP.NET Core 2.1 kullanılabilir.

Gerçek zamanlı istemci iletişimi WebSockets doğrudan ya da diğer teknikleri kullanarak olup olmadığını uygulama senaryoları çeşitli yararlıdır. Bazı örnekler:

- Canlı sohbet odası uygulamalar

- Uygulamaları izleme

- İş ilerleme güncelleştirmeleri

- Bildirimler

- Etkileşimli forms uygulamaları

İstemci iletişimi uygulamalarınızla oluştururken da genellikle iki bileşeni vardır:

- Sunucu tarafı Bağlantı Yöneticisi (SignalR hub'ı, WebSocketManager WebSocketHandler)

- İstemci tarafı kitaplık

İstemciler tarayıcılar – mobil uygulamaları, konsol uygulamaları, sınırlı değildir ve diğer yerel uygulamalar ayrıca SignalR/WebSockets kullanarak iletişim kurabilir. Aşağıdaki basit programı konsola sohbet uygulaması WebSocketManager örnek bir uygulama bir parçası olarak gönderilen tüm içeriği yankılayan:

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
}
```

Hangi uygulamalarınızın istemci uygulamaları ile doğrudan iletişim kurmak ve gerçek zamanlı iletişim uygulamanızın kullanıcı artardı olup olmadığını göz önünde bulundurun yolları deneyimi göz önünde bulundurun.

> ### <a name="references--client-communication"></a>Başvuruları – istemci iletişimi
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/aspnet/SignalR>
> - **WebSocket Yöneticisi**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Etki alanı Odaklı Tasarım – uygulanmalı?

Etki alanı Odaklı Tasarım (DDD) üzerinde odaklanarak vurgular yazılım oluşturmaya yönelik Çevik bir yaklaşım olan _iş etki alanı_. Bir iletişim ve geliştiriciler için gerçek sisteminin nasıl çalıştığı ilişkilendirebilirsiniz iş etki alanı expert(s) etkileşim ağır vurguyu yerleştirir. Örneğin, mal stoku işleyen bir sistem oluşturuyorsanız, etki alanı uzmanı deneyimli bir stok Aracısı olabilir. DDD büyük ve karmaşık iş sorunlarını çözmek için tasarlanmıştır ve anlaşılması ve etki alanı modelleme yatırım etkiliyorsa olmadığından daha küçük, daha basit uygulamalar için uygun değildir.

DDD yaklaşımı izleyerek yazılım oluştururken, takımınızın (teknik olmayan proje katılımcıları ve katkıda bulunanlar dahil) geliştirmelisiniz bir _bulunabilen dil_ sorun alanı için. Diğer bir deyişle, aynı terminoloji modellenmiş gerçek kavramı, yazılım eşdeğer ve (örneğin, veritabanı tablolarını) kavramı kalıcı hale getirmek için mevcut olabilecek tüm yapıları için kullanılmalıdır. Bu nedenle, bulunabilen dilde açıklanan kavramları temelini, _etki alanı modeli_.

Etki alanı modeliniz sistem davranışını temsil etmek için birbiriyle etkileşim kuran nesneleri içerir. Bu nesneler, aşağıdaki kategorilere ayrılır:

- [Varlıkları](https://deviq.com/entity/), bir iş parçacığı kimliğini nesneleriyle temsil eder. Varlıklar, tipik olarak, bunlar daha sonra alınabilmesi için bir anahtar ile kalıcı depolanır.

- [Toplamlar](https://deviq.com/aggregate-pattern/), bir birim olarak kalıcı nesne gruplarını temsil eder.

- [Değer nesneleri](https://deviq.com/value-object/), özellik değerlerine toplamını göndermemeniz karşılaştırılabilir kavramlar temsil eder. Örneğin, bir başlangıç ve bitiş tarihi oluşan DateRange.

- [Etki alanı olayları](https://martinfowler.com/eaaDev/DomainEvent.html), sistemin diğer bölümlerini ilgi içerisinde'olmuyor öğeleri temsil eder.

DDD etki alanı modeli model içindeki karmaşık davranış kapsülleyen unutmayın. Varlıklar, özellikle, yalnızca özellik koleksiyonları olmamalıdır. Etki alanı modeli davranışı azaltır ve yalnızca sistem durumunu temsil eder, bu olduğu söylenir bir [anemic modeli](https://deviq.com/anemic-model/), DDD istenmeyen olduğu.

Bu model türlerinin yanı sıra DDD desenlerini çeşitli genellikle kullanır:

- [Depo](https://deviq.com/repository-pattern/), Kalıcılık ayrıntılarını özetleyen için.

- [Fabrika](https://en.wikipedia.org/wiki/Factory_method_pattern), karmaşık nesne oluşturma kapsüllemek için.

- Ayırma davranışını tetiklemesini gelen bağımlı davranış için etki alanı olayları.

- [Hizmetleri](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), kapsayan karmaşık davranış ve/veya altyapı uygulama ayrıntıları.

- [Komut](https://en.wikipedia.org/wiki/Command_pattern), ayırma için verme komutları ve komut yürütülüyor.

- [Belirtimi](https://deviq.com/specification-pattern/), sorgu ayrıntılarını kapsüllemek için.

DDD gevşek bağ modelini, kapsülleme ve birim testlerini kullanma kolayca doğrulanabilir kod izin vererek temiz, daha önce açıklanan mimarisi kullanımını da önerir.

### <a name="when-should-you-apply-ddd"></a>DDD uyguladığınızda

DDD (yalnızca teknik) önemli iş karmaşıklığını ile büyük uygulamalar için çok uygundur. Uygulama etki alanı uzmanları bilgisi istemeniz gerekir. İş kuralları ve yalnızca depolama ve veri depolarından çeşitli kayıtlarının geçerli durumu alınırken ötesinde etkileşimleri temsil eden etki alanı modeli kendisini önemli davranışı olmalıdır.

### <a name="when-shouldnt-you-apply-ddd"></a>DDD uyguladığınızda olmaması gerekir

Modelleme mimarisi ve daha küçük uygulamalar veya aslında yalnızca CRUD (oluşturma/okuma/güncelleştirme/silme) olan uygulamalar için belirtir değil iletişim Yatırımlar DDD içerir. Uygulamanızı DDD aşağıdaki yaklaşımı, ancak etki alanınızın hiçbir davranış anemic bir model olduğunu bulmak tercih ederseniz yaklaşımınızı gözden geçirmeye itiyor gerekebilir. Uygulamanızı DDD gerekmeyebilir veya etki alanı modeli yerine, veritabanı veya kullanıcı arabirimi iş mantığı kapsülleyen uygulamanızı yeniden düzenleme yardıma ihtiyacınız.

Karma bir yaklaşım DDD, uygulamanın işlem ya da daha karmaşık alanları için ancak daha basit CRUD veya salt okunur bölümleri uygulamanın yalnızca kullanmak olabilir. Örneğin, bir raporu görüntülemek için veya bir Pano için verileri görselleştirmek üzere verileri sorguluyorsanız kısıtlamaları dahilinde bir toplama sahip yüklenebileceğinden. Ayrı, daha basit bir okuma modeli için bu gereksinimleri sağlamak için mükemmel bir şekilde kullanılabilir.

> ### <a name="references--domain-driven-design"></a>Başvuruları – etki alanı Odaklı Tasarım
>
> - **DDD düz İngilizce (StackOverflow yanıt)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Dağıtım

Nerede barındırılacağını bağımsız olarak ASP.NET Core uygulamanızı dağıtma sürecinde kullanılan birkaç adım vardır. Yapılabilir uygulamayı yayımlamak için ilk adımıdır kullanarak dotnet CLI komutunu yayımlayın. Uygulamayı derlemek ve tüm dosyaları belirtilen klasöre uygulamasını çalıştırmak için gerekli yerleştirin. Visual Studio'dan dağıttığınızda, bu adım, otomatik olarak gerçekleştirilir. Yayımlama klasörü .exe ve .dll dosyaları için uygulama ve onun bağımlılıklarını içerir. Kendi içinde bir uygulama .NET çalışma zamanının bir sürümünü de içerir. ASP.NET Core uygulamaları yapılandırma dosyalarını, statik istemciyi varlıklar ve MVC görünümleri de içerir.

ASP.NET Core, sunucunun önyüklenir ve uygulama (veya sunucu) kilitlenmesi durumunda yeniden başlatılması gerekir konsol uygulamaları uygulamalardır. Bir işlem yöneticisi, bu işlemi otomatikleştirmek için kullanılabilir. ASP.NET Core için en yaygın işlem yöneticileri Ngınx ve Linux ve IIS Apache veya Windows üzerinde Windows hizmeti ' dir.

Bir işlem yöneticisi yanı sıra Kestrel web sunucusunda barındırılan ASP.NET Core uygulamaları ters Ara sunucu kullanmanız gerekir. Ters Ara sunucu, internet'ten HTTP isteklerini alır ve bunları Kestrel için bazı ön işleme sonra iletir. Ters proxy sunucuları, uygulama için bir güvenlik katmanı sağlar ve edge dağıtımları (trafiği Internet'ten kullanıma sunulur) için gereklidir. Kestrel'i nispeten yeni ve henüz belirli saldırılara karşı savunma sunmaz. Kestrel'i aynı zamanda barındırma üstbilgileri tekniklerle birlikte aynı bağlantı noktası ve IP adresi üzerinde birden çok uygulama barındırmayı etkinleştirmek için kullanılamaz aynı bağlantı noktasında birden çok uygulama barındırma desteklemiyor.

![İnternet'e kestrel](./media/image7-5.png)

Şekil 7-5 Kestrel içinde bir ters proxy sunucusu arkasında barındırılan ASP.NET

Başka bir senaryo ters Ara sunucu yararlı olabilir, SSL/HTTPS kullanarak birden çok uygulama güvenliğini sağlamaktır. Bu durumda, yalnızca ters proxy SSL yapılandırılmış olması gerekir. Kestrel ve ters Ara sunucu arasındaki iletişimi Şekil 7-6'da gösterildiği gibi HTTP üzerinden yer alabilir.

![](./media/image7-6.png)

Şekil 7-6 bir HTTPS güvenlikli ters proxy sunucusunun barındırılan ASP.NET

Ardından yerel olarak barındırılan veya Azure'da barındırmak için bulut tabanlı dağıtılan bir Docker kapsayıcısında ASP.NET Core uygulamanızı barındırmak için giderek popüler yaklaşım. Docker kapsayıcısı Kestrel üzerinde çalışan uygulama kodunuzun içerebilir ve yukarıda da gösterildiği gibi bir ters proxy sunucunun arkasındaki dağıtılması.

Uygulamanız Azure üzerinde barındırıyorsanız, adanmış bir sanal gereç Microsoft Azure Application Gateway çeşitli hizmetleri sağlamak için kullanabilirsiniz. Tek tek uygulamalar için ters proxy gibi davranan ek olarak, Application Gateway ayrıca aşağıdaki özellikleri sunmaktadır:

- HTTP Yük Dengeleme

- SSL yük boşaltma (yalnızca Internet için SSL)

- Uçtan uca SSL

- Çok siteli yönlendirme (en fazla 20 siteleri tek bir uygulama ağ geçidinde birleştirmek)

- Web uygulaması güvenlik duvarı

- Websocket desteği

- Gelişmiş tanılama

_Azure dağıtım seçenekleri hakkında daha fazla bilgi [Bölüm 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Başvuru – dağıtım
>
> - **Barındırma ve dağıtımına genel bakış**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Ne zaman Kestrel ters Ara sunucu ile kullanılır.**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Docker içinde ASP.NET Core uygulamaları barındırın**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Azure uygulama ağ geçidi ile tanışın**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Önceki](common-client-side-web-technologies.md)
>[İleri](work-with-data-in-asp-net-core-apps.md)