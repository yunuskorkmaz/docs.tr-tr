---
title: Core MVC uygulamalarını test ASP.NET
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | Test ASP.NET Çekirdek MVC Uygulamaları
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: fa87fdba830398786cce8951d353e86bc4ff7491
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111055"
---
# <a name="test-aspnet-core-mvc-apps"></a>Core MVC uygulamalarını test ASP.NET

> *"Ürününüzü birim olarak test etmek istemiyorsanız, büyük olasılıkla müşterileriniz de bunu test etmek hoşlanmaz."*
 > \_- Anonim-

Herhangi bir karmaşıklık yazılım değişikliklere yanıt olarak beklenmedik şekillerde başarısız olabilir. Bu nedenle, değişiklik yaptıktan sonra test etmek, en önemsiz (veya en az kritik) uygulamalar hariç herkes için gereklidir. El ile sınama, yazılımı test etmek için en yavaş, en az güvenilir, en pahalı yoludur. Ne yazık ki, uygulamalar test edilebilir olacak şekilde tasarlanmıyorsa, kullanılabilir tek araç bu olabilir. [4. bölümde](architectural-principles.md) belirtilen mimari ilkelere uygun olarak yazılan başvurular ünite test edilebilir olmalıdır. ASP.NET Core uygulamaları otomatik tümleştirme ve işlevsel testleri destekler.

## <a name="kinds-of-automated-tests"></a>Otomatik test türleri

Yazılım uygulamaları için birçok türde otomatik test vardır. En basit, en düşük seviye testi birim testidir. Biraz daha yüksek bir düzeyde, entegrasyon testleri ve fonksiyonel testler vardır. UI testleri, yükleme testleri, stres testleri ve duman testleri gibi diğer test türleri bu belgenin kapsamı dışındadır.

### <a name="unit-tests"></a>Birim testleri

Birim testi, uygulamanızın mantığının tek bir parçasını sınar. Bir daha bazı şeyler değil listeleyerek açıklayabilir. Birim testi, kodunuzu bağımlılıklarla veya altyapıyla nasıl çalıştığını test etmez , bu tümleştirme testlerinin ne işe yaradığını belirtir. Birim testi, kodunuzu yazdığınızdaki çerçeveyi sınamaz – çalıştığını varsaymalısınız veya işe yaramazsa hata dosyalayın ve geçici bir çözüm kodlayın. Bir birim testi tamamen bellekte ve işlemde çalışır. Dosya sistemi, ağ veya veritabanı ile iletişim kurmaz. Birim testleri yalnızca kodunuzu test etmelidir.

Birim testleri, kodunuzu yalnızca tek bir birim test gerçeği nedeniyle, hiçbir dış bağımlılıkları ile, son derece hızlı bir şekilde yürütülmelidir. Böylece, birkaç saniye içinde birim testleri yüzlerce test paketleri çalıştırmak gerekir. Bunları sık sık, ideal olarak paylaşılan bir kaynak denetim deposuna her itmeden önce ve kesinlikle yapı sunucunuzdaki her otomatik yapıyla çalıştırın.

### <a name="integration-tests"></a>Tümleştirme testleri

Veritabanları ve dosya sistemleri gibi altyapıyla etkileşimde bulunarak kodunuzu kapsüllemek iyi bir fikir olsa da, bu kodun bir kısmına sahip olmaya devam edecektir ve büyük olasılıkla bunu sınamak isteyeceksiniz. Ayrıca, uygulamanızın bağımlılıkları tam olarak çözüldüğünde kodlarınızın katmanlarının beklediğiniz şekilde etkileşimde olduğunu doğrulamanız gerekir. Bu entegrasyon testlerinin sorumluluğundadır. Tümleştirme testleri genellikle dış bağımlılıklara ve altyapıya bağlı olduğundan, birim testlerinden daha yavaş ve kurulumu daha zor olma eğilimindedir. Bu nedenle, tümleştirme testlerinde birim testleri ile test edilebilir şeyleri test kaçınmalısınız. Belirli bir senaryoyu bir birim testi ile sınayabilirseniz, bunu bir birim testi ile test edebilirsiniz. Eğer yapamazsanız, o zaman bir tümleştirme testi kullanmayı düşünün.

