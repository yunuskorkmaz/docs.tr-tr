---
title: ASP.NET Core MVC test uygulamaları
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | ASP.NET Core MVC uygulamalarını test etme
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 06d2b576e70afb904683ca1a182c6e061faabf79
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663821"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="5a06c-103">ASP.NET Core MVC test uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a06c-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="5a06c-104">*"Birim testi ürününüzü kullanmak istemiyorsanız, büyük olasılıkla müşterileriniz, ya da test etmek gibi olmayacaktır."*</span><span class="sxs-lookup"><span data-stu-id="5a06c-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="5a06c-105">\_-Anonim-</span><span class="sxs-lookup"><span data-stu-id="5a06c-105">\_- Anonymous-</span></span>

<span data-ttu-id="5a06c-106">Yazılım tüm karmaşıklığı değişikliklere yanıt olarak beklenmedik bir şekilde başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="5a06c-107">Bu nedenle, değişiklikleri yaptıktan sonra test için en basit (veya en az önemli) uygulamaları dışındaki tüm alanlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="5a06c-108">El ile test yavaş, güvenilir az ve en pahalı yöntem yazılım test etmektir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="5a06c-109">Ne yazık ki, uygulamalar, test edilebilir olması için tasarlanmamış, yalnızca anlamına gelir kullanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="5a06c-110">Yazılan uygulamalar, normal bir kutudur mimari ilkeleri aşağıdaki [bölüm 4](architectural-principles.md) birim test edilebilir ve ASP.NET Core uygulamaları, otomatik tümleştirme ve işlevsel test de destekler.</span><span class="sxs-lookup"><span data-stu-id="5a06c-110">Applications written following the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="5a06c-111">Otomatik test türleri</span><span class="sxs-lookup"><span data-stu-id="5a06c-111">Kinds of automated tests</span></span>

<span data-ttu-id="5a06c-112">Yazılım uygulamaları için otomatik testler birçok çeşit vardır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-112">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="5a06c-113">Basit, en düşük düzey test birim testi olur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-113">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="5a06c-114">Biraz daha yüksek bir düzeyde tümleştirme testleri ve işlevsel testleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-114">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="5a06c-115">Diğer kullanıcı Arabirimi testleri, yük testleri, yük testleri ve Duman testleri gibi testler bu belgenin kapsamı dışındadır türleridir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-115">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="5a06c-116">Birim testleri</span><span class="sxs-lookup"><span data-stu-id="5a06c-116">Unit tests</span></span>

<span data-ttu-id="5a06c-117">Birim testi, uygulamanızın mantıksal tek bir parçası sınar.</span><span class="sxs-lookup"><span data-stu-id="5a06c-117">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="5a06c-118">Bir daha da öyle şeylerden bazıları listeleyerek tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-118">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="5a06c-119">Birim test, kodun çalıştığını bağımlılıkları veya hangi tümleştirme testleri olan altyapıya – içindir nasıl test değil.</span><span class="sxs-lookup"><span data-stu-id="5a06c-119">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="5a06c-120">Birim testi test kodunuzu üzerindeki yazılan çerçevesi değil – çalışır veya, bulursanız değil, hata bildirin ve geçici bir çözüm kod varsaymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-120">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="5a06c-121">Birim testi, bellek ve işlem tamamen çalışır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-121">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="5a06c-122">Dosya sistemi, ağ veya veritabanı ile iletişim kurmak değil.</span><span class="sxs-lookup"><span data-stu-id="5a06c-122">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="5a06c-123">Birim testleri yalnızca kodunuzu test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-123">Unit tests should only test your code.</span></span>

<span data-ttu-id="5a06c-124">Dış bağımlılıkları olmayan, kodunuzun yalnızca tek bir birim test etmenizi olgu da birim testleri, son derece hızlı bir şekilde getirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-124">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="5a06c-125">Bu nedenle, test paketleri, birim testleri yüzlerce birkaç saniye içinde çalıştırabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-125">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="5a06c-126">Bunları sık, ideal olarak her anında iletme paylaşılan kaynak denetim deposu ve kesinlikle her bir otomatik yapı önce yapı sunucunuzda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5a06c-126">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="5a06c-127">Tümleştirme testleri</span><span class="sxs-lookup"><span data-stu-id="5a06c-127">Integration tests</span></span>

