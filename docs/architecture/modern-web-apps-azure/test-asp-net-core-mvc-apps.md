---
title: MVC uygulamalarını test ASP.NET Core
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın MVC uygulamalarını test ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 6096bd3aa35a27c97862089d09d537bdc5b1fff0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971538"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="47279-103">MVC uygulamalarını test ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="47279-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="47279-104">*"Ürününüzün birim testini beğenmezseniz, büyük olasılıkla müşterileriniz test etmek zorunda kalmaz."*</span><span class="sxs-lookup"><span data-stu-id="47279-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="47279-105">\_-anonim-</span><span class="sxs-lookup"><span data-stu-id="47279-105">\_- Anonymous-</span></span>

<span data-ttu-id="47279-106">Herhangi bir karmaşıklığın yazılımı, değişikliklere yanıt olarak beklenmedik yollarla başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="47279-107">Bu nedenle, en önemsiz (veya en az kritik) uygulamalar için değişiklik yaptıktan sonra test edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="47279-108">El ile test etme, yazılımın test edilmesine yönelik en yavaş ve en ucuz yoldur.</span><span class="sxs-lookup"><span data-stu-id="47279-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="47279-109">Ne yazık ki, uygulamalar test edilebilir olacak şekilde tasarlanmamışsa, kullanılabilir tek yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="47279-110">[Bölüm 4](architectural-principles.md) ' te bulunan mimari ilkeleri takip eden bir şekilde yazılan uygulamalar Unit test edilmelidir ve ASP.NET Core uygulamalar otomatik tümleştirme ve işlevsel testi de destekler.</span><span class="sxs-lookup"><span data-stu-id="47279-110">Applications written following the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="47279-111">Otomatikleştirilmiş test türleri</span><span class="sxs-lookup"><span data-stu-id="47279-111">Kinds of automated tests</span></span>

<span data-ttu-id="47279-112">Yazılım uygulamaları için birçok tür otomatikleştirilmiş test vardır.</span><span class="sxs-lookup"><span data-stu-id="47279-112">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="47279-113">En basit, en düşük düzey test birim sınamadır.</span><span class="sxs-lookup"><span data-stu-id="47279-113">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="47279-114">Daha yüksek bir düzeyde, tümleştirme testleri ve işlevsel testler vardır.</span><span class="sxs-lookup"><span data-stu-id="47279-114">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="47279-115">UI testleri, yük testleri, stres testleri ve duman testleri gibi diğer test türleri, bu belgenin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="47279-115">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="47279-116">Birim testleri</span><span class="sxs-lookup"><span data-stu-id="47279-116">Unit tests</span></span>

<span data-ttu-id="47279-117">Birim testi, uygulamanızın mantığının tek bir kısmını sınar.</span><span class="sxs-lookup"><span data-stu-id="47279-117">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="47279-118">Bu, olmadığı bazı şeyleri listeleyerek daha ayrıntılı bir şekilde açıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-118">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="47279-119">Birim testi, kodunuzun bağımlılıklarla veya altyapıyla nasıl çalıştığını test etmez. Bu, tümleştirme sınamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-119">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="47279-120">Bir birim testi, kodunuzun yazıldığı çerçeveyi test etmez; Bunun çalıştığını varsaymalı veya buldıysanız, bir hata dosyaz ve bir geçici çözüm kodlayın.</span><span class="sxs-lookup"><span data-stu-id="47279-120">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="47279-121">Birim testi tamamen bellekte ve işlemde çalışır.</span><span class="sxs-lookup"><span data-stu-id="47279-121">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="47279-122">Dosya sistemi, ağ veya veritabanıyla iletişim kurmaz.</span><span class="sxs-lookup"><span data-stu-id="47279-122">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="47279-123">Birim testleri yalnızca kodunuzu test etmelidir.</span><span class="sxs-lookup"><span data-stu-id="47279-123">Unit tests should only test your code.</span></span>

