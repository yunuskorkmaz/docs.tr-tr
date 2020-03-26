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
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="158f5-103">Core MVC uygulamalarını test ASP.NET</span><span class="sxs-lookup"><span data-stu-id="158f5-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="158f5-104">*"Ürününüzü birim olarak test etmek istemiyorsanız, büyük olasılıkla müşterileriniz de bunu test etmek hoşlanmaz."*</span><span class="sxs-lookup"><span data-stu-id="158f5-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="158f5-105">\_- Anonim-</span><span class="sxs-lookup"><span data-stu-id="158f5-105">\_- Anonymous-</span></span>

<span data-ttu-id="158f5-106">Herhangi bir karmaşıklık yazılım değişikliklere yanıt olarak beklenmedik şekillerde başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="158f5-107">Bu nedenle, değişiklik yaptıktan sonra test etmek, en önemsiz (veya en az kritik) uygulamalar hariç herkes için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="158f5-108">El ile sınama, yazılımı test etmek için en yavaş, en az güvenilir, en pahalı yoludur.</span><span class="sxs-lookup"><span data-stu-id="158f5-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="158f5-109">Ne yazık ki, uygulamalar test edilebilir olacak şekilde tasarlanmıyorsa, kullanılabilir tek araç bu olabilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="158f5-110">[4. bölümde](architectural-principles.md) belirtilen mimari ilkelere uygun olarak yazılan başvurular ünite test edilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="158f5-111">ASP.NET Core uygulamaları otomatik tümleştirme ve işlevsel testleri destekler.</span><span class="sxs-lookup"><span data-stu-id="158f5-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="158f5-112">Otomatik test türleri</span><span class="sxs-lookup"><span data-stu-id="158f5-112">Kinds of automated tests</span></span>

<span data-ttu-id="158f5-113">Yazılım uygulamaları için birçok türde otomatik test vardır.</span><span class="sxs-lookup"><span data-stu-id="158f5-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="158f5-114">En basit, en düşük seviye testi birim testidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="158f5-115">Biraz daha yüksek bir düzeyde, entegrasyon testleri ve fonksiyonel testler vardır.</span><span class="sxs-lookup"><span data-stu-id="158f5-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="158f5-116">UI testleri, yükleme testleri, stres testleri ve duman testleri gibi diğer test türleri bu belgenin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="158f5-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="158f5-117">Birim testleri</span><span class="sxs-lookup"><span data-stu-id="158f5-117">Unit tests</span></span>

<span data-ttu-id="158f5-118">Birim testi, uygulamanızın mantığının tek bir parçasını sınar.</span><span class="sxs-lookup"><span data-stu-id="158f5-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="158f5-119">Bir daha bazı şeyler değil listeleyerek açıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="158f5-120">Birim testi, kodunuzu bağımlılıklarla veya altyapıyla nasıl çalıştığını test etmez , bu tümleştirme testlerinin ne işe yaradığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="158f5-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="158f5-121">Birim testi, kodunuzu yazdığınızdaki çerçeveyi sınamaz – çalıştığını varsaymalısınız veya işe yaramazsa hata dosyalayın ve geçici bir çözüm kodlayın.</span><span class="sxs-lookup"><span data-stu-id="158f5-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="158f5-122">Bir birim testi tamamen bellekte ve işlemde çalışır.</span><span class="sxs-lookup"><span data-stu-id="158f5-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="158f5-123">Dosya sistemi, ağ veya veritabanı ile iletişim kurmaz.</span><span class="sxs-lookup"><span data-stu-id="158f5-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="158f5-124">Birim testleri yalnızca kodunuzu test etmelidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="158f5-125">Birim testleri, kodunuzu yalnızca tek bir birim test gerçeği nedeniyle, hiçbir dış bağımlılıkları ile, son derece hızlı bir şekilde yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="158f5-126">Böylece, birkaç saniye içinde birim testleri yüzlerce test paketleri çalıştırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="158f5-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="158f5-127">Bunları sık sık, ideal olarak paylaşılan bir kaynak denetim deposuna her itmeden önce ve kesinlikle yapı sunucunuzdaki her otomatik yapıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="158f5-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="158f5-128">Tümleştirme testleri</span><span class="sxs-lookup"><span data-stu-id="158f5-128">Integration tests</span></span>