Tümleştirme testleri genellikle birim testlerinden daha karmaşık kurulum ve yıkma yordamlarına sahip olur. Örneğin, gerçek bir veritabanına karşı olan bir tümleştirme sınaması, veritabanını her test çalıştırmadan önce bilinen bir duruma döndürmenin bir yolunu niçin gerekir. Yeni testler eklendikçe ve üretim veritabanı şeması geliştikçe, bu test komut dosyaları boyut ve karmaşıklık olarak büyüme eğiliminde olacaktır. Birçok büyük sistemde, paylaşılan kaynak denetimindeki değişiklikleri denetlemeden önce geliştirici iş istasyonlarında tam tümleştirme testleri çalıştırmak pratik değildir. Bu gibi durumlarda, tümleştirme testleri bir yapı sunucusunda çalıştırılabilir.

### <a name="functional-tests"></a>Fonksiyonel testler

Tümleştirme testleri, sistemin bazı bileşenlerinin birlikte doğru çalıştığını doğrulamak için geliştiricinin perspektifinden yazılır. İşlevsel testler kullanıcının bakış açısından yazılır ve gereksinimlerine göre sistemin doğruluğunu doğrular. Aşağıdaki alıntı, birim testleri ile karşılaştırıldığında, fonksiyonel testler hakkında düşünmek için yararlı bir benzetme sunuyor:

> "Birçok kez bir sistemin geliştirilmesi bir evin inşasına benzetilir. Bu benzetme tam olarak doğru olmasa da, ünite ve fonksiyonel testler arasındaki farkı anlamak amacıyla genişletebiliriz. Birim testi, bir binanın şantiyesini ziyaret eden bir yapı denetçisine benzer. O evin çeşitli iç sistemleri üzerinde durulmaktadır, vakıf, çerçeveleme, elektrik, sıhhi tesisat, ve benzeri. Evin parçalarının doğru ve güvenli bir şekilde çalışmasını, yani bina kodunu karşılamasını sağlar (testler). Bu senaryoda fonksiyonel testler ev sahibi bu aynı şantiye ziyaret benzer. İç sistemlerin uygun şekilde işkuracağını, yapı denetçisinin görevini yerine getireceğini varsayar. Ev sahibi bu evde yaşamanın nasıl bir şey olacağına odaklanmış durumda. O evin nasıl göründüğünü ile ilgilidir, çeşitli odalar rahat bir boyut, evin ailenin ihtiyaçlarına uygun mu, sabah güneşi yakalamak için iyi bir noktada pencereler vardır. Ev sahibi evde fonksiyonel testler yapıyor. Kullanıcının bakış açısına sahip. Yapı denetçisi evde birim testleri yapıyor. O, inşaatçının bakış açısına sahip."

