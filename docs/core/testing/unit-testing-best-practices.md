---
title: Birim testleri yazmak için en iyi uygulamalar
description: Kod kalitesini ve esnekliği artırmaya birim testleri yazmak için en iyi uygulamaları öğrenin
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 69fe0cae141d1ed1e1281eecd78bf03e6e8be961
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530603"
---
# <a name="unit-testing-best-practices"></a><span data-ttu-id="51c22-103">Birim testi en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="51c22-103">Unit testing best practices</span></span>

<span data-ttu-id="51c22-104">Tarafından [John Reese](http://reesespieces.io) performanstan özel ile [Roy Osherove](http://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="51c22-104">By [John Reese](http://reesespieces.io) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

<span data-ttu-id="51c22-105">Birim testleri yazma için çok sayıda avantaj vardır; belgeler, regresyonla sağlar ve iyi bir tasarım kolaylaştırmak yardımcı olurlar.</span><span class="sxs-lookup"><span data-stu-id="51c22-105">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="51c22-106">Ancak, okuma ve kırılgan sabit bir birim testlerini kod tabanınız üzerinde düzensizliğe benzer zararlar verecektir.</span><span class="sxs-lookup"><span data-stu-id="51c22-106">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span>

<span data-ttu-id="51c22-107">Bu kılavuzda, esnek ve kolay anlaşılır testlerinizi tutmak için birim testleri yazılırken bazı en iyi uygulamaları öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="51c22-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="51c22-108">Neden birim testi?</span><span class="sxs-lookup"><span data-stu-id="51c22-108">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="51c22-109">Daha az zaman işlevsel testleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="51c22-109">Less time performing functional tests</span></span>
<span data-ttu-id="51c22-110">İşlevsel testleri pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-110">Functional tests are expensive.</span></span> <span data-ttu-id="51c22-111">Bunlar genellikle uygulamayı açmaktan ve bir dizi (veya bir başkasının), Beklenen davranış doğrulayabilmek izlemelidir adımları gerçekleştirerek de içerir.</span><span class="sxs-lookup"><span data-stu-id="51c22-111">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="51c22-112">Bu adımları her zaman daha bilgili birine alanı test gerçekleştirmek için ulaşmak olacağı anlamına gelir test edici için bilinmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-112">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="51c22-113">Kendi test Önemsiz değişiklikleri saniye veya daha büyük değişikliklerin dakika sürebilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-113">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="51c22-114">Son olarak, bu işlem her değişiklik için sistemde yaptığınız yinelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="51c22-114">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="51c22-115">Birim testleri, diğer el, milisaniye almak, bir düğmeye basarak çalıştırılabilir ve büyük sistemin herhangi bir Bilgi Bankası gerektirmeyebilecek.</span><span class="sxs-lookup"><span data-stu-id="51c22-115">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="51c22-116">Testin geçtiğini veya başarısız olup olmadığını test Çalıştırıcısı kadar kişi var.</span><span class="sxs-lookup"><span data-stu-id="51c22-116">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="51c22-117">Regresyon karşı koruma</span><span class="sxs-lookup"><span data-stu-id="51c22-117">Protection against regression</span></span>
<span data-ttu-id="51c22-118">Regresyon hataları uygulamada bir değişiklik yapıldığında, sunulan hatalar var.</span><span class="sxs-lookup"><span data-stu-id="51c22-118">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="51c22-119">Yalnızca test ediciler, yeni bir özellik test ancak beklendiği gibi özellikleri daha önce uygulanan doğrulamak için önceden varolan özellikleri işlevi ayrıca hala yaygındır.</span><span class="sxs-lookup"><span data-stu-id="51c22-119">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="51c22-120">Birim testi ile her derlemeden sonra veya bir kod satırı değiştirdikten sonra bile, tüm testleri paketi yeniden çalıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="51c22-120">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="51c22-121">Size yeni kodunuz var olan işlevselliği kesmez güvenilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="51c22-121">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="51c22-122">Yürütülebilir belgeleri</span><span class="sxs-lookup"><span data-stu-id="51c22-122">Executable documentation</span></span>
<span data-ttu-id="51c22-123">Bu her zaman belirli bir yöntem yapar veya belirli bir giriş nasıl davrandığını belirgin olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-123">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="51c22-124">Kendiniz isteyebilir: nasıl bu yöntem davranacağını boş bir dize başarılı olursa?</span><span class="sxs-lookup"><span data-stu-id="51c22-124">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="51c22-125">Null?</span><span class="sxs-lookup"><span data-stu-id="51c22-125">Null?</span></span>

<span data-ttu-id="51c22-126">İyi adlandırılmış birim testleri paketi varsa, her test açıkça belirtilen bir giriş için beklenen çıktıyı açıklamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="51c22-126">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="51c22-127">Ayrıca, aslında çalışıp çalışmadığını doğrulayabilirsiniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-127">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="51c22-128">Daha az bağlı kod</span><span class="sxs-lookup"><span data-stu-id="51c22-128">Less coupled code</span></span>
<span data-ttu-id="51c22-129">Kod sıkı şekilde bağlı olduğunda, birim testi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-129">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="51c22-130">Yazmakta olduğunuz koda yönelik birim testleri oluşturmadan bağlantısından daha az görünür olabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-130">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="51c22-131">Aksi takdirde test daha zor olduğundan kodunuz için testleri yazmak kodunuzu, doğal olarak ayırmak.</span><span class="sxs-lookup"><span data-stu-id="51c22-131">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="51c22-132">İyi birim testi özellikleri</span><span class="sxs-lookup"><span data-stu-id="51c22-132">Characteristics of a good unit test</span></span>
- <span data-ttu-id="51c22-133">**Hızlı**.</span><span class="sxs-lookup"><span data-stu-id="51c22-133">**Fast**.</span></span> <span data-ttu-id="51c22-134">Seyrek olgun projeleri için birim testleri binlerce sahip değil.</span><span class="sxs-lookup"><span data-stu-id="51c22-134">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="51c22-135">Birim testleri çalıştırmak için çok az zamanınız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51c22-135">Unit tests should take very little time to run.</span></span> <span data-ttu-id="51c22-136">Milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="51c22-136">Milliseconds.</span></span>
- <span data-ttu-id="51c22-137">**Yalıtılmış**.</span><span class="sxs-lookup"><span data-stu-id="51c22-137">**Isolated**.</span></span> <span data-ttu-id="51c22-138">Birim testleri tek başına olan, yalıtılmış olarak çalıştırabilir ve herhangi bir dosya sistemi veya veritabanı gibi faktörlere dışında hiçbir bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="51c22-138">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="51c22-139">**Tekrarlanabilir**.</span><span class="sxs-lookup"><span data-stu-id="51c22-139">**Repeatable**.</span></span> <span data-ttu-id="51c22-140">Birim testi sonuçlarını ile tutarlı olmalıdır, çalıştırmaları arasında herhangi bir şey değiştirmezseniz diğer bir deyişle, her zaman aynı sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="51c22-140">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="51c22-141">**Kendi kendine denetimi**.</span><span class="sxs-lookup"><span data-stu-id="51c22-141">**Self-Checking**.</span></span> <span data-ttu-id="51c22-142">Test, Geçti veya insan etkileşimi başarısız olursa otomatik olarak algılayabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-142">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="51c22-143">**Zamanında**.</span><span class="sxs-lookup"><span data-stu-id="51c22-143">**Timely**.</span></span> <span data-ttu-id="51c22-144">Birim testi test edilen kodu karşılaştırılan yazma orantısız uzun sürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="51c22-144">A unit test should not take a disproportionally long time to write compared to the code being tested.</span></span> <span data-ttu-id="51c22-145">Çok miktarda kod yazmaya kıyasla saat sürüyor kodu test etmek bulursanız, daha fazla test edilebilir bir tasarım kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="51c22-145">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="51c22-146">Aynı dili şimdi konuşun</span><span class="sxs-lookup"><span data-stu-id="51c22-146">Let's speak the same language</span></span>
<span data-ttu-id="51c22-147">Terim *sahte* testi hakkında konuşurken ne yazık ki çok yanlış kullanılmış olan.</span><span class="sxs-lookup"><span data-stu-id="51c22-147">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="51c22-148">En yaygın türleri, aşağıdaki tanımlar *fakes* birim testleri yazılırken:</span><span class="sxs-lookup"><span data-stu-id="51c22-148">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="51c22-149">*Sahte* -sahte bir saplama veya sahte bir nesne tanımlamak için kullanılan genel bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="51c22-149">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="51c22-150">Bir saplama veya sahte bir olup olmadığını, kullanıldığı bağlam üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-150">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="51c22-151">Bu nedenle başka bir deyişle, sahte bir saplama veya bir sahte olabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-151">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="51c22-152">*Sahte* -sahte bir nesne bir sahte bir birim testi geçti veya başarısız olup olmadığını karar sistemde nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="51c22-152">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="51c22-153">Karşı onaylanan kadar bir Sahne sahte başlar.</span><span class="sxs-lookup"><span data-stu-id="51c22-153">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="51c22-154">*Saplama* -bir saplama sistemde mevcut bağımlılık (veya ortak çalışanı) denetlenebilir bir ardılı olan.</span><span class="sxs-lookup"><span data-stu-id="51c22-154">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="51c22-155">Bir saplama kullanarak kodunuzu doğrudan bağımlılık uğraşmanızı olmadan test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51c22-155">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="51c22-156">Varsayılan olarak, sahte bir saplama başlar.</span><span class="sxs-lookup"><span data-stu-id="51c22-156">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="51c22-157">Aşağıdaki kod parçacığı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="51c22-157">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="51c22-158">Bu, kalıntı bir Sahne başvurulan bir örneği olabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-158">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="51c22-159">Bu durumda, bir saptama olur.</span><span class="sxs-lookup"><span data-stu-id="51c22-159">In this case, it is a stub.</span></span> <span data-ttu-id="51c22-160">Yalnızca örneklemek için bir yol sırada geçirme `Purchase` (test altındaki sistem).</span><span class="sxs-lookup"><span data-stu-id="51c22-160">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="51c22-161">Adı `MockOrder` yeniden sırasını sahte bir de çok yanıltıcı olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-161">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="51c22-162">Daha iyi bir yaklaşım olacaktır</span><span class="sxs-lookup"><span data-stu-id="51c22-162">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="51c22-163">Sınıfı yeniden adlandırarak `FakeOrder`sınıfı çok daha genel yaptığınız, sınıfı bir sahte veya bir saplama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-163">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="51c22-164">Hangisi, test çalışması için iyidir.</span><span class="sxs-lookup"><span data-stu-id="51c22-164">Whichever is better for the test case.</span></span> <span data-ttu-id="51c22-165">Yukarıdaki örnekte, `FakeOrder` yer tutucusu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51c22-165">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="51c22-166">Kullanmadığınız `FakeOrder` assert sırasında herhangi bir şekil veya biçimde.</span><span class="sxs-lookup"><span data-stu-id="51c22-166">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="51c22-167">`FakeOrder` yalnızca içine geçirilen `Purchase` Oluşturucu gereksinimlerini karşılamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="51c22-167">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="51c22-168">Bir Sahne kullanmak için aşağıdakine benzer yapabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="51c22-168">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="51c22-169">Bu durumda, (karşı sunduğundan), sahte bu nedenle Yukarıdaki kod parçacığında, bir özellik denetimi `mockOrder` bir sahte olduğu.</span><span class="sxs-lookup"><span data-stu-id="51c22-169">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51c22-170">Bu terimler doğru almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="51c22-170">It's important to get this terminology correct.</span></span> <span data-ttu-id="51c22-171">"Mocks", saptamalar çağırırsanız, diğer geliştiriciler, amacı hakkında varsayımlar false oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="51c22-171">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="51c22-172">Bir saplama karşı assert değil ise mocks yer tutucular yerine ilgili hatırlamak ana mocks yalnızca saptamalar gibi olan, ancak sahte bir nesneye karşı assert şeydir.</span><span class="sxs-lookup"><span data-stu-id="51c22-172">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="51c22-173">Önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="51c22-173">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="51c22-174">Testlerinizi adlandırma</span><span class="sxs-lookup"><span data-stu-id="51c22-174">Naming your tests</span></span>
<span data-ttu-id="51c22-175">Test adı üç bölümden oluşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="51c22-175">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="51c22-176">Test edilen yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="51c22-176">The name of the method being tested.</span></span>
- <span data-ttu-id="51c22-177">Altında sınanır senaryo.</span><span class="sxs-lookup"><span data-stu-id="51c22-177">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="51c22-178">Senaryo çağrıldığında Beklenen davranış.</span><span class="sxs-lookup"><span data-stu-id="51c22-178">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="51c22-179">Neden?</span><span class="sxs-lookup"><span data-stu-id="51c22-179">Why?</span></span>
- <span data-ttu-id="51c22-180">Adlandırma standartlarına, bunlar test amacı açıkça express için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="51c22-180">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="51c22-181">Testler daha fazlasını bulunduğunuzdan emin kodunuzun çalıştığı da sağladıkları belgeleri.</span><span class="sxs-lookup"><span data-stu-id="51c22-181">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="51c22-182">Yalnızca birim testleri suite'e bakarak bile koda göz bakmadan kodunuzu davranışını belirleyebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-182">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="51c22-183">Ayrıca, test başarısız olduğunda, tam olarak hangi senaryoların beklentilerinizi karşılamayan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51c22-183">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="51c22-184">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="51c22-184">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="51c22-185">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="51c22-185">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="51c22-186">Testlerinizi Düzenleme</span><span class="sxs-lookup"><span data-stu-id="51c22-186">Arranging your tests</span></span>
<span data-ttu-id="51c22-187">**Düzenleme, hareket, onaylama işlemi** yaygın olduğu zaman desen birim testi.</span><span class="sxs-lookup"><span data-stu-id="51c22-187">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="51c22-188">Adından da anlaşılacağı gibi üç ana eylemden oluşur:</span><span class="sxs-lookup"><span data-stu-id="51c22-188">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="51c22-189">*Düzenleme* nesnelerinizi, oluşturma ve bunları gerektiği şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="51c22-189">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="51c22-190">*ACT* bir nesne üzerinde.</span><span class="sxs-lookup"><span data-stu-id="51c22-190">*Act* on an object.</span></span>
- <span data-ttu-id="51c22-191">*Assert* , beklendiği gibi bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="51c22-191">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="51c22-192">Neden?</span><span class="sxs-lookup"><span data-stu-id="51c22-192">Why?</span></span>
- <span data-ttu-id="51c22-193">Açıkça ne gelen edildiğini ayıran *düzenleme* ve *assert* adımları.</span><span class="sxs-lookup"><span data-stu-id="51c22-193">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="51c22-194">"Eylem" kodlu bir onayları intermix olasılığı daha az.</span><span class="sxs-lookup"><span data-stu-id="51c22-194">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="51c22-195">Okunabilirlik en önemli yönlerinden test yazarken biridir.</span><span class="sxs-lookup"><span data-stu-id="51c22-195">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="51c22-196">Test içinde bu eylemlerin her birine ayırarak açıkça kodunuzu, kodunuzu nasıl çağrılan ve onay çalıştığınız çağırmak için gereken bağımlılıklar vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="51c22-196">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="51c22-197">Bazı adımlar birleştirin ve testinizi boyutunu küçültmek mümkün olabilir, ancak birincil amacı, test olarak okunabilir olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="51c22-197">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="51c22-198">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="51c22-198">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="51c22-199">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="51c22-199">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="51c22-200">En düşük düzeyde geçirme testleri yazma</span><span class="sxs-lookup"><span data-stu-id="51c22-200">Write minimally passing tests</span></span>
<span data-ttu-id="51c22-201">Şu anda test ettiğiniz davranışına doğrulamak için bir birim testinde kullanılacak giriş basit mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51c22-201">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="51c22-202">Neden?</span><span class="sxs-lookup"><span data-stu-id="51c22-202">Why?</span></span>
- <span data-ttu-id="51c22-203">Testler kod tabanındaki gelecekteki değişikliklere daha dayanıklı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="51c22-203">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="51c22-204">Uygulama davranışı test yakın.</span><span class="sxs-lookup"><span data-stu-id="51c22-204">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="51c22-205">Test geçirmek için gerekenden daha fazla bilgi içeren testler hataları teste giriş, daha yüksek şansına sahip olabilirsiniz ve amacı, az NET test yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51c22-205">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="51c22-206">Testleri yazılırken davranışı odaklanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="51c22-206">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="51c22-207">Modeller üzerinde ek özellikleri ayarlamak veya gerekli olduğunda sıfır olmayan değerler kullanarak, yalnızca ne kanıtlamak çalışıyorsunuz gelen detracts.</span><span class="sxs-lookup"><span data-stu-id="51c22-207">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="51c22-208">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="51c22-208">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="51c22-209">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="51c22-209">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="51c22-210">Sihirli dize kaçının</span><span class="sxs-lookup"><span data-stu-id="51c22-210">Avoid magic strings</span></span>
<span data-ttu-id="51c22-211">Değişkenleri adlandırma birim testleri gibi önemli değil daha da önemlisi, üretim kodunda adlandırma değişkenleri daha.</span><span class="sxs-lookup"><span data-stu-id="51c22-211">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="51c22-212">Birim testleri Sihirli dize içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="51c22-212">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="51c22-213">Neden?</span><span class="sxs-lookup"><span data-stu-id="51c22-213">Why?</span></span>
- <span data-ttu-id="51c22-214">Değer özel kılan anlamak için üretim kodu incelemek için gereken test okuyucu engeller.</span><span class="sxs-lookup"><span data-stu-id="51c22-214">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="51c22-215">Açmaya çalıştığınız açıkça gösterir *kanıtlamak* çalışılırken yerine *gerçekleştirmek*.</span><span class="sxs-lookup"><span data-stu-id="51c22-215">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="51c22-216">Sihirli dize testlerinizin Okuyucu için karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-216">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="51c22-217">Bir dize normal dışı görünüyorsa, bunlar belirli bir değer için bir parametre neden seçildiğini merak ediyor veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="51c22-217">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="51c22-218">Bu test yakından odak yerine uygulama ayrıntılarını almak için bunları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-218">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="51c22-219">Testleri yazılırken, mümkün olduğunca fazla hedefi ifade etmek için indirmeyi amaçlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51c22-219">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="51c22-220">Sihirli dize söz konusu olduğunda, bu değerleri sabitleri atama iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-220">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="51c22-221">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="51c22-221">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="51c22-222">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="51c22-222">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="51c22-223">Testleri mantığı kaçının</span><span class="sxs-lookup"><span data-stu-id="51c22-223">Avoid logic in tests</span></span>
<span data-ttu-id="51c22-224">Birim testleri önlemek el ile dize birleştirme ve mantıksal gibi koşullar yazılırken `if`, `while`, `for`, `switch`vb.</span><span class="sxs-lookup"><span data-stu-id="51c22-224">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="51c22-225">Neden?</span><span class="sxs-lookup"><span data-stu-id="51c22-225">Why?</span></span>
- <span data-ttu-id="51c22-226">Testlerinizi içinde bir hata tanıtmak için fırsat daha az.</span><span class="sxs-lookup"><span data-stu-id="51c22-226">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="51c22-227">Sonuç, yerine uygulama ayrıntılarını odaklanın.</span><span class="sxs-lookup"><span data-stu-id="51c22-227">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="51c22-228">Mantıksal test paketiniz aldığımızda, içine bir hata ile tanışın olasılığını önemli ölçüde artırır.</span><span class="sxs-lookup"><span data-stu-id="51c22-228">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="51c22-229">Bir hatayı bulmak için istediğiniz son içinde test çalışmalarıyla yerdir.</span><span class="sxs-lookup"><span data-stu-id="51c22-229">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="51c22-230">Testlerinizi iş güvenle yüksek düzeyde olmalıdır, aksi takdirde, bunları güvenir değil.</span><span class="sxs-lookup"><span data-stu-id="51c22-230">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="51c22-231">Güvenmediğiniz, testler herhangi bir değer sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="51c22-231">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="51c22-232">Bir test başarısız olduğunda, bir şeyin aslında kodunuzla yanlış olduğunu ve bunu göz ardı edilemez olduğunu bir fikir edindiniz istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="51c22-232">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="51c22-233">Testinizde mantıksal kaçınılmaz görünüyorsa, iki veya daha fazla farklı testlere test bölmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="51c22-233">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="51c22-234">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="51c22-234">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="51c22-235">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="51c22-235">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="51c22-236">Kurulumu ve kaldırma için yardımcı yöntemler tercih et</span><span class="sxs-lookup"><span data-stu-id="51c22-236">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="51c22-237">Testleriniz için benzer bir nesne ya da durum gerekiyorsa, bir yardımcı yöntemi varsa, kurulumu ve kaldırma öznitelikleri yararlanarak daha tercih eder.</span><span class="sxs-lookup"><span data-stu-id="51c22-237">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="51c22-238">Neden?</span><span class="sxs-lookup"><span data-stu-id="51c22-238">Why?</span></span>
- <span data-ttu-id="51c22-239">Daha az karışıklık, testlerin tüm kodu beri okunurken her test içinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-239">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="51c22-240">Çok fazla veya çok küçük bir verilen test için kurma olasılığı daha az.</span><span class="sxs-lookup"><span data-stu-id="51c22-240">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="51c22-241">Bunlar arasında istenmeyen bağımlılıklar oluşturan testleri arasında durum paylaşma şansı daha az.</span><span class="sxs-lookup"><span data-stu-id="51c22-241">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="51c22-242">Birim test çerçeveleri, `Setup` içinde test çalışmalarıyla her birim testi önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="51c22-242">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="51c22-243">Bazı faydalı bir araç olarak görebilir, ancak bu genellikle için bloated ve testleri okunmasını sonlanan sona erer.</span><span class="sxs-lookup"><span data-stu-id="51c22-243">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="51c22-244">Her test genellikle test çalıştırmaya almak için farklı gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="51c22-244">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="51c22-245">Ne yazık ki `Setup` , her test için aynı gereksinimlerinin tamamı kullanmaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-245">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="51c22-246">xUnit sürümden itibaren kaldırdı hem kurulumu ve kaldırma 2.x</span><span class="sxs-lookup"><span data-stu-id="51c22-246">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="51c22-247">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="51c22-247">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="51c22-248">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="51c22-248">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="51c22-249">Birden çok önlemek onaylar</span><span class="sxs-lookup"><span data-stu-id="51c22-249">Avoid multiple asserts</span></span>
<span data-ttu-id="51c22-250">Testlerinizi yazarken, yalnızca test başına bir onay içerecek şekilde deneyin.</span><span class="sxs-lookup"><span data-stu-id="51c22-250">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="51c22-251">Yalnızca birini kullanarak genel yaklaşımları onaylama Ekle:</span><span class="sxs-lookup"><span data-stu-id="51c22-251">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="51c22-252">Her onay için ayrı bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="51c22-252">Create a separate test for each assert.</span></span>
- <span data-ttu-id="51c22-253">Parametreli testleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="51c22-253">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="51c22-254">Neden?</span><span class="sxs-lookup"><span data-stu-id="51c22-254">Why?</span></span>
- <span data-ttu-id="51c22-255">Bir onay başarısız olursa, sonraki Asserts değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="51c22-255">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="51c22-256">Birden çok durum testlerinizde sunduğundan değil sağlar.</span><span class="sxs-lookup"><span data-stu-id="51c22-256">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="51c22-257">Testlerinizi neden başarısız dair tüm resim sunar.</span><span class="sxs-lookup"><span data-stu-id="51c22-257">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="51c22-258">Birden çok giriş için bir test çalışmasına onaylar, bu, tüm garanti edilmez, onaylar yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-258">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="51c22-259">Onaylama başarısız bir birim test, sonra çoğu birim testi çerçevelerini içinde devam etmeden testleri otomatik olarak başarısız olduğunu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-259">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="51c22-260">Gerçekten çalışmaktadır, işlevselliği gösterilecek şekilde başarısız olarak bu kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="51c22-260">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="51c22-261">Bir nesneye karşı sunduğundan bu kural için ortak bir özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="51c22-261">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="51c22-262">Bu durumda olması genellikle kabul edilebilirdir nesne, olmasını beklediğiniz durumunda olduğundan emin olmak için her bir özellik karşı birden çok onaylar.</span><span class="sxs-lookup"><span data-stu-id="51c22-262">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="51c22-263">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="51c22-263">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="51c22-264">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="51c22-264">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="51c22-265">Özel birim testi genel yöntemleri yöntemle doğrula</span><span class="sxs-lookup"><span data-stu-id="51c22-265">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="51c22-266">Çoğu durumda olmamalıdır test bir özel yöntemi gerekir.</span><span class="sxs-lookup"><span data-stu-id="51c22-266">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="51c22-267">Bir uygulama ayrıntısı özel yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="51c22-267">Private methods are an implementation detail.</span></span> <span data-ttu-id="51c22-268">Bunu bu şekilde düşünebilirsiniz: özel yöntemler yalıtım modunda hiçbir zaman yok.</span><span class="sxs-lookup"><span data-stu-id="51c22-268">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="51c22-269">Belirli bir noktada oluşacak uygulanması bir parçası olarak özel yöntemi çağıran bir genel kullanıma yönelik yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51c22-269">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="51c22-270">Önem verdiğiniz metodun özel bir çağıran son sonucudur.</span><span class="sxs-lookup"><span data-stu-id="51c22-270">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="51c22-271">Aşağıdaki örneği inceleyin</span><span class="sxs-lookup"><span data-stu-id="51c22-271">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="51c22-272">Bir test için yazmaya başlamak için ilk tepkinizi olabilir `trimInput` yöntemi beklendiği gibi çalıştığından emin olmak istememiz.</span><span class="sxs-lookup"><span data-stu-id="51c22-272">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="51c22-273">Ancak, bu tamamen mümkündür, `ParseLogLine` yöneten `sanitizedInput` gibi bir sınaması işleme beklediğiniz olmayan bir şekilde `trimInput` gereksiz.</span><span class="sxs-lookup"><span data-stu-id="51c22-273">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="51c22-274">Gerçek bir testin genel kullanıma yönelik yöntemi karşı yapılmalıdır `ParseLogLine` ne sonuçta verdiğiniz, çünkü.</span><span class="sxs-lookup"><span data-stu-id="51c22-274">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="51c22-275">Bu bakış açısı ile özel bir yöntem görürseniz, genel yöntemini bulun ve karşı bu yöntemi testlerinizi yazın.</span><span class="sxs-lookup"><span data-stu-id="51c22-275">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="51c22-276">Özel bir yöntem yalnızca beklenen sonuç döndürdüğünden, sonunda özel yöntemi çağıran sistem sonucu doğru kullandığı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="51c22-276">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="51c22-277">Saplama statik başvuruları</span><span class="sxs-lookup"><span data-stu-id="51c22-277">Stub static references</span></span>
<span data-ttu-id="51c22-278">İlkeleri bir birim testinin, test altındaki sistem tam denetimi olmalıdır biridir.</span><span class="sxs-lookup"><span data-stu-id="51c22-278">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="51c22-279">Üretim kodu statik başvuruları çağrıları içerdiğinde bu sorunlu olabilir (örneğin `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="51c22-279">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="51c22-280">Aşağıdaki kodu düşünün</span><span class="sxs-lookup"><span data-stu-id="51c22-280">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="51c22-281">Nasıl Bu kod, birim test büyük olasılıkla olabilir?</span><span class="sxs-lookup"><span data-stu-id="51c22-281">How can this code possibly be unit tested?</span></span> <span data-ttu-id="51c22-282">Bir yaklaşım gibi çalışabilir</span><span class="sxs-lookup"><span data-stu-id="51c22-282">You may try an approach such as</span></span>

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

<span data-ttu-id="51c22-283">Ne yazık ki, testlerinizi birkaç sorunlar olduğunu hızla fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="51c22-283">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="51c22-284">Test paketi Salı günü çalıştırırsanız, ikinci test geçer, ancak ilk test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="51c22-284">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="51c22-285">Test paketi başka bir günü çalıştırırsanız, ilk test geçer, ancak ikinci test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="51c22-285">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="51c22-286">Bu sorunları çözmek için tanıtmak gerekecektir bir *bağlantı yeri* üretim kodunuzla.</span><span class="sxs-lookup"><span data-stu-id="51c22-286">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="51c22-287">Bir arabirim, denetlemek ve bu arabirimdeki bağımlı üretim kodu için gereken kodu kaydırmak bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="51c22-287">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public bool GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
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

<span data-ttu-id="51c22-288">Test paketiniz artık hale gelir</span><span class="sxs-lookup"><span data-stu-id="51c22-288">Your test suite now becomes</span></span>

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

<span data-ttu-id="51c22-289">Test paketi üzerinde tam denetime sahiptir. Şimdi `DateTime.Now` ve herhangi bir değer yöntemi çağırırken saplama.</span><span class="sxs-lookup"><span data-stu-id="51c22-289">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
