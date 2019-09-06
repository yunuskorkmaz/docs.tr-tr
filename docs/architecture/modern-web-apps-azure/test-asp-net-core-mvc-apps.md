---
title: MVC uygulamalarını test ASP.NET Core
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın MVC uygulamalarını test ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 4e4ab71cc542767460e92be1510ccc5c5e0e7ce0
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374078"
---
# <a name="test-aspnet-core-mvc-apps"></a>MVC uygulamalarını test ASP.NET Core

> *"Ürününüzün birim testini beğenmezseniz, büyük olasılıkla müşterileriniz test etmek zorunda kalmaz."*
 > \_Deðeri

Herhangi bir karmaşıklığın yazılımı, değişikliklere yanıt olarak beklenmedik yollarla başarısız olabilir. Bu nedenle, en önemsiz (veya en az kritik) uygulamalar için değişiklik yaptıktan sonra test edilmesi gerekir. El ile test etme, yazılımın test edilmesine yönelik en yavaş ve en ucuz yoldur. Ne yazık ki, uygulamalar test edilebilir olacak şekilde tasarlanmamışsa, kullanılabilir tek yol olabilir. [Bölüm 4](architectural-principles.md) ' te bulunan mimari ilkeleri takip eden bir şekilde yazılan uygulamalar Unit test edilmelidir ve ASP.NET Core uygulamalar otomatik tümleştirme ve işlevsel testi de destekler.

## <a name="kinds-of-automated-tests"></a>Otomatikleştirilmiş test türleri

Yazılım uygulamaları için birçok tür otomatikleştirilmiş test vardır. En basit, en düşük düzey test birim sınamadır. Daha yüksek bir düzeyde, tümleştirme testleri ve işlevsel testler vardır. UI testleri, yük testleri, stres testleri ve duman testleri gibi diğer test türleri, bu belgenin kapsamı dışındadır.

### <a name="unit-tests"></a>Birim testleri

Birim testi, uygulamanızın mantığının tek bir kısmını sınar. Bu, olmadığı bazı şeyleri listeleyerek daha ayrıntılı bir şekilde açıklayabilir. Birim testi, kodunuzun bağımlılıklarla veya altyapıyla nasıl çalıştığını test etmez. Bu, tümleştirme sınamalarıdır. Bir birim testi, kodunuzun yazıldığı çerçeveyi test etmez; Bunun çalıştığını varsaymalı veya buldıysanız, bir hata dosyaz ve bir geçici çözüm kodlayın. Birim testi tamamen bellekte ve işlemde çalışır. Dosya sistemi, ağ veya veritabanıyla iletişim kurmaz. Birim testleri yalnızca kodunuzu test etmelidir.

Birim testleri, dış bağımlılıklar olmadan yalnızca kodunuzun tek bir birimini test ettikleri ve çok hızlı bir şekilde yürütülmesi gerekir. Bu nedenle, birkaç saniye içinde yüzlerce birim testinin test paketlerini çalıştırabilmelisiniz. Her bir paylaşılan kaynak denetimi deposuna her gönderim yapmadan önce ve yapı sunucunuzdaki her bir otomatik derleme ile, bunları sık sık çalıştırın.

### <a name="integration-tests"></a>Tümleştirme testleri

Veritabanları ve dosya sistemleri gibi altyapıyla etkileşim kuran kodunuzu kapsüllemek iyi bir fikir olsa da, bu kodun bir kısmını yine de test etmek isteyeceksiniz. Ayrıca, uygulamanızın bağımlılıkları tamamen çözümlendiğinde kodunuzun katmanlarınızın bekledikleri gibi etkileşimde bulunduğunu doğrulamanız gerekir. Bu, tümleştirme testlerinin sorumluluğundadır. Genellikle dış bağımlılıklara ve altyapıya bağlı olduklarından, tümleştirme testlerinin daha yavaş ve birim testlerinin ayarlanmasından daha zor olma eğilimindedir. Bu nedenle, tümleştirme testlerinde birim testleriyle test edilmiş şeyleri test etmeyi önönüne almalısınız. Belirli bir senaryoyu birim testi ile test edebilirsiniz, onu bir birim testiyle test etmelisiniz. Bu durumda, bir tümleştirme testi kullanmayı göz önünde bulundurun.