<span data-ttu-id="158f5-129">Veritabanları ve dosya sistemleri gibi altyapıyla etkileşimde bulunarak kodunuzu kapsüllemek iyi bir fikir olsa da, bu kodun bir kısmına sahip olmaya devam edecektir ve büyük olasılıkla bunu sınamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="158f5-130">Ayrıca, uygulamanızın bağımlılıkları tam olarak çözüldüğünde kodlarınızın katmanlarının beklediğiniz şekilde etkileşimde olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="158f5-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="158f5-131">Bu entegrasyon testlerinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="158f5-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="158f5-132">Tümleştirme testleri genellikle dış bağımlılıklara ve altyapıya bağlı olduğundan, birim testlerinden daha yavaş ve kurulumu daha zor olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="158f5-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="158f5-133">Bu nedenle, tümleştirme testlerinde birim testleri ile test edilebilir şeyleri test kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="158f5-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="158f5-134">Belirli bir senaryoyu bir birim testi ile sınayabilirseniz, bunu bir birim testi ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="158f5-135">Eğer yapamazsanız, o zaman bir tümleştirme testi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="158f5-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="158f5-136">Tümleştirme testleri genellikle birim testlerinden daha karmaşık kurulum ve yıkma yordamlarına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="158f5-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="158f5-137">Örneğin, gerçek bir veritabanına karşı olan bir tümleştirme sınaması, veritabanını her test çalıştırmadan önce bilinen bir duruma döndürmenin bir yolunu niçin gerekir.</span><span class="sxs-lookup"><span data-stu-id="158f5-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="158f5-138">Yeni testler eklendikçe ve üretim veritabanı şeması geliştikçe, bu test komut dosyaları boyut ve karmaşıklık olarak büyüme eğiliminde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="158f5-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="158f5-139">Birçok büyük sistemde, paylaşılan kaynak denetimindeki değişiklikleri denetlemeden önce geliştirici iş istasyonlarında tam tümleştirme testleri çalıştırmak pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="158f5-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="158f5-140">Bu gibi durumlarda, tümleştirme testleri bir yapı sunucusunda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="158f5-141">Fonksiyonel testler</span><span class="sxs-lookup"><span data-stu-id="158f5-141">Functional tests</span></span>

