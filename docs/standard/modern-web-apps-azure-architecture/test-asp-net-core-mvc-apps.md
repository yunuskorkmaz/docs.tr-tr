---
title: ASP.NET Core MVC uygulamaları sınama
description: ASP.NET Core ve Azure ile modern Web uygulamaları mimari | ASP.NET Core MVC uygulamaları sınama
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.openlocfilehash: 7b4bcb1c39ddbbc104820558532b03bc9341804e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592567"
---
# <a name="test-aspnet-core-mvc-apps"></a>ASP.NET Core MVC uygulamaları sınama

> _"Birim testi ürününüzü hoşlanmıyorsanız, büyük olasılıkla müşterilerinizin, ya da test etmek gibi olmaz."_
> _ - Anonim -

## <a name="summary"></a>Özet

Yazılım herhangi karmaşıklık değişikliklere yanıt beklenmeyen şekilde başarısız olabilir. Bu nedenle, değişiklikleri yaptıktan sonra test en Önemsiz (veya en az önemli) uygulamalar dışındaki tüm için gereklidir. Manuel test yavaş, az güvenilir, en pahalı şekilde yazılım test etmektir. Ne yazık ki, uygulamaları sınanabilir olacak şekilde tasarlanmıştır değil, yalnızca anlamına gelir kullanılabilir olabilir. Mimari ilkelerini düzenlendiği aşağıdaki bölümde X yazılmış uygulamalar için birim test edilebilir olmalıdır ve ASP.NET Core uygulamaları otomatik tümleştirme ve işlevsel testleri de destekler.

## <a name="kinds-of-automated-tests"></a>Otomatikleştirilmiş test türleri

Yazılım uygulamaları için otomatikleştirilmiş testleri birçok çeşit vardır. Basit, en düşük düzey test birim testi olur. Biraz daha yüksek bir düzeyde tümleştirme testleri ve işlevsel testleri vardır. Diğer UI testleri, yük testleri, stres testleri ve Duman testleri gibi testler bu belgenin kapsamı dışındadır türleridir.

### <a name="unit-tests"></a>Birim testleri

Birim testi uygulama mantığının tek bir parçası sınar. Bir başka onu öyle şeylerden bazıları listeleyerek açıklayabilirsiniz. Birim testi kodu çalışır bağımlılıklar veya hangi tümleştirme testleri altyapıyı – içindir nasıl test değil. Birim testi test kodunuzu üzerine yazılır çerçevesi değil – çalışır veya, bulursanız değil, dosyalama ve geçici bir çözüm kod varsayın. Birim testi tamamen bellek ve işleminde çalışır. Dosya sistemi, ağ veya bir veritabanı ile iletişim kuran değil. Birim testleri yalnızca kodunuzu test etmeniz gerekir.

Yalnızca tek bir birim, dış bağımlılıklar ile kodunuzu test olgu, birim testleri son derece hızlı bir şekilde çalıştırılmalıdır. Bu nedenle, test paketlerini, birim testleri yüzlerce çalıştırabilir ve birkaç saniye içinde olmalıdır. Bunları sık, ideal olarak her itme paylaşılan kaynak denetim deponuza ve her otomatik derleme ile kesinlikle önce derleme sunucunuzda çalıştırın.

### <a name="integration-tests"></a>Tümleştirme testleri

Bu altyapı veritabanları ve dosya sistemleri gibi etkileşimde kodunuzu kapsüllemek için iyi bir fikir olsa da, bazı kodun hala olacaktır ve muhtemelen test istersiniz. Ayrıca, uygulamanızın bağımlılıkları tam olarak çözümlenmiş olduğunda beklediğiniz gibi kodun katman etkileşim doğrulamanız gerekir. Tümleştirme testleri sorumluluğundadır. Tümleştirme testleri genellikle dış bağımlılıkları ve altyapı üzerinde bağımlı olduğundan daha yavaştır ve birim testleri ayarlamak daha zor olma eğilimindedir. Bu nedenle, tümleştirme testlerinde birim testleri testleriyle olabilir şeyler sınama kaçınmalısınız. Birim testi ile belirli bir senaryo test edebilirsiniz, birim testi ile test etmeniz gerekir. Şunları yapamazsınız, ardından bir tümleştirme test kullanmayı düşünün.

