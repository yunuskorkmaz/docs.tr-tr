---
title: ASP.NET Core MVC test uygulamaları
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | ASP.NET Core MVC uygulamalarını test etme
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: e3edec65fd10b0a7c05d1865703f2e0a591d8b03
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827558"
---
# <a name="test-aspnet-core-mvc-apps"></a>ASP.NET Core MVC test uygulamaları

> *"Birim testi ürününüzü kullanmak istemiyorsanız, büyük olasılıkla müşterileriniz, ya da test etmek gibi olmayacaktır."*
 > \_-Anonim-

Yazılım tüm karmaşıklığı değişikliklere yanıt olarak beklenmedik bir şekilde başarısız olabilir. Bu nedenle, değişiklikleri yaptıktan sonra test için en basit (veya en az önemli) uygulamaları dışındaki tüm alanlar gereklidir. El ile test yavaş, güvenilir az ve en pahalı yöntem yazılım test etmektir. Ne yazık ki, uygulamalar, test edilebilir olması için tasarlanmamış, yalnızca anlamına gelir kullanılabilir olabilir. Yazılan uygulamalar, normal bir kutudur mimari ilkeleri aşağıdaki [bölüm 4](architectural-principles.md) birim test edilebilir ve ASP.NET Core uygulamaları, otomatik tümleştirme ve işlevsel test de destekler.

## <a name="kinds-of-automated-tests"></a>Otomatik test türleri

Yazılım uygulamaları için otomatik testler birçok çeşit vardır. Basit, en düşük düzey test birim testi olur. Biraz daha yüksek bir düzeyde tümleştirme testleri ve işlevsel testleri vardır. Diğer kullanıcı Arabirimi testleri, yük testleri, yük testleri ve Duman testleri gibi testler bu belgenin kapsamı dışındadır türleridir.

### <a name="unit-tests"></a>Birim testleri

Birim testi, uygulamanızın mantıksal tek bir parçası sınar. Bir daha da öyle şeylerden bazıları listeleyerek tanımlayabilirsiniz. Birim test, kodun çalıştığını bağımlılıkları veya hangi tümleştirme testleri olan altyapıya – içindir nasıl test değil. Birim testi test kodunuzu üzerindeki yazılan çerçevesi değil – çalışır veya, bulursanız değil, hata bildirin ve geçici bir çözüm kod varsaymanız gerekir. Birim testi, bellek ve işlem tamamen çalışır. Dosya sistemi, ağ veya veritabanı ile iletişim kurmak değil. Birim testleri yalnızca kodunuzu test etmeniz gerekir.

Dış bağımlılıkları olmayan, kodunuzun yalnızca tek bir birim test etmenizi olgu da birim testleri, son derece hızlı bir şekilde getirmesi gerekir. Bu nedenle, test paketleri, birim testleri yüzlerce birkaç saniye içinde çalıştırabilir olmalıdır. Bunları sık, ideal olarak her anında iletme paylaşılan kaynak denetim deposu ve kesinlikle her bir otomatik yapı önce yapı sunucunuzda çalıştırın.

### <a name="integration-tests"></a>Tümleştirme testleri

Veritabanları ve dosya sistemleri gibi altyapı ile etkileşime giren kodunuzu kapsüllemek için iyi bir fikir olsa da hala bazı kod gerekir ve büyük olasılıkla bunu test etmek istersiniz. Ayrıca, uygulama bağımlılıklarınızın tamamen çözümlendiğinde beklediğiniz gibi kodunuzun katman etkileşim doğrulamanız gerekir. Bu tümleştirme testleri sorumluluğundadır. Tümleştirme testleri, genellikle dış bağımlılıkları ve altyapınıza bağlı olduğundan daha yavaş ve birim testleri ayarlamak daha zor olma eğilimindedir. Bu nedenle, testleri tümleştirme testleri, birim testleriyle olabilir öğeleri test kaçınmanız gerekir. Belirli bir senaryo bir birim testi ile test, birim testi ile test etmeniz gerekir. Çözemezseniz, bir tümleştirme testini kullanmayı deneyin.

Tümleştirme testleri genellikle daha karmaşık kurulum ve kaldırma yordamları birim testlerinden sahip olur. Örneğin, gerçek bir veritabanında giden bir tümleştirme testi veritabanını, her test çalışması önce bilinen bir duruma döndürmek için bir yol gerekir. Yeni testler eklenir ve üretim veritabanı şemasını geliştikçe, bu test betikleri boyutu ve karmaşıklığı büyümesine eğilimli. Birçok büyük sistemde, değişiklikleri paylaşılan kaynak denetimine iade etmeden önce Geliştirici iş istasyonları üzerinde tam paketleri tümleştirme testleri çalıştırmak için zordur. Bu durumlarda, tümleştirme testlerini bir yapı sunucusunda çalışabilir.

