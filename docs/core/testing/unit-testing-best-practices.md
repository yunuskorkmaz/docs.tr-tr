---
title: Birim testlerini yazmak için en iyi uygulamalar
description: .NET Core ve .NET Standard projeleri için Code Quality ve esnekliği çalıştıran birim testlerini yazmak için en iyi yöntemleri öğrenin.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 9115ff69b269e3723820fd8505d1a9f8ca278d12
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989375"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="7152e-103">.NET Core ve .NET Standard ile birim testi en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="7152e-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="7152e-104">Birim testlerini yazmanın çok sayıda avantajı vardır; gerileme sayesinde, belge sağlar ve iyi tasarımı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7152e-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="7152e-105">Ancak, okuma ve Brittle birim testleri, kod tabanınız üzerinde wreak düzensizliğe olabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="7152e-106">Bu makalede, .NET Core ve .NET Standard projeleriniz için birim testi tasarımı ile ilgili bazı en iyi yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7152e-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="7152e-107">Bu kılavuzda, testlerinizi dayanıklı ve kolay bir şekilde anlamak için birim testlerini yazarken bazı en iyi yöntemleri öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="7152e-108">[John Reese](https://reese.dev) tarafından, [Roy Osherove](https://osherove.com/) için teşekkürler</span><span class="sxs-lookup"><span data-stu-id="7152e-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="7152e-109">Birim testi neden?</span><span class="sxs-lookup"><span data-stu-id="7152e-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="7152e-110">İşlevsel testleri daha az zaman gerçekleştiriyor</span><span class="sxs-lookup"><span data-stu-id="7152e-110">Less time performing functional tests</span></span>
<span data-ttu-id="7152e-111">İşlevsel testler pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="7152e-111">Functional tests are expensive.</span></span> <span data-ttu-id="7152e-112">Genellikle uygulamayı açıp, beklenen davranışı doğrulamak için sizin (ya da başka birinin) izlemeniz gereken bir dizi adımı gerçekleştirerek.</span><span class="sxs-lookup"><span data-stu-id="7152e-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="7152e-113">Bu adımlar, her zaman sınayıcı tarafından bilinmeyebilir, bu da testi yürütmek için alana daha bilgili bir kişiye ulaşmaları gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7152e-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="7152e-114">Kendisini test etmek, önemsiz değişiklikler için saniye veya daha büyük değişiklikler için dakikalar alabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="7152e-115">Son olarak, bu işlem sistemde yaptığınız her değişiklik için tekrarlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7152e-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="7152e-116">Diğer yandan birim testleri, diğer taraftan, bir düğmeye basarak çalıştırılabilir ve çok büyük bir sistem bilgisi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="7152e-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="7152e-117">Testin başarılı veya başarısız olmasına bakılmaksızın, bireysel olarak değil Test Çalıştırıcısına.</span><span class="sxs-lookup"><span data-stu-id="7152e-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="7152e-118">Gerileme karşı koruma</span><span class="sxs-lookup"><span data-stu-id="7152e-118">Protection against regression</span></span>
<span data-ttu-id="7152e-119">Gerileme hataları, uygulamada bir değişiklik yapıldığında ortaya çıkan arızalardır.</span><span class="sxs-lookup"><span data-stu-id="7152e-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="7152e-120">Test ediciler için, yalnızca yeni özelliklerini test etmek ve daha önce uygulanan özelliklerin beklendiği gibi çalıştığını doğrulamak için önceden varolan özellikleri test etmek yaygın bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="7152e-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="7152e-121">Birim testinde, her derlemeden sonra veya bir kod satırını değiştirdikten sonra bile tüm test paketlerinizi yeniden çalıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7152e-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="7152e-122">Yeni kodunuzun mevcut işlevselliği bozmadığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="7152e-123">Yürütülebilir belge</span><span class="sxs-lookup"><span data-stu-id="7152e-123">Executable documentation</span></span>
<span data-ttu-id="7152e-124">Belirli bir yöntemin ne yaptığını veya belirli bir giriş verilen bir girişi nasıl davranacağını her zaman açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="7152e-125">Kendinize şunu sorabilirsiniz: boş bir dize geçirdiğimde bu yöntem nasıl davranır?</span><span class="sxs-lookup"><span data-stu-id="7152e-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="7152e-126">Değer?</span><span class="sxs-lookup"><span data-stu-id="7152e-126">Null?</span></span>

<span data-ttu-id="7152e-127">Bir iyi adlı birim testi paketiniz olduğunda, her bir test, belirli bir giriş için beklenen çıktıyı açıkça açıklayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="7152e-128">Ayrıca, aslında gerçekten çalıştığını doğrulayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="7152e-129">Daha az bağlanmış kod</span><span class="sxs-lookup"><span data-stu-id="7152e-129">Less coupled code</span></span>
<span data-ttu-id="7152e-130">Kod sıkı bir şekilde birleştirildiğinde, birim testi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="7152e-131">Yazmakta olduğunuz kod için birim testleri oluşturmadan, bağlantısı daha az görünebilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="7152e-132">Kodunuz için yazma testleri doğal olarak kodunuzu ayırır, çünkü aksi takdirde test daha zordur.</span><span class="sxs-lookup"><span data-stu-id="7152e-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="7152e-133">İyi birim testinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="7152e-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="7152e-134">**Hızlı**.</span><span class="sxs-lookup"><span data-stu-id="7152e-134">**Fast**.</span></span> <span data-ttu-id="7152e-135">Yetişkinlere yönelik projelerin binlerce birim testi olması için bu, yaygın olmayan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="7152e-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="7152e-136">Birim testlerinin çalışması çok az zaman almalıdır.</span><span class="sxs-lookup"><span data-stu-id="7152e-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="7152e-137">Mayacak.</span><span class="sxs-lookup"><span data-stu-id="7152e-137">Milliseconds.</span></span>
- <span data-ttu-id="7152e-138">**Yalıtılmıştır**.</span><span class="sxs-lookup"><span data-stu-id="7152e-138">**Isolated**.</span></span> <span data-ttu-id="7152e-139">Birim testleri tek başına, yalıtımıyla çalıştırılabilir ve dosya sistemi veya veritabanı gibi herhangi bir dış faktörde bağımlılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="7152e-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="7152e-140">**Yinelenebilir**.</span><span class="sxs-lookup"><span data-stu-id="7152e-140">**Repeatable**.</span></span> <span data-ttu-id="7152e-141">Bir birim testinin çalıştırılması sonuçlarıyla tutarlı olmalıdır, diğer bir deyişle, çalışma arasındaki herhangi bir şeyi değiştirmemelisiniz, her zaman aynı sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7152e-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="7152e-142">**Kendi kendine denetim**.</span><span class="sxs-lookup"><span data-stu-id="7152e-142">**Self-Checking**.</span></span> <span data-ttu-id="7152e-143">Testin, herhangi bir insan etkileşimi olmadan başarılı veya başarısız olup olmadığını otomatik olarak algılayabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7152e-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="7152e-144">**Zamanında**.</span><span class="sxs-lookup"><span data-stu-id="7152e-144">**Timely**.</span></span> <span data-ttu-id="7152e-145">Bir birim testinin, test edilmekte olan koda kıyasla yazılması, ne zaman orantılı bir şekilde sürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="7152e-146">Kodu yazmaya kıyasla kodun büyük bir süre sürmesi sınamasını fark ederseniz, daha fazla test edilen bir tasarıma göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7152e-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="code-coverage"></a><span data-ttu-id="7152e-147">Kod kapsamı</span><span class="sxs-lookup"><span data-stu-id="7152e-147">Code coverage</span></span>

<span data-ttu-id="7152e-148">Yüksek kod kapsamı yüzdesi genellikle daha yüksek bir kod kalitesiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-148">A high code coverage percentage is often associated with a higher quality of code.</span></span> <span data-ttu-id="7152e-149">Ancak, *ölçümün kendisi kodun kalitesini belirleyemez.*</span><span class="sxs-lookup"><span data-stu-id="7152e-149">However, the measurement itself *cannot* determine the quality of code.</span></span> <span data-ttu-id="7152e-150">Aşırı hırslı kod kapsamı yüzdesi hedefini ayarlamak, karşı üretken olabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-150">Setting an overly ambitious code coverage percentage goal can be counterproductive.</span></span> <span data-ttu-id="7152e-151">Binlerce koşullu dalı olan karmaşık bir projeyi düşünün ve %95 kod kapsamının hedefini ayarlayadığınızı düşünelim.</span><span class="sxs-lookup"><span data-stu-id="7152e-151">Imagine a complex project with thousands of conditional branches, and imagine that you set a goal of 95% code coverage.</span></span> <span data-ttu-id="7152e-152">Şu anda proje %90 kod kapsamını tutar.</span><span class="sxs-lookup"><span data-stu-id="7152e-152">Currently the project maintains 90% code coverage.</span></span> <span data-ttu-id="7152e-153">Kalan %5 ' teki tüm uç durumlarının hesaba alınması için gereken süre, büyük ölçüde düşük bir miktar olabilir ve değer teklifi hızla azalmıştır.</span><span class="sxs-lookup"><span data-stu-id="7152e-153">The amount of time it takes to account for all of the edge cases in the remaining 5% could be a massive undertaking, and the value proposition quickly diminishes.</span></span>

<span data-ttu-id="7152e-154">Yüksek kod kapsamı yüzdesi başarı göstergesi değildir ve yüksek kod kalitesini göstermez.</span><span class="sxs-lookup"><span data-stu-id="7152e-154">A high code coverage percentage is not an indicator of success, nor does it imply high code quality.</span></span> <span data-ttu-id="7152e-155">It tist, birim testlerin kapsadığı kod miktarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7152e-155">It jusst represents the amount of code that is covered by unit tests.</span></span> <span data-ttu-id="7152e-156">Daha fazla bilgi için bkz. [birim testi kod kapsamı](unit-testing-code-coverage.md).</span><span class="sxs-lookup"><span data-stu-id="7152e-156">For more information, see [unit testing code coverage](unit-testing-code-coverage.md).</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="7152e-157">Aynı dili konuşalım</span><span class="sxs-lookup"><span data-stu-id="7152e-157">Let's speak the same language</span></span>
<span data-ttu-id="7152e-158">Test hakkında konuşurken, *sahte* terimi çok yanlış bir şekilde görülür.</span><span class="sxs-lookup"><span data-stu-id="7152e-158">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="7152e-159">Aşağıda birim testlerini yazarken en yaygın *Fakes* türleri tanımlanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="7152e-159">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="7152e-160">*Sahte* -sahte, bir saplama ya da bir sahte nesne tanımlamakta kullanılabilecek genel bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="7152e-160">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="7152e-161">Bunun bir saplama veya bir sahte olup olmadığı, kullanıldığı bağlama göre değişir.</span><span class="sxs-lookup"><span data-stu-id="7152e-161">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="7152e-162">Diğer bir deyişle, sahte bir saplama veya bir sahte olabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-162">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="7152e-163">*Sahte nesne* , sistem içindeki bir birim testinin geçtiğini veya başarısız olduğunu belirten sahte bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="7152e-163">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="7152e-164">Bir sahte, bir öne çıkana kadar sahte olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7152e-164">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="7152e-165">*Saplama* -bir saplama, sistemdeki mevcut bir bağımlılık (veya ortak çalışan) için denetlenebilir bir değiştirme işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="7152e-165">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="7152e-166">Bir saplama kullanarak, doğrudan bağımlılık ile ilgilenmeden kodunuzu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-166">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="7152e-167">Varsayılan olarak, sahte bir saplama olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7152e-167">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="7152e-168">Aşağıdaki kod parçacığını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7152e-168">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="7152e-169">Bu, sahte olarak başvurulan bir saplama örneği olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7152e-169">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="7152e-170">Bu durumda, bir saplama olur.</span><span class="sxs-lookup"><span data-stu-id="7152e-170">In this case, it is a stub.</span></span> <span data-ttu-id="7152e-171">Siparişi, örneklendirilecek (test edilen sistem) bir yol olarak geçiriyoruz `Purchase` .</span><span class="sxs-lookup"><span data-stu-id="7152e-171">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="7152e-172">Ad `MockOrder` aynı zamanda çok yanıltıcı olduğundan, sıra bir sahte değildir.</span><span class="sxs-lookup"><span data-stu-id="7152e-172">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="7152e-173">Daha iyi bir yaklaşım</span><span class="sxs-lookup"><span data-stu-id="7152e-173">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="7152e-174">Sınıfını olarak yeniden adlandırarak, sınıfı çok `FakeOrder` daha genel hale getirdiğiniz için sınıf, bir sahte veya saplama olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-174">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="7152e-175">Test çalışması için ne olursa daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-175">Whichever is better for the test case.</span></span> <span data-ttu-id="7152e-176">Yukarıdaki örnekte, `FakeOrder` bir saplama olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7152e-176">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="7152e-177">`FakeOrder`Onaylama sırasında herhangi bir şekil veya formda öğesini kullanmıyoruz.</span><span class="sxs-lookup"><span data-stu-id="7152e-177">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="7152e-178">`FakeOrder``Purchase`, oluşturucunun gereksinimlerini karşılamak için yalnızca sınıfa geçildi.</span><span class="sxs-lookup"><span data-stu-id="7152e-178">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="7152e-179">Bunu bir sahte olarak kullanmak için şöyle bir şey yapabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="7152e-179">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="7152e-180">Bu durumda, bir özelliği sahte (buna karşı) olarak denetlemekte, yukarıdaki kod parçacığında bir `mockOrder` sahte olur.</span><span class="sxs-lookup"><span data-stu-id="7152e-180">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7152e-181">Bu terminolojinin doğru olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-181">It's important to get this terminology correct.</span></span> <span data-ttu-id="7152e-182">Saplailerinizi "izlerinizi" çağırırsanız, diğer geliştiriciler sizin amacınızla ilgili yanlış varsayımlar yapar.</span><span class="sxs-lookup"><span data-stu-id="7152e-182">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="7152e-183">Her şeyi ve saplamalar hakkında hatırlayabilmeniz gereken ana şey, her bir saplamaya benzer ancak sahte nesne ile ilgili olarak sizin için onay almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7152e-183">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="7152e-184">En iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="7152e-184">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="7152e-185">Testlerinizi adlandırma</span><span class="sxs-lookup"><span data-stu-id="7152e-185">Naming your tests</span></span>
<span data-ttu-id="7152e-186">Testinizin adı üç bölümden oluşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7152e-186">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="7152e-187">Test edilmekte olan yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="7152e-187">The name of the method being tested.</span></span>
- <span data-ttu-id="7152e-188">Altında test edilmekte olan senaryo.</span><span class="sxs-lookup"><span data-stu-id="7152e-188">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="7152e-189">Senaryo çağrıldığında beklenen davranış.</span><span class="sxs-lookup"><span data-stu-id="7152e-189">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="7152e-190">Neden mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-190">Why?</span></span>

- <span data-ttu-id="7152e-191">Adlandırma standartları, testin amacını açıkça ifade ettiğinden önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-191">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="7152e-192">Testler yalnızca kodunuzun çalıştığından emin olmanızı sağlamaktan daha fazla.</span><span class="sxs-lookup"><span data-stu-id="7152e-192">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="7152e-193">Yalnızca birim testleri paketine bakarak, kodun kendisini araymaksızın bile kodunuzun davranışını çıkarsanbilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-193">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="7152e-194">Ayrıca, testler başarısız olduğunda, beklentilerinizi tam olarak hangi senaryoların karşılayabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-194">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="7152e-195">Kötü:</span><span class="sxs-lookup"><span data-stu-id="7152e-195">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="7152e-196">Görünmesi</span><span class="sxs-lookup"><span data-stu-id="7152e-196">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="7152e-197">Testlerinizi düzenleme</span><span class="sxs-lookup"><span data-stu-id="7152e-197">Arranging your tests</span></span>
<span data-ttu-id="7152e-198">Birim testi yaparken, **düzenleme, Yasası, onaylama** ortak bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="7152e-198">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="7152e-199">Adından da anlaşılacağı gibi, üç ana eylemden oluşur:</span><span class="sxs-lookup"><span data-stu-id="7152e-199">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="7152e-200">Nesnelerinizi *düzenleyin* , oluşturma ve bunları gerektiği şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="7152e-200">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="7152e-201">Bir nesne üzerinde *işlem* yapın.</span><span class="sxs-lookup"><span data-stu-id="7152e-201">*Act* on an object.</span></span>
- <span data-ttu-id="7152e-202">Bir şeyin beklenildiği konusunda bir *onaylama* .</span><span class="sxs-lookup"><span data-stu-id="7152e-202">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="7152e-203">Neden mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-203">Why?</span></span>

- <span data-ttu-id="7152e-204">, *Düzenleme* ve *onaylama* adımlarından ne test edildiğini açıkça ayırır.</span><span class="sxs-lookup"><span data-stu-id="7152e-204">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="7152e-205">"Yasası" kodu ile onayların nasıl karıştıracağından daha az şans vardır.</span><span class="sxs-lookup"><span data-stu-id="7152e-205">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="7152e-206">Okunabilirlik, bir testi yazarken en önemli yönlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="7152e-206">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="7152e-207">Test içindeki bu eylemlerin her birini, kodunuzun çağrılması için gereken bağımlılıkları, kodunuzun nasıl çağrılacağını ve ne yapmaya çalıştığınız hakkında açık bir şekilde vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="7152e-207">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="7152e-208">Bazı adımları birleştirmek ve testinizin boyutunu azaltmak mümkün olsa da, birincil hedef, testi mümkün olduğunca okunabilir hale getirmek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7152e-208">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="7152e-209">Kötü:</span><span class="sxs-lookup"><span data-stu-id="7152e-209">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="7152e-210">Görünmesi</span><span class="sxs-lookup"><span data-stu-id="7152e-210">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="7152e-211">Testleri en düşük düzeyde geçirmeyi yaz</span><span class="sxs-lookup"><span data-stu-id="7152e-211">Write minimally passing tests</span></span>
<span data-ttu-id="7152e-212">Bir birim testinde kullanılacak giriş, şu anda sınamakta olduğunuz davranışı doğrulamak için en basit olabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-212">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="7152e-213">Neden mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-213">Why?</span></span>

- <span data-ttu-id="7152e-214">Testler, kod temelinin gelecekteki değişikliklerine daha dayanıklı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="7152e-214">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="7152e-215">Uygulama üzerinde test davranışına daha yakın.</span><span class="sxs-lookup"><span data-stu-id="7152e-215">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="7152e-216">Testi geçirmek için gerekenden daha fazla bilgi içeren testlerin, teste hata ekleme şansı daha yüksektir ve testin amacını daha az net hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-216">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="7152e-217">Testleri yazarken, davranışa odaklanmak istediğiniz zaman.</span><span class="sxs-lookup"><span data-stu-id="7152e-217">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="7152e-218">Modellerdeki ek özellikleri ayarlama veya gerekmediği zaman sıfır olmayan değerler kullanma, yalnızca kanıtlamaya çalıştığınız kadar olan özelliklerden arının.</span><span class="sxs-lookup"><span data-stu-id="7152e-218">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="7152e-219">Kötü:</span><span class="sxs-lookup"><span data-stu-id="7152e-219">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="7152e-220">Görünmesi</span><span class="sxs-lookup"><span data-stu-id="7152e-220">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="7152e-221">Sihirli dizelerinden kaçının</span><span class="sxs-lookup"><span data-stu-id="7152e-221">Avoid magic strings</span></span>
<span data-ttu-id="7152e-222">Birim testlerinde adlandırma değişkenleri, daha önemli değilse, üretim kodundaki adlandırma değişkenlerinden daha önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="7152e-222">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="7152e-223">Birim testleri sihirli dizeler içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="7152e-223">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="7152e-224">Neden mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-224">Why?</span></span>

- <span data-ttu-id="7152e-225">, Değeri özel hale getiren şeyi anlamak için test okuyucunun üretim kodunu incelemesi gereksinimini ortadan önler.</span><span class="sxs-lookup"><span data-stu-id="7152e-225">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="7152e-226">*Gerçekleştirmeyi*denemek yerine açıkça *kanıtlamaya* çalıştığınız öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="7152e-226">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="7152e-227">Sihirli dizeler, testlerinizin okuyucularına karışmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-227">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="7152e-228">Bir dize sıradan görünüyorsa, bir parametre veya dönüş değeri için belirli bir değerin seçili olduğunu merak edebilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-228">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="7152e-229">Bu, bunlara, teste odaklanmak yerine uygulama ayrıntılarına daha yakından bakmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-229">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="7152e-230">Testleri yazarken, mümkün olduğunca çok amaç ifade etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7152e-230">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="7152e-231">Sihirli dizeler söz konusu olduğunda, bu değerleri sabitlere atamak iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="7152e-231">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="7152e-232">Kötü:</span><span class="sxs-lookup"><span data-stu-id="7152e-232">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="7152e-233">Görünmesi</span><span class="sxs-lookup"><span data-stu-id="7152e-233">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="7152e-234">Sınamalarda mantığın</span><span class="sxs-lookup"><span data-stu-id="7152e-234">Avoid logic in tests</span></span>
<span data-ttu-id="7152e-235">Birim testlerinizi yazarken,,,, `if` `while` `for` vb. el ile dize birleştirmesini ve mantıksal koşulları önleyin `switch` .</span><span class="sxs-lookup"><span data-stu-id="7152e-235">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="7152e-236">Neden mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-236">Why?</span></span>

- <span data-ttu-id="7152e-237">Testlerinizin içindeki bir hatayı tanıtmak için daha az şans.</span><span class="sxs-lookup"><span data-stu-id="7152e-237">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="7152e-238">Uygulama ayrıntıları yerine son sonuca odaklanın.</span><span class="sxs-lookup"><span data-stu-id="7152e-238">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="7152e-239">Test paketiniz için mantık tanıdığınızda, hataya bir hata tanıtma olasılığı önemli ölçüde artar.</span><span class="sxs-lookup"><span data-stu-id="7152e-239">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="7152e-240">Bir hata bulmak istediğiniz son yer, test paketinizin içindedir.</span><span class="sxs-lookup"><span data-stu-id="7152e-240">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="7152e-241">Testlerinizin çalışması için yüksek düzeyde bir güveniniz olması gerekir, aksi takdirde bunlara güvenmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-241">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="7152e-242">Güvenmediğiniz testler, hiçbir değer sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="7152e-242">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="7152e-243">Bir test başarısız olduğunda, kodunuzun kodunuzda gerçekten yanlış olduğunu ve yoksayılıp yoksayılmayacağını belirten bir fikir sahibi olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-243">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="7152e-244">Testinizin mantığı kaçınılmaz görünüyorsa, testi iki veya daha fazla farklı teste bölmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7152e-244">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="7152e-245">Kötü:</span><span class="sxs-lookup"><span data-stu-id="7152e-245">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="7152e-246">Görünmesi</span><span class="sxs-lookup"><span data-stu-id="7152e-246">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="7152e-247">Kurulum ve test etmek için yardımcı yöntemleri tercih etme</span><span class="sxs-lookup"><span data-stu-id="7152e-247">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="7152e-248">Testleriniz için benzer bir nesne veya durum gerekiyorsa, kurulum ve Tearı özniteliklerini kullanmaktan önce bir yardımcı yöntemi tercih edin.</span><span class="sxs-lookup"><span data-stu-id="7152e-248">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="7152e-249">Neden mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-249">Why?</span></span>

- <span data-ttu-id="7152e-250">Tüm kod her test içinde görünür olduğundan testleri okurken daha az karışıklık vardır.</span><span class="sxs-lookup"><span data-stu-id="7152e-250">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="7152e-251">Verilen test için çok fazla veya çok az olma olasılığı daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="7152e-251">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="7152e-252">Aralarında istenmeyen bağımlılıklar oluşturan testler arasında durum paylaşma şansı daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="7152e-252">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="7152e-253">Birim testi çerçeveleri ' nde, `Setup` test paketinizdeki her bir ve her birim testinin önünde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7152e-253">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="7152e-254">Bazıları bunu yararlı bir araç olarak görebilir, ancak testleri okumak için genellikle önde gelen ve zor olacak şekilde sona erer.</span><span class="sxs-lookup"><span data-stu-id="7152e-254">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="7152e-255">Her test, testi çalıştırmak ve çalıştırmak için genellikle farklı gereksinimlere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="7152e-255">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="7152e-256">Ne yazık ki, `Setup` her test için tam olarak aynı gereksinimleri kullanmanıza zorlar.</span><span class="sxs-lookup"><span data-stu-id="7152e-256">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="7152e-257">xUnit, sürüm 2. x itibariyle kurulum ve test düzeyini kaldırdı</span><span class="sxs-lookup"><span data-stu-id="7152e-257">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="7152e-258">Kötü:</span><span class="sxs-lookup"><span data-stu-id="7152e-258">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="7152e-259">Görünmesi</span><span class="sxs-lookup"><span data-stu-id="7152e-259">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="7152e-260">Çoklu Onaylamalar kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="7152e-260">Avoid multiple asserts</span></span>
<span data-ttu-id="7152e-261">Testlerinizi yazarken, her test için yalnızca bir onaylama eklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="7152e-261">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="7152e-262">Yalnızca bir onay kullanımı için yaygın yaklaşımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7152e-262">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="7152e-263">Her onaylama için ayrı bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7152e-263">Create a separate test for each assert.</span></span>
- <span data-ttu-id="7152e-264">Parametreli testleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="7152e-264">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="7152e-265">Neden mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-265">Why?</span></span>

- <span data-ttu-id="7152e-266">Bir onaylama başarısız olursa, sonraki onaylar değerlendirilmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="7152e-266">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="7152e-267">Testlerinizde birden çok durumu ele almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7152e-267">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="7152e-268">Testlerinizin neden başarısız olduğuna ilişkin tüm resmi verir.</span><span class="sxs-lookup"><span data-stu-id="7152e-268">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="7152e-269">Bir test çalışması için birden fazla onay tanıtımı yaparken, tüm Onaylamalar yürütülecektir.</span><span class="sxs-lookup"><span data-stu-id="7152e-269">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="7152e-270">Çoğu birim testi çerçevesi içinde, bir onaylama işlemi bir birim testinde başarısız olduktan sonra, devam eden testler otomatik olarak başarısız sayılır.</span><span class="sxs-lookup"><span data-stu-id="7152e-270">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="7152e-271">Bu, gerçekten çalışmakta olan bir işlev kadar kafa karıştırıcı olabilir, ancak başarısız olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-271">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="7152e-272">Bu kural için genel bir özel durum, bir nesneye yönelik olarak ele geçmiştir.</span><span class="sxs-lookup"><span data-stu-id="7152e-272">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="7152e-273">Bu durumda, nesnenin içinde olmasını istediğiniz durumda olduğundan emin olmak için her bir özelliğe karşı birden fazla onay sağlamak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-273">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="7152e-274">Kötü:</span><span class="sxs-lookup"><span data-stu-id="7152e-274">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="7152e-275">Görünmesi</span><span class="sxs-lookup"><span data-stu-id="7152e-275">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="7152e-276">Özel metotları birim testi genel yöntemlerine göre doğrula</span><span class="sxs-lookup"><span data-stu-id="7152e-276">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="7152e-277">Çoğu durumda, özel bir yöntemi test etmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="7152e-277">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="7152e-278">Özel yöntemler bir uygulama ayrıntısıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="7152e-278">Private methods are an implementation detail.</span></span> <span data-ttu-id="7152e-279">Bunu şu şekilde düşünebilirsiniz: özel yöntemler hiçbir şekilde yalıtımına yok.</span><span class="sxs-lookup"><span data-stu-id="7152e-279">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="7152e-280">Bir noktada, uygulamasının bir parçası olarak özel yöntemi çağıran bir genel kullanıma yönelik yöntem olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7152e-280">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="7152e-281">İlgilenmelisiniz, özel bir yönteme çağrı yapan genel metodun nihai sonucudur.</span><span class="sxs-lookup"><span data-stu-id="7152e-281">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="7152e-282">Aşağıdaki durumu göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="7152e-282">Consider the following case</span></span>

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

<span data-ttu-id="7152e-283">`TrimInput`Yöntemin beklendiği gibi çalıştığından emin olmak istediğiniz için ilk yeniden eyleminiz bir test yazmaya başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-283">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="7152e-284">Ancak, bu `ParseLogLine` `sanitizedInput` şekilde, bir testi gereksiz bir şekilde işlemek için beklenmez `TrimInput` .</span><span class="sxs-lookup"><span data-stu-id="7152e-284">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="7152e-285">Gerçek test, `ParseLogLine` en sonunda ilgilenmelisiniz çünkü bu, son önem verdiğiniz şeydir.</span><span class="sxs-lookup"><span data-stu-id="7152e-285">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="7152e-286">Bu görüş açısından, özel bir yöntem görürseniz ortak yöntemi bulun ve testlerinizi bu yönteme göre yazın.</span><span class="sxs-lookup"><span data-stu-id="7152e-286">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="7152e-287">Özel bir yöntem beklenen sonucu döndürdüğünden, sonuçta özel yöntemi çağıran sistem sonucu doğru bir şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="7152e-287">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="7152e-288">Saplama statik başvuruları</span><span class="sxs-lookup"><span data-stu-id="7152e-288">Stub static references</span></span>
<span data-ttu-id="7152e-289">Bir birim testinin prensipleri, test altındaki sistem üzerinde tam denetime sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7152e-289">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="7152e-290">Bu, üretim kodu statik başvurulara çağrı içerdiğinde (ör.) sorunlu olabilir `DateTime.Now` .</span><span class="sxs-lookup"><span data-stu-id="7152e-290">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="7152e-291">Aşağıdaki kodu göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="7152e-291">Consider the following code</span></span>

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

<span data-ttu-id="7152e-292">Bu kod büyük olasılıkla birim test edilebilir mi?</span><span class="sxs-lookup"><span data-stu-id="7152e-292">How can this code possibly be unit tested?</span></span> <span data-ttu-id="7152e-293">Şöyle bir yaklaşım deneyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="7152e-293">You may try an approach such as</span></span>

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

<span data-ttu-id="7152e-294">Ne yazık ki testlerinizde birkaç sorun olduğunu hızla fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="7152e-294">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="7152e-295">Test paketi bir Salı üzerinde çalışıyorsa ikinci test geçer, ancak ilk test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7152e-295">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="7152e-296">Test paketi başka bir gün üzerinde çalışıyorsa, ilk test geçer, ancak ikinci test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7152e-296">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="7152e-297">Bu sorunları gidermek için, üretim kodunuzda bir *yhar* belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7152e-297">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="7152e-298">Bir yaklaşım, bir arabirimde denetim yapmanız gereken kodu sarmanın ve üretim kodunun bu arabirime bağlı olmasını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7152e-298">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

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

<span data-ttu-id="7152e-299">Test paketiniz artık</span><span class="sxs-lookup"><span data-stu-id="7152e-299">Your test suite now becomes</span></span>

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

<span data-ttu-id="7152e-300">Artık test paketinin üzerinde tam denetimi vardır `DateTime.Now` ve yöntemine çağrı yapıldığında herhangi bir değer bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7152e-300">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
