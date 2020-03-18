---
title: Birim testleri yazmak için en iyi uygulamalar
description: .NET Core ve .NET Standard projeleri için kod kalitesini ve esnekliğini artıran birim testleri yazmak için en iyi uygulamaları öğrenin.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 586373381bcb18384cbf29bb2ca2bd220a2b2d3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240967"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="9c02c-103">.NET Core ve .NET Standard ile en iyi uygulamaları test etme birimi</span><span class="sxs-lookup"><span data-stu-id="9c02c-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="9c02c-104">Birim testleri yazmanın sayısız faydası vardır; gerilemeye yardımcı olurlar, dokümantasyon sağlarlar ve iyi tasarımı kolaylaştırırlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="9c02c-105">Ancak, okunması zor ve kırılgan birim testleri kod tabanınızda hasara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="9c02c-106">Bu makalede, .NET Core ve .NET Standard projeleriniz için birim test tasarımıyla ilgili en iyi bazı uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="9c02c-107">Bu kılavuzda, testlerinizi esnek ve kolay anlaşılır tutmak için birim testleri yazarken bazı en iyi uygulamaları öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="9c02c-108">John [Reese](https://reese.dev) tarafından [Roy Osherove](https://osherove.com/) için özel teşekkür</span><span class="sxs-lookup"><span data-stu-id="9c02c-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="9c02c-109">Neden birim testi?</span><span class="sxs-lookup"><span data-stu-id="9c02c-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="9c02c-110">İşlevsel testler gerçekleştirmede daha az zaman</span><span class="sxs-lookup"><span data-stu-id="9c02c-110">Less time performing functional tests</span></span>
<span data-ttu-id="9c02c-111">Fonksiyonel testler pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-111">Functional tests are expensive.</span></span> <span data-ttu-id="9c02c-112">Bunlar genellikle uygulamayı açmayı ve beklenen davranışı doğrulamak için sizin (veya başka birinin) izlemesi gereken bir dizi adımı gerçekleştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="9c02c-113">Bu adımlar her zaman test eden tarafından bilinmeyebilir, bu da testi gerçekleştirmek için bölgede daha bilgili birine ulaşmaları gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="9c02c-114">Test in kendisi önemsiz değişiklikler için saniyeler, daha büyük değişiklikler için dakikalar sürebilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="9c02c-115">Son olarak, bu işlem sistemde yaptığınız her değişiklik için yinelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="9c02c-116">Birim testleri, diğer taraftan, milisaniye sürebilir, bir düğmeye basarak çalıştırılabilir ve mutlaka büyük sistem herhangi bir bilgi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="9c02c-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="9c02c-117">Testin geçip geçmediği tek tek değil, test koşucusudur.</span><span class="sxs-lookup"><span data-stu-id="9c02c-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="9c02c-118">Regresyona karşı koruma</span><span class="sxs-lookup"><span data-stu-id="9c02c-118">Protection against regression</span></span>
<span data-ttu-id="9c02c-119">Regresyon kusurları, uygulamada değişiklik yapıldığında ortaya çıkan kusurlardır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="9c02c-120">Test edenlerin, daha önce uygulanan özelliklerin beklendiği gibi çalıştığını doğrulamak için yalnızca yeni özelliklerini değil, önceden var olan özellikleri de sınaması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="9c02c-121">Birim testi ile, her yapıdan sonra veya hatta bir kod satırını değiştirdikten sonra tüm test paketinizi yeniden çalıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9c02c-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="9c02c-122">Yeni kodunuzu varolan işlevselliği bozmaz güven verir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="9c02c-123">Çalıştırılabilir belgeler</span><span class="sxs-lookup"><span data-stu-id="9c02c-123">Executable documentation</span></span>
<span data-ttu-id="9c02c-124">Belirli bir yöntemin ne yaptığı veya belirli bir girdi verildiğinde nasıl çalıştığı her zaman açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="9c02c-125">Kendinize sorabilirsiniz: Boş bir dize geçersem bu yöntem nasıl olur?</span><span class="sxs-lookup"><span data-stu-id="9c02c-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="9c02c-126">Null?</span><span class="sxs-lookup"><span data-stu-id="9c02c-126">Null?</span></span>

<span data-ttu-id="9c02c-127">İyi adlandırılmış birim testleri paketiniz olduğunda, her test belirli bir giriş için beklenen çıktıyı açıkça açıklayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="9c02c-128">Buna ek olarak, gerçekten çalıştığını doğrulamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="9c02c-129">Daha az birleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="9c02c-129">Less coupled code</span></span>
<span data-ttu-id="9c02c-130">Kod sıkıca birleştiğinde, testi birleştirmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="9c02c-131">Yazdığınız kod için birim testleri oluşturmadan, bağlantı daha az belirgin olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="9c02c-132">Kodunuz için testler yazmak doğal olarak kodunuzu ayıracaktır, çünkü aksi takdirde test etmek daha zor olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="9c02c-133">İyi bir birim testinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="9c02c-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="9c02c-134">**Hızlı.**</span><span class="sxs-lookup"><span data-stu-id="9c02c-134">**Fast**.</span></span> <span data-ttu-id="9c02c-135">Olgun projelerin binlerce birim testi olması nadir değildir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="9c02c-136">Birim testleri çalıştırmak için çok az zaman almalısınız.</span><span class="sxs-lookup"><span data-stu-id="9c02c-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="9c02c-137">Milisaniye.</span><span class="sxs-lookup"><span data-stu-id="9c02c-137">Milliseconds.</span></span>
- <span data-ttu-id="9c02c-138">**İzole edilmiş.**</span><span class="sxs-lookup"><span data-stu-id="9c02c-138">**Isolated**.</span></span> <span data-ttu-id="9c02c-139">Birim testleri tek başınadır, yalıtımda çalıştırılabilir ve dosya sistemi veya veritabanı gibi dış etkenlere hiçbir bağımlılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="9c02c-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="9c02c-140">**Tekrarlanabilir.**</span><span class="sxs-lookup"><span data-stu-id="9c02c-140">**Repeatable**.</span></span> <span data-ttu-id="9c02c-141">Bir birim testi çalıştırmak sonuçlarıyla tutarlı olmalıdır, yani, çalıştırmalar arasında hiçbir şeyi değiştirmezseniz her zaman aynı sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c02c-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="9c02c-142">**Kendi kendini kontrol etme.**</span><span class="sxs-lookup"><span data-stu-id="9c02c-142">**Self-Checking**.</span></span> <span data-ttu-id="9c02c-143">Test, herhangi bir insan etkileşimi olmadan geçip geçemediğini veya başarısız olup olmadığını otomatik olarak algılayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="9c02c-144">**Zamanında.**</span><span class="sxs-lookup"><span data-stu-id="9c02c-144">**Timely**.</span></span> <span data-ttu-id="9c02c-145">Bir birim testi, test edilen kodla karşılaştırıldığında yazmak için orantısız olarak uzun bir zaman almamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="9c02c-146">Kodu yazmaya kıyasla büyük miktarda zaman alarak kodu sınamayı bulursanız, daha sınanabilir bir tasarım düşünün.</span><span class="sxs-lookup"><span data-stu-id="9c02c-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="9c02c-147">Aynı dili konuşalım.</span><span class="sxs-lookup"><span data-stu-id="9c02c-147">Let's speak the same language</span></span>
<span data-ttu-id="9c02c-148">Terim *mock* ne yazık ki çok test hakkında konuşurken yanlış.</span><span class="sxs-lookup"><span data-stu-id="9c02c-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="9c02c-149">Birim testleri yazarken en yaygın *sahte* türleri aşağıda tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="9c02c-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="9c02c-150">*Sahte* - Sahte bir saplama veya sahte bir nesne tanımlamak için kullanılabilecek genel bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="9c02c-151">Bir saplama veya bir alay olup olmadığını kullanılan bağlam bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="9c02c-152">Yani başka bir deyişle, sahte bir saplama ya da bir alay olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="9c02c-153">*Mock* - Sahte nesne, birim testinin geçip geçmediğine karar veren sistemdeki sahte bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="9c02c-154">Bir sahte karşı iddia edilene kadar bir Sahte olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="9c02c-155">*Saplama* - Saplama, sistemdeki varolan bir bağımlılık (veya ortak layıcı) için denetlenebilir bir değiştirmedir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="9c02c-156">Bir saplama kullanarak, doğrudan bağımlılık ile uğraşmadan kodunuzu sınayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="9c02c-157">Varsayılan olarak, sahte bir saplama olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="9c02c-158">Aşağıdaki kod parçacıklarını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9c02c-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="9c02c-159">Bu saplama bir mock olarak anılacaktır bir örnek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="9c02c-160">Bu durumda, bir saplama olduğunu.</span><span class="sxs-lookup"><span data-stu-id="9c02c-160">In this case, it is a stub.</span></span> <span data-ttu-id="9c02c-161">Anında `Purchase` (test altındaki sistem) yapabilmek için Sipariş'i sadece geçiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="9c02c-162">Adı `MockOrder` da çok yanıltıcı dır, çünkü yine, sipariş bir alay değildir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="9c02c-163">Daha iyi bir yaklaşım olurdu</span><span class="sxs-lookup"><span data-stu-id="9c02c-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="9c02c-164">Sınıfı yeniden `FakeOrder`adlandırarak, sınıfı çok daha genel hale getirdiniz, sınıf sahte veya saplama olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="9c02c-165">Hangisi test çalışması için daha iyi.</span><span class="sxs-lookup"><span data-stu-id="9c02c-165">Whichever is better for the test case.</span></span> <span data-ttu-id="9c02c-166">Yukarıdaki örnekte, `FakeOrder` saplama olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="9c02c-167">İddia sırasında herhangi `FakeOrder` bir şekil veya biçimde kullanmıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="9c02c-168">`FakeOrder`sadece yapıcı gereksinimlerini `Purchase` karşılamak için sınıfa geçti.</span><span class="sxs-lookup"><span data-stu-id="9c02c-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="9c02c-169">Sahte olarak kullanmak için böyle bir şey yapabilirsin.</span><span class="sxs-lookup"><span data-stu-id="9c02c-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="9c02c-170">Bu durumda, Sahte bir özelliği kontrol (buna karşı iddia), bu yüzden yukarıdaki kod `mockOrder` snippet, bir Mock olduğunu.</span><span class="sxs-lookup"><span data-stu-id="9c02c-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c02c-171">Bu terminolojiyi doğru yapmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="9c02c-172">Saplamalarınıza "alay" diyorsanız, diğer geliştiriciler niyetiniz hakkında yanlış varsayımlarda bulunurlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="9c02c-173">Alaylar ve saplamalar hakkında hatırlanması gereken en önemli şey, alayların saplamalar gibi olduğudur, ama siz sahte nesneye karşı iddiada bulunmaktadırsınız, oysa siz bir saplama ya karşı iddiada yoktur.</span><span class="sxs-lookup"><span data-stu-id="9c02c-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="9c02c-174">En iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="9c02c-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="9c02c-175">Testlerinizi adlandırma</span><span class="sxs-lookup"><span data-stu-id="9c02c-175">Naming your tests</span></span>
<span data-ttu-id="9c02c-176">Testinizin adı üç bölümden oluşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="9c02c-176">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="9c02c-177">Test edilen yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="9c02c-177">The name of the method being tested.</span></span>
- <span data-ttu-id="9c02c-178">Test edildiği senaryo.</span><span class="sxs-lookup"><span data-stu-id="9c02c-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="9c02c-179">Senaryo çağrıldığında beklenen davranış.</span><span class="sxs-lookup"><span data-stu-id="9c02c-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="9c02c-180">Neden?</span><span class="sxs-lookup"><span data-stu-id="9c02c-180">Why?</span></span>

- <span data-ttu-id="9c02c-181">Adlandırma standartları önemlidir, çünkü testin amacını açıkça ifade ederler.</span><span class="sxs-lookup"><span data-stu-id="9c02c-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="9c02c-182">Testler, kodunuzu çalıştığından emin olmaktan çok daha fazlasıdır, ayrıca belgeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="9c02c-183">Birim testleri paketine bakarak, kodunuzun davranışını kodun uzun bir bölümüne bakmadan çıkarabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="9c02c-184">Ayrıca, testler başarısız olduğunda, tam olarak hangi senaryoların beklentilerinizi karşılamadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="9c02c-185">Kötü:</span><span class="sxs-lookup"><span data-stu-id="9c02c-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="9c02c-186">Iyi:</span><span class="sxs-lookup"><span data-stu-id="9c02c-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="9c02c-187">Testlerinizi düzenleme</span><span class="sxs-lookup"><span data-stu-id="9c02c-187">Arranging your tests</span></span>
<span data-ttu-id="9c02c-188">**Düzenleme, Hareket, Assert** birim test edildiğinde ortak bir desendir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="9c02c-189">Adından da anlaşılacağı gibi, üç ana eylemden oluşur:</span><span class="sxs-lookup"><span data-stu-id="9c02c-189">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="9c02c-190">Nesnelerinizi *düzenleyin,* bunları oluşturup gerektiği gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c02c-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="9c02c-191">Bir nesneye göre *hareket* edin.</span><span class="sxs-lookup"><span data-stu-id="9c02c-191">*Act* on an object.</span></span>
- <span data-ttu-id="9c02c-192">Bir şeyin beklendiği gibi olduğunu *iddia edin.*</span><span class="sxs-lookup"><span data-stu-id="9c02c-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="9c02c-193">Neden?</span><span class="sxs-lookup"><span data-stu-id="9c02c-193">Why?</span></span>

- <span data-ttu-id="9c02c-194">Test edilenleri *düzenleme* ve ileri *sayıliş* adımlarından açıkça ayırır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="9c02c-195">"Act" kodu ile iddiaları karıştırmak için daha az şans.</span><span class="sxs-lookup"><span data-stu-id="9c02c-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="9c02c-196">Okunabilirlik, bir test yazarken en önemli yönlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="9c02c-197">Testteki bu eylemlerin her birini ayırmak, kodunuzu aramak için gereken bağımlılıkları, kodunuzun nasıl çağrıldığını ve ne iddia etmeye çalıştığınızı açıkça vurgular.</span><span class="sxs-lookup"><span data-stu-id="9c02c-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="9c02c-198">Bazı adımları birleştirmek ve testinizin boyutunu küçültmek mümkün olsa da, birincil amaç testi olabildiğince okunabilir hale getirmektir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="9c02c-199">Kötü:</span><span class="sxs-lookup"><span data-stu-id="9c02c-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="9c02c-200">Iyi:</span><span class="sxs-lookup"><span data-stu-id="9c02c-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="9c02c-201">Minimum geçen testleri yazma</span><span class="sxs-lookup"><span data-stu-id="9c02c-201">Write minimally passing tests</span></span>
<span data-ttu-id="9c02c-202">Birim testinde kullanılacak giriş, şu anda test ettiğiniz davranışı doğrulamak için mümkün olan en basit giriş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="9c02c-203">Neden?</span><span class="sxs-lookup"><span data-stu-id="9c02c-203">Why?</span></span>

- <span data-ttu-id="9c02c-204">Testler, kod tabanındaki gelecekteki değişikliklere karşı daha esnek hale gelir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="9c02c-205">Uygulama üzerinde davranışı sınamaya daha yakın.</span><span class="sxs-lookup"><span data-stu-id="9c02c-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="9c02c-206">Testi geçmek için gerekenden daha fazla bilgi içeren testler, teste hata getirme olasılığı daha yüksektir ve testin amacını daha az net hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="9c02c-207">Testleri yazarken davranışa odaklanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="9c02c-208">Modellerde fazladan özellikler ayarlama veya gerekli olmadığında sıfır olmayan değerleri kullanma, yalnızca kanıtlamaya çalıştığınız şeyi bozar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="9c02c-209">Kötü:</span><span class="sxs-lookup"><span data-stu-id="9c02c-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="9c02c-210">Iyi:</span><span class="sxs-lookup"><span data-stu-id="9c02c-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="9c02c-211">Sihirli dizeleri kaçının</span><span class="sxs-lookup"><span data-stu-id="9c02c-211">Avoid magic strings</span></span>
<span data-ttu-id="9c02c-212">Birim testlerde değişkenleri adlandırma, üretim kodundaki değişkenleri adlandırmak kadar önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="9c02c-213">Birim testleri sihirli dizeleri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="9c02c-214">Neden?</span><span class="sxs-lookup"><span data-stu-id="9c02c-214">Why?</span></span>

- <span data-ttu-id="9c02c-215">Değeri özel kılanın ne olduğunu anlamak için test okuyucusunun üretim kodunu incelemesi gereğini önler.</span><span class="sxs-lookup"><span data-stu-id="9c02c-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="9c02c-216">*Başarmaya*çalışmaktansa *neyi kanıtlamaya* çalıştığınızı açıkça gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="9c02c-217">Sihirli dizeleri testlerinizi okuyucu için karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="9c02c-218">Bir dize olağan dışı görünüyorsa, bir parametre veya geri dönüş değeri için neden belirli bir değerin seçildiğini merak edebilirler.</span><span class="sxs-lookup"><span data-stu-id="9c02c-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="9c02c-219">Bu, teste odaklanmak yerine uygulama ayrıntılarına daha yakından bakmalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="9c02c-220">Testleri yazarken, mümkün olduğunca çok niyet ifade etmek amaçlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="9c02c-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="9c02c-221">Sihirli dizeleri söz konusu olduğunda, iyi bir yaklaşım sabitlere bu değerleri atamaktır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="9c02c-222">Kötü:</span><span class="sxs-lookup"><span data-stu-id="9c02c-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="9c02c-223">Iyi:</span><span class="sxs-lookup"><span data-stu-id="9c02c-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="9c02c-224">Testlerde mantıktan kaçının</span><span class="sxs-lookup"><span data-stu-id="9c02c-224">Avoid logic in tests</span></span>
<span data-ttu-id="9c02c-225">Birim testleri yazarken manuel dize concatenation `if`ve `while` `for`mantıksal `switch`koşullar gibi kaçının , , , , vb.</span><span class="sxs-lookup"><span data-stu-id="9c02c-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="9c02c-226">Neden?</span><span class="sxs-lookup"><span data-stu-id="9c02c-226">Why?</span></span>

- <span data-ttu-id="9c02c-227">Testlerinizin içinde bir hata tanıtmak için daha az şans.</span><span class="sxs-lookup"><span data-stu-id="9c02c-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="9c02c-228">Uygulama ayrıntıları yerine sonuca odaklanın.</span><span class="sxs-lookup"><span data-stu-id="9c02c-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="9c02c-229">Test paketinize mantık kattığında, içine bir hata girme şansı önemli ölçüde artar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="9c02c-230">Hata bulmak istediğiniz son yer test paketinizdedir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="9c02c-231">Testlerinizin işe yarayacağına dair yüksek düzeyde bir güvene sahip olmalısınız, aksi takdirde onlara güvenmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="9c02c-232">Güvenmediğiniz testler, herhangi bir değer sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="9c02c-233">Bir test başarısız olduğunda, bir şeyin kodunuzda gerçekten yanlış olduğunu ve göz ardı edilemeyeceğini hissetmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="9c02c-234">Testinizdeki mantık kaçınılmaz görünüyorsa, testi iki veya daha fazla farklı teste bölmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="9c02c-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="9c02c-235">Kötü:</span><span class="sxs-lookup"><span data-stu-id="9c02c-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="9c02c-236">Iyi:</span><span class="sxs-lookup"><span data-stu-id="9c02c-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="9c02c-237">Kurulum ve yıkma için yardımcı yöntemleri tercih etme</span><span class="sxs-lookup"><span data-stu-id="9c02c-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="9c02c-238">Testleriniz için benzer bir nesne veya durum gerekiyorsa, varsa Kurulum ve Yıkıntı özniteliklerinden yararlanmak yerine yardımcı yöntemi tercih edin.</span><span class="sxs-lookup"><span data-stu-id="9c02c-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="9c02c-239">Neden?</span><span class="sxs-lookup"><span data-stu-id="9c02c-239">Why?</span></span>

- <span data-ttu-id="9c02c-240">Kodun tümü her testin içinden görülebildiğinden testleri okurken daha az karışıklık.</span><span class="sxs-lookup"><span data-stu-id="9c02c-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="9c02c-241">Verilen test için çok fazla veya çok az ayarlama şansı daha az.</span><span class="sxs-lookup"><span data-stu-id="9c02c-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="9c02c-242">Aralarında istenmeyen bağımlılıklar yaratan testler arasında durum paylaşımı daha az şansı.</span><span class="sxs-lookup"><span data-stu-id="9c02c-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="9c02c-243">Birim test çerçevelerinde, `Setup` test paketinizdeki her birim testiöncesinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="9c02c-244">Bazı yararlı bir araç olarak görebilirsiniz, genellikle şişirilmiş ve testleri okumak zor yol biter.</span><span class="sxs-lookup"><span data-stu-id="9c02c-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="9c02c-245">Her test, testi çalışır hale getirmek için genellikle farklı gereksinimlere sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="9c02c-246">Ne `Setup` yazık ki, her test için tam olarak aynı gereksinimleri kullanmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="9c02c-247">xUnit sürüm 2.x olarak hem SetUp ve TearDown kaldırdı</span><span class="sxs-lookup"><span data-stu-id="9c02c-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="9c02c-248">Kötü:</span><span class="sxs-lookup"><span data-stu-id="9c02c-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="9c02c-249">Iyi:</span><span class="sxs-lookup"><span data-stu-id="9c02c-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="9c02c-250">Birden fazla iddiadan kaçının</span><span class="sxs-lookup"><span data-stu-id="9c02c-250">Avoid multiple asserts</span></span>
<span data-ttu-id="9c02c-251">Testlerinizi yazarken, test başına yalnızca bir Assert eklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="9c02c-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="9c02c-252">Yalnızca bir assert kullanarak ortak yaklaşımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9c02c-252">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="9c02c-253">Her assert için ayrı bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c02c-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="9c02c-254">Parametreli testler kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c02c-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="9c02c-255">Neden?</span><span class="sxs-lookup"><span data-stu-id="9c02c-255">Why?</span></span>

- <span data-ttu-id="9c02c-256">Bir Assert başarısız olursa, sonraki Asserts değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="9c02c-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="9c02c-257">Testlerinizde birden çok servis vakası iddia etmemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="9c02c-258">Testlerinizin neden başarısız olduğuna ilgili resmin tamamını verir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-258">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="9c02c-259">Bir test çalışmasına birden çok assert sayılırken, tüm ileri bulguların yürütüleceği garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="9c02c-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="9c02c-260">Çoğu birim test çerçevesinde, bir birim testinde bir iddia başarısız olduğunda, devam eden testler otomatik olarak başarısız olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="9c02c-261">Bu, gerçekten çalışan işlevsellik olarak kafa karıştırıcı olabilir, başarısız olarak gösterilecek.</span><span class="sxs-lookup"><span data-stu-id="9c02c-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="9c02c-262">Bu kuralın yaygın bir istisnası, bir nesneye karşı ileri sayılmaktır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="9c02c-263">Bu durumda, nesnenin içinde olmasını beklediğiniz durumda olduğundan emin olmak için her özellik aleyhinde birden çok iddia olması genellikle kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="9c02c-264">Kötü:</span><span class="sxs-lookup"><span data-stu-id="9c02c-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="9c02c-265">Iyi:</span><span class="sxs-lookup"><span data-stu-id="9c02c-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="9c02c-266">Ortak yöntemleri birim test ederek özel yöntemleri doğrulama</span><span class="sxs-lookup"><span data-stu-id="9c02c-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="9c02c-267">Çoğu durumda, özel bir yöntemi sınamaya gerek olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="9c02c-268">Özel yöntemler bir uygulama ayrıntısIdir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="9c02c-269">Şöyle düşünebilirsiniz: özel yöntemler asla izole olarak bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="9c02c-270">Bir noktada, uygulanmasının bir parçası olarak özel yöntem çağıran bir kamu bakan yöntem olacak.</span><span class="sxs-lookup"><span data-stu-id="9c02c-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="9c02c-271">Dikkat etmesi gereken şey, özel yönteme çağıran genel yöntemin sonucudur.</span><span class="sxs-lookup"><span data-stu-id="9c02c-271">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="9c02c-272">Aşağıdaki örneği göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="9c02c-272">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="9c02c-273">İlk tepkiniz, yöntemin beklendiği `TrimInput` gibi çalıştığından emin olmak istediğiniz için bir test yazmaya başlamak olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-273">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="9c02c-274">Ancak, hiç beklemediğiniz `ParseLogLine` şekilde `sanitizedInput` manipüle etmek, yararsız aleyhine `TrimInput` bir test oluşturmatamamen mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9c02c-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="9c02c-275">Gerçek test kamu bakan yönteme `ParseLogLine` karşı yapılmalıdır, çünkü sonuçta ne hakkında bakım olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="9c02c-276">Bu bakış açısıyla, özel bir yöntem görürseniz, ortak yöntemi bulun ve testlerinizi bu yönteme karşı yazın.</span><span class="sxs-lookup"><span data-stu-id="9c02c-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="9c02c-277">Özel bir yöntemin beklenen sonucu döndürmesi, sonunda özel yöntemi çağıran sistemin sonucu doğru kullandığı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="9c02c-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="9c02c-278">Stub statik referanslar</span><span class="sxs-lookup"><span data-stu-id="9c02c-278">Stub static references</span></span>
<span data-ttu-id="9c02c-279">Bir birim testinin ilkelerinden biri, test altında sistemin tam denetimine sahip olması gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="9c02c-280">Üretim kodu statik başvurulara çağrı içeriyorsa (örn. `DateTime.Now`</span><span class="sxs-lookup"><span data-stu-id="9c02c-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="9c02c-281">Aşağıdaki kodu göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="9c02c-281">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="9c02c-282">Bu kod nasıl birim test edilebilir?</span><span class="sxs-lookup"><span data-stu-id="9c02c-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="9c02c-283">Gibi bir yaklaşım deneyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="9c02c-283">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="9c02c-284">Ne yazık ki, hızlı bir şekilde testleri ile bir çift sorun olduğunu fark edecektir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="9c02c-285">Test paketi Salı günü çalıştırılırsa, ikinci test geçer, ancak ilk test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9c02c-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="9c02c-286">Test paketi başka bir gün çalıştırılırsa, ilk test geçer, ancak ikinci test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9c02c-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="9c02c-287">Bu sorunları çözmek için, üretim kodunuza bir *dikiş* girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="9c02c-288">Bir yaklaşım, bir arabirimde denetlemeniz gereken kodu sarmak ve üretim kodunun bu arabirime bağlı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="9c02c-289">Test paketiniz artık</span><span class="sxs-lookup"><span data-stu-id="9c02c-289">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="9c02c-290">Artık test paketi üzerinde `DateTime.Now` tam kontrole sahiptir ve yönteme araverirken herhangi bir değer saplayabilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