<span data-ttu-id="5a06c-128">Veritabanları ve dosya sistemleri gibi altyapı ile etkileşime giren kodunuzu kapsüllemek için iyi bir fikir olsa da hala bazı kod gerekir ve büyük olasılıkla bunu test etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-128">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="5a06c-129">Ayrıca, uygulama bağımlılıklarınızın tamamen çözümlendiğinde beklediğiniz gibi kodunuzun katman etkileşim doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-129">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="5a06c-130">Bu tümleştirme testleri sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-130">This is the responsibility of integration tests.</span></span> <span data-ttu-id="5a06c-131">Tümleştirme testleri, genellikle dış bağımlılıkları ve altyapınıza bağlı olduğundan daha yavaş ve birim testleri ayarlamak daha zor olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-131">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="5a06c-132">Bu nedenle, tümleştirme testlerini birim testleriyle denetlenecek noktalar test kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-132">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="5a06c-133">Belirli bir senaryo bir birim testi ile test, birim testi ile test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-133">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="5a06c-134">Çözemezseniz, bir tümleştirme testini kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="5a06c-134">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="5a06c-135">Tümleştirme testleri genellikle daha karmaşık kurulum ve kaldırma yordamları birim testlerinden sahip olur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-135">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="5a06c-136">Örneğin, gerçek bir veritabanında giden bir tümleştirme testi veritabanını, her test çalışması önce bilinen bir duruma döndürmek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-136">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="5a06c-137">Yeni testler eklenir ve üretim veritabanı şemasını geliştikçe, bu test betikleri boyutu ve karmaşıklığı büyümesine eğilimli.</span><span class="sxs-lookup"><span data-stu-id="5a06c-137">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="5a06c-138">Birçok büyük sistemde, değişiklikleri paylaşılan kaynak denetimine iade etmeden önce Geliştirici iş istasyonları üzerinde tam paketleri tümleştirme testleri çalıştırmak için zordur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-138">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="5a06c-139">Bu durumlarda, tümleştirme testlerini bir yapı sunucusunda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-139">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="5a06c-140">LocalFileImageService uygulama sınıfımızın getirmeye ve bir görüntü dosyasının baytlar verilen bir kimlik, belirli bir klasörden döndüren mantığını uygular:</span><span class="sxs-lookup"><span data-stu-id="5a06c-140">The LocalFileImageService implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

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

### <a name="functional-tests"></a><span data-ttu-id="5a06c-141">İşlevsel testler</span><span class="sxs-lookup"><span data-stu-id="5a06c-141">Functional tests</span></span>

<span data-ttu-id="5a06c-142">Tümleştirme testleri sisteminin bazı bileşenleri düzgün birlikte çalıştığını doğrulamak için geliştirici perspektifinden yazılır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="5a06c-143">İşlevsel testleri, kullanıcı perspektifinden yazılır ve kendi gereksinimlerine göre sistem doğruluğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="5a06c-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="5a06c-144">Aşağıdaki alıntıda işlevsel testleri, birim testleri karşılaştırıldığında düşünün öğrenmek için kullanışlı bir benzerliği sunar:</span><span class="sxs-lookup"><span data-stu-id="5a06c-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="5a06c-145">"Bir sistemin geliştirme birden çok kez bir ev oluşturulmasını likened.</span><span class="sxs-lookup"><span data-stu-id="5a06c-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="5a06c-146">Bu benzerleme oldukça doğru değildir; ancak biz birim ve işlev testleri arasındaki farkı anlamak amacıyla genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="5a06c-147">Birim testi house'nın yapı sitesinden bir yapı denetleyici benzerdir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="5a06c-148">He house, çerçeve, elektrik Sıhhi tesisat ve bu şekilde foundation çeşitli dahili sistemlerinde odaklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="5a06c-149">He (evi bölümlerini düzgün ve güvenli bir şekilde, diğer bir deyişle, yapı kod karşılamak testleri) sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a06c-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="5a06c-150">Bu senaryoda işlevsel testleri bu aynı yapı siteyi ziyaret sakininin benzer.</span><span class="sxs-lookup"><span data-stu-id="5a06c-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="5a06c-151">He iç sistemleri uygun şekilde davranır, yapı Inspector'ı kendi görevi çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="5a06c-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="5a06c-152">Sakininin ne gibi bu Merkezi'nde Canlı de artar üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="5a06c-153">He evi nasıl göründüğünü ile ilgilidir, çeşitli rooms rahat boyutu, ev ailesinin gereksinimlerine uygun, sabah sun yakalamak için iyi bir kolayca Windows.</span><span class="sxs-lookup"><span data-stu-id="5a06c-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="5a06c-154">Sakininin işlevsel testleri evi gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="5a06c-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="5a06c-155">Kullanıcı açısından sahip.</span><span class="sxs-lookup"><span data-stu-id="5a06c-155">He has the user's perspective.</span></span> <span data-ttu-id="5a06c-156">Birim testleri, derleme denetçisi evi gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="5a06c-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="5a06c-157">Oluşturucunun perspektif sahip."</span><span class="sxs-lookup"><span data-stu-id="5a06c-157">He has the builder's perspective."</span></span>