<span data-ttu-id="47279-124">Birim testleri, dış bağımlılıklar olmadan yalnızca kodunuzun tek bir birimini test ettikleri ve çok hızlı bir şekilde yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-124">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="47279-125">Bu nedenle, birkaç saniye içinde yüzlerce birim testinin test paketlerini çalıştırabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-125">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="47279-126">Her bir paylaşılan kaynak denetimi deposuna her gönderim yapmadan önce ve yapı sunucunuzdaki her bir otomatik derleme ile, bunları sık sık çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="47279-126">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="47279-127">Tümleştirme testleri</span><span class="sxs-lookup"><span data-stu-id="47279-127">Integration tests</span></span>

<span data-ttu-id="47279-128">Veritabanları ve dosya sistemleri gibi altyapıyla etkileşim kuran kodunuzu kapsüllemek iyi bir fikir olsa da, bu kodun bir kısmını yine de test etmek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-128">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="47279-129">Ayrıca, uygulamanızın bağımlılıkları tamamen çözümlendiğinde kodunuzun katmanlarınızın bekledikleri gibi etkileşimde bulunduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-129">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="47279-130">Bu, tümleştirme testlerinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="47279-130">This is the responsibility of integration tests.</span></span> <span data-ttu-id="47279-131">Genellikle dış bağımlılıklara ve altyapıya bağlı olduklarından, tümleştirme testlerinin daha yavaş ve birim testlerinin ayarlanmasından daha zor olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="47279-131">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="47279-132">Bu nedenle, tümleştirme testlerinde birim testleriyle test edilmiş şeyleri test etmeyi önönüne almalısınız.</span><span class="sxs-lookup"><span data-stu-id="47279-132">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="47279-133">Belirli bir senaryoyu birim testi ile test edebilirsiniz, onu bir birim testiyle test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-133">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="47279-134">Bu durumda, bir tümleştirme testi kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="47279-134">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="47279-135">Tümleştirme testlerinde genellikle birim testlerinden daha karmaşık kurulum ve Teari yordamları olur.</span><span class="sxs-lookup"><span data-stu-id="47279-135">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="47279-136">Örneğin, gerçek bir veritabanına yönelik bir tümleştirme testi, her test çalıştırılmadan önce veritabanını bilinen bir duruma döndürmek için bir yönteme ihtiyaç duyar.</span><span class="sxs-lookup"><span data-stu-id="47279-136">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="47279-137">Yeni testler eklendikçe ve üretim veritabanı şeması geliştikçe, bu test betikleri boyut ve karmaşıklık bakımından büyümeye eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="47279-137">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="47279-138">Birçok büyük sistemde, paylaşılan kaynak denetimi değişikliklerini iade etmeden önce, geliştirici iş istasyonlarında tümleştirme testlerinin tam paketlerinin çalıştırılabilmesi pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="47279-138">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="47279-139">Bu durumlarda, tümleştirme testleri bir yapı sunucusu üzerinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-139">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="47279-140">İşlevsel testler</span><span class="sxs-lookup"><span data-stu-id="47279-140">Functional tests</span></span>