Tümleştirme testleri genellikle daha karmaşık kurulum ve birim testleri daha erdirme yordamları sahip olur. Örneğin, gerçek bir veritabanına karşı giden bir tümleştirme test veritabanı her test çalışması önce bilinen bir duruma döndürmek için bir yol gerekir. Yeni testleri eklenir ve üretim veritabanı şeması dönüşmesi, komut dosyaları eğilimindedir boyutu ve karmaşıklığı büyümeye bu test. Birçok büyük sisteminde değişiklik paylaşılan kaynak denetimine iade önce Geliştirici istasyonlarında tümleştirme testlerinin tam paketlerini çalıştırmaya zordur. Bu durumlarda, tümleştirme testleri bir yapı sunucuda çalışabilir.

LocalFileImageService uygulama sınıfı getirme ve bir görüntü dosyası bayt kimliği verilen belirli bir klasörden döndürmek için mantığını uygular:

```cs
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
```

### <a name="functional-tests"></a>İşlevsel testleri

Tümleştirme testleri sistem bazı bileşenleri düzgün bir şekilde birlikte çalışmasını doğrulamak için geliştirici perspektifinden yazılır. İşlevsel testleri kullanıcı perspektifinden yazılır ve kendi gereksinimlerine göre sistem doğruluğundan emin olun. Aşağıdaki alıntı nasıl için birim testleri karşılaştırılması işlevsel testleri hakkında düşünmek için yararlı bir benzerleme sunar:

> "Birçok kez geliştirme sisteminin bir ev oluşturulmasını likened. Bu benzerleme oldukça doğru olmasa da, biz birim ve işlevsel testleri arasındaki farkı anlamak amacıyla genişletebilirsiniz. Birim testi house'nın yapım sitesinden bir yapı denetçisi benzerdir. Müşterinizle çerçeveleme, elektrik, Sıhhi tesisat ve vb. foundation house çeşitli iç sistemlerde odaklanmıştır. Kendisine (ev bölümlerini düzgün çalışması ve güvenli bir şekilde, diğer bir deyişle, yapı kod karşılayan testleri) sağlar. Bu senaryoda işlevsel testleri, bu aynı yapım siteyi ziyaret konut benzer. Müşterinizle iç sistemlerinin uygun şekilde davranır, yapı denetçisi kendi görev çalıştığını varsayar. Konut ne bu gibi bu house Canlı olacaktır üzerinde odaklanmıştır. Kendisine evin nasıl göründüğünü ile ilgilidir, çeşitli rooms rahat boyutu, ev ailesinin gereksinimlerinize uygun olmadığından, sabah sun yakalamak için iyi bir nokta olarak Windows. Konut işlevsel testleri evi gerçekleştiriyor. Kullanıcı açısından sahip. Yapı denetçisi birim testleri evi gerçekleştiriyor. Oluşturucunun perspektif sahip."