Kaynak: [Ünite Testi ve Fonksiyonel Testler](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

"Geliştiriciler olarak, iki şekilde başarısız oluruz: ya yanlış bir şey yaparız, ya da yanlış bir şey yaparız." Birim testleri, doğru bir şey inşa emin olun; fonksiyonel testler doğru şeyi oluşturmanızı sağlar.

İşlevsel testler sistem düzeyinde çalıştığı için, bir dereceye kadar UI otomasyonu gerektirebilir. Entegrasyon testleri gibi, genellikle bir tür test altyapısıyla da çalışırlar. Bu onları birim ve tümleştirme testlerinden daha yavaş ve daha kırılgan hale getirir. Sistemin kullanıcıların beklediği gibi davrandığından emin olmak için gereken kadar işlevsel teste sahip olmalısınız.

### <a name="testing-pyramid"></a>Test Piramidi

Martin Fowler test piramidi hakkında yazdı, bunun bir örneği Şekil 9-1'de gösterilmiştir.

![Test Piramidi](./media/image9-1.png)

**Şekil 9-1**. Test Piramidi

Piramidin farklı katmanları ve bunların göreli boyutları, farklı türde testleri ve uygulamanız için kaç tane yazmanız gerektiğini temsil eder. Gördüğünüz gibi, öneri, daha küçük bir tümleştirme testi katmanı tarafından desteklenen ve daha da küçük bir işlevsel test katmanıyla birlikte büyük bir birim testi tabanına sahip olmaktır. Her katman ideal olarak sadece yeterli bir alt katmanda gerçekleştirilemez testler olmalıdır. Belirli bir senaryo için hangi test türüne ihtiyacınız olduğuna karar vermeye çalışırken test piramidini aklınızda bulundurun.

### <a name="what-to-test"></a>Ne test etmek

Otomatik testler yazma konusunda deneyimsiz geliştiriciler için ortak bir sorun ne test etmek için geliyor. İyi bir başlangıç noktası koşullu mantığı test etmektir. Koşullu bir ifadeye (if-else, switch, vb.) dayalı olarak değişen davranışiçeren bir yöntemin olduğu her yerde, belirli koşullar için doğru davranışı onaylayan en az birkaç test bulabilmeniz gerekir. Kodunuzda hata koşulları varsa, kod üzerinden "mutlu yol" için en az bir test (hatasız) ve uygulamanızın hatalar karşısında beklendiği gibi şekilde şekilde olduğunu doğrulamak için "üzücü yol" (hatalar veya atipik sonuçlarla) için en az bir test yazmak iyidir. Son olarak, kod kapsamı gibi ölçümlere odaklanmak yerine başarısız olabilecek şeyleri sınamaya odaklanın. Daha fazla kod kapsamı genellikle, daha az daha iyidir. Ancak, karmaşık ve iş açısından kritik bir yöntemin birkaç test daha yazma genellikle sadece test kodu kapsama ölçümleri geliştirmek için otomatik özellikleri için testler yazma daha zaman daha iyi bir kullanımıdır.

## <a name="organizing-test-projects"></a>Test projelerinin düzenlenmesi

Test projeleri ancak sizin için en iyi çalışır organize edilebilir. Testleri türüne (birim testi, tümleştirme testi) ve test ettikleri şeye (projeye göre, ad alanına göre) ayırmak iyi bir fikirdir. Bu ayırmanın tek bir test projesi içindeki klasörlerden veya birden çok test projesinden oluşup oluşmadığı bir tasarım kararıdır. Bir proje en basittir, ancak birçok teste sahip büyük projeler de veya farklı test kümelerini daha kolay çalıştırmak için birkaç farklı test projesine sahip olmak isteyebilirsiniz. Birçok ekip test projelerini test ettikleri projeye göre düzenler, bu da birkaç projeden fazla olan uygulamalar için çok sayıda test projesine neden olabilir, özellikle de bunları her projede ne tür testlerolduğuna göre yıkıyorsanız. Uzlaşmacı bir yaklaşım, test projelerinin içindeki klasörlerin test (ve sınıf) test edildiğini belirtmek için uygulama başına bir tür teste sahip olmasıdır.

Yaygın bir yaklaşım bir 'src' klasörü altında uygulama projeleri düzenlemek ve paralel bir 'testler' klasörü altında uygulamanın test projeleri. Bu organizasyonu yararlı bulursanız, Visual Studio'da eşleşen çözüm klasörleri oluşturabilirsiniz.

![Çözümünüzde test organizasyonu](./media/image9-2.png)

**Şekil 9-2**. Çözümünüzde test organizasyonu

Hangi test çerçevesini tercih ederseniz o labilirsiniz. xUnit çerçevesi iyi çalışır ve tüm ASP.NET Core ve EF Core testlerinin yazıldığı şeydir. Şekil 9-3'te gösterilen şablonu kullanarak Visual Studio'da veya CLI'den `dotnet new xunit`xUnit test projesi ekleyebilirsiniz.

![Visual Studio'da xUnit Test Projesi Ekleme](./media/image9-3.png)

**Şekil 9-3**. Visual Studio'da xUnit Test Projesi Ekleme

### <a name="test-naming"></a>Test adlandırma

Testlerinizi, her testin ne yaptığını gösteren adlarla tutarlı bir şekilde adlandırın. Ben büyük bir başarı elde ettik bir yaklaşım sınıf ve yöntem test göre test sınıfları isim etmektir. Bu, birçok küçük test sınıfına neden olur, ancak her testin ne sorumlusu olduğunu son derece açık hale getirir. Test sınıfı adı sınıf ve test edilecek yöntemi tanımlamak için ayarlanmış, test yöntemi adı test edilen davranışı belirtmek için kullanılabilir. Bu beklenen davranışı ve bu davranışı verim gereken herhangi bir girdi veya varsayımlar içermelidir. Bazı örnek test adları:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Bu yaklaşımın bir varyasyonu her test sınıfı adını "Should" ile bitirir ve zamanı biraz değiştirir:

- `CatalogControllerGetImage`**Aramalı**`.`**Call**`ImageServiceWithId`

- `CatalogControllerGetImage`**Oturum**`.`**Açmalı**`WarningGivenImageMissingException`

Bazı takımlar ikinci adlandırma yaklaşımını daha net bulurlar, ancak biraz daha ayrıntılıdır. Her durumda, bir veya daha fazla test başarısız olduğunda, hangi durumlarda başarısız olduğu adlarından belli olacak şekilde, test davranışı hakkında bilgi sağlayan bir adlandırma kuralı kullanmaya çalışın. Test sonuçlarını gördüğünüzde hiçbir değer sunamadığınız için, Testlerinizi ControllerTests.Test1 gibi belirsiz bir şekilde adlandırmaktan kaçının.

Yukarıdaki gibi birçok küçük test sınıfı üreten bir adlandırma kuralını izlerseniz, klasörleri ve ad boşluklarını kullanarak testlerinizi daha da düzenlemek iyi bir fikirdir. Şekil 9-4, çeşitli test projeleri içinde testleri klasöre göre düzenlemeye bir yaklaşım gösterir.

![Test sınıflarını test edilen sınıfa göre klasöre göre düzenleme](./media/image9-4.png)

**Şekil 9-4.** Test sınıflarını test edilen sınıfa göre klasöre göre düzenleme.

Belirli bir uygulama sınıfının test edilen birçok yöntemi (ve dolayısıyla birçok test sınıfı) varsa, bunları uygulama sınıfına karşılık gelen bir klasöre yerleştirmek mantıklı olabilir. Bu kuruluş, dosyaları başka bir yerde klasörlere nasıl düzenleyebileceğinizdir. Başka birçok dosya içeren bir klasörde üç veya dörtten fazla ilgili dosya nız varsa, bunları kendi alt klasörlerine taşımak genellikle yararlıdır.

## <a name="unit-testing-aspnet-core-apps"></a>Core uygulamaları ASP.NET birim testi

İyi tasarlanmış bir ASP.NET Core uygulamasında, karmaşıklık ve iş mantığının çoğu iş varlıklarında ve çeşitli hizmetlerde kapsüllenecektir. ASP.NET Core MVC uygulamasının kendisi, denetleyicileri, filtreleri, görüntüleme modelleri ve görünümleri ile çok az birim testi gerektirmelidir. Belirli bir eylemin işlevselliğinin çoğu eylem yönteminin dışındadır. Yönlendirmenin doğru çalışıp çalışmadığını veya genel hata işlemenin bir birim testi ile etkili bir şekilde yapılamayacağını test etmek. Aynı şekilde, model doğrulama, kimlik doğrulama ve yetkilendirme filtreleri de dahil olmak üzere tüm filtreler, denetleyicinin eylem yöntemini hedefleyen bir testle birim test edilemez. Bu davranış kaynakları olmadan, çoğu eylem yöntemi önemsiz derecede küçük olmalı ve çalışmalarının büyük bir kısmını, bunları kullanan denetleyiciden bağımsız olarak sınanabilecek hizmetlere devretilmelidir.

Bazen birimi test etmek için kodunuzu yeniden düzenlemeniz gerekir. Sık sık bu soyutlamaları tanımlamak ve doğrudan altyapıya karşı kodlama yerine, test etmek istediğiniz koddaki soyutlama erişmek için bağımlılık enjeksiyonu kullanarak içerir. Örneğin, görüntüleri görüntülemek için bu basit eylem yöntemini göz önünde bulundurun:

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

Birim testi bu yöntem, dosya sisteminden `System.IO.File`okumak için kullandığı doğrudan bağımlılığı ile zorlanır. Beklendiği gibi çalıştığından emin olmak için bu davranışı sınayabilirsiniz, ancak bunu gerçek dosyalarla yapmak bir tümleştirme testidir. Bu yöntemin rotasını birim olarak test edemezsiniz – bunu kısa süre içinde işlevsel bir testle nasıl yapacağınızı göreceksiniz.

Dosya sistemi davranışını doğrudan birim olarak test edemezseniz ve rotayı test edemezseniz, sınamak için ne var? Birim sınamamümkün kılmak için yeniden düzenleme yaptıktan sonra, bazı test örnekleri ve hata işleme gibi eksik davranışları keşfedebilirsiniz. Bir dosya bulunamıyorsa yöntem ne yapar? Ne yapmalı? Bu örnekte, yeniden düzenleme yöntemi aşağıdaki gibi görünür:

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

`_logger`ve `_imageService` her ikisi de bağımlılık olarak enjekte edilir. Artık, eylem yöntemine geçirilen aynı kimliğin `_imageService`,'e geçirildiğini ve elde edilen baytların FileResult'ın bir parçası olarak döndürülderken" test edebilirsiniz. Ayrıca, hata günlüğe kaydetmenin beklendiği gibi `NotFound` gerçekleştiğini ve görüntü eksikse, bunun önemli bir uygulama davranışı olduğunu varsayarak bir sonucun döndürüldürün (diğer bir zamanda geliştiricinin bir sorunu tanılamak için eklenen geçici kodu değil) test edebilirsiniz. Gerçek dosya mantığı ayrı bir uygulama hizmetine taşındı ve eksik bir dosya örneği için uygulamaya özgü bir özel durum döndürmek için artırıldı. Bu uygulamayı bir tümleştirme sınama kullanarak bağımsız olarak sınatabilirsiniz.

Çoğu durumda, denetleyicilerinizde genel özel durum işleyicileri kullanmak isteyeceksiniz, bu nedenle bu durumda mantık miktarı en az düzeyde olmalı ve büyük olasılıkla birim sınamaya değmez. İşlevsel testleri ve aşağıda açıklanan `TestServer` sınıfı kullanarak denetleyici eylemleri test çoğu yapın.

## <a name="integration-testing-aspnet-core-apps"></a>Core uygulamaları ASP.NET entegrasyon testi

ASP.NET Core uygulamalarınızdaki tümleştirme testlerinin çoğu, Altyapı projenizde tanımlanan hizmetleri ve diğer uygulama türlerini test etmelidir. Örneğin, EF Core'un Altyapı projesinde bulunan veri erişim sınıflarınızdan [beklediğiniz verileri başarıyla güncelleştirip aldığınızı test](https://docs.microsoft.com/ef/core/miscellaneous/testing/) edebilirsiniz. ASP.NET Core MVC projenizin doğru davrandığını test etmenin en iyi yolu, uygulamanız için bir test ana bilgisayarında çalışan işlevsel testlerdir.

## <a name="functional-testing-aspnet-core-apps"></a>Core uygulamaları ASP.NET işlevsel test

ASP.NET Core uygulamaları `TestServer` için, sınıf işlevsel testleri yazmayı oldukça kolaylaştırır. Doğrudan (uygulamanız `WebHostBuilder` için `HostBuilder`yaptığınız gibi) veya `WebApplicationFactory` tür (sürüm 2.1'den beri kullanılabilir) kullanarak bir `TestServer` (veya ) kullanarak yapılandırAbilirsiniz. Test ana bilgisayarınızın üretim ana tonunu mümkün olduğunca yakından eşleştirmeye çalışın, böylece testlerinizin uygulamanın üretimde yapacağına benzer davranışlar sergilemesi. Sınıf, `WebApplicationFactory` ASP.NET Core tarafından Görünümler gibi statik kaynağı bulmak için kullanılan TestServer'ın ContentRoot'unu yapılandırmak için yararlıdır.

TEntry web uygulamanızın Başlangıç sınıfı olduğu>> IClassFixture\<\<WebApplicationFactory TEntry uygulayan bir test sınıfı oluşturarak basit işlevsel testler oluşturabilirsiniz. Bu durumda, test fikstürfabrikanın CreateClient yöntemini kullanarak bir istemci oluşturabilirsiniz:

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

Sık sık, her test çalışmadan önce sitenizin bazı ek yapılandırma gerçekleştirmek isteyeceksiniz (örneğin, bellek veri deposunda bir uygulama kullanmak için uygulama yapılandırma ve daha sonra test verileri ile uygulama tohumlama. Bunu yapmak için, WebApplicationFactory\<TEntry> kendi alt sınıf oluşturmanız ve YapılandırmaWebHost yöntemini geçersiz kılmanız gerekir. Aşağıdaki örnek eShopOnWeb FunctionalTests projesinden ve ana web uygulaması üzerinde testlerin bir parçası olarak kullanılır.

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
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
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
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

Testler, bir istemci oluşturmak için kullanarak ve daha sonra bu istemci örneğini kullanarak uygulamaya istekte bulunarak bu özel WebApplicationFactory'den yararlanabilir. Uygulama, testin iddialarının bir parçası olarak kullanılabilecek verilere sahip olacaktır. Aşağıdaki test, eShopOnWeb uygulamasının ana sayfasının doğru yüklenir ve tohum verilerinin bir parçası olarak uygulamaya eklenen bir ürün listesi içerir doğrular.

```cs
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
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

Bu işlevsel test, tüm ara yazılımlar, filtreler, bağlayıcılar, vb yerinde olabilir dahil olmak üzere core mvc / Razor Pages uygulama yığını, tam ASP.NET egzersizleri. Belirli bir rotanın ("/") beklenen başarı durum kodunu ve HTML çıktısını döndürür doğrular. Bunu gerçek bir web sunucusu kurmadan yapar ve bu nedenle test etmek için gerçek bir web sunucusu kullanarak (örneğin, güvenlik duvarı ayarları ile ilgili sorunlar) karşılaşabileceğiniz kırılganlık çok önler. TestServer'a karşı çalışan işlevsel testler genellikle tümleştirme ve birim testlerinden daha yavaş, ancak ağ üzerinden bir test web sunucusuna çalışacak testlerden çok daha hızlıdır. Uygulamanızın ön uç yığınının beklendiği gibi çalıştığından emin olmak için işlevsel testler kullanın. Bu testler, denetleyicilerinizde veya sayfalarınızda yineleme bulduğunuzda ve filtreler ekleyerek yinelemeyi ele aldığınızda özellikle yararlıdır. İdeal olarak, bu yeniden düzenleme uygulamanın davranışını değiştirmez ve bir dizi işlevsel test bunun böyle olduğunu doğrular.

> ### <a name="references--test-aspnet-core-mvc-apps"></a>Referanslar – Test ASP.NET Core MVC uygulamaları
>
> - **ASP.NET Core'da Test** \
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Ünite Test Adlandırma Sözleşmesi** \
>   <https://ardalis.com/unit-test-naming-convention>
> - **EF Çekirdeğini Test Etme** \
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - **ASP.NET Core'da entegrasyon testleri** \
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
>[Önceki](work-with-data-in-asp-net-core-apps.md)
>[Sonraki](development-process-for-azure.md)