Tümleştirme testlerinde genellikle birim testlerinden daha karmaşık kurulum ve Teari yordamları olur. Örneğin, gerçek bir veritabanına yönelik bir tümleştirme testi, her test çalıştırılmadan önce veritabanını bilinen bir duruma döndürmek için bir yönteme ihtiyaç duyar. Yeni testler eklendikçe ve üretim veritabanı şeması geliştikçe, bu test betikleri boyut ve karmaşıklık bakımından büyümeye eğilimindedir. Birçok büyük sistemde, paylaşılan kaynak denetimi değişikliklerini iade etmeden önce, geliştirici iş istasyonlarında tümleştirme testlerinin tam paketlerinin çalıştırılabilmesi pratik değildir. Bu durumlarda, tümleştirme testleri bir yapı sunucusu üzerinde çalıştırılabilir.

### <a name="functional-tests"></a>İşlevsel testler

Tümleştirme testleri, sistemin bazı bileşenlerinin birlikte düzgün çalıştığını doğrulamak için, geliştiricinin perspektifinden yazılır. İşlevsel testler kullanıcının perspektifinden yazılır ve gereksinimlerine göre sistemin doğruluğunu doğrular. Aşağıdaki alıntıda, birim testlerine kıyasla işlevsel testlerin nasıl düşündüğleriyle ilgili yararlı bir benzerleme vurguladı sunulmaktadır:

> "Bir sistemin geliştirilmesi birçok kez bir evin oluşturulmasına sahiptir. Bu benzerleme vurguladı oldukça doğru olmasa da, birim ve işlev testleri arasındaki farkı anlamak amacıyla onu genişletebiliriz. Birim testi, evin yapım sitesini ziyaret eden bir yapı denetçisine benzerdir. BT, temel, çerçevelendirme, elektrik, sıhhi tesisat gibi çeşitli iç sistemlere odaklanılmıştır. Evin bölümlerinin doğru ve güvenli şekilde çalışmasını sağlar (testler) ve derleme kodunu karşılayın. Bu senaryodaki işlevsel testler, aynı yapı sitesini ziyaret eden Homeowner 'a benzerdir. İç sistemlerin uygun şekilde davrandığını varsayar, derleme denetçisi görevini gerçekleştiriyor. Homeowner, bu evinizde ne kadar canlı hale görüneceğine odaklanılmıştır. Evin nasıl göründüğü, çeşitli odaların rahat bir boyut olduğu konusunda endişe duymaktadır, evin aile ihtiyaçlarına uyum sağlaması, Windows 'un sabah güneyi yakalamak için iyi bir nokta halinde. Homeowner, evinizde işlevsel testler gerçekleştiriyor. Kullanıcının perspektifi vardır. Yapı denetçisi, evinizde birim testlerini gerçekleştiriyor. Oluşturucunun perspektifi vardır. "