Kaynak: [birim testi işlevsel testleri](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Bildiren, Acıyı ben "geliştiriciler şu iki yolla başarısız: biz yanlış şey oluşturmak veya biz yanlış şeyi yapı." Birim testleri şey sağ oluşturmakta olduğunuz emin olun; işlevsel testleri doğru şeyi oluşturmakta olduğunuz emin olun.

İşlevsel testleri sistem düzeyinde çalışır olduğundan, bunlar dereceye UI Otomasyon gerektirebilir. Tümleştirme testleri gibi genellikle test altyapısını bazı tür çalışırlar. Bu onları daha yavaştır ve birim ve tümleştirme testleri daha kırılır hale getirir. Yalnızca olması kullanıcılar beklendiği gibi sistem davranmakta emin olmanız gerekir sayıda işlevsel testleri.

### <a name="testing-pyramid"></a>Piramit test etme

Bir örneği, Şekil 9-1'de gösterilen test Piramit hakkında Martin Fowler yazıldı.

![](./media/image9-1.png)

Şekil 9-1 Piramit test etme

Piramit ve göreli boyutlarının farklı katmanları farklı türdeki testleri ve uygulamanız için yazmalısınız kaç temsil eder. Gördüğünüz gibi daha küçük bir tümleştirme testleri katmanında işlevsel testleri bile daha küçük bir katmanı ile desteklenen birim testleri, büyük bir taban olması önerilir. Her katman, alt katman yeterli gerçekleştirilemiyor, ideal olarak testleri yalnızca olmalıdır. Belirli bir senaryo için gereken test hangi tür karar vermeye çalışırken test Piramit göz önünde bulundurun.

### <a name="what-to-test"></a>Test gerekenler

Otomatikleştirilmiş testleri yazma ile deneyimsiz geliştiriciler için ortak bir sorun ile test etmek yakında. İyi bir başlangıç noktası koşullu mantık test etmektir. Değişiklikleri koşullu bir ifadesine dayalı olarak davranışına sahip bir yöntem sahip herhangi bir yerde (if-else, geçiş, vb.), en az birkaç belirli koşulların doğru davranışını Onayla testleri gelmesi gerekir. Kodunuzu hata koşulları varsa, "mutluluk yolu için" kod aracılığıyla en az bir test (hatasız) ve "üzücü yolu" için en az bir test uygulamanızın hatalarını karşısında beklendiği gibi davranır onaylamak için (hataları veya alışılmadık sonuçları) yazmak iyidir. Kod kapsamı gibi ölçümleri odaklanan yerine yük devredebilir şeyler sınama odaklanmak son olarak, deneyin. Daha fazla kod kapsamı genellikle daha az daha iyi olur. Ancak, çok karmaşık ve iş açısından kritik yönteminin birkaç daha fazla testleri yazma genellikle testleri yalnızca test kod kapsamı ölçümleri geliştirmek otomatik-özellikleri için yazma değerinden bir daha iyi zaman kullanılır.

## <a name="organizing-test-projects"></a>Test projeleri düzenleme

Ancak, Works sizin için en iyi test projeleri düzenlenebilir. Testleri türünü (birim testi, tümleştirme test) ve hangi (projeye göre ad alanı) test ettikleri göre ayırmak için iyi bir fikirdir. Bu ayrım tek test projesi ya da birden çok test projeleri, klasörlere oluşur olup olmadığını tasarım bir karardır. Bir proje en kolayıdır ancak birçok testleriyle ya da daha kolay farklı testleri kümesi çalıştırmak için büyük projeler için birkaç farklı test projeleri sahip olmak isteyebilirsiniz. Birçok ekip test projeleri özellikle, hala bu tür testleri her projede nelerdir göre ayırırsanız birkaç projeleri olan uygulamalar için çok sayıda test projeleri sonuçlanabilir sınıyorsanız, proje göre düzenler. Bir tehlikeye yaklaşım sınanan proje (ve sınıf) belirtmek için test projeleri klasörlerde ile uygulama başına test tür başına tek bir proje olmalıdır.

'Src' klasörü altında uygulama projeleri ve paralel 'test' klasörü altında uygulamanın test projeleri düzenlemek ortak bir yaklaşımdır. Bu kuruluş yararlı bulursanız, Visual Studio'da eşleşen çözüm klasörler oluşturabilirsiniz.

![](./media/image9-2.png)

Şekil 9-2 Test kuruluş çözümünüzdeki

Tercih ettiğiniz çerçeveye test kullanabilirsiniz. XUnit framework iyi çalışır ve nedir tüm ASP.NET Core ve EF çekirdek testleri yazılır. Visual Studio'da Şekil 9-3'te veya dotnet yeni xunit kullanarak clı'dan gösterilen şablonu kullanarak bir xUnit test projesi ekleyebilirsiniz.

![](./media/image9-3.png)

Şekil 9-3 Ekle xUnit Visual Studio'da Test projesi

### <a name="test-naming"></a>Test adlandırma

Her sınama ne yaptığını gösteren adlarla testlerinizi tutarlı bir şekilde adlandırmanız gerekir. Harika başarı ile sahip bir sınıf ve test ettiğiniz yöntemi göre ad test sınıflarını yaklaşımdır. Bu çok sayıda küçük test sınıflarda olur, ancak son derece her test sorumlu nedir temizleyin sağlar. Test yöntemi adı sınıfı ve sınanacak yöntemi tanımlamak için ayarladığınız test sınıf adı ile test edilen davranışını belirtmek için kullanılır. Bu beklenen bir davranış ve girişleri veya bu davranış verim varsayımlar içermelidir. Bazı örnek test adları:

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

Bu yaklaşımın bir değişim her test sınıfı adı "Gerekir" ile biten ve zamanın biraz değiştirir:

-   CatalogControllerGetImage**gereken**. **Çağrı**ImageServiceWithId

-   CatalogControllerGetImage**gereken**. **Günlük**WarningGivenImageMissingException

NET, ikinci adlandırma yaklaşımını bazı ekipler bulmak ancak biraz daha ayrıntılı. Herhangi bir durumda, böylece bir veya birkaç sınama başarısız olduğunda hangi durumlarda başarısız olmuş kendi adlarından belirgin test davranışı hakkında bilgi sağlayan bir adlandırma kuralı kullanmayı deneyin. Test sonuçlarında görüntülendiğinde bu herhangi bir değer sunar gibi testleri ControllerTests.Test1 gibi vaguely, adlandırma kaçının.

Çok sayıda küçük test sınıfları, yukarıdakine üreten gibi bir adlandırma kuralı izlerseniz, daha fazla klasörleri ve ad alanlarını kullanarak testlerinizi düzenlemek için bir fikirdir. Şekil 9-4 birkaç test projeleri klasördeki tarafından testlerin düzenlenmesi için bir yaklaşım gösterir.

![](./media/image9-4.png)

**Şekil 9-4.** Test sınıfları tarafından test edilen sınıfına göre klasör düzenleme.

Elbette, belirli uygulama sınıfı sınanan birçok yöntemleri vardır (ve böylece çoğu sınıfları test varsa), bu uygulama sınıfına karşılık gelen bir klasöre yerleştirin mantıklı olabilir. Bu kuruluş nasıl, dosyaları başka bir yerde klasörler halinde düzenleyebileceğini farklı değildir. En fazla üç varsa veya dört ilgili diğer birçok dosyalarını içeren bir klasördeki dosyaları, genellikle kendi alt klasöre taşımak yararlıdır.

## <a name="unit-testing-aspnet-core-apps"></a>Birim testi ASP.NET Core uygulamaları

İyi tasarlanmış bir ASP.NET Core uygulama karmaşıklığını ve iş mantığı çoğu iş varlıkları ve çeşitli hizmetlere kapsüllenmiş. ASP.NET Core MVC uygulamayla kendisini denetleyicileri, filtreleri, viewmodels ve görünümler, çok az birim testleri istemeniz gerekir. Belirli bir eylemi işlevlerinin çoğunu eylem yönteminin kendisi dışında arasındadır. Etkin yönlendirme düzgün çalıştığını olup olmadığını test etme ya da genel hata işleme ile birim testi yapılamaz. Benzer şekilde, herhangi bir model doğrulama ve kimlik doğrulaması gibi filtreler ve yetkilendirme filtreleri olamaz test birim. Bu davranış kaynakları, çoğu eylem yöntemleri bunları kullanan denetleyicisinin bağımsız sınanabilir Hizmetleri iş toplu temsilci trivially küçük olmalıdır.

Bazen birim testi kodunuzda sipariş düzenleme gerekir. Sık bu soyutlama tanımlama ve test etmek istediğiniz kod soyutlama erişmek için bağımlılık ekleme kullanılarak yerine doğrudan altyapı karşı kodlama içerir. Örneğin, görüntüleri görüntüleme için bu basit eylem yöntemine göz önünde bulundurun:

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Birim testi bu yöntem, dosya sisteminden okumak için kullandığı System.IO.File doğrudan bağımlı tarafından zor olarak yapılır. Bu davranış beklendiği gibi çalışır, ancak gerçek dosyalarıyla böylece tümleştirme test olduğundan emin olmak için test edebilirsiniz. Bu yöntemin rota test edilemez – bu işlev bir test ile kısa süre içinde nasıl yapılacağı görürsünüz dikkate değerdir.

Birim testi dosya sistemi davranışını doğrudan yükleyemezsiniz ve rota test edilemez, var. test etmek için nedir? İyi, birim testi mümkün kılmak için yeniden düzenleme sonra bazı test durumları ve hata işleme gibi eksik davranışı fark edebilirsiniz. Bir dosya bulunamadığında zaman yöntemi ne yapar? Neler? Bu örnekte, işlenmiş yöntemi şöyle görünür:

```cs
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

\_Günlükçü ve \_Imageservice her ikisi de eklenmiş bağımlılıkları. Eylem yöntemine geçirilen aynı kimliği geçirilecek test artık \_Imageservice, ve sonuçta elde edilen bayt FileResult bir parçası olarak döndürülür. Ayrıca hata günlüğünü beklendiği gibi gerçekleşmekte olduğunu ve görüntünün eksikse NotFound sonuç döndürülür bu önemli uygulama davranışına (diğer bir deyişle, yalnızca geçici kodu bir sorunu tanılamak için eklenen Geliştirici) olduğunu varsayarak test edebilirsiniz. Gerçek dosya mantığı ayrı uygulama hizmetine taşınmıştır ve bir uygulamaya özgü özel durum dosyası eksik çalışması için döndürmek için genişletilebilir. Bir tümleştirme test kullanarak bu uygulama bağımsız olarak, test edebilirsiniz.

## <a name="integration-testing-aspnet-core-apps"></a>Tümleştirme ASP.NET Core uygulamaları test etme

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

Bu hizmet, yalnızca ayrı bir hizmet yeniden düzenlenmeden önce kodu vermedi CatalogController olarak IHostingEnvironment kullanır. Bu IHostingEnvironment kullanılan denetleyici yalnızca kod olduğundan, bu bağımlılık CatalogController'ın oluşturucudan kaldırıldı.

Bu hizmet düzgün çalıştığını test etmek için bilinen test görüntü dosyası oluşturmak ve hizmet, belirli bir giriş verilen döndürür doğrulamak gerekir. Sahte nesneler gerçekte (dosya sisteminden okuma bu durumda,) test etmek istediğiniz davranışı üzerinde kullanmayacak şekilde halletmeniz. Ancak, sahte nesneler hala tümleştirme testleri oluşturma yararlı olabilir. Bu durumda, böylece kendi ContentRootPath test görüntüsü için kullanacaksanız klasörü işaret IHostingEnvironment mock. Tüm çalışma tümleştirme test sınıf burada gösterilir:

```cs
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";
    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }
    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
            var location = System.Reflection.Assembly.GetEntryAssembly().Location;
            return Path.GetDirectoryName(location);
        }

        [Fact]
        public void ReturnsFileContentResultGivenValidId()
        {
            var fileService = new LocalFileImageService(_mockEnvironment.Object);
            var result = fileService.GetImageBytesById(_testImageId);
            Assert.Equal(_testBytes, result);
        }
    }