<span data-ttu-id="158f5-142">Tümleştirme testleri, sistemin bazı bileşenlerinin birlikte doğru çalıştığını doğrulamak için geliştiricinin perspektifinden yazılır.</span><span class="sxs-lookup"><span data-stu-id="158f5-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="158f5-143">İşlevsel testler kullanıcının bakış açısından yazılır ve gereksinimlerine göre sistemin doğruluğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="158f5-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="158f5-144">Aşağıdaki alıntı, birim testleri ile karşılaştırıldığında, fonksiyonel testler hakkında düşünmek için yararlı bir benzetme sunuyor:</span><span class="sxs-lookup"><span data-stu-id="158f5-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="158f5-145">"Birçok kez bir sistemin geliştirilmesi bir evin inşasına benzetilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="158f5-146">Bu benzetme tam olarak doğru olmasa da, ünite ve fonksiyonel testler arasındaki farkı anlamak amacıyla genişletebiliriz.</span><span class="sxs-lookup"><span data-stu-id="158f5-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="158f5-147">Birim testi, bir binanın şantiyesini ziyaret eden bir yapı denetçisine benzer.</span><span class="sxs-lookup"><span data-stu-id="158f5-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="158f5-148">O evin çeşitli iç sistemleri üzerinde durulmaktadır, vakıf, çerçeveleme, elektrik, sıhhi tesisat, ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="158f5-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="158f5-149">Evin parçalarının doğru ve güvenli bir şekilde çalışmasını, yani bina kodunu karşılamasını sağlar (testler).</span><span class="sxs-lookup"><span data-stu-id="158f5-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="158f5-150">Bu senaryoda fonksiyonel testler ev sahibi bu aynı şantiye ziyaret benzer.</span><span class="sxs-lookup"><span data-stu-id="158f5-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="158f5-151">İç sistemlerin uygun şekilde işkuracağını, yapı denetçisinin görevini yerine getireceğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="158f5-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="158f5-152">Ev sahibi bu evde yaşamanın nasıl bir şey olacağına odaklanmış durumda.</span><span class="sxs-lookup"><span data-stu-id="158f5-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="158f5-153">O evin nasıl göründüğünü ile ilgilidir, çeşitli odalar rahat bir boyut, evin ailenin ihtiyaçlarına uygun mu, sabah güneşi yakalamak için iyi bir noktada pencereler vardır.</span><span class="sxs-lookup"><span data-stu-id="158f5-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="158f5-154">Ev sahibi evde fonksiyonel testler yapıyor.</span><span class="sxs-lookup"><span data-stu-id="158f5-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="158f5-155">Kullanıcının bakış açısına sahip.</span><span class="sxs-lookup"><span data-stu-id="158f5-155">He has the user's perspective.</span></span> <span data-ttu-id="158f5-156">Yapı denetçisi evde birim testleri yapıyor.</span><span class="sxs-lookup"><span data-stu-id="158f5-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="158f5-157">O, inşaatçının bakış açısına sahip."</span><span class="sxs-lookup"><span data-stu-id="158f5-157">He has the builder's perspective."</span></span>