<span data-ttu-id="47279-141">Tümleştirme testleri, sistemin bazı bileşenlerinin birlikte düzgün çalıştığını doğrulamak için, geliştiricinin perspektifinden yazılır.</span><span class="sxs-lookup"><span data-stu-id="47279-141">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="47279-142">İşlevsel testler kullanıcının perspektifinden yazılır ve gereksinimlerine göre sistemin doğruluğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="47279-142">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="47279-143">Aşağıdaki alıntıda, birim testlerine kıyasla işlevsel testlerin nasıl düşündüğleriyle ilgili yararlı bir benzerleme vurguladı sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="47279-143">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="47279-144">"Bir sistemin geliştirilmesi birçok kez bir evin oluşturulmasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="47279-144">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="47279-145">Bu benzerleme vurguladı oldukça doğru olmasa da, birim ve işlev testleri arasındaki farkı anlamak amacıyla onu genişletebiliriz.</span><span class="sxs-lookup"><span data-stu-id="47279-145">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="47279-146">Birim testi, evin yapım sitesini ziyaret eden bir yapı denetçisine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="47279-146">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="47279-147">BT, temel, çerçevelendirme, elektrik, sıhhi tesisat gibi çeşitli iç sistemlere odaklanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="47279-147">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="47279-148">Evin bölümlerinin doğru ve güvenli şekilde çalışmasını sağlar (testler) ve derleme kodunu karşılayın.</span><span class="sxs-lookup"><span data-stu-id="47279-148">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="47279-149">Bu senaryodaki işlevsel testler, aynı yapı sitesini ziyaret eden Homeowner 'a benzerdir.</span><span class="sxs-lookup"><span data-stu-id="47279-149">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="47279-150">İç sistemlerin uygun şekilde davrandığını varsayar, derleme denetçisi görevini gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="47279-150">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="47279-151">Homeowner, bu evinizde ne kadar canlı hale görüneceğine odaklanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="47279-151">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="47279-152">Evin nasıl göründüğü, çeşitli odaların rahat bir boyut olduğu konusunda endişe duymaktadır, evin aile ihtiyaçlarına uyum sağlaması, Windows 'un sabah güneyi yakalamak için iyi bir nokta halinde.</span><span class="sxs-lookup"><span data-stu-id="47279-152">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="47279-153">Homeowner, evinizde işlevsel testler gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="47279-153">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="47279-154">Kullanıcının perspektifi vardır.</span><span class="sxs-lookup"><span data-stu-id="47279-154">He has the user's perspective.</span></span> <span data-ttu-id="47279-155">Yapı denetçisi, evinizde birim testlerini gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="47279-155">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="47279-156">Oluşturucunun perspektifi vardır. "</span><span class="sxs-lookup"><span data-stu-id="47279-156">He has the builder's perspective."</span></span>

