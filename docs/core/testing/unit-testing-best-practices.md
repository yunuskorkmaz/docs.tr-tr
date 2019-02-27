---
title: Birim testleri yazmak için en iyi uygulamalar
description: Bu sürücü kod kalite ve esneklik için .NET Core ve .NET Standard projelerine birim testleri yazmak için en iyi uygulamaları öğrenin.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: 812b89ff163c9d39a658f817495ac12616c28f6f
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836259"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="60159-103">Birim testi .NET Core ve .NET Standard ile en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="60159-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="60159-104">Birim testleri yazma için çok sayıda avantaj vardır; belgeler, regresyonla sağlar ve iyi bir tasarım kolaylaştırmak yardımcı olurlar.</span><span class="sxs-lookup"><span data-stu-id="60159-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="60159-105">Ancak, okuma ve kırılgan sabit bir birim testlerini kod tabanınız üzerinde düzensizliğe benzer zararlar verecektir.</span><span class="sxs-lookup"><span data-stu-id="60159-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="60159-106">Bu makalede, .NET Core ve .NET Standard projeleri için birim test tasarımı ile ilgili bazı en iyi uygulamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="60159-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="60159-107">Bu kılavuzda, esnek ve kolay anlaşılır testlerinizi tutmak için birim testleri yazılırken bazı en iyi uygulamaları öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="60159-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="60159-108">Tarafından [John Reese](https://reese.dev) performanstan özel ile [Roy Osherove](http://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="60159-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="60159-109">Neden birim testi?</span><span class="sxs-lookup"><span data-stu-id="60159-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="60159-110">Daha az zaman işlevsel testleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="60159-110">Less time performing functional tests</span></span>
<span data-ttu-id="60159-111">İşlevsel testleri pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="60159-111">Functional tests are expensive.</span></span> <span data-ttu-id="60159-112">Bunlar genellikle uygulamayı açmaktan ve bir dizi (veya bir başkasının), Beklenen davranış doğrulayabilmek izlemelidir adımları gerçekleştirerek de içerir.</span><span class="sxs-lookup"><span data-stu-id="60159-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="60159-113">Bu adımları her zaman daha bilgili birine alanı test gerçekleştirmek için ulaşmak olacağı anlamına gelir test edici için bilinmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="60159-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="60159-114">Kendi test Önemsiz değişiklikleri saniye veya daha büyük değişikliklerin dakika sürebilir.</span><span class="sxs-lookup"><span data-stu-id="60159-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="60159-115">Son olarak, bu işlem her değişiklik için sistemde yaptığınız yinelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="60159-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="60159-116">Birim testleri, diğer el, milisaniye almak, bir düğmeye basarak çalıştırılabilir ve büyük sistemin herhangi bir Bilgi Bankası gerektirmeyebilecek.</span><span class="sxs-lookup"><span data-stu-id="60159-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="60159-117">Testin geçtiğini veya başarısız olup olmadığını test Çalıştırıcısı kadar kişi var.</span><span class="sxs-lookup"><span data-stu-id="60159-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="60159-118">Regresyon karşı koruma</span><span class="sxs-lookup"><span data-stu-id="60159-118">Protection against regression</span></span>
<span data-ttu-id="60159-119">Regresyon hataları uygulamada bir değişiklik yapıldığında, sunulan hatalar var.</span><span class="sxs-lookup"><span data-stu-id="60159-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="60159-120">Yalnızca test ediciler, yeni bir özellik test ancak beklendiği gibi özellikleri daha önce uygulanan doğrulamak için önceden varolan özellikleri işlevi ayrıca hala yaygındır.</span><span class="sxs-lookup"><span data-stu-id="60159-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="60159-121">Birim testi ile her derlemeden sonra veya bir kod satırı değiştirdikten sonra bile, tüm testleri paketi yeniden çalıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="60159-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="60159-122">Size yeni kodunuz var olan işlevselliği kesmez güvenilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="60159-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="60159-123">Yürütülebilir belgeleri</span><span class="sxs-lookup"><span data-stu-id="60159-123">Executable documentation</span></span>
<span data-ttu-id="60159-124">Bu her zaman belirli bir yöntem yapar veya belirli bir giriş nasıl davrandığını belirgin olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="60159-125">Kendiniz isteyebilir: Boş bir dize başarılı olursa bu yöntem nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="60159-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="60159-126">Null?</span><span class="sxs-lookup"><span data-stu-id="60159-126">Null?</span></span>

<span data-ttu-id="60159-127">İyi adlandırılmış birim testleri paketi varsa, her test açıkça belirtilen bir giriş için beklenen çıktıyı açıklamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="60159-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="60159-128">Ayrıca, aslında çalışıp çalışmadığını doğrulayabilirsiniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60159-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="60159-129">Daha az bağlı kod</span><span class="sxs-lookup"><span data-stu-id="60159-129">Less coupled code</span></span>
<span data-ttu-id="60159-130">Kod sıkı şekilde bağlı olduğunda, birim testi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="60159-131">Yazmakta olduğunuz koda yönelik birim testleri oluşturmadan bağlantısından daha az görünür olabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="60159-132">Aksi takdirde test daha zor olduğundan kodunuz için testleri yazmak kodunuzu, doğal olarak ayırmak.</span><span class="sxs-lookup"><span data-stu-id="60159-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="60159-133">İyi birim testi özellikleri</span><span class="sxs-lookup"><span data-stu-id="60159-133">Characteristics of a good unit test</span></span>
- <span data-ttu-id="60159-134">**Hızlı**.</span><span class="sxs-lookup"><span data-stu-id="60159-134">**Fast**.</span></span> <span data-ttu-id="60159-135">Seyrek olgun projeleri için birim testleri binlerce sahip değil.</span><span class="sxs-lookup"><span data-stu-id="60159-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="60159-136">Birim testleri çalıştırmak için çok az zamanınız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60159-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="60159-137">Milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="60159-137">Milliseconds.</span></span>
- <span data-ttu-id="60159-138">**Yalıtılmış**.</span><span class="sxs-lookup"><span data-stu-id="60159-138">**Isolated**.</span></span> <span data-ttu-id="60159-139">Birim testleri tek başına olan, yalıtılmış olarak çalıştırabilir ve herhangi bir dosya sistemi veya veritabanı gibi faktörlere dışında hiçbir bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="60159-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="60159-140">**Tekrarlanabilir**.</span><span class="sxs-lookup"><span data-stu-id="60159-140">**Repeatable**.</span></span> <span data-ttu-id="60159-141">Birim testi sonuçlarını ile tutarlı olmalıdır, çalıştırmaları arasında herhangi bir şey değiştirmezseniz diğer bir deyişle, her zaman aynı sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="60159-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="60159-142">**Kendi kendine denetimi**.</span><span class="sxs-lookup"><span data-stu-id="60159-142">**Self-Checking**.</span></span> <span data-ttu-id="60159-143">Test, Geçti veya insan etkileşimi başarısız olursa otomatik olarak algılayabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60159-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="60159-144">**Zamanında**.</span><span class="sxs-lookup"><span data-stu-id="60159-144">**Timely**.</span></span> <span data-ttu-id="60159-145">Birim testi test edilen kodu karşılaştırılan yazma orantısız uzun sürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="60159-145">A unit test should not take a disproportionally long time to write compared to the code being tested.</span></span> <span data-ttu-id="60159-146">Çok miktarda kod yazmaya kıyasla saat sürüyor kodu test etmek bulursanız, daha fazla test edilebilir bir tasarım kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="60159-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="60159-147">Aynı dili şimdi konuşun</span><span class="sxs-lookup"><span data-stu-id="60159-147">Let's speak the same language</span></span>
<span data-ttu-id="60159-148">Terim *sahte* testi hakkında konuşurken ne yazık ki çok yanlış kullanılmış olan.</span><span class="sxs-lookup"><span data-stu-id="60159-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="60159-149">En yaygın türleri, aşağıdaki tanımlar *fakes* birim testleri yazılırken:</span><span class="sxs-lookup"><span data-stu-id="60159-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="60159-150">*Sahte* -sahte bir saplama veya sahte bir nesne tanımlamak için kullanılan genel bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="60159-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="60159-151">Bir saplama veya sahte bir olup olmadığını, kullanıldığı bağlam üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="60159-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="60159-152">Bu nedenle başka bir deyişle, sahte bir saplama veya bir sahte olabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="60159-153">*Sahte* -sahte bir nesne bir sahte bir birim testi geçti veya başarısız olup olmadığını karar sistemde nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="60159-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="60159-154">Karşı onaylanan kadar bir Sahne sahte başlar.</span><span class="sxs-lookup"><span data-stu-id="60159-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="60159-155">*Saplama* -bir saplama sistemde mevcut bağımlılık (veya ortak çalışanı) denetlenebilir bir ardılı olan.</span><span class="sxs-lookup"><span data-stu-id="60159-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="60159-156">Bir saplama kullanarak kodunuzu doğrudan bağımlılık uğraşmanızı olmadan test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60159-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="60159-157">Varsayılan olarak, sahte bir saplama başlar.</span><span class="sxs-lookup"><span data-stu-id="60159-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="60159-158">Aşağıdaki kod parçacığı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="60159-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="60159-159">Bu, kalıntı bir Sahne başvurulan bir örneği olabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="60159-160">Bu durumda, bir saptama olur.</span><span class="sxs-lookup"><span data-stu-id="60159-160">In this case, it is a stub.</span></span> <span data-ttu-id="60159-161">Yalnızca örneklemek için bir yol sırada geçirme `Purchase` (test altındaki sistem).</span><span class="sxs-lookup"><span data-stu-id="60159-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="60159-162">Adı `MockOrder` yeniden sırasını sahte bir de çok yanıltıcı olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="60159-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="60159-163">Daha iyi bir yaklaşım olacaktır</span><span class="sxs-lookup"><span data-stu-id="60159-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="60159-164">Sınıfı yeniden adlandırarak `FakeOrder`sınıfı çok daha genel yaptığınız, sınıfı bir sahte veya bir saplama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="60159-165">Hangisi, test çalışması için iyidir.</span><span class="sxs-lookup"><span data-stu-id="60159-165">Whichever is better for the test case.</span></span> <span data-ttu-id="60159-166">Yukarıdaki örnekte, `FakeOrder` yer tutucusu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60159-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="60159-167">Kullanmadığınız `FakeOrder` assert sırasında herhangi bir şekil veya biçimde.</span><span class="sxs-lookup"><span data-stu-id="60159-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="60159-168">`FakeOrder` yalnızca içine geçirilen `Purchase` Oluşturucu gereksinimlerini karşılamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="60159-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="60159-169">Bir Sahne kullanmak için aşağıdakine benzer yapabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="60159-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="60159-170">Bu durumda, (karşı sunduğundan), sahte bu nedenle Yukarıdaki kod parçacığında, bir özellik denetimi `mockOrder` bir sahte olduğu.</span><span class="sxs-lookup"><span data-stu-id="60159-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="60159-171">Bu terimler doğru almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="60159-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="60159-172">"Mocks", saptamalar çağırırsanız, diğer geliştiriciler, amacı hakkında varsayımlar false oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="60159-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="60159-173">Bir saplama karşı assert değil ise mocks yer tutucular yerine ilgili hatırlamak ana mocks yalnızca saptamalar gibi olan, ancak sahte bir nesneye karşı assert şeydir.</span><span class="sxs-lookup"><span data-stu-id="60159-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="60159-174">Önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="60159-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="60159-175">Testlerinizi adlandırma</span><span class="sxs-lookup"><span data-stu-id="60159-175">Naming your tests</span></span>
<span data-ttu-id="60159-176">Test adı üç bölümden oluşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="60159-176">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="60159-177">Test edilen yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="60159-177">The name of the method being tested.</span></span>
- <span data-ttu-id="60159-178">Altında sınanır senaryo.</span><span class="sxs-lookup"><span data-stu-id="60159-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="60159-179">Senaryo çağrıldığında Beklenen davranış.</span><span class="sxs-lookup"><span data-stu-id="60159-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="60159-180">Neden?</span><span class="sxs-lookup"><span data-stu-id="60159-180">Why?</span></span>
- <span data-ttu-id="60159-181">Adlandırma standartlarına, bunlar test amacı açıkça express için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="60159-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="60159-182">Testler daha fazlasını bulunduğunuzdan emin kodunuzun çalıştığı da sağladıkları belgeleri.</span><span class="sxs-lookup"><span data-stu-id="60159-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="60159-183">Yalnızca birim testleri suite'e bakarak bile koda göz bakmadan kodunuzu davranışını belirleyebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60159-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="60159-184">Ayrıca, test başarısız olduğunda, tam olarak hangi senaryoların beklentilerinizi karşılamayan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60159-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="60159-185">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="60159-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="60159-186">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="60159-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="60159-187">Testlerinizi Düzenleme</span><span class="sxs-lookup"><span data-stu-id="60159-187">Arranging your tests</span></span>
<span data-ttu-id="60159-188">**Düzenleme, hareket, onaylama işlemi** yaygın olduğu zaman desen birim testi.</span><span class="sxs-lookup"><span data-stu-id="60159-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="60159-189">Adından da anlaşılacağı gibi üç ana eylemden oluşur:</span><span class="sxs-lookup"><span data-stu-id="60159-189">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="60159-190">*Düzenleme* nesnelerinizi, oluşturma ve bunları gerektiği şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="60159-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="60159-191">*ACT* bir nesne üzerinde.</span><span class="sxs-lookup"><span data-stu-id="60159-191">*Act* on an object.</span></span>
- <span data-ttu-id="60159-192">*Assert* , beklendiği gibi bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="60159-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="60159-193">Neden?</span><span class="sxs-lookup"><span data-stu-id="60159-193">Why?</span></span>
- <span data-ttu-id="60159-194">Açıkça ne gelen edildiğini ayıran *düzenleme* ve *assert* adımları.</span><span class="sxs-lookup"><span data-stu-id="60159-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="60159-195">"Eylem" kodlu bir onayları intermix olasılığı daha az.</span><span class="sxs-lookup"><span data-stu-id="60159-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="60159-196">Okunabilirlik en önemli yönlerinden test yazarken biridir.</span><span class="sxs-lookup"><span data-stu-id="60159-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="60159-197">Test içinde bu eylemlerin her birine ayırarak açıkça kodunuzu, kodunuzu nasıl çağrılan ve onay çalıştığınız çağırmak için gereken bağımlılıklar vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="60159-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="60159-198">Bazı adımlar birleştirin ve testinizi boyutunu küçültmek mümkün olabilir, ancak birincil amacı, test olarak okunabilir olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="60159-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="60159-199">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="60159-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="60159-200">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="60159-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="60159-201">En düşük düzeyde geçirme testleri yazma</span><span class="sxs-lookup"><span data-stu-id="60159-201">Write minimally passing tests</span></span>
<span data-ttu-id="60159-202">Şu anda test ettiğiniz davranışına doğrulamak için bir birim testinde kullanılacak giriş basit mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60159-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="60159-203">Neden?</span><span class="sxs-lookup"><span data-stu-id="60159-203">Why?</span></span>
- <span data-ttu-id="60159-204">Testler kod tabanındaki gelecekteki değişikliklere daha dayanıklı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="60159-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="60159-205">Uygulama davranışı test yakın.</span><span class="sxs-lookup"><span data-stu-id="60159-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="60159-206">Test geçirmek için gerekenden daha fazla bilgi içeren testler hataları teste giriş, daha yüksek şansına sahip olabilirsiniz ve amacı, az NET test yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60159-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="60159-207">Testleri yazılırken davranışı odaklanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="60159-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="60159-208">Modeller üzerinde ek özellikleri ayarlamak veya gerekli olduğunda sıfır olmayan değerler kullanarak, yalnızca ne kanıtlamak çalışıyorsunuz gelen detracts.</span><span class="sxs-lookup"><span data-stu-id="60159-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="60159-209">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="60159-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="60159-210">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="60159-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="60159-211">Sihirli dize kaçının</span><span class="sxs-lookup"><span data-stu-id="60159-211">Avoid magic strings</span></span>
<span data-ttu-id="60159-212">Değişkenleri adlandırma birim testleri gibi önemli değil daha da önemlisi, üretim kodunda adlandırma değişkenleri daha.</span><span class="sxs-lookup"><span data-stu-id="60159-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="60159-213">Birim testleri Sihirli dize içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="60159-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="60159-214">Neden?</span><span class="sxs-lookup"><span data-stu-id="60159-214">Why?</span></span>
- <span data-ttu-id="60159-215">Değer özel kılan anlamak için üretim kodu incelemek için gereken test okuyucu engeller.</span><span class="sxs-lookup"><span data-stu-id="60159-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="60159-216">Açmaya çalıştığınız açıkça gösterir *kanıtlamak* çalışılırken yerine *gerçekleştirmek*.</span><span class="sxs-lookup"><span data-stu-id="60159-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="60159-217">Sihirli dize testlerinizin Okuyucu için karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="60159-218">Bir dize normal dışı görünüyorsa, bunlar belirli bir değer için bir parametre neden seçildiğini merak ediyor veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="60159-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="60159-219">Bu test yakından odak yerine uygulama ayrıntılarını almak için bunları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="60159-220">Testleri yazılırken, mümkün olduğunca fazla hedefi ifade etmek için indirmeyi amaçlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60159-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="60159-221">Sihirli dize söz konusu olduğunda, bu değerleri sabitleri atama iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="60159-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="60159-222">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="60159-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="60159-223">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="60159-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="60159-224">Testleri mantığı kaçının</span><span class="sxs-lookup"><span data-stu-id="60159-224">Avoid logic in tests</span></span>
<span data-ttu-id="60159-225">Birim testleri önlemek el ile dize birleştirme ve mantıksal gibi koşullar yazılırken `if`, `while`, `for`, `switch`vb.</span><span class="sxs-lookup"><span data-stu-id="60159-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="60159-226">Neden?</span><span class="sxs-lookup"><span data-stu-id="60159-226">Why?</span></span>
- <span data-ttu-id="60159-227">Testlerinizi içinde bir hata tanıtmak için fırsat daha az.</span><span class="sxs-lookup"><span data-stu-id="60159-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="60159-228">Sonuç, yerine uygulama ayrıntılarını odaklanın.</span><span class="sxs-lookup"><span data-stu-id="60159-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="60159-229">Mantıksal test paketiniz aldığımızda, içine bir hata ile tanışın olasılığını önemli ölçüde artırır.</span><span class="sxs-lookup"><span data-stu-id="60159-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="60159-230">Bir hatayı bulmak için istediğiniz son içinde test çalışmalarıyla yerdir.</span><span class="sxs-lookup"><span data-stu-id="60159-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="60159-231">Testlerinizi iş güvenle yüksek düzeyde olmalıdır, aksi takdirde, bunları güvenir değil.</span><span class="sxs-lookup"><span data-stu-id="60159-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="60159-232">Güvenmediğiniz, testler herhangi bir değer sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="60159-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="60159-233">Bir test başarısız olduğunda, bir şeyin aslında kodunuzla yanlış olduğunu ve bunu göz ardı edilemez olduğunu bir fikir edindiniz istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="60159-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="60159-234">Testinizde mantıksal kaçınılmaz görünüyorsa, iki veya daha fazla farklı testlere test bölmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="60159-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="60159-235">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="60159-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="60159-236">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="60159-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="60159-237">Kurulumu ve kaldırma için yardımcı yöntemler tercih et</span><span class="sxs-lookup"><span data-stu-id="60159-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="60159-238">Testleriniz için benzer bir nesne ya da durum gerekiyorsa, bir yardımcı yöntemi varsa, kurulumu ve kaldırma öznitelikleri yararlanarak daha tercih eder.</span><span class="sxs-lookup"><span data-stu-id="60159-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="60159-239">Neden?</span><span class="sxs-lookup"><span data-stu-id="60159-239">Why?</span></span>
- <span data-ttu-id="60159-240">Daha az karışıklık, testlerin tüm kodu beri okunurken her test içinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="60159-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="60159-241">Çok fazla veya çok küçük bir verilen test için kurma olasılığı daha az.</span><span class="sxs-lookup"><span data-stu-id="60159-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="60159-242">Bunlar arasında istenmeyen bağımlılıklar oluşturan testleri arasında durum paylaşma şansı daha az.</span><span class="sxs-lookup"><span data-stu-id="60159-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="60159-243">Birim test çerçeveleri, `Setup` içinde test çalışmalarıyla her birim testi önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="60159-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="60159-244">Bazı faydalı bir araç olarak görebilir, ancak bu genellikle için bloated ve testleri okunmasını sonlanan sona erer.</span><span class="sxs-lookup"><span data-stu-id="60159-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="60159-245">Her test genellikle test çalıştırmaya almak için farklı gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="60159-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="60159-246">Ne yazık ki `Setup` , her test için aynı gereksinimlerinin tamamı kullanmaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="60159-247">xUnit sürümden itibaren kaldırdı hem kurulumu ve kaldırma 2.x</span><span class="sxs-lookup"><span data-stu-id="60159-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="60159-248">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="60159-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="60159-249">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="60159-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="60159-250">Birden çok önlemek onaylar</span><span class="sxs-lookup"><span data-stu-id="60159-250">Avoid multiple asserts</span></span>
<span data-ttu-id="60159-251">Testlerinizi yazarken, yalnızca test başına bir onay içerecek şekilde deneyin.</span><span class="sxs-lookup"><span data-stu-id="60159-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="60159-252">Yalnızca birini kullanarak genel yaklaşımları onaylama Ekle:</span><span class="sxs-lookup"><span data-stu-id="60159-252">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="60159-253">Her onay için ayrı bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="60159-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="60159-254">Parametreli testleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="60159-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="60159-255">Neden?</span><span class="sxs-lookup"><span data-stu-id="60159-255">Why?</span></span>
- <span data-ttu-id="60159-256">Bir onay başarısız olursa, sonraki Asserts değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="60159-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="60159-257">Birden çok durum testlerinizde sunduğundan değil sağlar.</span><span class="sxs-lookup"><span data-stu-id="60159-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="60159-258">Testlerinizi neden başarısız dair tüm resim sunar.</span><span class="sxs-lookup"><span data-stu-id="60159-258">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="60159-259">Birden çok giriş için bir test çalışmasına onaylar, bu, tüm garanti edilmez, onaylar yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="60159-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="60159-260">Onaylama başarısız bir birim test, sonra çoğu birim testi çerçevelerini içinde devam etmeden testleri otomatik olarak başarısız olduğunu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="60159-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="60159-261">Gerçekten çalışmaktadır, işlevselliği gösterilecek şekilde başarısız olarak bu kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="60159-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="60159-262">Bir nesneye karşı sunduğundan bu kural için ortak bir özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="60159-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="60159-263">Bu durumda olması genellikle kabul edilebilirdir nesne, olmasını beklediğiniz durumunda olduğundan emin olmak için her bir özellik karşı birden çok onaylar.</span><span class="sxs-lookup"><span data-stu-id="60159-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="60159-264">Hatalı:</span><span class="sxs-lookup"><span data-stu-id="60159-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="60159-265">Daha iyi:</span><span class="sxs-lookup"><span data-stu-id="60159-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="60159-266">Özel birim testi genel yöntemleri yöntemle doğrula</span><span class="sxs-lookup"><span data-stu-id="60159-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="60159-267">Çoğu durumda olmamalıdır test bir özel yöntemi gerekir.</span><span class="sxs-lookup"><span data-stu-id="60159-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="60159-268">Bir uygulama ayrıntısı özel yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="60159-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="60159-269">Bunu bu şekilde düşünebilirsiniz: özel yöntemler yalıtım modunda hiçbir zaman yok.</span><span class="sxs-lookup"><span data-stu-id="60159-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="60159-270">Belirli bir noktada oluşacak uygulanması bir parçası olarak özel yöntemi çağıran bir genel kullanıma yönelik yöntemi.</span><span class="sxs-lookup"><span data-stu-id="60159-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="60159-271">Önem verdiğiniz metodun özel bir çağıran son sonucudur.</span><span class="sxs-lookup"><span data-stu-id="60159-271">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="60159-272">Aşağıdaki örneği inceleyin</span><span class="sxs-lookup"><span data-stu-id="60159-272">Consider the following case</span></span>

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

<span data-ttu-id="60159-273">Bir test için yazmaya başlamak için ilk tepkinizi olabilir `trimInput` yöntemi beklendiği gibi çalıştığından emin olmak istememiz.</span><span class="sxs-lookup"><span data-stu-id="60159-273">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="60159-274">Ancak, bu tamamen mümkündür, `ParseLogLine` yöneten `sanitizedInput` gibi bir sınaması işleme beklediğiniz olmayan bir şekilde `trimInput` gereksiz.</span><span class="sxs-lookup"><span data-stu-id="60159-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="60159-275">Gerçek bir testin genel kullanıma yönelik yöntemi karşı yapılmalıdır `ParseLogLine` ne sonuçta verdiğiniz, çünkü.</span><span class="sxs-lookup"><span data-stu-id="60159-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="60159-276">Bu bakış açısı ile özel bir yöntem görürseniz, genel yöntemini bulun ve karşı bu yöntemi testlerinizi yazın.</span><span class="sxs-lookup"><span data-stu-id="60159-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="60159-277">Özel bir yöntem yalnızca beklenen sonuç döndürdüğünden, sonunda özel yöntemi çağıran sistem sonucu doğru kullandığı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="60159-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="60159-278">Saplama statik başvuruları</span><span class="sxs-lookup"><span data-stu-id="60159-278">Stub static references</span></span>
<span data-ttu-id="60159-279">İlkeleri bir birim testinin, test altındaki sistem tam denetimi olmalıdır biridir.</span><span class="sxs-lookup"><span data-stu-id="60159-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="60159-280">Üretim kodu statik başvuruları çağrıları içerdiğinde bu sorunlu olabilir (örneğin `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="60159-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="60159-281">Aşağıdaki kodu düşünün</span><span class="sxs-lookup"><span data-stu-id="60159-281">Consider the following code</span></span>

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

<span data-ttu-id="60159-282">Nasıl Bu kod, birim test büyük olasılıkla olabilir?</span><span class="sxs-lookup"><span data-stu-id="60159-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="60159-283">Bir yaklaşım gibi çalışabilir</span><span class="sxs-lookup"><span data-stu-id="60159-283">You may try an approach such as</span></span>

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

<span data-ttu-id="60159-284">Ne yazık ki, testlerinizi birkaç sorunlar olduğunu hızla fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="60159-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="60159-285">Test paketi Salı günü çalıştırırsanız, ikinci test geçer, ancak ilk test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="60159-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="60159-286">Test paketi başka bir günü çalıştırırsanız, ilk test geçer, ancak ikinci test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="60159-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="60159-287">Bu sorunları çözmek için tanıtmak gerekecektir bir *bağlantı yeri* üretim kodunuzla.</span><span class="sxs-lookup"><span data-stu-id="60159-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="60159-288">Bir arabirim, denetlemek ve bu arabirimdeki bağımlı üretim kodu için gereken kodu kaydırmak bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="60159-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

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

<span data-ttu-id="60159-289">Test paketiniz artık hale gelir</span><span class="sxs-lookup"><span data-stu-id="60159-289">Your test suite now becomes</span></span>

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

<span data-ttu-id="60159-290">Test paketi üzerinde tam denetime sahiptir. Şimdi `DateTime.Now` ve herhangi bir değer yöntemi çağırırken saplama.</span><span class="sxs-lookup"><span data-stu-id="60159-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