<span data-ttu-id="5a06c-158">Kaynak: [Birim testi işlevsel testler](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="5a06c-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="5a06c-159">Bildiren, Acıyı istiyorum "geliştiriciler, size iki yolla başarısız: yanlış bir şey ekliyoruz veya yanlış bir şey ekliyoruz."</span><span class="sxs-lookup"><span data-stu-id="5a06c-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="5a06c-160">Birim testleri şey sağ oluşturmakta olduğunuz emin olun. işlevsel testler doğru şeyi oluşturmakta olduğunuz emin olun.</span><span class="sxs-lookup"><span data-stu-id="5a06c-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="5a06c-161">Sistem düzeyinde işlevsel testleri çalıştırma olduğundan, bunlar UI Otomasyonu derece gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="5a06c-162">Tümleştirme testleri gibi bunlar genellikle test altyapısı tür ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="5a06c-163">Bu, bunların daha yavaş ve birim ve tümleştirme testleri daha kırılır sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a06c-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="5a06c-164">Yalnızca olmalıdır sistem kullanıcılar beklendiği gibi davrandığından emin olmanız gerekir kadar işlevsel testleri.</span><span class="sxs-lookup"><span data-stu-id="5a06c-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="5a06c-165">Piramit test etme</span><span class="sxs-lookup"><span data-stu-id="5a06c-165">Testing Pyramid</span></span>

<span data-ttu-id="5a06c-166">Şekil 9-1'de, bir örnek gösterilir, test Piramit hakkında Martin Fowler yazıldı.</span><span class="sxs-lookup"><span data-stu-id="5a06c-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="5a06c-167">Şekil 9-1 Piramit test etme</span><span class="sxs-lookup"><span data-stu-id="5a06c-167">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="5a06c-168">Piramit ve bunların göreli boyutlarını farklı katmanlara testleri ve uygulamanız için yazmalısınız kaç farklı türde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a06c-168">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="5a06c-169">Gördüğünüz gibi büyük bir temel birim testleri, tümleştirme testleri, daha küçük bir katman işlevsel testlerin bile küçük bir katman ile tarafından desteklenen olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-169">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="5a06c-170">Her katman, daha düşük bir katmanda yeterince gerçekleştirilemiyor, ideal olarak testleri yalnızca olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-170">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="5a06c-171">Ne tür bir test belirli bir senaryo için gereken karar vermeye çalışırken test Piramit göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5a06c-171">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="5a06c-172">Hangi test etmek için</span><span class="sxs-lookup"><span data-stu-id="5a06c-172">What to test</span></span>

<span data-ttu-id="5a06c-173">Otomatik testler yazmaya deneyimsiz geliştiriciler için ortak bir sorunu ile test etmek yakında.</span><span class="sxs-lookup"><span data-stu-id="5a06c-173">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="5a06c-174">Koşullu mantık test etmek için iyi bir başlangıç noktası var.</span><span class="sxs-lookup"><span data-stu-id="5a06c-174">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="5a06c-175">Değişiklikler bir koşullu ifadeye göre davranışı yöntemiyle sahip herhangi bir yerde (if-else, geçiş, vb.), en az birkaç yukarı doğru davranışı belirli koşullarda onaylayan testlerini gelen olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-175">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="5a06c-176">Hata koşulları kodunuz varsa (hatasız) en az bir test kodu "Mutlu yolu" ve "Üzgün yolu" için en az bir test uygulamanız karşılaşıldığında hataları beklendiği gibi davranır onaylamak için (hataları veya alışılmadık sonuçları ile) yazmak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-176">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="5a06c-177">Son olarak, kod kapsamı gibi ölçümleri odaklanan yerine eklenemeyecek olan şeyleri test odaklanmak deneyin.</span><span class="sxs-lookup"><span data-stu-id="5a06c-177">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="5a06c-178">Daha fazla kod kapsamı, genel olarak küçük, daha iyi olur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-178">More code coverage is better than less, generally.</span></span> <span data-ttu-id="5a06c-179">Ancak, birkaç daha fazla test çok karmaşık ve iş açısından kritik yönteminin yazma genellikle testleri yalnızca test kod kapsamı ölçümleri geliştirmek otomatik özelliklerde için yazma daha zaman daha iyi bir kullanımı olur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-179">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="5a06c-180">Test projeleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="5a06c-180">Organizing test projects</span></span>

<span data-ttu-id="5a06c-181">Test projeleri Works sizin için en iyi ancak düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-181">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="5a06c-182">Test türü (birim testi, tümleştirme testi) ve hangi (proje, ad alanı tarafından) test ettikleri göre ayırmak için iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-182">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="5a06c-183">Bu ayrım tek bir test projesi ya da birden çok test projesini klasörler oluşur olup olmadığını bir tasarım kararıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-183">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="5a06c-184">Bir proje basit olmakla birlikte çok sayıda test ya da daha kolay farklı test kümesini çalıştırmak için büyük projeler için birkaç farklı test projeleri bulundurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-184">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="5a06c-185">Birçok takım test projeleri özellikle, yine de bu tür testler her projede nelerdir göre bölmek, fazla sayıda projeleri ile uygulamalar için çok sayıda test projeleri neden olabilir, test, proje göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="5a06c-185">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="5a06c-186">Bir güvenlik ihlali yaklaşım, test, test edilen proje (ve sınıf) belirtmek için test projeleri klasörlerde ile uygulama başına tür başına tek bir proje sahip olmaktır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-186">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="5a06c-187">'Src' klasörü altındaki uygulama projeleri ve uygulamanın paralel 'test' klasörü altında test projeleri düzenleme yaygın bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-187">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="5a06c-188">Bu kuruluş kullanışlı, Visual Studio eşleşen çözümü klasörler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-188">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="5a06c-189">Şekil 9-2, çözümünüzdeki Test kuruluş</span><span class="sxs-lookup"><span data-stu-id="5a06c-189">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="5a06c-190">Tercih ettiğiniz test çerçeveye kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-190">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="5a06c-191">XUnit framework iyi çalışır ve nedir tüm ASP.NET Core ve EF Core testleri yazılır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-191">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="5a06c-192">Şekil 9-3'te veya yeni dotnet xunit kullanarak clı'dan gösterilen şablonu kullanarak Visual Studio'da bir xUnit test projesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-192">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="5a06c-193">Şekil 9-3, Visual Studio'da bir xUnit Test projesi Ekle</span><span class="sxs-lookup"><span data-stu-id="5a06c-193">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="5a06c-194">Test adlandırma</span><span class="sxs-lookup"><span data-stu-id="5a06c-194">Test naming</span></span>

<span data-ttu-id="5a06c-195">Her test ne yaptığını gösteren adlarla testlerinizi tutarlı bir biçimde adlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5a06c-195">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="5a06c-196">Harika başarılı bir şekilde sahip bir ad test sınıflarında sınıfı ve test ettikleri yöntemi göre yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-196">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="5a06c-197">Bu çok sayıda küçük test sınıflarında olur, ancak her test ne sorumlu olduğu son derece Temizle sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a06c-197">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="5a06c-198">Sınıfı ve test edilecek yöntem tanımlamak üzere ayarlanan sahte test sınıfı adıyla test yönteminin adı, test edilen davranışını belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-198">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="5a06c-199">Bu, Beklenen davranış ve giriş veya bu davranışı yield varsayımlar içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-199">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="5a06c-200">Bazı örnek test adları:</span><span class="sxs-lookup"><span data-stu-id="5a06c-200">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="5a06c-201">Bu yaklaşımın bir değişim her test sınıfı adı "Gerekir" ile biten ve şimdiki biraz değiştirir:</span><span class="sxs-lookup"><span data-stu-id="5a06c-201">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="5a06c-202">`CatalogControllerGetImage`**Gereken**`.`**çağırın**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="5a06c-202">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="5a06c-203">`CatalogControllerGetImage`**Gereken**`.`**günlüğü**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="5a06c-203">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="5a06c-204">İkinci adlandırma yaklaşım daha net, bazı ekipler bulabilirsiniz ancak biraz daha ayrıntılı.</span><span class="sxs-lookup"><span data-stu-id="5a06c-204">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="5a06c-205">Herhangi bir durumda, bir veya daha fazla test başarısız olduğunda, hangi durumlarda başarısız olmuş adlarını belirgin olması test davranış sağlayan bir adlandırma kuralını kullanmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="5a06c-205">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="5a06c-206">Bu değer, test sonuçlarında gördüğünüzde sunar gibi testler ControllerTests.Test1 gibi vaguely, adlandırma kaçının.</span><span class="sxs-lookup"><span data-stu-id="5a06c-206">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="5a06c-207">Birçok küçük test sınıfları, yukarıdaki üretir gibi bir adlandırma kuralını izler, ek klasörleri ve ad alanlarını kullanarak testlerinizi düzenlemek için iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-207">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="5a06c-208">Şekil 9-4 birkaç test projesi içinde klasöre göre testlerin düzenlenmesi için bir yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-208">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="5a06c-209">**Şekil 9-4.**</span><span class="sxs-lookup"><span data-stu-id="5a06c-209">**Figure 9-4.**</span></span> <span data-ttu-id="5a06c-210">Test edilen sınıfına göre klasöre göre test sınıflarında düzenleme.</span><span class="sxs-lookup"><span data-stu-id="5a06c-210">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="5a06c-211">Elbette, belirli uygulama sınıfı sınanan birçok yöntem vardır (ve bu nedenle çoğu test sınıflarına değilse), bu uygulama sınıfına karşılık gelen bir klasöre yerleştirmek için mantıklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-211">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="5a06c-212">Bu kuruluş nasıl dosyaları başka bir yerde klasörler halinde düzenlediğiniz farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-212">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="5a06c-213">En fazla üç varsa veya dört ilgili çok sayıda dosya içeren bir klasördeki dosyaları genellikle bunları kendi alt klasöre taşımak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-213">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="5a06c-214">Birim testi ASP.NET Core uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a06c-214">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="5a06c-215">İyi tasarlanmış bir ASP.NET Core uygulaması birçok karmaşıklığı ve iş mantığı iş varlıklarını ve Hizmetleri çeşitli kapsüllenmiş.</span><span class="sxs-lookup"><span data-stu-id="5a06c-215">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="5a06c-216">ASP.NET Core MVC uygulama içinden denetleyicileri, filtreler, viewmodel'lar ve görünümler ile çok az sayıda birim testleri istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-216">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="5a06c-217">Belirli bir eylemi işlevselliğinin bir eylem yönteminin kendisi dışında arasındadır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-217">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="5a06c-218">Etkin bir birim testini yönlendirme düzgün çalışıp çalışmadığını test edilmesi veya genel hata işleme yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-218">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="5a06c-219">Benzer şekilde, tüm model doğrulama ve kimlik doğrulama dahil olmak üzere, filtreleri ve yetkilendirme filtrelerini olamaz birim test.</span><span class="sxs-lookup"><span data-stu-id="5a06c-219">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="5a06c-220">Bu davranışı kaynakları olmadan çoğu eylem yöntemleri bunları kullanan denetleyicinin bağımsız test edilebilir hizmetlere çalışmalarının toplu temsilci olarak görevlendirme basit bir şekilde küçük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-220">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="5a06c-221">Bazen, birim testi için kodunuzda sipariş yeniden düzenlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-221">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="5a06c-222">Bu sık soyutlama tanımlama ve test etmek istediğiniz kod soyutlama erişmek için bağımlılık ekleme kullanılarak yerine doğrudan karşı altyapı kodları yazmasına içerir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-222">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="5a06c-223">Örneğin, resimleri görüntülemek için bu basit bir eylem yöntemine göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5a06c-223">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="5a06c-224">Birim testi bu yöntem, dosya sisteminden okumak için kullandığı System.IO.File doğrudan bağımlı tarafından zor olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-224">Unit testing this method is made difficult by its direct dependency on System.IO.File, which it uses to read from the file system.</span></span> <span data-ttu-id="5a06c-225">Bu davranış, beklendiği gibi çalışır, ancak gerçek dosyalarıyla bunu bir tümleştirme testini olduğundan emin olmak için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-225">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="5a06c-226">Birim yapamazsınız hatalarının ayıklanabileceğini belirtmekte yarar bu yöntemin rota test – işlevsel bir testi ile kısa bir süre sonra bunun nasıl yapılacağını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-226">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="5a06c-227">Birim testi dosya sistemi davranışını doğrudan olamaz ve rota test edilemez, var. test etmek için nedir?</span><span class="sxs-lookup"><span data-stu-id="5a06c-227">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="5a06c-228">De birim testi mümkün hale getirmek için yeniden düzenleme sonra bazı test çalışmaları ve hata işleme gibi eksik bir davranışı fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-228">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="5a06c-229">Bir dosya bulunamadığında, yöntem ne yapar?</span><span class="sxs-lookup"><span data-stu-id="5a06c-229">What does the method do when a file isn't found?</span></span> <span data-ttu-id="5a06c-230">Neler?</span><span class="sxs-lookup"><span data-stu-id="5a06c-230">What should it do?</span></span> <span data-ttu-id="5a06c-231">Bu örnekte, işlenmiş yöntemi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="5a06c-231">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="5a06c-232">\_Günlükçü ve \_Imageservice hem de eklenmiş bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="5a06c-232">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="5a06c-233">Eylem yöntemine geçirilen aynı kimliği geçirilecek test artık \_Imageservice, ve sonuçta elde edilen bayt FileResult bir parçası olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5a06c-233">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="5a06c-234">Ayrıca hata günlüğünü beklendiği gibi oluyor ve görüntü yoksa bir NotFound sonuç döndürülür bu önemli uygulamanın davranış (diğer bir deyişle, yalnızca geçici kodu bir sorunu tanılamak için eklenen Geliştirici) olduğunu varsayarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-234">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="5a06c-235">Gerçek dosya mantığı ayrı uygulama hizmetinde taşınmıştır ve bir uygulamaya özgü özel eksik dosya durumu için döndürülecek büyütülmüştür.</span><span class="sxs-lookup"><span data-stu-id="5a06c-235">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="5a06c-236">Bir tümleştirme testini kullanarak bu uygulama bağımsız olarak, test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-236">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="5a06c-237">Çoğu durumda, mantık miktarını en düşük bu nedenle denetleyicilerinizi ve büyük olasılıkla birim testi değer genel özel durum işleyicilerini kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-237">In most cases, you’ll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="5a06c-238">Denetleyici eylemleri işlevsel testler kullanarak test çoğu yapmanız gerekir ve `TestServer` aşağıda açıklanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5a06c-238">You should do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="5a06c-239">Tümleştirme testi ASP.NET Core uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a06c-239">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="5a06c-240">ASP.NET Core uygulamalarınızı tümleştirme testleri çoğunu, hizmetler ve altyapı projenizde tanımlanan diğer uygulama türleri test.</span><span class="sxs-lookup"><span data-stu-id="5a06c-240">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="5a06c-241">ASP.NET Core MVC projenize doğru mu davrandığı, test etmek için en iyi bir test ana bilgisayarı çalışan uygulamanızı çalıştırmanızı işlevsel testleri yoludur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-241">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span> <span data-ttu-id="5a06c-242">Bu bölümde daha önce tümleştirme testi bölümündeki bir tümleştirme testini bir veri erişim sınıfın bir örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-242">An example of an integration test of a data access class is shown in the Integration Testing section earlier in this chapter.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="5a06c-243">İşlevsel test ASP.NET Core uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a06c-243">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="5a06c-244">ASP.NET Core uygulamaları için `TestServer` sınıfı işlevsel testleri yazmak oldukça kolay kılar.</span><span class="sxs-lookup"><span data-stu-id="5a06c-244">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="5a06c-245">Yapılandırdığınız bir `TestServer` kullanarak bir `WebHostBuilder` doğrudan (normalde, uygulamanız için yaptığınız gibi), veya `WebApplicationFactory` türü (2.1 sürümünden itibaren kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="5a06c-245">You configure a `TestServer` using a `WebHostBuilder` directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="5a06c-246">Testlerinizi uygulamayı üretim ortamında neler yapabileceği için benzer bir davranış alıştırma şekilde, test ana bilgisayarı, üretim barındırmak için mümkün olduğunca yakın bir şekilde eşleşecek şekilde denemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-246">You should try to match your test host to your production host as closely as possible, so your tests will exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="5a06c-247">`WebApplicationFactory` Sınıfı ile ASP.NET Core görünümleri gibi statik kaynak bulmak için kullanılan TestServer'ın ContentRoot yapılandırmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-247">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="5a06c-248">Basit işlevsel testler IClassFixture uygulayan bir test sınıfı oluşturarak oluşturabileceğiniz\<WebApplicationFactory\<TEntry >> TEntry, web uygulamanızın başlangıç sınıfı olduğu.</span><span class="sxs-lookup"><span data-stu-id="5a06c-248">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="5a06c-249">Bu yerinde fabrikasının CreateClient yöntemini kullanarak bir istemci, test düzeni oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a06c-249">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

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

<span data-ttu-id="5a06c-250">Genellikle, bir bellek içi kullanmak için uygulamayı yapılandırma gibi her bir testi çalıştırmadan önce bazı ek yapılandırmalar sitenizin gerçekleştirmek isteyebilirsiniz veri deposuna ve daha sonra uygulama test verileri ile dengeli dağıtım.</span><span class="sxs-lookup"><span data-stu-id="5a06c-250">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="5a06c-251">Bunu yapmak için kendi alt WebApplicationFactory oluşturmalısınız\<TEntry > ve onun ConfigureWebHost yöntemi yok sayın.</span><span class="sxs-lookup"><span data-stu-id="5a06c-251">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="5a06c-252">Aşağıdaki örnekte eShopOnWeb FunctionalTests projeden ve testleri ana web uygulamasında bir parçası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-252">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

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

<span data-ttu-id="5a06c-253">Testler bu özel WebApplicationFactory, bunu bir istemci oluşturmak için kullanarak ve ardından bu istemci örneği kullanarak uygulamaya istekleri yapabilen yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a06c-253">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="5a06c-254">Uygulama, onaylamalar testin bir parçası olarak kullanılan çekirdek değeri oluşturulmuş veri sahip olur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-254">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="5a06c-255">Şu test doğrular: eShopOnWeb uygulama ana sayfası düzgün şekilde yüklenir ve çekirdek veri parçası olarak uygulamaya eklenen ürün listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-255">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

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

<span data-ttu-id="5a06c-256">Bu işlevsel test tam ASP.NET Core MVC sınayan / Razor sayfaları, tüm ara yazılım, filtreler, bağlayıcıları, yerinde olabilir vb. dahil olmak üzere uygulama yığını.</span><span class="sxs-lookup"><span data-stu-id="5a06c-256">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="5a06c-257">Belirli bir yol ("/") beklenen başarılı durum kodu ve HTML çıktı döndürür doğrular.</span><span class="sxs-lookup"><span data-stu-id="5a06c-257">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="5a06c-258">Gerçek bir web sunucusu ayarını olmadan bunu yapar ve bu nedenle, gerçek bir Web sunucusu test etmek için (örneğin, güvenlik duvarı ayarları ile ilgili sorunlar) oluşabilir brittleness çoğunu ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-258">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="5a06c-259">TestServer karşı çalışan işlevsel testleri genellikle tümleştirme ve birim testleri yavaş ancak ağ üzerinden bir test web sunucusuna çalıştıracağınız testleri hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a06c-259">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="5a06c-260">İşlevsel testleri, uygulamanızın ön uç yığın beklendiği gibi çalıştığından emin olmak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a06c-260">You should use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="5a06c-261">Bu testler, sayfalar ve filtreler ekleyerek çoğaltma adres ya da çoğaltma denetleyicilerinizi içinde bulmak özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="5a06c-261">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="5a06c-262">İdeal olarak, bu yeniden düzenleme, uygulama davranışını değiştirmez ve işlevsel testleri paketi bu durumda doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="5a06c-262">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5a06c-263">[Önceki](work-with-data-in-asp-net-core-apps.md)
>[İleri](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="5a06c-263">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