<span data-ttu-id="158f5-158">Kaynak: [Ünite Testi ve Fonksiyonel Testler](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="158f5-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="158f5-159">"Geliştiriciler olarak, iki şekilde başarısız oluruz: ya yanlış bir şey yaparız, ya da yanlış bir şey yaparız."</span><span class="sxs-lookup"><span data-stu-id="158f5-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="158f5-160">Birim testleri, doğru bir şey inşa emin olun; fonksiyonel testler doğru şeyi oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="158f5-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="158f5-161">İşlevsel testler sistem düzeyinde çalıştığı için, bir dereceye kadar UI otomasyonu gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="158f5-162">Entegrasyon testleri gibi, genellikle bir tür test altyapısıyla da çalışırlar.</span><span class="sxs-lookup"><span data-stu-id="158f5-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="158f5-163">Bu onları birim ve tümleştirme testlerinden daha yavaş ve daha kırılgan hale getirir.</span><span class="sxs-lookup"><span data-stu-id="158f5-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="158f5-164">Sistemin kullanıcıların beklediği gibi davrandığından emin olmak için gereken kadar işlevsel teste sahip olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="158f5-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="158f5-165">Test Piramidi</span><span class="sxs-lookup"><span data-stu-id="158f5-165">Testing Pyramid</span></span>

<span data-ttu-id="158f5-166">Martin Fowler test piramidi hakkında yazdı, bunun bir örneği Şekil 9-1'de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="158f5-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![Test Piramidi](./media/image9-1.png)

<span data-ttu-id="158f5-168">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="158f5-168">**Figure 9-1**.</span></span> <span data-ttu-id="158f5-169">Test Piramidi</span><span class="sxs-lookup"><span data-stu-id="158f5-169">Testing Pyramid</span></span>

<span data-ttu-id="158f5-170">Piramidin farklı katmanları ve bunların göreli boyutları, farklı türde testleri ve uygulamanız için kaç tane yazmanız gerektiğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="158f5-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="158f5-171">Gördüğünüz gibi, öneri, daha küçük bir tümleştirme testi katmanı tarafından desteklenen ve daha da küçük bir işlevsel test katmanıyla birlikte büyük bir birim testi tabanına sahip olmaktır.</span><span class="sxs-lookup"><span data-stu-id="158f5-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="158f5-172">Her katman ideal olarak sadece yeterli bir alt katmanda gerçekleştirilemez testler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="158f5-173">Belirli bir senaryo için hangi test türüne ihtiyacınız olduğuna karar vermeye çalışırken test piramidini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="158f5-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="158f5-174">Ne test etmek</span><span class="sxs-lookup"><span data-stu-id="158f5-174">What to test</span></span>

<span data-ttu-id="158f5-175">Otomatik testler yazma konusunda deneyimsiz geliştiriciler için ortak bir sorun ne test etmek için geliyor.</span><span class="sxs-lookup"><span data-stu-id="158f5-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="158f5-176">İyi bir başlangıç noktası koşullu mantığı test etmektir.</span><span class="sxs-lookup"><span data-stu-id="158f5-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="158f5-177">Koşullu bir ifadeye (if-else, switch, vb.) dayalı olarak değişen davranışiçeren bir yöntemin olduğu her yerde, belirli koşullar için doğru davranışı onaylayan en az birkaç test bulabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="158f5-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="158f5-178">Kodunuzda hata koşulları varsa, kod üzerinden "mutlu yol" için en az bir test (hatasız) ve uygulamanızın hatalar karşısında beklendiği gibi şekilde şekilde olduğunu doğrulamak için "üzücü yol" (hatalar veya atipik sonuçlarla) için en az bir test yazmak iyidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="158f5-179">Son olarak, kod kapsamı gibi ölçümlere odaklanmak yerine başarısız olabilecek şeyleri sınamaya odaklanın.</span><span class="sxs-lookup"><span data-stu-id="158f5-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="158f5-180">Daha fazla kod kapsamı genellikle, daha az daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="158f5-181">Ancak, karmaşık ve iş açısından kritik bir yöntemin birkaç test daha yazma genellikle sadece test kodu kapsama ölçümleri geliştirmek için otomatik özellikleri için testler yazma daha zaman daha iyi bir kullanımıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="158f5-182">Test projelerinin düzenlenmesi</span><span class="sxs-lookup"><span data-stu-id="158f5-182">Organizing test projects</span></span>

<span data-ttu-id="158f5-183">Test projeleri ancak sizin için en iyi çalışır organize edilebilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="158f5-184">Testleri türüne (birim testi, tümleştirme testi) ve test ettikleri şeye (projeye göre, ad alanına göre) ayırmak iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="158f5-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="158f5-185">Bu ayırmanın tek bir test projesi içindeki klasörlerden veya birden çok test projesinden oluşup oluşmadığı bir tasarım kararıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="158f5-186">Bir proje en basittir, ancak birçok teste sahip büyük projeler de veya farklı test kümelerini daha kolay çalıştırmak için birkaç farklı test projesine sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="158f5-187">Birçok ekip test projelerini test ettikleri projeye göre düzenler, bu da birkaç projeden fazla olan uygulamalar için çok sayıda test projesine neden olabilir, özellikle de bunları her projede ne tür testlerolduğuna göre yıkıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="158f5-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="158f5-188">Uzlaşmacı bir yaklaşım, test projelerinin içindeki klasörlerin test (ve sınıf) test edildiğini belirtmek için uygulama başına bir tür teste sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="158f5-189">Yaygın bir yaklaşım bir 'src' klasörü altında uygulama projeleri düzenlemek ve paralel bir 'testler' klasörü altında uygulamanın test projeleri.</span><span class="sxs-lookup"><span data-stu-id="158f5-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="158f5-190">Bu organizasyonu yararlı bulursanız, Visual Studio'da eşleşen çözüm klasörleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![Çözümünüzde test organizasyonu](./media/image9-2.png)

<span data-ttu-id="158f5-192">**Şekil 9-2**.</span><span class="sxs-lookup"><span data-stu-id="158f5-192">**Figure 9-2**.</span></span> <span data-ttu-id="158f5-193">Çözümünüzde test organizasyonu</span><span class="sxs-lookup"><span data-stu-id="158f5-193">Test organization in your solution</span></span>

<span data-ttu-id="158f5-194">Hangi test çerçevesini tercih ederseniz o labilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="158f5-195">xUnit çerçevesi iyi çalışır ve tüm ASP.NET Core ve EF Core testlerinin yazıldığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="158f5-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="158f5-196">Şekil 9-3'te gösterilen şablonu kullanarak Visual Studio'da veya CLI'den `dotnet new xunit`xUnit test projesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![Visual Studio'da xUnit Test Projesi Ekleme](./media/image9-3.png)

<span data-ttu-id="158f5-198">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="158f5-198">**Figure 9-3**.</span></span> <span data-ttu-id="158f5-199">Visual Studio'da xUnit Test Projesi Ekleme</span><span class="sxs-lookup"><span data-stu-id="158f5-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="158f5-200">Test adlandırma</span><span class="sxs-lookup"><span data-stu-id="158f5-200">Test naming</span></span>

<span data-ttu-id="158f5-201">Testlerinizi, her testin ne yaptığını gösteren adlarla tutarlı bir şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="158f5-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="158f5-202">Ben büyük bir başarı elde ettik bir yaklaşım sınıf ve yöntem test göre test sınıfları isim etmektir.</span><span class="sxs-lookup"><span data-stu-id="158f5-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="158f5-203">Bu, birçok küçük test sınıfına neden olur, ancak her testin ne sorumlusu olduğunu son derece açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="158f5-203">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="158f5-204">Test sınıfı adı sınıf ve test edilecek yöntemi tanımlamak için ayarlanmış, test yöntemi adı test edilen davranışı belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-204">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="158f5-205">Bu beklenen davranışı ve bu davranışı verim gereken herhangi bir girdi veya varsayımlar içermelidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-205">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="158f5-206">Bazı örnek test adları:</span><span class="sxs-lookup"><span data-stu-id="158f5-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="158f5-207">Bu yaklaşımın bir varyasyonu her test sınıfı adını "Should" ile bitirir ve zamanı biraz değiştirir:</span><span class="sxs-lookup"><span data-stu-id="158f5-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="158f5-208">`CatalogControllerGetImage`**Aramalı**`.`**Call**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="158f5-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="158f5-209">`CatalogControllerGetImage`**Oturum**`.`**Açmalı**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="158f5-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="158f5-210">Bazı takımlar ikinci adlandırma yaklaşımını daha net bulurlar, ancak biraz daha ayrıntılıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="158f5-211">Her durumda, bir veya daha fazla test başarısız olduğunda, hangi durumlarda başarısız olduğu adlarından belli olacak şekilde, test davranışı hakkında bilgi sağlayan bir adlandırma kuralı kullanmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="158f5-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="158f5-212">Test sonuçlarını gördüğünüzde hiçbir değer sunamadığınız için, Testlerinizi ControllerTests.Test1 gibi belirsiz bir şekilde adlandırmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="158f5-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="158f5-213">Yukarıdaki gibi birçok küçük test sınıfı üreten bir adlandırma kuralını izlerseniz, klasörleri ve ad boşluklarını kullanarak testlerinizi daha da düzenlemek iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="158f5-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="158f5-214">Şekil 9-4, çeşitli test projeleri içinde testleri klasöre göre düzenlemeye bir yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="158f5-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![Test sınıflarını test edilen sınıfa göre klasöre göre düzenleme](./media/image9-4.png)

<span data-ttu-id="158f5-216">**Şekil 9-4.**</span><span class="sxs-lookup"><span data-stu-id="158f5-216">**Figure 9-4.**</span></span> <span data-ttu-id="158f5-217">Test sınıflarını test edilen sınıfa göre klasöre göre düzenleme.</span><span class="sxs-lookup"><span data-stu-id="158f5-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="158f5-218">Belirli bir uygulama sınıfının test edilen birçok yöntemi (ve dolayısıyla birçok test sınıfı) varsa, bunları uygulama sınıfına karşılık gelen bir klasöre yerleştirmek mantıklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="158f5-219">Bu kuruluş, dosyaları başka bir yerde klasörlere nasıl düzenleyebileceğinizdir.</span><span class="sxs-lookup"><span data-stu-id="158f5-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="158f5-220">Başka birçok dosya içeren bir klasörde üç veya dörtten fazla ilgili dosya nız varsa, bunları kendi alt klasörlerine taşımak genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="158f5-221">Core uygulamaları ASP.NET birim testi</span><span class="sxs-lookup"><span data-stu-id="158f5-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="158f5-222">İyi tasarlanmış bir ASP.NET Core uygulamasında, karmaşıklık ve iş mantığının çoğu iş varlıklarında ve çeşitli hizmetlerde kapsüllenecektir.</span><span class="sxs-lookup"><span data-stu-id="158f5-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="158f5-223">ASP.NET Core MVC uygulamasının kendisi, denetleyicileri, filtreleri, görüntüleme modelleri ve görünümleri ile çok az birim testi gerektirmelidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="158f5-224">Belirli bir eylemin işlevselliğinin çoğu eylem yönteminin dışındadır.</span><span class="sxs-lookup"><span data-stu-id="158f5-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="158f5-225">Yönlendirmenin doğru çalışıp çalışmadığını veya genel hata işlemenin bir birim testi ile etkili bir şekilde yapılamayacağını test etmek.</span><span class="sxs-lookup"><span data-stu-id="158f5-225">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="158f5-226">Aynı şekilde, model doğrulama, kimlik doğrulama ve yetkilendirme filtreleri de dahil olmak üzere tüm filtreler, denetleyicinin eylem yöntemini hedefleyen bir testle birim test edilemez.</span><span class="sxs-lookup"><span data-stu-id="158f5-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="158f5-227">Bu davranış kaynakları olmadan, çoğu eylem yöntemi önemsiz derecede küçük olmalı ve çalışmalarının büyük bir kısmını, bunları kullanan denetleyiciden bağımsız olarak sınanabilecek hizmetlere devretilmelidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="158f5-228">Bazen birimi test etmek için kodunuzu yeniden düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="158f5-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="158f5-229">Sık sık bu soyutlamaları tanımlamak ve doğrudan altyapıya karşı kodlama yerine, test etmek istediğiniz koddaki soyutlama erişmek için bağımlılık enjeksiyonu kullanarak içerir.</span><span class="sxs-lookup"><span data-stu-id="158f5-229">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="158f5-230">Örneğin, görüntüleri görüntülemek için bu basit eylem yöntemini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="158f5-230">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="158f5-231">Birim testi bu yöntem, dosya sisteminden `System.IO.File`okumak için kullandığı doğrudan bağımlılığı ile zorlanır.</span><span class="sxs-lookup"><span data-stu-id="158f5-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="158f5-232">Beklendiği gibi çalıştığından emin olmak için bu davranışı sınayabilirsiniz, ancak bunu gerçek dosyalarla yapmak bir tümleştirme testidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="158f5-233">Bu yöntemin rotasını birim olarak test edemezsiniz – bunu kısa süre içinde işlevsel bir testle nasıl yapacağınızı göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-233">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="158f5-234">Dosya sistemi davranışını doğrudan birim olarak test edemezseniz ve rotayı test edemezseniz, sınamak için ne var?</span><span class="sxs-lookup"><span data-stu-id="158f5-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="158f5-235">Birim sınamamümkün kılmak için yeniden düzenleme yaptıktan sonra, bazı test örnekleri ve hata işleme gibi eksik davranışları keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="158f5-236">Bir dosya bulunamıyorsa yöntem ne yapar?</span><span class="sxs-lookup"><span data-stu-id="158f5-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="158f5-237">Ne yapmalı?</span><span class="sxs-lookup"><span data-stu-id="158f5-237">What should it do?</span></span> <span data-ttu-id="158f5-238">Bu örnekte, yeniden düzenleme yöntemi aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="158f5-238">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="158f5-239">`_logger`ve `_imageService` her ikisi de bağımlılık olarak enjekte edilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="158f5-240">Artık, eylem yöntemine geçirilen aynı kimliğin `_imageService`,'e geçirildiğini ve elde edilen baytların FileResult'ın bir parçası olarak döndürülderken" test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="158f5-241">Ayrıca, hata günlüğe kaydetmenin beklendiği gibi `NotFound` gerçekleştiğini ve görüntü eksikse, bunun önemli bir uygulama davranışı olduğunu varsayarak bir sonucun döndürüldürün (diğer bir zamanda geliştiricinin bir sorunu tanılamak için eklenen geçici kodu değil) test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="158f5-242">Gerçek dosya mantığı ayrı bir uygulama hizmetine taşındı ve eksik bir dosya örneği için uygulamaya özgü bir özel durum döndürmek için artırıldı.</span><span class="sxs-lookup"><span data-stu-id="158f5-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="158f5-243">Bu uygulamayı bir tümleştirme sınama kullanarak bağımsız olarak sınatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="158f5-244">Çoğu durumda, denetleyicilerinizde genel özel durum işleyicileri kullanmak isteyeceksiniz, bu nedenle bu durumda mantık miktarı en az düzeyde olmalı ve büyük olasılıkla birim sınamaya değmez.</span><span class="sxs-lookup"><span data-stu-id="158f5-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="158f5-245">İşlevsel testleri ve aşağıda açıklanan `TestServer` sınıfı kullanarak denetleyici eylemleri test çoğu yapın.</span><span class="sxs-lookup"><span data-stu-id="158f5-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="158f5-246">Core uygulamaları ASP.NET entegrasyon testi</span><span class="sxs-lookup"><span data-stu-id="158f5-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="158f5-247">ASP.NET Core uygulamalarınızdaki tümleştirme testlerinin çoğu, Altyapı projenizde tanımlanan hizmetleri ve diğer uygulama türlerini test etmelidir.</span><span class="sxs-lookup"><span data-stu-id="158f5-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="158f5-248">Örneğin, EF Core'un Altyapı projesinde bulunan veri erişim sınıflarınızdan [beklediğiniz verileri başarıyla güncelleştirip aldığınızı test](https://docs.microsoft.com/ef/core/miscellaneous/testing/) edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="158f5-249">ASP.NET Core MVC projenizin doğru davrandığını test etmenin en iyi yolu, uygulamanız için bir test ana bilgisayarında çalışan işlevsel testlerdir.</span><span class="sxs-lookup"><span data-stu-id="158f5-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="158f5-250">Core uygulamaları ASP.NET işlevsel test</span><span class="sxs-lookup"><span data-stu-id="158f5-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="158f5-251">ASP.NET Core uygulamaları `TestServer` için, sınıf işlevsel testleri yazmayı oldukça kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="158f5-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="158f5-252">Doğrudan (uygulamanız `WebHostBuilder` için `HostBuilder`yaptığınız gibi) veya `WebApplicationFactory` tür (sürüm 2.1'den beri kullanılabilir) kullanarak bir `TestServer` (veya ) kullanarak yapılandırAbilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="158f5-253">Test ana bilgisayarınızın üretim ana tonunu mümkün olduğunca yakından eşleştirmeye çalışın, böylece testlerinizin uygulamanın üretimde yapacağına benzer davranışlar sergilemesi.</span><span class="sxs-lookup"><span data-stu-id="158f5-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="158f5-254">Sınıf, `WebApplicationFactory` ASP.NET Core tarafından Görünümler gibi statik kaynağı bulmak için kullanılan TestServer'ın ContentRoot'unu yapılandırmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="158f5-255">TEntry web uygulamanızın Başlangıç sınıfı olduğu>> IClassFixture\<\<WebApplicationFactory TEntry uygulayan bir test sınıfı oluşturarak basit işlevsel testler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158f5-255">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="158f5-256">Bu durumda, test fikstürfabrikanın CreateClient yöntemini kullanarak bir istemci oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="158f5-256">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

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

<span data-ttu-id="158f5-257">Sık sık, her test çalışmadan önce sitenizin bazı ek yapılandırma gerçekleştirmek isteyeceksiniz (örneğin, bellek veri deposunda bir uygulama kullanmak için uygulama yapılandırma ve daha sonra test verileri ile uygulama tohumlama.</span><span class="sxs-lookup"><span data-stu-id="158f5-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="158f5-258">Bunu yapmak için, WebApplicationFactory\<TEntry> kendi alt sınıf oluşturmanız ve YapılandırmaWebHost yöntemini geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="158f5-258">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="158f5-259">Aşağıdaki örnek eShopOnWeb FunctionalTests projesinden ve ana web uygulaması üzerinde testlerin bir parçası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="158f5-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

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

<span data-ttu-id="158f5-260">Testler, bir istemci oluşturmak için kullanarak ve daha sonra bu istemci örneğini kullanarak uygulamaya istekte bulunarak bu özel WebApplicationFactory'den yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="158f5-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="158f5-261">Uygulama, testin iddialarının bir parçası olarak kullanılabilecek verilere sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="158f5-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="158f5-262">Aşağıdaki test, eShopOnWeb uygulamasının ana sayfasının doğru yüklenir ve tohum verilerinin bir parçası olarak uygulamaya eklenen bir ürün listesi içerir doğrular.</span><span class="sxs-lookup"><span data-stu-id="158f5-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

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

<span data-ttu-id="158f5-263">Bu işlevsel test, tüm ara yazılımlar, filtreler, bağlayıcılar, vb yerinde olabilir dahil olmak üzere core mvc / Razor Pages uygulama yığını, tam ASP.NET egzersizleri.</span><span class="sxs-lookup"><span data-stu-id="158f5-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="158f5-264">Belirli bir rotanın ("/") beklenen başarı durum kodunu ve HTML çıktısını döndürür doğrular.</span><span class="sxs-lookup"><span data-stu-id="158f5-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="158f5-265">Bunu gerçek bir web sunucusu kurmadan yapar ve bu nedenle test etmek için gerçek bir web sunucusu kullanarak (örneğin, güvenlik duvarı ayarları ile ilgili sorunlar) karşılaşabileceğiniz kırılganlık çok önler.</span><span class="sxs-lookup"><span data-stu-id="158f5-265">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="158f5-266">TestServer'a karşı çalışan işlevsel testler genellikle tümleştirme ve birim testlerinden daha yavaş, ancak ağ üzerinden bir test web sunucusuna çalışacak testlerden çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="158f5-267">Uygulamanızın ön uç yığınının beklendiği gibi çalıştığından emin olmak için işlevsel testler kullanın.</span><span class="sxs-lookup"><span data-stu-id="158f5-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="158f5-268">Bu testler, denetleyicilerinizde veya sayfalarınızda yineleme bulduğunuzda ve filtreler ekleyerek yinelemeyi ele aldığınızda özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="158f5-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="158f5-269">İdeal olarak, bu yeniden düzenleme uygulamanın davranışını değiştirmez ve bir dizi işlevsel test bunun böyle olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="158f5-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="158f5-270">Referanslar – Test ASP.NET Core MVC uygulamaları</span><span class="sxs-lookup"><span data-stu-id="158f5-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="158f5-271">**ASP.NET Core'da Test** </span><span class="sxs-lookup"><span data-stu-id="158f5-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="158f5-272">**Ünite Test Adlandırma Sözleşmesi** </span><span class="sxs-lookup"><span data-stu-id="158f5-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="158f5-273">**EF Çekirdeğini Test Etme** </span><span class="sxs-lookup"><span data-stu-id="158f5-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="158f5-274">**ASP.NET Core'da entegrasyon testleri** </span><span class="sxs-lookup"><span data-stu-id="158f5-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="158f5-275">[Önceki](work-with-data-in-asp-net-core-apps.md)
>[Sonraki](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="158f5-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