<span data-ttu-id="47279-157">Kaynak: [birim testi ve Işlev testlerine karşı](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="47279-157">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="47279-158">"Geliştirici olarak" geliştirici olarak söyliyoruz, iki şekilde başarısız oldu: bir şeyi yanlış oluşturacağız veya yanlış bir şey oluşturacağız. "</span><span class="sxs-lookup"><span data-stu-id="47279-158">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="47279-159">Birim testleri, şeyi doğru bir şekilde oluşturduğunuzu güvence altına alarak, işlevsel sınamalar, doğru şeyi oluşturduğunuzdan emin olmanızı sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="47279-159">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="47279-160">İşlevsel testler sistem düzeyinde çalıştığından, bazı Kullanıcı Arabirimi Otomasyonu gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="47279-160">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="47279-161">Tümleştirme testlerine benzer şekilde, genellikle bir tür test altyapısıyla da çalışırlar.</span><span class="sxs-lookup"><span data-stu-id="47279-161">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="47279-162">Bu, birim ve tümleştirme sınamalarından daha yavaş ve daha Brittle sağlar.</span><span class="sxs-lookup"><span data-stu-id="47279-162">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="47279-163">Sistemin kullanıcıların beklediği şekilde davranmakta olduğundan emin olmanız gerektiği için yalnızca birçok işlevsel teste sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-163">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="47279-164">Piramit test ediliyor</span><span class="sxs-lookup"><span data-stu-id="47279-164">Testing Pyramid</span></span>

<span data-ttu-id="47279-165">Marwler, Şekil 9-1 ' de gösterilen bir örnek olan test piramit hakkında yazdı.</span><span class="sxs-lookup"><span data-stu-id="47279-165">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![Piramit test ediliyor](./media/image9-1.png)

<span data-ttu-id="47279-167">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="47279-167">**Figure 9-1**.</span></span> <span data-ttu-id="47279-168">Piramit test ediliyor</span><span class="sxs-lookup"><span data-stu-id="47279-168">Testing Pyramid</span></span>

<span data-ttu-id="47279-169">Piramit 'in farklı katmanları ve bunların göreli boyutları, farklı test türlerini ve uygulamanız için kaç tane yazmanız gerektiğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="47279-169">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="47279-170">Görebileceğiniz gibi, öneri, daha küçük bir tümleştirme testi katmanı tarafından desteklenen, daha küçük bir işlevsel test katmanı ile desteklenen, büyük miktarda birim testi olan bir temeldir.</span><span class="sxs-lookup"><span data-stu-id="47279-170">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="47279-171">Her katmanın ideal olması için yalnızca daha düşük bir katmanda yeterince gerçekleştirilemediği testlerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-171">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="47279-172">Belirli bir senaryo için hangi tür teste ihtiyacınız olduğuna karar verirken, testi piramit ' i göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="47279-172">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="47279-173">Test edilecek</span><span class="sxs-lookup"><span data-stu-id="47279-173">What to test</span></span>

<span data-ttu-id="47279-174">Otomatikleştirilmiş testler yazma konusunda deneyimli geliştiriciler için sık karşılaşılan bir sorun test edilecek.</span><span class="sxs-lookup"><span data-stu-id="47279-174">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="47279-175">İyi bir başlangıç noktası, koşullu mantığı test etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47279-175">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="47279-176">Bir koşullu ifadeye (If-Else, Switch, vb.) göre değişen davranışlardan herhangi bir yerde, belirli koşullarda doğru davranışı onaylamak için en az birkaç test sunabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-176">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="47279-177">Kodunuzun hata koşulları varsa, kod aracılığıyla "mutlu yol" için en az bir test yazmak iyi olur (hata olmadan) ve uygulamanın hata durumunda beklendiği gibi davrandığını doğrulamak için en az bir test (hata olmadan) ve "Sad yol" (hatalar veya tipik sonuçlar içeren)</span><span class="sxs-lookup"><span data-stu-id="47279-177">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="47279-178">Son olarak, kod kapsamı gibi ölçümlere odaklanmak yerine başarısız olan test işlemleri üzerinde odaklanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="47279-178">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="47279-179">Daha fazla kod kapsamı, genellikle daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="47279-179">More code coverage is better than less, generally.</span></span> <span data-ttu-id="47279-180">Ancak, çok karmaşık ve iş açısından kritik bir yöntemin birkaç testini yazmak genellikle test kod kapsamı ölçümlerini geliştirmek üzere otomatik özellikler için testlerin yazılmasından daha iyi bir zaman kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="47279-180">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="47279-181">Test projelerini düzenleme</span><span class="sxs-lookup"><span data-stu-id="47279-181">Organizing test projects</span></span>

<span data-ttu-id="47279-182">Test projeleri düzenlenebilir, ancak sizin için en iyi şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-182">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="47279-183">Testleri türe (birim testi, tümleştirme testi) ve test ettikleri öğeleri (projeye göre, ad alanına göre) ayırmak iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="47279-183">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="47279-184">Bu ayırmaların tek bir test projesi veya birden çok test projesi içindeki klasörlerden oluşan bir tasarım kararı olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="47279-184">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="47279-185">Bir proje en basit, ancak birçok test içeren büyük projeler için veya farklı test kümelerini daha kolay çalıştırmak için, farklı test projelerine sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-185">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="47279-186">Birçok ekip test projelerini test ettikleri projeye göre düzenler, ancak bu, birkaç projeden daha fazla projeye sahip olan uygulamalar çok sayıda test projesine neden olabilir, ancak bu, özellikle de her projede ne tür testlerin ne olduğuna göre bunları daha düşük bir şekilde kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-186">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="47279-187">Bir riskli yaklaşım, test projeleri içindeki her bir proje (ve sınıfı) test edilen bir proje (ve sınıf) belirtmek için bir proje türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-187">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="47279-188">Ortak bir yaklaşım, bir ' src ' klasörü altında uygulama projelerini ve uygulamanın test projelerini paralel bir ' test ' klasörü altında düzenlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="47279-188">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="47279-189">Bu kuruluşu kullanışlı buldıysanız, Visual Studio 'da eşleşen çözüm klasörleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-189">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![Çözümünüzde test organizasyonu](./media/image9-2.png)

<span data-ttu-id="47279-191">**Şekil 9-2**.</span><span class="sxs-lookup"><span data-stu-id="47279-191">**Figure 9-2**.</span></span> <span data-ttu-id="47279-192">Çözümünüzde test organizasyonu</span><span class="sxs-lookup"><span data-stu-id="47279-192">Test organization in your solution</span></span>

<span data-ttu-id="47279-193">Tercih ettiğiniz test çerçevesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-193">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="47279-194">XUnit çerçevesi iyi çalışmaktadır ve tüm ASP.NET Core ve EF Core testlerin yazıldığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="47279-194">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="47279-195">Şekil 9-3 ' de gösterilen şablonu kullanarak Visual Studio 'da bir xUnit test projesi veya DotNet New xUnit kullanarak CLı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-195">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![Visual Studio 'da bir xUnit test projesi ekleme](./media/image9-3.png)

<span data-ttu-id="47279-197">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="47279-197">**Figure 9-3**.</span></span> <span data-ttu-id="47279-198">Visual Studio 'da bir xUnit test projesi ekleme</span><span class="sxs-lookup"><span data-stu-id="47279-198">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="47279-199">Test adlandırma</span><span class="sxs-lookup"><span data-stu-id="47279-199">Test naming</span></span>

<span data-ttu-id="47279-200">Her testin ne yaptığını belirten adlarla, testlerinizi tutarlı bir biçimde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="47279-200">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="47279-201">İle harika bir yaklaşım, test sınıflarını test ettikleri sınıfa ve yönteme göre adlandırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-201">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="47279-202">Bu, birçok küçük test sınıfı ile sonuçlanır, ancak her bir testin sorumlu olduğu son derece net hale getirir.</span><span class="sxs-lookup"><span data-stu-id="47279-202">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="47279-203">Test sınıfı adı, sınanacak sınıfı ve yöntemi belirlemek üzere ayarlandığında, test yöntemi adı test edilen davranışı belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-203">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="47279-204">Bu, beklenen davranışı ve bu davranışı gerektiren tüm giriş veya varsayımları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="47279-204">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="47279-205">Bazı örnek test adları:</span><span class="sxs-lookup"><span data-stu-id="47279-205">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="47279-206">Bu yaklaşımın bir çeşitlemesi, her bir test sınıfı adını "olmalıdır" ile sonlandırır ve zaman hali hafifçe değiştirir:</span><span class="sxs-lookup"><span data-stu-id="47279-206">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="47279-207">`CatalogControllerGetImage` **çağrısı**`.``ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="47279-207">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="47279-208">`CatalogControllerGetImage` **`.`** **günlük**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="47279-208">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="47279-209">Bazı takımlar ikinci adlandırma yaklaşımını daha net, ancak biraz daha ayrıntılı bir şekilde bulur.</span><span class="sxs-lookup"><span data-stu-id="47279-209">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="47279-210">Herhangi bir durumda, test davranışına Öngörüler sağlayan bir adlandırma kuralı kullanmayı deneyin, böylece bir veya daha fazla testin başarısız olması durumunda, bazı durumlarda kendi adlarından belirgin olur.</span><span class="sxs-lookup"><span data-stu-id="47279-210">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="47279-211">Bu teklif, test sonuçlarında gördüğünüz zaman hiçbir değer olmadığı için, ControllerTests. test1 gibi testlerin bir şekilde adlandırılmasını önleyin.</span><span class="sxs-lookup"><span data-stu-id="47279-211">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="47279-212">Yukarıdaki gibi birçok küçük test sınıfı üreten bir adlandırma kuralını izlerseniz, testlerinizi klasörler ve ad alanları kullanarak daha fazla düzenlemek iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="47279-212">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="47279-213">Şekil 9-4, birkaç test projesi içindeki testleri klasöre göre düzenlemek için bir yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="47279-213">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![Test sınıflarını, sınanmakta olan sınıfa göre klasöre göre düzenleme](./media/image9-4.png)

<span data-ttu-id="47279-215">**Şekil 9-4.**</span><span class="sxs-lookup"><span data-stu-id="47279-215">**Figure 9-4.**</span></span> <span data-ttu-id="47279-216">Test sınıflarını, sınanmakta olan sınıfa göre klasöre göre düzenleme.</span><span class="sxs-lookup"><span data-stu-id="47279-216">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="47279-217">Kuşkusuz, belirli bir uygulama sınıfının test edilmekte olan çok sayıda yöntemi (ve bu nedenle birçok test sınıfı) varsa, bunları uygulama sınıfına karşılık gelen bir klasöre yerleştirmek mantıklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-217">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="47279-218">Bu kuruluş, dosyaları başka bir yerde farklı şekilde düzenlemenize göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="47279-218">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="47279-219">Birçok başka dosya içeren bir klasörde üçten fazla veya dört ilişkili dosya varsa, bunları kendi alt klasörüne taşımak genellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="47279-219">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="47279-220">Uygulamalar ASP.NET Core birim testi</span><span class="sxs-lookup"><span data-stu-id="47279-220">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="47279-221">İyi tasarlanmış bir ASP.NET Core uygulamasında, karmaşıklık ve iş mantığının çoğu iş varlıklarında ve çeşitli hizmetlerde kapsüllenir.</span><span class="sxs-lookup"><span data-stu-id="47279-221">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="47279-222">ASP.NET Core MVC uygulamasının kendisi, denetleyiciler, filtreler, viewmodeller ve görünümleriyle, çok az sayıda birim testi gerektirmelidir.</span><span class="sxs-lookup"><span data-stu-id="47279-222">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="47279-223">Belirli bir eylemin işlevselliğinin çoğu eylem yönteminin dışında kalıyor.</span><span class="sxs-lookup"><span data-stu-id="47279-223">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="47279-224">Yönlendirmenin doğru şekilde çalışıp çalışmadığını test etme veya küresel hata işleme, birim testi ile etkin bir şekilde yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="47279-224">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="47279-225">Benzer şekilde, model doğrulama ve kimlik doğrulama ve Yetkilendirme filtreleri dahil olmak üzere herhangi bir filtre de birim test edilemez.</span><span class="sxs-lookup"><span data-stu-id="47279-225">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="47279-226">Bu davranış kaynakları olmadan, çoğu eylem yöntemi, bunları kullanan denetleyiciden bağımsız olarak test edilebilir hizmetler için çalışmanın toplu olarak küçük olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-226">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="47279-227">Bazen kodunuzu birim test etmek için yeniden düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-227">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="47279-228">Genellikle bu, soyutlamaları tanımlamayı ve doğrudan altyapıya yönelik olarak kodlamak yerine test etmek istediğiniz koddaki soyutlamadan erişmek için bağımlılık ekleme kullanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="47279-228">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="47279-229">Örneğin, görüntüleri görüntülemek için bu basit eylem yöntemini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="47279-229">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="47279-230">Birim testi bu yöntemin, dosya sisteminden okumak için kullandığı `System.IO.File`doğrudan bağımlılığı tarafından güçleşir.</span><span class="sxs-lookup"><span data-stu-id="47279-230">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="47279-231">Beklendiği gibi çalıştığından emin olmak için bu davranışı test edebilirsiniz, ancak bunu gerçek dosyalarla yapmak bir tümleştirme testi olur.</span><span class="sxs-lookup"><span data-stu-id="47279-231">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="47279-232">Bu yöntemin yolunu birim testi yapamıyoruz. Bu, kısa bir süre içinde bunu nasıl yapacağım hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-232">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="47279-233">Dosya sistemi davranışını doğrudan birim testi yapamıyoruz ve yolu sınayamıyoruz, ne test etmek istiyorsunuz?</span><span class="sxs-lookup"><span data-stu-id="47279-233">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="47279-234">Ayrıca, birim testi yapmak için yeniden düzenleme yapıldıktan sonra, bazı test çalışmalarını ve hata işleme gibi eksik davranışları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-234">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="47279-235">Bir dosya bulunamadığında Yöntem ne yapar?</span><span class="sxs-lookup"><span data-stu-id="47279-235">What does the method do when a file isn't found?</span></span> <span data-ttu-id="47279-236">Ne yapmalıyım?</span><span class="sxs-lookup"><span data-stu-id="47279-236">What should it do?</span></span> <span data-ttu-id="47279-237">Bu örnekte, yeniden düzenlenmiş yöntemi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="47279-237">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="47279-238">\_günlükçüsü ve \_ımageservice, her ikisi de bağımlılıklar olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="47279-238">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="47279-239">Artık eylem yöntemine geçirilen aynı kimliğin \_ımageservice 'e geçtiğini ve sonuçta elde edilen baytların FileResult 'nin bir parçası olarak döndürüldüğünü test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-239">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="47279-240">Ayrıca, hata günlüğü 'nün beklenen şekilde olduğunu ve görüntü eksikse bir NotFound sonucunun döndürüldüğünü, bunun önemli uygulama davranışı olduğunu (yani, bir sorunu tanılamak için geliştiricinin eklediği geçici bir kod değil) kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-240">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="47279-241">Gerçek dosya mantığı ayrı bir uygulama hizmetine taşındı ve eksik bir dosya olması durumunda uygulamaya özel bir özel durum döndürecek şekilde geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="47279-241">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="47279-242">Bu uygulamayı bir tümleştirme testi kullanarak bağımsız olarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-242">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="47279-243">Çoğu durumda, denetleyicilerinizde genel özel durum işleyicilerini kullanmak isteyeceksiniz. bu nedenle, içindeki mantık miktarı minimum ve büyük olasılıkla birim testi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-243">In most cases, you’ll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="47279-244">İşlev testlerini ve aşağıda açıklanan `TestServer` sınıfını kullanarak, denetleyici eylemlerinin büyük bir kısmını test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-244">You should do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="47279-245">Tümleştirme testi ASP.NET Core uygulamalar</span><span class="sxs-lookup"><span data-stu-id="47279-245">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="47279-246">ASP.NET Core uygulamalarınızın çoğu tümleştirme testi, altyapı projenizde tanımlanmış test hizmetleri ve diğer uygulama türleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-246">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="47279-247">Örneğin, EF Core altyapı projesinde bulunan veri erişim sınıflarınızda [beklediğinizi ve verileri başarıyla güncelleştirdiğini test](https://docs.microsoft.com/ef/core/miscellaneous/testing/) edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-247">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="47279-248">ASP.NET Core MVC projenizin doğru şekilde davrandığının en iyi yolu, bir test ana bilgisayarında çalışan uygulamanıza karşı çalıştırılan işlevsel testlerdir.</span><span class="sxs-lookup"><span data-stu-id="47279-248">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="47279-249">Uygulamalar ASP.NET Core işlevsel test</span><span class="sxs-lookup"><span data-stu-id="47279-249">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="47279-250">ASP.NET Core uygulamalar için `TestServer` sınıfı, işlevsel testleri yazma konusunda oldukça kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="47279-250">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="47279-251">Bir `TestServer` doğrudan (uygulamanız için yaptığınız gibi) veya `WebApplicationFactory` türüyle (2,1 sürümünden itibaren kullanılabilir) `WebHostBuilder` kullanarak yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-251">You configure a `TestServer` using a `WebHostBuilder` directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="47279-252">Test ana bilgisayarınızı üretim konağınız için mümkün olduğunca yakından eşleştirmeye çalışmalısınız, bu sayede testleriniz, uygulamanın üretimde ne yapacaklarına benzer davranışlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="47279-252">You should try to match your test host to your production host as closely as possible, so your tests will exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="47279-253">`WebApplicationFactory` sınıfı, TestServer 'ın, görünümler gibi statik kaynağı bulmak için ASP.NET Core tarafından kullanılan ContentRoot 'yi yapılandırmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-253">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="47279-254">Issfixture\<WebApplicationFactory\<TEntry > > uygulayan bir test sınıfı oluşturarak (TEntry Web uygulamanızın başlangıç sınıfı olduğunda) basit işlevsel testler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47279-254">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="47279-255">Bu şekilde, test armatürü, fabrika 'nin CreateClient metodunu kullanarak bir istemci oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="47279-255">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

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

<span data-ttu-id="47279-256">Genellikle, her bir test çalıştırılmadan önce sitenizin bazı ek yapılandırmalarını gerçekleştirmek isteyeceksiniz; Örneğin, uygulamayı bellek içi veri deposu kullanacak şekilde yapılandırma ve ardından uygulamayı test verileriyle sağlama.</span><span class="sxs-lookup"><span data-stu-id="47279-256">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="47279-257">Bunu yapmak için, WebApplicationFactory\<TEntry > kendi alt sınıfını oluşturmanız ve ConfigureWebHost metodunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-257">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="47279-258">Aşağıdaki örnek eShopOnWeb FunctionalTests projesinden ve ana Web uygulamasındaki testlerin bir parçası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47279-258">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

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

<span data-ttu-id="47279-259">Testler, bu özel WebApplicationFactory 'yi kullanarak bir istemci oluşturup bu istemci örneğini kullanarak uygulamaya istekler yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="47279-259">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="47279-260">Uygulamanın, test onaylamaları kapsamında kullanılabilecek verileri, çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="47279-260">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="47279-261">Aşağıdaki test, eShopOnWeb uygulamasının giriş sayfasının doğru şekilde yüklendiğini doğrular ve tohum verilerinin bir parçası olarak uygulamaya eklenen bir ürün listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="47279-261">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

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

<span data-ttu-id="47279-262">Bu fonksiyonel test, bir bütün ara yazılım, filtre, cilt, vb. dahil olmak üzere tam ASP.NET Core MVC/Razor Pages uygulama yığınını uygular.</span><span class="sxs-lookup"><span data-stu-id="47279-262">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="47279-263">Belirli bir yolun ("/") beklenen başarı durum kodunu ve HTML çıkışını döndürdüğünü doğrular.</span><span class="sxs-lookup"><span data-stu-id="47279-263">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="47279-264">Bu, gerçek bir Web sunucusu ayarlamadan ve bu sayede, test için gerçek bir Web sunucusu kullanan brittın büyük bölümünü önler (örneğin, Güvenlik Duvarı ayarlarıyla ilgili sorunlar).</span><span class="sxs-lookup"><span data-stu-id="47279-264">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="47279-265">TestServer 'a karşı çalışan işlevsel testler genellikle tümleştirme ve birim testlerinden daha yavaştır, ancak ağ üzerinden bir test Web sunucusuna çalışacak testlerden çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-265">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="47279-266">Uygulamanızın ön uç yığınının beklendiği gibi çalıştığından emin olmak için işlevsel testler kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47279-266">You should use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="47279-267">Bu sınamalar, denetleyicilerde veya sayfalarınızda yineleme bulduğunuzda ve filtreler ekleyerek yinelemeyi adresleyerek özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="47279-267">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="47279-268">İdeal olarak, bu yeniden düzenleme uygulamanın davranışını değiştirmez ve işlevsel testlerin bir paketi bu durumun olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="47279-268">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="47279-269">Başvurular – test ASP.NET Core MVC uygulamaları</span><span class="sxs-lookup"><span data-stu-id="47279-269">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="47279-270">**ASP.NET Core \ test etme**</span><span class="sxs-lookup"><span data-stu-id="47279-270">**Testing in ASP.NET Core** \</span></span>
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="47279-271">**Birim testi adlandırma kuralı** </span><span class="sxs-lookup"><span data-stu-id="47279-271">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="47279-272">**Test EF Core** </span><span class="sxs-lookup"><span data-stu-id="47279-272">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="47279-273">**ASP.NET Core \ tümleştirme testleri**</span><span class="sxs-lookup"><span data-stu-id="47279-273">**Integration tests in ASP.NET Core** \</span></span>
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>
> - <span data-ttu-id="47279-274">**ASP.net Community-15 Mayıs, 2018-Javier C. Nelson-YouTube videosu Ile MVC testi**</span><span class="sxs-lookup"><span data-stu-id="47279-274">**ASP.NET Community Standup - May 15, 2018 - MVC Testing with Javier C. Nelson** - YouTube video \</span></span>
>   <https://www.youtube.com/watch?v=wtOE-xmFJkw&list=PL1rZQsJPBU2StolNg0aqvQswETPcYnNKL&index=5>

>[!div class="step-by-step"]
><span data-ttu-id="47279-275">[Önceki](work-with-data-in-asp-net-core-apps.md)
>[İleri](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="47279-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