Kaynaktaki [Birim testi ve Işlev testlerine karşı](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

"Geliştirici olarak" geliştirici olarak söyliyoruz, iki şekilde başarısız oldu: bir şeyi yanlış oluşturacağız veya yanlış bir şey oluşturacağız. " Birim testleri, şeyi doğru bir şekilde oluşturduğunuzu güvence altına alarak, işlevsel sınamalar, doğru şeyi oluşturduğunuzdan emin olmanızı sağlamaktır.

İşlevsel testler sistem düzeyinde çalıştığından, bazı Kullanıcı Arabirimi Otomasyonu gerektirebilir. Tümleştirme testlerine benzer şekilde, genellikle bir tür test altyapısıyla da çalışırlar. Bu, birim ve tümleştirme sınamalarından daha yavaş ve daha Brittle sağlar. Sistemin kullanıcıların beklediği şekilde davranmakta olduğundan emin olmanız gerektiği için yalnızca birçok işlevsel teste sahip olmanız gerekir.

### <a name="testing-pyramid"></a>Piramit test ediliyor

Marwler, Şekil 9-1 ' de gösterilen bir örnek olan test piramit hakkında yazdı.

![Piramit test ediliyor](./media/image9-1.png)

**Şekil 9-1**. Piramit test ediliyor

Piramit 'in farklı katmanları ve bunların göreli boyutları, farklı test türlerini ve uygulamanız için kaç tane yazmanız gerektiğini temsil eder. Görebileceğiniz gibi, öneri, daha küçük bir tümleştirme testi katmanı tarafından desteklenen, daha küçük bir işlevsel test katmanı ile desteklenen, büyük miktarda birim testi olan bir temeldir. Her katmanın ideal olması için yalnızca daha düşük bir katmanda yeterince gerçekleştirilemediği testlerin olması gerekir. Belirli bir senaryo için hangi tür teste ihtiyacınız olduğuna karar verirken, testi piramit ' i göz önünde bulundurun.

### <a name="what-to-test"></a>Test edilecek

Otomatikleştirilmiş testler yazma konusunda deneyimli geliştiriciler için sık karşılaşılan bir sorun test edilecek. İyi bir başlangıç noktası, koşullu mantığı test etmek için kullanılır. Bir koşullu ifadeye (If-Else, Switch, vb.) göre değişen davranışlardan herhangi bir yerde, belirli koşullarda doğru davranışı onaylamak için en az birkaç test sunabileceksiniz. Kodunuzun hata koşulları varsa, kod aracılığıyla "mutlu yol" için en az bir test yazmak iyi olur (hata olmadan) ve uygulamanın hata durumunda beklendiği gibi davrandığını doğrulamak için en az bir test (hata olmadan) ve "Sad yol" (hatalar veya tipik sonuçlar içeren) Son olarak, kod kapsamı gibi ölçümlere odaklanmak yerine başarısız olan test işlemleri üzerinde odaklanmayı deneyin. Daha fazla kod kapsamı, genellikle daha küçüktür. Ancak, çok karmaşık ve iş açısından kritik bir yöntemin birkaç testini yazmak genellikle test kod kapsamı ölçümlerini geliştirmek üzere otomatik özellikler için testlerin yazılmasından daha iyi bir zaman kullanmaktır.

## <a name="organizing-test-projects"></a>Test projelerini düzenleme

Test projeleri düzenlenebilir, ancak sizin için en iyi şekilde kullanılabilir. Testleri türe (birim testi, tümleştirme testi) ve test ettikleri öğeleri (projeye göre, ad alanına göre) ayırmak iyi bir fikirdir. Bu ayırmaların tek bir test projesi veya birden çok test projesi içindeki klasörlerden oluşan bir tasarım kararı olup olmadığı. Bir proje en basit, ancak birçok test içeren büyük projeler için veya farklı test kümelerini daha kolay çalıştırmak için, farklı test projelerine sahip olmak isteyebilirsiniz. Birçok ekip test projelerini test ettikleri projeye göre düzenler, ancak bu, birkaç projeden daha fazla projeye sahip olan uygulamalar çok sayıda test projesine neden olabilir, ancak bu, özellikle de her projede ne tür testlerin ne olduğuna göre bunları daha düşük bir şekilde kesebilirsiniz. Bir riskli yaklaşım, test projeleri içindeki her bir proje (ve sınıfı) test edilen bir proje (ve sınıf) belirtmek için bir proje türüne sahip olmalıdır.

Ortak bir yaklaşım, bir ' src ' klasörü altında uygulama projelerini ve uygulamanın test projelerini paralel bir ' test ' klasörü altında düzenlemenize yardımcı olur. Bu kuruluşu kullanışlı buldıysanız, Visual Studio 'da eşleşen çözüm klasörleri oluşturabilirsiniz.

![Çözümünüzde test organizasyonu](./media/image9-2.png)

**Şekil 9-2**. Çözümünüzde test organizasyonu

Tercih ettiğiniz test çerçevesini kullanabilirsiniz. XUnit çerçevesi iyi çalışmaktadır ve tüm ASP.NET Core ve EF Core testlerin yazıldığı şeydir. Şekil 9-3 ' de gösterilen şablonu kullanarak Visual Studio 'da bir xUnit test projesi veya DotNet New xUnit kullanarak CLı ekleyebilirsiniz.

![Visual Studio 'da bir xUnit test projesi ekleme](./media/image9-3.png)

**Şekil 9-3**. Visual Studio 'da bir xUnit test projesi ekleme

### <a name="test-naming"></a>Test adlandırma

Her testin ne yaptığını belirten adlarla, testlerinizi tutarlı bir biçimde adlandırın. İle harika bir yaklaşım, test sınıflarını test ettikleri sınıfa ve yönteme göre adlandırmalıdır. Bu, birçok küçük test sınıfı ile sonuçlanır, ancak her bir testin sorumlu olduğu son derece net hale getirir. Test sınıfı adı, sınanacak sınıfı ve yöntemi belirlemek üzere ayarlandığında, test yöntemi adı test edilen davranışı belirtmek için kullanılabilir. Bu, beklenen davranışı ve bu davranışı gerektiren tüm giriş veya varsayımları içermelidir. Bazı örnek test adları:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Bu yaklaşımın bir çeşitlemesi, her bir test sınıfı adını "olmalıdır" ile sonlandırır ve zaman hali hafifçe değiştirir:

- `CatalogControllerGetImage`Çağırmalıdır`.``ImageServiceWithId`

- `CatalogControllerGetImage`**Günlüğe kaydedilecek**`.``WarningGivenImageMissingException`

Bazı takımlar ikinci adlandırma yaklaşımını daha net, ancak biraz daha ayrıntılı bir şekilde bulur. Herhangi bir durumda, test davranışına Öngörüler sağlayan bir adlandırma kuralı kullanmayı deneyin, böylece bir veya daha fazla testin başarısız olması durumunda, bazı durumlarda kendi adlarından belirgin olur. Bu teklif, test sonuçlarında gördüğünüz zaman hiçbir değer olmadığı için, ControllerTests. test1 gibi testlerin bir şekilde adlandırılmasını önleyin.

Yukarıdaki gibi birçok küçük test sınıfı üreten bir adlandırma kuralını izlerseniz, testlerinizi klasörler ve ad alanları kullanarak daha fazla düzenlemek iyi bir fikirdir. Şekil 9-4, birkaç test projesi içindeki testleri klasöre göre düzenlemek için bir yaklaşımı gösterir.

![Test sınıflarını, sınanmakta olan sınıfa göre klasöre göre düzenleme](./media/image9-4.png)

**Şekil 9-4.** Test sınıflarını, sınanmakta olan sınıfa göre klasöre göre düzenleme.

Kuşkusuz, belirli bir uygulama sınıfının test edilmekte olan çok sayıda yöntemi (ve bu nedenle birçok test sınıfı) varsa, bunları uygulama sınıfına karşılık gelen bir klasöre yerleştirmek mantıklı olabilir. Bu kuruluş, dosyaları başka bir yerde farklı şekilde düzenlemenize göre farklılık gösterebilir. Birçok başka dosya içeren bir klasörde üçten fazla veya dört ilişkili dosya varsa, bunları kendi alt klasörüne taşımak genellikle yararlı olur.

## <a name="unit-testing-aspnet-core-apps"></a>Uygulamalar ASP.NET Core birim testi

İyi tasarlanmış bir ASP.NET Core uygulamasında, karmaşıklık ve iş mantığının çoğu iş varlıklarında ve çeşitli hizmetlerde kapsüllenir. ASP.NET Core MVC uygulamasının kendisi, denetleyiciler, filtreler, viewmodeller ve görünümleriyle, çok az sayıda birim testi gerektirmelidir. Belirli bir eylemin işlevselliğinin çoğu eylem yönteminin dışında kalıyor. Yönlendirmenin doğru şekilde çalışıp çalışmadığını test etme veya küresel hata işleme, birim testi ile etkin bir şekilde yapılamaz. Benzer şekilde, model doğrulama ve kimlik doğrulama ve Yetkilendirme filtreleri dahil olmak üzere herhangi bir filtre de birim test edilemez. Bu davranış kaynakları olmadan, çoğu eylem yöntemi, bunları kullanan denetleyiciden bağımsız olarak test edilebilir hizmetler için çalışmanın toplu olarak küçük olması gerekir.

Bazen kodunuzu birim test etmek için yeniden düzenlemeniz gerekir. Genellikle bu, soyutlamaları tanımlamayı ve doğrudan altyapıya yönelik olarak kodlamak yerine test etmek istediğiniz koddaki soyutlamadan erişmek için bağımlılık ekleme kullanımını içerir. Örneğin, görüntüleri görüntülemek için bu basit eylem yöntemini göz önünde bulundurun:

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Bu yöntemin birim testi, doğrudan bağımlılığı `System.IO.File`tarafından zor hale getirilir ve dosya sisteminden okumak için kullanılır. Beklendiği gibi çalıştığından emin olmak için bu davranışı test edebilirsiniz, ancak bunu gerçek dosyalarla yapmak bir tümleştirme testi olur. Bu yöntemin yolunu birim testi yapamıyoruz. Bu, kısa bir süre içinde bunu nasıl yapacağım hakkında bilgi edineceksiniz.

Dosya sistemi davranışını doğrudan birim testi yapamıyoruz ve yolu sınayamıyoruz, ne test etmek istiyorsunuz? Ayrıca, birim testi yapmak için yeniden düzenleme yapıldıktan sonra, bazı test çalışmalarını ve hata işleme gibi eksik davranışları bulabilirsiniz. Bir dosya bulunamadığında Yöntem ne yapar? Ne yapmalıyım? Bu örnekte, yeniden düzenlenmiş yöntemi şöyle görünür:

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

Günlükçü \_ ve\_ımageservice, her ikisi de bağımlılıklar olarak eklenir. Artık eylem yöntemine geçirilen aynı kimliğin \_ımageservice 'e geçtiğini ve elde edilen baytların FileResult 'nin bir parçası olarak döndürüldüğünü test edebilirsiniz. Ayrıca, hata günlüğü 'nün beklenen şekilde olduğunu ve görüntü eksikse bir NotFound sonucunun döndürüldüğünü, bunun önemli uygulama davranışı olduğunu (yani, bir sorunu tanılamak için geliştiricinin eklediği geçici bir kod değil) kabul edebilirsiniz. Gerçek dosya mantığı ayrı bir uygulama hizmetine taşındı ve eksik bir dosya olması durumunda uygulamaya özel bir özel durum döndürecek şekilde geliştirilmiştir. Bu uygulamayı bir tümleştirme testi kullanarak bağımsız olarak test edebilirsiniz.

Çoğu durumda, denetleyicilerinizde genel özel durum işleyicilerini kullanmak isteyeceksiniz. bu nedenle, içindeki mantık miktarı minimum ve büyük olasılıkla birim testi olmamalıdır. İşlev testlerini ve `TestServer` aşağıda açıklanan sınıfı kullanarak, denetleyici eylemlerinin çoğunu test etmeniz gerekir.

## <a name="integration-testing-aspnet-core-apps"></a>Tümleştirme testi ASP.NET Core uygulamalar

ASP.NET Core uygulamalarınızın çoğu tümleştirme testi, altyapı projenizde tanımlanmış test hizmetleri ve diğer uygulama türleri olmalıdır. Örneğin, EF Core altyapı projesinde bulunan veri erişim sınıflarınızda [beklediğinizi ve verileri başarıyla güncelleştirdiğini test](https://docs.microsoft.com/ef/core/miscellaneous/testing/) edebilirsiniz. ASP.NET Core MVC projenizin doğru şekilde davrandığının en iyi yolu, bir test ana bilgisayarında çalışan uygulamanıza karşı çalıştırılan işlevsel testlerdir.

## <a name="functional-testing-aspnet-core-apps"></a>Uygulamalar ASP.NET Core işlevsel test

ASP.NET Core uygulamalar için, `TestServer` sınıf işlevsel testleri yazma konusunda oldukça kolay hale getirir. Bir `TestServer` `WebApplicationFactory` kullanarak doğrudan (uygulamanız için yaptığınız gibi) veya türü (2,1 sürümünden itibaren kullanılabilir) ile yapılandırabilirsiniz. `WebHostBuilder` Test ana bilgisayarınızı üretim konağınız için mümkün olduğunca yakından eşleştirmeye çalışmalısınız, bu sayede testleriniz, uygulamanın üretimde ne yapacaklarına benzer davranışlar sağlar. `WebApplicationFactory` Sınıf, görünümler gibi statik kaynağı bulmak için ASP.NET Core tarafından kullanılan TestServer 'ın contentroot 'yi yapılandırmaya yardımcı olur.

Web uygulamanızın başlangıç sınıfı olduğu ıssfixture\<webapplicationfactory\<tentry > > uygulayan bir test sınıfı oluşturarak basit işlevsel testler oluşturabilirsiniz. Bu şekilde, test armatürü, fabrika 'nin CreateClient metodunu kullanarak bir istemci oluşturabilir:

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

Genellikle, her bir test çalıştırılmadan önce sitenizin bazı ek yapılandırmalarını gerçekleştirmek isteyeceksiniz; Örneğin, uygulamayı bellek içi veri deposu kullanacak şekilde yapılandırma ve ardından uygulamayı test verileriyle sağlama. Bunu yapmak için, webapplicationfactory\<tentry > kendi alt sınıfını oluşturmanız ve configurewebhost metodunu geçersiz kılmanız gerekir. Aşağıdaki örnek eShopOnWeb FunctionalTests projesinden ve ana Web uygulamasındaki testlerin bir parçası olarak kullanılır.

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web.Controllers
{
    public class CustomWebApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory 
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<CustomWebApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

Testler, bu özel WebApplicationFactory 'yi kullanarak bir istemci oluşturup bu istemci örneğini kullanarak uygulamaya istekler yapmasını sağlar. Uygulamanın, test onaylamaları kapsamında kullanılabilecek verileri, çalıştırılabilir. Aşağıdaki test, eShopOnWeb uygulamasının giriş sayfasının doğru şekilde yüklendiğini doğrular ve tohum verilerinin bir parçası olarak uygulamaya eklenen bir ürün listesini içerir.

```cs
using Microsoft.eShopWeb.FunctionalTests.Web.Controllers;
using Microsoft.eShopWeb.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebApplicationFactory<Startup> factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

Bu fonksiyonel test, bir bütün ara yazılım, filtre, cilt, vb. dahil olmak üzere tam ASP.NET Core MVC/Razor Pages uygulama yığınını uygular. Belirli bir yolun ("/") beklenen başarı durum kodunu ve HTML çıkışını döndürdüğünü doğrular. Bu, gerçek bir Web sunucusu ayarlamadan ve bu sayede, test için gerçek bir Web sunucusu kullanan brittın büyük bölümünü önler (örneğin, Güvenlik Duvarı ayarlarıyla ilgili sorunlar). TestServer 'a karşı çalışan işlevsel testler genellikle tümleştirme ve birim testlerinden daha yavaştır, ancak ağ üzerinden bir test Web sunucusuna çalışacak testlerden çok daha hızlıdır. Uygulamanızın ön uç yığınının beklendiği gibi çalıştığından emin olmak için işlevsel testler kullanmanız gerekir. Bu sınamalar, denetleyicilerde veya sayfalarınızda yineleme bulduğunuzda ve filtreler ekleyerek yinelemeyi adresleyerek özellikle yararlıdır. İdeal olarak, bu yeniden düzenleme uygulamanın davranışını değiştirmez ve işlevsel testlerin bir paketi bu durumun olduğunu doğrular.

> ### <a name="references--test-aspnet-core-mvc-apps"></a>Başvurular – test ASP.NET Core MVC uygulamaları
>
> - **ASP.NET Core 'de test etme**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Birim testi adlandırma kuralı**  
>   <https://ardalis.com/unit-test-naming-convention>
> - **Test EF Core**  
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>

>[!div class="step-by-step"]
>[Önceki](work-with-data-in-asp-net-core-apps.md)İleri
>[](development-process-for-azure.md)