LocalFileImageService uygulama sınıfımızın getirmeye ve bir görüntü dosyasının baytlar verilen bir kimlik, belirli bir klasörden döndüren mantığını uygular:

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a>İşlevsel testler

Tümleştirme testleri sisteminin bazı bileşenleri düzgün birlikte çalıştığını doğrulamak için geliştirici perspektifinden yazılır. İşlevsel testleri, kullanıcı perspektifinden yazılır ve kendi gereksinimlerine göre sistem doğruluğunu doğrulayın. Aşağıdaki alıntıda işlevsel testleri, birim testleri karşılaştırıldığında düşünün öğrenmek için kullanışlı bir benzerliği sunar:

> "Bir sistemin geliştirme birden çok kez bir ev oluşturulmasını likened. Bu benzerleme oldukça doğru değildir; ancak biz birim ve işlev testleri arasındaki farkı anlamak amacıyla genişletebilirsiniz. Birim testi house'nın yapı sitesinden bir yapı denetleyici benzerdir. He house, çerçeve, elektrik Sıhhi tesisat ve bu şekilde foundation çeşitli dahili sistemlerinde odaklanmıştır. He (evi bölümlerini düzgün ve güvenli bir şekilde, diğer bir deyişle, yapı kod karşılamak testleri) sağlar. Bu senaryoda işlevsel testleri bu aynı yapı siteyi ziyaret sakininin benzer. He iç sistemleri uygun şekilde davranır, yapı Inspector'ı kendi görevi çalıştığını varsayar. Sakininin ne gibi bu Merkezi'nde Canlı de artar üzerinde odaklanır. He evi nasıl göründüğünü ile ilgilidir, çeşitli rooms rahat boyutu, ev ailesinin gereksinimlerine uygun, sabah sun yakalamak için iyi bir kolayca Windows. Sakininin işlevsel testleri evi gerçekleştiriyor. Kullanıcı açısından sahip. Birim testleri, derleme denetçisi evi gerçekleştiriyor. Oluşturucunun perspektif sahip."