```

> [!NOTE]
> test çok basit – kod toplu sistem yapılandırmak ve test altyapısında (diskten okumak için bu durumda, asıl dosyası) oluşturmak gerekli olmasıdır. Birim testleri'den daha karmaşık kurulum çalışması genellikle gerektiren tümleştirme testleri için bu normaldir.

## <a name="functional-testing-aspnet-core-apps"></a>İşlevsel bir ASP.NET Core uygulamalarını test etme

ASP.NET Core uygulamaları TestServer sınıfı işlevsel testleri yazmak oldukça kolay hale getirir. Normalde, uygulamanız için yaptığınız gibi bir WebHostBuilder kullanarak bir TestServer yapılandırın. Bu WebHostBuilder yalnızca uygulamanızın gerçek ana bilgisayar gibi yapılandırılması gerekir, ancak test işlemini kolaylaştıran tüm yönleriyle değiştirebilirsiniz. Çoğu zaman, yeniden kullanılabilir bir yöntem (belki de bir taban sınıf) kapsülleyen şekilde birçok test çalışmaları için aynı TestServer yeniden:

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

GetProjectPath yöntemi yalnızca web projesine (indirme örnek çözümü) fiziksel yolu döndürür. WebHostBuilder bu durumda yalnızca burada web uygulaması için içerik kök ve gerçek web uygulamasını kullanan aynı başlangıç sınıfı başvuran belirtir. TestServer ile çalışmak için istekleri yapmak için standart System.Net.HttpClient türü kullanın. TestServer TestServer üzerinde çalışan uygulama isteklerini yapmaya hazır önceden yapılandırılmış bir istemci sağlayan yararlı bir CreateClient yöntemi gösterir. Bu İstemcisi'ni kullanın (korunan ayarlamak \_yukarıdaki temel test istemci üyesinde) işlevsel testleri ASP.NET Core uygulamanız için yazarken:

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

Bu işlev sınama tüm ara yazılım, filtreleri, bağlayıcıları, yerinde olabilir vb. de dahil olmak üzere tam ASP.NET Core MVC uygulama yığınını uygular. Olduğunu doğrular bir rota verilen ("/ PIC/katalog/1") bilinen bir konumda bir dosya için beklenen bayt dizisi döndürür. Bunu gerçek web sunucunuzu kurmak ayarlamadan yapar ve bu nedenle, gerçek web kullanarak test etmek için sunucu (örneğin, güvenlik duvarı ayarlarını sorunları) yaşayabilirsiniz brittleness çoğunu önler. TestServer karşı çalıştırmak işlevsel testleri tümleştirme ve birim testleri genellikle yavaştır, ancak ağ üzerinden bir test web sunucusunda çalışır testleri hızlıdır.

>[!div class="step-by-step"]
[Önceki] (work-with-data-in-asp-net-core-apps.md) [sonraki] (geliştirme-işlem-için-azure.md)