Kaynak: [Birim testi işlevsel testler](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Bildiren, Acıyı istiyorum "geliştiriciler, size iki yolla başarısız: yanlış bir şey ekliyoruz veya yanlış bir şey ekliyoruz." Birim testleri şey sağ oluşturmakta olduğunuz emin olun. işlevsel testler doğru şeyi oluşturmakta olduğunuz emin olun.

Sistem düzeyinde işlevsel testleri çalıştırma olduğundan, bunlar UI Otomasyonu derece gerektirebilir. Tümleştirme testleri gibi bunlar genellikle test altyapısı tür ile çalışır. Bu, bunların daha yavaş ve birim ve tümleştirme testleri daha kırılır sağlar. Yalnızca olmalıdır sistem kullanıcılar beklendiği gibi davrandığından emin olmanız gerekir kadar işlevsel testleri.

### <a name="testing-pyramid"></a>Piramit test etme

Şekil 9-1'de, bir örnek gösterilir, test Piramit hakkında Martin Fowler yazıldı.

![](./media/image9-1.png)

Şekil 9-1 Piramit test etme

Piramit ve bunların göreli boyutlarını farklı katmanlara testleri ve uygulamanız için yazmalısınız kaç farklı türde temsil eder. Gördüğünüz gibi büyük bir temel birim testleri, tümleştirme testleri, daha küçük bir katman işlevsel testlerin bile küçük bir katman ile tarafından desteklenen olması önerilir. Her katman, daha düşük bir katmanda yeterince gerçekleştirilemiyor, ideal olarak testleri yalnızca olmalıdır. Ne tür bir test belirli bir senaryo için gereken karar vermeye çalışırken test Piramit göz önünde bulundurun.

### <a name="what-to-test"></a>Hangi test etmek için

Otomatik testler yazmaya deneyimsiz geliştiriciler için ortak bir sorunu ile test etmek yakında. Koşullu mantık test etmek için iyi bir başlangıç noktası var. Değişiklikler bir koşullu ifadeye göre davranışı yöntemiyle sahip herhangi bir yerde (if-else, geçiş, vb.), en az birkaç yukarı doğru davranışı belirli koşullarda onaylayan testlerini gelen olmalıdır. Hata koşulları kodunuz varsa (hatasız) en az bir test kodu "Mutlu yolu" ve "Üzgün yolu" için en az bir test uygulamanız karşılaşıldığında hataları beklendiği gibi davranır onaylamak için (hataları veya alışılmadık sonuçları ile) yazmak geçerlidir. Son olarak, kod kapsamı gibi ölçümleri odaklanan yerine eklenemeyecek olan şeyleri test odaklanmak deneyin. Daha fazla kod kapsamı, genel olarak küçük, daha iyi olur. Ancak, birkaç daha fazla test çok karmaşık ve iş açısından kritik yönteminin yazma genellikle testleri yalnızca test kod kapsamı ölçümleri geliştirmek otomatik özelliklerde için yazma daha zaman daha iyi bir kullanımı olur.

## <a name="organizing-test-projects"></a>Test projeleri düzenleme

Test projeleri Works sizin için en iyi ancak düzenlenebilir. Test türü (birim testi, tümleştirme testi) ve hangi (proje, ad alanı tarafından) test ettikleri göre ayırmak için iyi bir fikirdir. Bu ayrım tek bir test projesi ya da birden çok test projesini klasörler oluşur olup olmadığını bir tasarım kararıdır. Bir proje basit olmakla birlikte çok sayıda test ya da daha kolay farklı test kümesini çalıştırmak için büyük projeler için birkaç farklı test projeleri bulundurmak isteyebilirsiniz. Birçok takım test projeleri özellikle, yine de bu tür testler her projede nelerdir göre bölmek, fazla sayıda projeleri ile uygulamalar için çok sayıda test projeleri neden olabilir, test, proje göre düzenler. Bir güvenlik ihlali yaklaşım, test, test edilen proje (ve sınıf) belirtmek için test projeleri klasörlerde ile uygulama başına tür başına tek bir proje sahip olmaktır.

'Src' klasörü altındaki uygulama projeleri ve uygulamanın paralel 'test' klasörü altında test projeleri düzenleme yaygın bir yaklaşımdır. Bu kuruluş kullanışlı, Visual Studio eşleşen çözümü klasörler oluşturabilirsiniz.

![](./media/image9-2.png)

Şekil 9-2, çözümünüzdeki Test kuruluş

Tercih ettiğiniz test çerçeveye kullanabilirsiniz. XUnit framework iyi çalışır ve nedir tüm ASP.NET Core ve EF Core testleri yazılır. Şekil 9-3'te veya yeni dotnet xunit kullanarak clı'dan gösterilen şablonu kullanarak Visual Studio'da bir xUnit test projesi ekleyebilirsiniz.

![](./media/image9-3.png)

Şekil 9-3, Visual Studio'da bir xUnit Test projesi Ekle

### <a name="test-naming"></a>Test adlandırma

Her test ne yaptığını gösteren adlarla testlerinizi tutarlı bir biçimde adlandırmalısınız. Harika başarılı bir şekilde sahip bir ad test sınıflarında sınıfı ve test ettikleri yöntemi göre yaklaşımdır. Bu çok sayıda küçük test sınıflarında olur, ancak her test ne sorumlu olduğu son derece Temizle sağlar. Sınıfı ve test edilecek yöntem tanımlamak üzere ayarlanan sahte test sınıfı adıyla test yönteminin adı, test edilen davranışını belirtmek için kullanılabilir. Bu, Beklenen davranış ve giriş veya bu davranışı yield varsayımlar içermelidir. Bazı örnek test adları:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Bu yaklaşımın bir değişim her test sınıfı adı "Gerekir" ile biten ve şimdiki biraz değiştirir:

- `CatalogControllerGetImage`**Gereken**`.`**çağırın**`ImageServiceWithId`

- `CatalogControllerGetImage`**Gereken**`.`**günlüğü**`WarningGivenImageMissingException`

İkinci adlandırma yaklaşım daha net, bazı ekipler bulabilirsiniz ancak biraz daha ayrıntılı. Herhangi bir durumda, bir veya daha fazla test başarısız olduğunda, hangi durumlarda başarısız olmuş adlarını belirgin olması test davranış sağlayan bir adlandırma kuralını kullanmaya çalışın. Bu değer, test sonuçlarında gördüğünüzde sunar gibi testler ControllerTests.Test1 gibi vaguely, adlandırma kaçının.

Birçok küçük test sınıfları, yukarıdaki üretir gibi bir adlandırma kuralını izler, ek klasörleri ve ad alanlarını kullanarak testlerinizi düzenlemek için iyi bir fikirdir. Şekil 9-4 birkaç test projesi içinde klasöre göre testlerin düzenlenmesi için bir yaklaşımı gösterir.

![](./media/image9-4.png)

**Şekil 9-4.** Test edilen sınıfına göre klasöre göre test sınıflarında düzenleme.

Elbette, belirli uygulama sınıfı sınanan birçok yöntem vardır (ve bu nedenle çoğu test sınıflarına değilse), bu uygulama sınıfına karşılık gelen bir klasöre yerleştirmek için mantıklı olabilir. Bu kuruluş nasıl dosyaları başka bir yerde klasörler halinde düzenlediğiniz farklı değildir. En fazla üç varsa veya dört ilgili çok sayıda dosya içeren bir klasördeki dosyaları genellikle bunları kendi alt klasöre taşımak yararlıdır.

## <a name="unit-testing-aspnet-core-apps"></a>Birim testi ASP.NET Core uygulamaları

İyi tasarlanmış bir ASP.NET Core uygulaması birçok karmaşıklığı ve iş mantığı iş varlıklarını ve Hizmetleri çeşitli kapsüllenmiş. ASP.NET Core MVC uygulama içinden denetleyicileri, filtreler, viewmodel'lar ve görünümler ile çok az sayıda birim testleri istemeniz gerekir. Belirli bir eylemi işlevselliğinin bir eylem yönteminin kendisi dışında arasındadır. Etkin bir birim testini yönlendirme düzgün çalışıp çalışmadığını test edilmesi veya genel hata işleme yapılamaz. Benzer şekilde, tüm model doğrulama ve kimlik doğrulama dahil olmak üzere, filtreleri ve yetkilendirme filtrelerini olamaz birim test. Bu davranışı kaynakları olmadan çoğu eylem yöntemleri bunları kullanan denetleyicinin bağımsız test edilebilir hizmetlere çalışmalarının toplu temsilci olarak görevlendirme basit bir şekilde küçük olmalıdır.

Bazen, birim testi için kodunuzda sipariş yeniden düzenlenmesi gerekir. Bu sık soyutlama tanımlama ve test etmek istediğiniz kod soyutlama erişmek için bağımlılık ekleme kullanılarak yerine doğrudan karşı altyapı kodları yazmasına içerir. Örneğin, resimleri görüntülemek için bu basit bir eylem yöntemine göz önünde bulundurun:

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

Birim testi bu yöntem, dosya sisteminden okumak için kullandığı System.IO.File doğrudan bağımlı tarafından zor olarak yapılır. Bu davranış, beklendiği gibi çalışır, ancak gerçek dosyalarıyla bunu bir tümleştirme testini olduğundan emin olmak için test edebilirsiniz. Birim yapamazsınız hatalarının ayıklanabileceğini belirtmekte yarar bu yöntemin rota test – işlevsel bir testi ile kısa bir süre sonra bunun nasıl yapılacağını görürsünüz.

Birim testi dosya sistemi davranışını doğrudan olamaz ve rota test edilemez, var. test etmek için nedir? De birim testi mümkün hale getirmek için yeniden düzenleme sonra bazı test çalışmaları ve hata işleme gibi eksik bir davranışı fark edebilirsiniz. Bir dosya bulunamadığında, yöntem ne yapar? Neler? Bu örnekte, işlenmiş yöntemi şöyle görünür:

```csharp
[HttpGet("[controller]/pic/{id}")\]
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

\_Günlükçü ve \_Imageservice hem de eklenmiş bağımlılıkları. Eylem yöntemine geçirilen aynı kimliği geçirilecek test artık \_Imageservice, ve sonuçta elde edilen bayt FileResult bir parçası olarak döndürülür. Ayrıca hata günlüğünü beklendiği gibi oluyor ve görüntü yoksa bir NotFound sonuç döndürülür bu önemli uygulamanın davranış (diğer bir deyişle, yalnızca geçici kodu bir sorunu tanılamak için eklenen Geliştirici) olduğunu varsayarak test edebilirsiniz. Gerçek dosya mantığı ayrı uygulama hizmetinde taşınmıştır ve bir uygulamaya özgü özel eksik dosya durumu için döndürülecek büyütülmüştür. Bir tümleştirme testini kullanarak bu uygulama bağımsız olarak, test edebilirsiniz.

Çoğu durumda, mantık miktarını en düşük bu nedenle denetleyicilerinizi ve büyük olasılıkla birim testi değer genel özel durum işleyicilerini kullanmak isteyebilirsiniz. Denetleyici eylemleri işlevsel testler kullanarak test çoğu yapmanız gerekir ve `TestServer` aşağıda açıklanan sınıfı.

## <a name="integration-testing-aspnet-core-apps"></a>Tümleştirme testi ASP.NET Core uygulamaları

ASP.NET Core uygulamalarınızı tümleştirme testleri çoğunu, hizmetler ve altyapı projenizde tanımlanan diğer uygulama türleri test. ASP.NET Core MVC projenize doğru mu davrandığı, test etmek için en iyi bir test ana bilgisayarı çalışan uygulamanızı çalıştırmanızı işlevsel testleri yoludur. Bu bölümde daha önce tümleştirme testi bölümündeki bir tümleştirme testini bir veri erişim sınıfın bir örneği gösterilmektedir.

## <a name="functional-testing-aspnet-core-apps"></a>İşlevsel test ASP.NET Core uygulamaları

ASP.NET Core uygulamaları için `TestServer` sınıfı işlevsel testleri yazmak oldukça kolay kılar. Yapılandırdığınız bir `TestServer` kullanarak bir `WebHostBuilder` doğrudan (normalde, uygulamanız için yaptığınız gibi), veya `WebApplicationFactory` türü (2.1 sürümünden itibaren kullanılabilir). Testlerinizi uygulamayı üretim ortamında neler yapabileceği için benzer bir davranış alıştırma şekilde, test ana bilgisayarı, üretim barındırmak için mümkün olduğunca yakın bir şekilde eşleşecek şekilde denemelisiniz. `WebApplicationFactory` Sınıfı ile ASP.NET Core görünümleri gibi statik kaynak bulmak için kullanılan TestServer'ın ContentRoot yapılandırmak için yararlıdır.

Basit işlevsel testler IClassFixture uygulayan bir test sınıfı oluşturarak oluşturabileceğiniz\<WebApplicationFactory\<TEntry >> TEntry, web uygulamanızın başlangıç sınıfı olduğu. Bu yerinde fabrikasının CreateClient yöntemini kullanarak bir istemci, test düzeni oluşturabilirsiniz:

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

Genellikle, bir bellek içi kullanmak için uygulamayı yapılandırma gibi her bir testi çalıştırmadan önce bazı ek yapılandırmalar sitenizin gerçekleştirmek isteyebilirsiniz veri deposuna ve daha sonra uygulama test verileri ile dengeli dağıtım. Bunu yapmak için kendi alt WebApplicationFactory oluşturmalısınız<TEntry> ve kendi ConfigureWebHost yöntemi yok sayın. Aşağıdaki örnekte eShopOnWeb FunctionalTests projeden ve testleri ana web uygulamasında bir parçası olarak kullanılır.

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

Testler bu özel WebApplicationFactory, bunu bir istemci oluşturmak için kullanarak ve ardından bu istemci örneği kullanarak uygulamaya istekleri yapabilen yararlanabilirsiniz. Uygulama, onaylamalar testin bir parçası olarak kullanılan çekirdek değeri oluşturulmuş veri sahip olur. Şu test doğrular: eShopOnWeb uygulama ana sayfası düzgün şekilde yüklenir ve çekirdek veri parçası olarak uygulamaya eklenen ürün listesini içerir.

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

Bu işlevsel test tam ASP.NET Core MVC sınayan / Razor sayfaları, tüm ara yazılım, filtreler, bağlayıcıları, yerinde olabilir vb. dahil olmak üzere uygulama yığını. Belirli bir yol ("/") beklenen başarılı durum kodu ve HTML çıktı döndürür doğrular. Gerçek bir web sunucusu ayarını olmadan bunu yapar ve bu nedenle, gerçek bir Web sunucusu test etmek için (örneğin, güvenlik duvarı ayarları ile ilgili sorunlar) oluşabilir brittleness çoğunu ortadan kaldırır. TestServer karşı çalışan işlevsel testleri genellikle tümleştirme ve birim testleri yavaş ancak ağ üzerinden bir test web sunucusuna çalıştıracağınız testleri hızlıdır. İşlevsel testleri, uygulamanızın ön uç yığın beklendiği gibi çalıştığından emin olmak için kullanmanız gerekir. Bu testler, sayfalar ve filtreler ekleyerek çoğaltma adres ya da çoğaltma denetleyicilerinizi içinde bulmak özellikle yararlı olur. İdeal olarak, bu yeniden düzenleme, uygulama davranışını değiştirmez ve işlevsel testleri paketi bu durumda doğrulayın.

>[!div class="step-by-step"]
>[Önceki](work-with-data-in-asp-net-core-apps.md)
>[İleri](development-process-for-azure.md)
