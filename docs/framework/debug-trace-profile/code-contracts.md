---
title: Kod Sözleşmeleri
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e40f93be7f2dad4a80a4f4d23f61f3c93061751
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977347"
---
# <a name="code-contracts"></a><span data-ttu-id="22566-102">Kod Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="22566-102">Code Contracts</span></span>

<span data-ttu-id="22566-103">Kod sözleşmeleri, önkoşulları ve koşul sonralarına nesne okuduğunuzda kodunuzda belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="22566-103">Code contracts provide a way to specify preconditions, postconditions, and object invariants in your code.</span></span> <span data-ttu-id="22566-104">Önkoşulları, bir metot veya özellik girerken karşılanması gereken gereksinimleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="22566-104">Preconditions are requirements that must be met when entering a method or property.</span></span> <span data-ttu-id="22566-105">Koşul sonralarına beklentileri metot veya özellik kod çıkar zaman açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22566-105">Postconditions describe expectations at the time the method or property code exits.</span></span> <span data-ttu-id="22566-106">Beklenen durum iyi durumda olan bir sınıf için nesne okuduğunuzda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22566-106">Object invariants describe the expected state for a class that is in a good state.</span></span>

<span data-ttu-id="22566-107">Kod sözleşmeleri kodunuzu, derleme zamanı analiz için statik bir Çözümleyicisi ve çalışma zamanı Çözümleyicisi işaretlemek için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="22566-107">Code contracts include classes for marking your code, a static analyzer for compile-time analysis, and a runtime analyzer.</span></span> <span data-ttu-id="22566-108">Kod sözleşmeleri sınıflarını bulunabilir <xref:System.Diagnostics.Contracts> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="22566-108">The classes for code contracts can be found in the <xref:System.Diagnostics.Contracts> namespace.</span></span>

<span data-ttu-id="22566-109">Kod sözleşmeleri avantajları şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="22566-109">The benefits of code contracts include the following:</span></span>

- <span data-ttu-id="22566-110">Test geliştirildi: Kod sözleşmeleri statik sözleşme doğrulama, çalışma zamanı denetimi ve belgeleri oluşturma sağlar.</span><span class="sxs-lookup"><span data-stu-id="22566-110">Improved testing: Code contracts provide static contract verification, runtime checking, and documentation generation.</span></span>

- <span data-ttu-id="22566-111">Otomatik test araçları: Önkoşulları karşılayan değil anlamsız test değişkenlerinin filtreleyerek daha anlamlı Birim testler üretmek için kod sözleşmeleri'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22566-111">Automatic testing tools: You can use code contracts to generate more meaningful unit tests by filtering out meaningless test arguments that do not satisfy preconditions.</span></span>

- <span data-ttu-id="22566-112">Statik doğrulama: Statik denetleyicisi programı çalıştırmadan herhangi bir sözleşme ihlali olup olmadığına karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22566-112">Static verification: The static checker can decide whether there are any contract violations without running the program.</span></span> <span data-ttu-id="22566-113">Null gibi örtük sözleşmeleri denetler başvurusunu kaldırır ve dizi sınırları ve açık anlaşmaları.</span><span class="sxs-lookup"><span data-stu-id="22566-113">It checks for implicit contracts, such as null dereferences and array bounds, and explicit contracts.</span></span>

- <span data-ttu-id="22566-114">Başvuru belgeleri: Belgeleri Oluşturucu bilgi Sözleşmesi ile varolan bir XML belgesi dosyalarının artırmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22566-114">Reference documentation: The documentation generator augments existing XML documentation files with contract information.</span></span> <span data-ttu-id="22566-115">Kullanılabilir stil sayfaları da vardır [Sandcastle](https://github.com/EWSoftware/SHFB) oluşturulan belge sayfalarına sözleşme bölümleri edinecek olmanızdır.</span><span class="sxs-lookup"><span data-stu-id="22566-115">There are also style sheets that can be used with [Sandcastle](https://github.com/EWSoftware/SHFB) so that the generated documentation pages have contract sections.</span></span>

<span data-ttu-id="22566-116">Tüm .NET Framework dillerinde sözleşmeleri hemen yararlanabilirsiniz; Özel ayrıştırıcı veya derleyici yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="22566-116">All .NET Framework languages can immediately take advantage of contracts; you do not have to write a special parser or compiler.</span></span> <span data-ttu-id="22566-117">Bir Visual Studio eklentisi gerçekleştirilecek kod sözleşme analizi düzeyini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="22566-117">A Visual Studio add-in lets you specify the level of code contract analysis to be performed.</span></span> <span data-ttu-id="22566-118">Çözümleyicileri anlaşmalar doğru oluşturulduğunu onaylayın (tür denetimini ve ad çözümlemesi) ve Microsoft Ara dili (MSIL) biçimde sözleşmelerinin derlenmiş form üretebilir.</span><span class="sxs-lookup"><span data-stu-id="22566-118">The analyzers can confirm that the contracts are well-formed (type checking and name resolution) and can produce a compiled form of the contracts in Microsoft intermediate language (MSIL) format.</span></span> <span data-ttu-id="22566-119">Visual Studio'da sözleşmeleri yazma IntelliSense araç tarafından sağlanan standart avantajlarından yararlanmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="22566-119">Authoring contracts in Visual Studio lets you take advantage of the standard IntelliSense provided by the tool.</span></span>

<span data-ttu-id="22566-120">Çoğu sözleşme sınıfı yöntemleri koşullu olarak derlenir; diğer bir deyişle, yalnızca CONTRACTS_FULL, özel bir simge kullanarak tanımlarken bu yöntemlere yapılan çağrılar derleyici yayar `#define` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="22566-120">Most methods in the contract class are conditionally compiled; that is, the compiler emits calls to these methods only when  you define a special symbol, CONTRACTS_FULL, by using the `#define` directive.</span></span> <span data-ttu-id="22566-121">CONTRACTS_FULL sözleşmeleri olmadan kodunuzu yazmanıza olanak tanır `#ifdef` yönergeleri; farklı yapılar, bazı sözleşmeler ve bazı olmadan üretebilir.</span><span class="sxs-lookup"><span data-stu-id="22566-121">CONTRACTS_FULL lets you write contracts in your code without using `#ifdef` directives; you can produce different builds, some with contracts, and some without.</span></span>

<span data-ttu-id="22566-122">Araçlar ve kod sözleşmeleri kullanmaya yönelik ayrıntılı yönergeler için bkz. [kod sözleşmeleri](https://go.microsoft.com/fwlink/?LinkId=152461) MSDN DevLabs Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="22566-122">For tools and detailed instructions for using code contracts, see [Code Contracts](https://go.microsoft.com/fwlink/?LinkId=152461) on the MSDN DevLabs Web site.</span></span>

## <a name="preconditions"></a><span data-ttu-id="22566-123">Önkoşulları</span><span class="sxs-lookup"><span data-stu-id="22566-123">Preconditions</span></span>

<span data-ttu-id="22566-124">Kullanarak önkoşulları ifade edebilirsiniz <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22566-124">You can express preconditions by using the <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="22566-125">Bir yöntem çağrıldığında önkoşulları durumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="22566-125">Preconditions specify state when a method is invoked.</span></span> <span data-ttu-id="22566-126">Bunlar, genellikle geçerli parametre değerleri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22566-126">They are generally used to specify valid parameter values.</span></span> <span data-ttu-id="22566-127">Önkoşullarda belirtildiği tüm üyeleri en az yöntemi olarak olarak erişilebilir olması gerekir; Aksi takdirde, önkoşuluna tüm bir yöntemi çağıranlar tarafından anlaşılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="22566-127">All members that are mentioned in preconditions must be at least as accessible as the method itself; otherwise, the precondition might not be understood by all callers of a method.</span></span> <span data-ttu-id="22566-128">Koşul herhangi bir yan etkisi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="22566-128">The condition must have no side-effects.</span></span> <span data-ttu-id="22566-129">Başarısız önkoşulları çalışma zamanı davranışını çalışma zamanı çözümleyici tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="22566-129">The run-time behavior of failed preconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="22566-130">Örneğin, bu parametre aşağıdaki önkoşul ifade `x` null olmayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22566-130">For example, the following precondition expresses that parameter `x` must be non-null.</span></span>

```csharp
Contract.Requires(x != null);
```

<span data-ttu-id="22566-131">Kodunuz, bir önkoşul hatası belirli bir özel durum throw gerekir, genel aşırı yüklemesini kullanabilirsiniz <xref:System.Diagnostics.Contracts.Contract.Requires%2A> gibi.</span><span class="sxs-lookup"><span data-stu-id="22566-131">If your code must throw a particular exception on failure of a precondition, you can use the generic overload of <xref:System.Diagnostics.Contracts.Contract.Requires%2A> as follows.</span></span>

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a><span data-ttu-id="22566-132">Eski #requires</span><span class="sxs-lookup"><span data-stu-id="22566-132">Legacy Requires Statements</span></span>

<span data-ttu-id="22566-133">Bazı parametre doğrulaması biçiminde çoğu kod içeren `if` - `then` - `throw` kod.</span><span class="sxs-lookup"><span data-stu-id="22566-133">Most code contains some parameter validation in the form of `if`-`then`-`throw` code.</span></span> <span data-ttu-id="22566-134">Sözleşme araçları bu deyimler önkoşulları aşağıdaki durumlarda olarak tanır:</span><span class="sxs-lookup"><span data-stu-id="22566-134">The contract tools recognize these statements as preconditions in the following cases:</span></span>

- <span data-ttu-id="22566-135">Önce bir yöntem içinde herhangi bir deyim deyimlerinizin.</span><span class="sxs-lookup"><span data-stu-id="22566-135">The statements appear before any other statements in a method.</span></span>

- <span data-ttu-id="22566-136">Bu tür ifadeleri kümesinin tamamını açık bir tarafından izlenir <xref:System.Diagnostics.Contracts.Contract> gibi bir çağrı, yöntem çağrısının <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, veya <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22566-136">The entire set of such statements is followed by an explicit <xref:System.Diagnostics.Contracts.Contract> method call, such as a call to the <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, or <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> method.</span></span>

<span data-ttu-id="22566-137">Zaman `if` - `then` - `throw` deyimleri araçları tanıması bunları bilinen bu formda görünen `requires` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="22566-137">When `if`-`then`-`throw` statements appear in this form, the tools recognize them as legacy `requires` statements.</span></span> <span data-ttu-id="22566-138">Diğer bir sözleşme izlerseniz `if` - `then` - `throw` sıra, kod ile bitiş <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22566-138">If no other contracts follow the `if`-`then`-`throw` sequence, end the code with the <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> method.</span></span>

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

<span data-ttu-id="22566-139">Önceki test koşulu çevrilerek önkoşul olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22566-139">Note that the condition in the preceding test is a negated precondition.</span></span> <span data-ttu-id="22566-140">(Gerçek önkoşuluna olacaktır `x != null`.) İleri derecede kısıtlı bir çevrilerek önkoşulu: Önceki örnekte gösterildiği gibi yazılmalıdır; diğer bir deyişle, Hayır içermelidir `else` yan tümceleri ve gövdesini `then` yan tümcesi olmalıdır tek bir `throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="22566-140">(The actual precondition would be `x != null`.) A negated precondition is highly restricted: It must be written as shown in the previous example; that is, it should contain no `else` clauses, and the body of the `then` clause must be a single `throw` statement.</span></span> <span data-ttu-id="22566-141">`if` Sınamadır tabi olmak üzere hem görünürlük kuralları (bkz [kullanım yönergeleri](#usage_guidelines)), ancak `throw` ifadesidir yalnızca saflığa kurallarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="22566-141">The `if` test is subject to both purity and visibility rules (see [Usage Guidelines](#usage_guidelines)), but the `throw` expression is subject only to purity rules.</span></span> <span data-ttu-id="22566-142">Ancak, oluşturulan özel durum türü olarak sözleşme oluştuğu yöntemi olarak görünür olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="22566-142">However, the type of the exception thrown must be as visible as the method in which the contract occurs.</span></span>

## <a name="postconditions"></a><span data-ttu-id="22566-143">Koşul sonralarına</span><span class="sxs-lookup"><span data-stu-id="22566-143">Postconditions</span></span>

<span data-ttu-id="22566-144">Koşul sonralarına sonlandırmasına sözleşmeler için bir yöntem durumunu olur.</span><span class="sxs-lookup"><span data-stu-id="22566-144">Postconditions are contracts for the state of a method when it terminates.</span></span> <span data-ttu-id="22566-145">Bir yöntem çıkmadan önce Sonkoşul denetlenir.</span><span class="sxs-lookup"><span data-stu-id="22566-145">The postcondition is checked just before exiting a method.</span></span> <span data-ttu-id="22566-146">Başarısız bir koşul sonralarına çalışma zamanı davranışını çalışma zamanı çözümleyici tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="22566-146">The run-time behavior of failed postconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="22566-147">Önkoşulları, daha az görünürlük üyeleriyle koşul sonralarına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="22566-147">Unlike preconditions, postconditions may reference members with less visibility.</span></span> <span data-ttu-id="22566-148">Bir istemci anlamak veya mümkün olmayabilir, bazı özel durumu kullanarak Sonkoşul tarafından gösterilen bilgiler kullanır, ancak bu istemcinin yöntemi doğru şekilde kullanma yeteneğini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="22566-148">A client may not be able to understand or make use of some of the information expressed by a postcondition using private state, but this does not affect the client's ability to use the method correctly.</span></span>

### <a name="standard-postconditions"></a><span data-ttu-id="22566-149">Standart koşul Sonralarına</span><span class="sxs-lookup"><span data-stu-id="22566-149">Standard Postconditions</span></span>

<span data-ttu-id="22566-150">Kullanarak standart koşul sonralarına ifade edebilirsiniz <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22566-150">You can express standard postconditions by using the <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> method.</span></span> <span data-ttu-id="22566-151">Koşul sonralarına express olması gereken bir koşul `true` normal sonlandırmada yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22566-151">Postconditions express a condition that must be `true` upon normal termination of the method.</span></span>

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a><span data-ttu-id="22566-152">Olağanüstü bir koşul Sonralarına</span><span class="sxs-lookup"><span data-stu-id="22566-152">Exceptional Postconditions</span></span>

<span data-ttu-id="22566-153">Olağanüstü bir koşul sonralarına olan olmalıdır koşul sonralarına `true` belirli bir özel durumun yöntemi tarafından harekete geçirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="22566-153">Exceptional postconditions are postconditions that should be `true` when a particular exception is thrown by a method.</span></span> <span data-ttu-id="22566-154">Bu koşul sonralarına kullanarak belirtebilirsiniz <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> yöntemi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="22566-154">You can specify these postconditions by using the <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> method, as the following example shows.</span></span>

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

<span data-ttu-id="22566-155">Bağımsız değişken olmalıdır durumdur `true` bir alt türünde bir özel durum olduğunda `T` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="22566-155">The argument is the condition that must be `true` whenever an exception that is a subtype of `T` is thrown.</span></span>

<span data-ttu-id="22566-156">Olağanüstü bir Sonkoşul içinde kullanılacak zor olan bazı özel durum türü vardır.</span><span class="sxs-lookup"><span data-stu-id="22566-156">There are some exception types that are difficult to use in an exceptional postcondition.</span></span> <span data-ttu-id="22566-157">Örneğin, türü kullanılarak <xref:System.Exception> için `T` bir yığın taşması veya diğer denetim imkansız özel durumu olsa bile oluşturulan, özel durum türü ne olursa olsun koşul güvence altına almak için bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="22566-157">For example, using the type <xref:System.Exception> for `T` requires the method to guarantee the condition regardless of the type of exception that is thrown, even if it is a stack overflow or other impossible-to-control exception.</span></span> <span data-ttu-id="22566-158">Olağanüstü bir koşul sonralarına üyesi, örneğin, ne zaman çağrıldığında oluşturulabilecek özel durum için kullanması gereken bir <xref:System.InvalidTimeZoneException> için oluşturulan bir <xref:System.TimeZoneInfo> yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="22566-158">You should use exceptional postconditions only for specific exceptions that might be thrown when a member is called, for example, when an <xref:System.InvalidTimeZoneException> is thrown for a <xref:System.TimeZoneInfo> method call.</span></span>

### <a name="special-postconditions"></a><span data-ttu-id="22566-159">Özel koşul Sonralarına</span><span class="sxs-lookup"><span data-stu-id="22566-159">Special Postconditions</span></span>

<span data-ttu-id="22566-160">Aşağıdaki yöntemlerden yalnızca koşul sonralarına içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="22566-160">The following methods may be used only within postconditions:</span></span>

- <span data-ttu-id="22566-161">İfade kullanarak koşul sonralarına yöntem dönüş değerlerine başvurabilir `Contract.Result<T>()`burada `T` yöntemin dönüş türü tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="22566-161">You can refer to method return values in postconditions by using the expression `Contract.Result<T>()`, where `T` is replaced by the return type of the method.</span></span> <span data-ttu-id="22566-162">Derleyicinin türü çıkarımı işlenemediğinde açıkça sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="22566-162">When the compiler is unable to infer the type, you must explicitly provide it.</span></span> <span data-ttu-id="22566-163">Örneğin, C# derleyici, aşağıdaki Sonkoşul gerektirir böylece herhangi bir bağımsız değişken almayan yöntemleri için türlerini çıkarması tamamlayamıyor: `Contract.Ensures(0 <Contract.Result<int>())` Yöntem dönüş türüne sahip `void` başvurulamaz `Contract.Result<T>()` kendi koşul sonralarına içinde.</span><span class="sxs-lookup"><span data-stu-id="22566-163">For example, the C# compiler is unable to infer types for methods that do not take any arguments, so it requires the following postcondition: `Contract.Ensures(0 <Contract.Result<int>())` Methods with a return type of `void` cannot refer to `Contract.Result<T>()` in their postconditions.</span></span>

- <span data-ttu-id="22566-164">Sonkoşul prestate değeri bir ifade başlatma sırasında bir yöntem veya özellik değerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="22566-164">A prestate value in a postcondition refers to the value of an expression at the start of a method or property.</span></span> <span data-ttu-id="22566-165">İfade kullanır `Contract.OldValue<T>(e)`burada `T` türü `e`.</span><span class="sxs-lookup"><span data-stu-id="22566-165">It uses the expression `Contract.OldValue<T>(e)`, where `T` is the type of `e`.</span></span> <span data-ttu-id="22566-166">Derleyici, türü çıkarımı mümkün olduğunda genel tür bağımsız değişkeni atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22566-166">You can omit the generic type argument whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="22566-167">(Bağımsız değişken aldığından Örneğin, C# Derleyici her zaman türü çıkarır.) Ne ortaya çıkabilir bazı kısıtlamalar vardır `e` ve eski deyim görünebilir bağlamı.</span><span class="sxs-lookup"><span data-stu-id="22566-167">(For example, the C# compiler always infers the type because it takes an argument.) There are several restrictions on what can occur in `e` and the contexts in which an old expression may appear.</span></span> <span data-ttu-id="22566-168">Eski bir ifade başka bir eski ifadesi içeremez.</span><span class="sxs-lookup"><span data-stu-id="22566-168">An old expression cannot contain another old expression.</span></span> <span data-ttu-id="22566-169">En önemlisi, eski bir ifade yöntemin önkoşulu durumunda var olan bir değer başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22566-169">Most importantly, an old expression must refer to a value that existed in the method's precondition state.</span></span> <span data-ttu-id="22566-170">Diğer bir deyişle, yöntemin önkoşulu olduğu sürece değerlendirilebilen bir ifade olmalıdır `true`.</span><span class="sxs-lookup"><span data-stu-id="22566-170">In other words, it must be an expression that can be evaluated as long as the method's precondition is `true`.</span></span> <span data-ttu-id="22566-171">Bu kural için birkaç örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="22566-171">Here are several instances of that rule.</span></span>

  - <span data-ttu-id="22566-172">Değer yöntemin önkoşulu durumda mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="22566-172">The value must exist in the method's precondition state.</span></span> <span data-ttu-id="22566-173">Bir alan bir nesne üzerinde başvurmak için önkoşulları nesneyi her zaman null olmayan olduğunu garanti gerekir.</span><span class="sxs-lookup"><span data-stu-id="22566-173">In order to reference a field on an object, the preconditions must guarantee that the object is always non-null.</span></span>

  - <span data-ttu-id="22566-174">Eski bir ifade yöntemin dönüş değeri başvuruda bulunamaz:</span><span class="sxs-lookup"><span data-stu-id="22566-174">You cannot refer to the method's return value in an old expression:</span></span>

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - <span data-ttu-id="22566-175">Başvuruda bulunamaz `out` eski bir ifadede parametreleri.</span><span class="sxs-lookup"><span data-stu-id="22566-175">You cannot refer to `out` parameters in an old expression.</span></span>

  - <span data-ttu-id="22566-176">Nicelik aralığı yöntemin dönüş değerini temel bağlıysa, eski bir ifade bağlı bir miktar belirleyiciyi değişkenin üzerine bağımlı olamaz:</span><span class="sxs-lookup"><span data-stu-id="22566-176">An old expression cannot depend on the bound variable of a quantifier if the range of the quantifier depends on the return value of the method:</span></span>

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - <span data-ttu-id="22566-177">Eski bir ifade anonim temsilci parametresine başvuramaz bir <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> bir dizin oluşturucu veya yöntem çağrısı için bağımsız değişkeni olarak kullanılmadığı sürece çağırın:</span><span class="sxs-lookup"><span data-stu-id="22566-177">An old expression cannot refer to the parameter of the anonymous delegate in a <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> call unless it is used as an indexer or argument to a method call:</span></span>

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - <span data-ttu-id="22566-178">Eski ifadenin değerini herhangi bir anonim metot temsilcisinin parametre bağlıysa anonim temsilci bağımsız değişken olmadığı sürece eski bir ifade anonim bir temsilci gövdesinde gerçekleşemez <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="22566-178">An old expression cannot occur in the body of an anonymous delegate if the value of the old expression depends on any of the parameters of the anonymous delegate, unless the anonymous delegate is an argument to the <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> method:</span></span>

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - <span data-ttu-id="22566-179">`Out` parametreleri mevcut bir sorun sözleşmeleri Yöntemin gövdesi önce görünür ve derleyicilerin çoğu başvuruları izin vermez çünkü `out` koşul sonralarına parametreleri.</span><span class="sxs-lookup"><span data-stu-id="22566-179">`Out` parameters present a problem because contracts appear before the body of the method, and most compilers do not allow references to `out` parameters in postconditions.</span></span> <span data-ttu-id="22566-180">Bu sorunu çözmek için <xref:System.Diagnostics.Contracts.Contract> sağlar sınıfını <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> göre Sonkoşul sağlayan yöntemi bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="22566-180">To solve this problem, the <xref:System.Diagnostics.Contracts.Contract> class provides the <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method, which allows a postcondition based on an `out` parameter.</span></span>

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      <span data-ttu-id="22566-181">Olduğu gibi <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> yöntemi çıkarabilirsiniz genel tür parametresi derleyici türünü çıkarsamak mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="22566-181">As with the <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> method, you can omit the generic type parameter whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="22566-182">Sözleşme rewriter yöntem çağrısında değeri ile değiştirir. `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="22566-182">The contract rewriter replaces the method call with the value of the `out` parameter.</span></span> <span data-ttu-id="22566-183"><xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Yöntemi yalnızca koşul sonralarına görünebilir.</span><span class="sxs-lookup"><span data-stu-id="22566-183">The <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method may appear only in postconditions.</span></span> <span data-ttu-id="22566-184">Yöntem bağımsız değişkeni olmalıdır bir `out` parametresi veya bir yapının bir alan `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="22566-184">The argument to the method must be an `out` parameter or a field of a structure `out` parameter.</span></span> <span data-ttu-id="22566-185">İkincisi de yapısı oluşturucunun Sonkoşul alanları söz konusu olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="22566-185">The latter is also useful when referring to fields in the postcondition of a structure constructor.</span></span>

      > [!NOTE]
      > <span data-ttu-id="22566-186">Şu anda, kod sözleşme çözümleme araçları işaretlemeyin olmadığını `out` parametreleri düzgün başlatılmadı ve bunların Bahsetme Sonkoşul içinde göz ardı.</span><span class="sxs-lookup"><span data-stu-id="22566-186">Currently, the code contract analysis tools do not check whether `out` parameters are initialized properly and disregard their mention in the postcondition.</span></span> <span data-ttu-id="22566-187">Sözleşme satırdan değerini kullanmışsınız bu nedenle, önceki örnekte, `x` tamsayı kendisine atamak yerine, derleyici doğru hatası sorunu değil.</span><span class="sxs-lookup"><span data-stu-id="22566-187">Therefore, in the previous example, if the line after the contract had used the value of `x` instead of assigning an integer to it, a compiler would not issue the correct error.</span></span> <span data-ttu-id="22566-188">Ancak, CONTRACTS_FULL önişlemci sembolü olduğu bir derleme (Bu tür asa yayın derleme) tanımlı değil, derleyici bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="22566-188">However, on a build where the CONTRACTS_FULL preprocessor symbol is not defined (such asa release build), the compiler will issue an error.</span></span>

## <a name="invariants"></a><span data-ttu-id="22566-189">Okuduğunuzda</span><span class="sxs-lookup"><span data-stu-id="22566-189">Invariants</span></span>

<span data-ttu-id="22566-190">Nesne okuduğunuzda o nesnenin bir istemci tarafından görünür olduğunda, bir sınıfın her örneği için true olması gereken koşullardır.</span><span class="sxs-lookup"><span data-stu-id="22566-190">Object invariants are conditions that should be true for each instance of a class whenever that object is visible to a client.</span></span> <span data-ttu-id="22566-191">Bunlar, nesnenin altında doğru olarak kabul edilir koşullar express.</span><span class="sxs-lookup"><span data-stu-id="22566-191">They express the conditions under which the object is considered to be correct.</span></span>

<span data-ttu-id="22566-192">Sabit yöntemleri ile işaretlenen tarafından tanımlanan <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="22566-192">The invariant methods are identified by being marked with the <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> attribute.</span></span> <span data-ttu-id="22566-193">Sabit yöntem çağrıları bir dizi dışında hiçbir kod içermelidir <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> yöntemi, her biri belirten tek bir değişmez değer aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="22566-193">The invariant methods must contain no code except for a sequence of calls to the <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> method, each of which specifies an individual invariant, as shown in the following example.</span></span>

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

<span data-ttu-id="22566-194">Okuduğunuzda koşullu CONTRACTS_FULL önişlemci sembolü tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="22566-194">Invariants are conditionally defined by the CONTRACTS_FULL preprocessor symbol.</span></span> <span data-ttu-id="22566-195">Çalışma zamanı denetimi sırasında her bir genel yöntem sonunda okuduğunuzda denetlenir.</span><span class="sxs-lookup"><span data-stu-id="22566-195">During run-time checking, invariants are checked at the end of each public method.</span></span> <span data-ttu-id="22566-196">Değişmez değer aynı sınıftaki bir genel yöntem bahsetmeleri normalde, genel yönteminin sonunda olacağını sabit denetimi devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="22566-196">If an invariant mentions a public method in the same class, the invariant check that would normally happen at the end of that public method is disabled.</span></span> <span data-ttu-id="22566-197">Bunun yerine, yalnızca o sınıfın en dıştaki yöntem çağrısına sonunda onay gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="22566-197">Instead, the check occurs only at the end of the outermost method call to that class.</span></span> <span data-ttu-id="22566-198">Bu durum, aynı zamanda sınıfın başka bir sınıftaki bir yönteme bir çağrı nedeniyle yeniden girilirse gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="22566-198">This also happens if the class is re-entered because of a call to a method on another class.</span></span> <span data-ttu-id="22566-199">Okuduğunuzda bir nesnenin Sonlandırıcısı için onaylanmamış ve <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="22566-199">Invariants are not checked for an object finalizer and an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span>

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a><span data-ttu-id="22566-200">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="22566-200">Usage Guidelines</span></span>

### <a name="contract-ordering"></a><span data-ttu-id="22566-201">Sözleşme sıralama</span><span class="sxs-lookup"><span data-stu-id="22566-201">Contract Ordering</span></span>

<span data-ttu-id="22566-202">Aşağıdaki tabloda yöntemi sözleşmeleri yazdığınızda kullanması gereken öğelerin sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22566-202">The following table shows the order of elements you should use when you write method contracts.</span></span>

|`If-then-throw statements`|<span data-ttu-id="22566-203">Geriye dönük olarak uyumlu genel Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="22566-203">Backward-compatible public preconditions</span></span>|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|<span data-ttu-id="22566-204">Tüm genel önkoşulları.</span><span class="sxs-lookup"><span data-stu-id="22566-204">All public preconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="22566-205">Tüm genel (normal) koşul sonralarına.</span><span class="sxs-lookup"><span data-stu-id="22566-205">All public (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="22566-206">Tüm genel olağanüstü koşul sonralarına.</span><span class="sxs-lookup"><span data-stu-id="22566-206">All public exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="22566-207">Tüm özel/iç (normal) koşul sonralarına.</span><span class="sxs-lookup"><span data-stu-id="22566-207">All private/internal (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="22566-208">Tüm özel/iç olağanüstü koşul sonralarına.</span><span class="sxs-lookup"><span data-stu-id="22566-208">All private/internal exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|<span data-ttu-id="22566-209">Kullanıyorsanız `if` - `then` - `throw` stil önkoşulları diğer tüm sözleşmeleri olmadan, bir çağrı yapmak <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> göstermek için önceki tüm denetimleri önkoşulları varsa.</span><span class="sxs-lookup"><span data-stu-id="22566-209">If using `if`-`then`-`throw` style preconditions without any other contracts, place a call to <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> to indicate that all previous if checks are preconditions.</span></span>|

<a name="purity"></a>

### <a name="purity"></a><span data-ttu-id="22566-210">Saflığa</span><span class="sxs-lookup"><span data-stu-id="22566-210">Purity</span></span>

<span data-ttu-id="22566-211">Bir sözleşme içinde çağrılan tüm yöntemlere saf olmalıdır; diğer bir deyişle, bunlar önceden var olan herhangi bir durum güncelleştirmeyi gerekir.</span><span class="sxs-lookup"><span data-stu-id="22566-211">All methods that are called within a contract must be pure; that is, they must not update any preexisting state.</span></span> <span data-ttu-id="22566-212">Saf yönteminin saf yönteminin girişine sonra oluşturulan nesneleri değiştirme izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="22566-212">A pure method is allowed to modify objects that have been created after entry into the pure method.</span></span>

<span data-ttu-id="22566-213">Kod sözleşme araçları, şu anda aşağıdaki kod öğelerinden saf olduğunu varsayar:</span><span class="sxs-lookup"><span data-stu-id="22566-213">Code contract tools currently assume that the following code elements are pure:</span></span>

- <span data-ttu-id="22566-214">İle işaretlenmiş yöntemler <xref:System.Diagnostics.Contracts.PureAttribute>.</span><span class="sxs-lookup"><span data-stu-id="22566-214">Methods that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span>

- <span data-ttu-id="22566-215">İle işaretlenmiş türler <xref:System.Diagnostics.Contracts.PureAttribute> (öznitelik türün tüm yöntemleri için geçerlidir).</span><span class="sxs-lookup"><span data-stu-id="22566-215">Types that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute> (the attribute applies to all the type's methods).</span></span>

- <span data-ttu-id="22566-216">Özellik get erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="22566-216">Property get accessors.</span></span>

- <span data-ttu-id="22566-217">İşleçler (bir veya iki parametre ve void olmayan dönüş türüne sahip adları "op" ve, ile başlayan statik yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="22566-217">Operators (static methods whose names start with "op", and that have one or two parameters and a non-void return type).</span></span>

- <span data-ttu-id="22566-218">Tam adı "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" veya "System.Type" ile başlayan herhangi bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="22566-218">Any method whose fully qualified name begins with "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path", or "System.Type".</span></span>

- <span data-ttu-id="22566-219">Temsilci türü ile öznitelendirilen şartıyla tüm temsilci çağrılır <xref:System.Diagnostics.Contracts.PureAttribute>.</span><span class="sxs-lookup"><span data-stu-id="22566-219">Any invoked delegate, provided that the delegate type itself is attributed with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span> <span data-ttu-id="22566-220">Temsilci türleriyle <xref:System.Predicate%601?displayProperty=nameWithType> ve <xref:System.Comparison%601?displayProperty=nameWithType> saf olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="22566-220">The delegate types <xref:System.Predicate%601?displayProperty=nameWithType> and <xref:System.Comparison%601?displayProperty=nameWithType> are considered pure.</span></span>

<a name="visibility"></a>

### <a name="visibility"></a><span data-ttu-id="22566-221">Görünürlük</span><span class="sxs-lookup"><span data-stu-id="22566-221">Visibility</span></span>

<span data-ttu-id="22566-222">Tüm üyeleri bir sözleşmede belirtilen en az göründükleri yöntemi olarak olarak görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22566-222">All members mentioned in a contract must be at least as visible as the method in which they appear.</span></span> <span data-ttu-id="22566-223">Örneğin, özel bir alan genel bir yöntem için bir önkoşul olarak belirtilen olamaz; Bunlar yöntemi çağırmadan önce istemcileri böyle bir sözleşme doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="22566-223">For example, a private field cannot be mentioned in a precondition for a public method; clients cannot validate such a contract before they call the method.</span></span> <span data-ttu-id="22566-224">Ancak, alan ile işaretlenmişse <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, bu kurallardan muaf.</span><span class="sxs-lookup"><span data-stu-id="22566-224">However, if the field is marked with the <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, it is exempt from these rules.</span></span>

## <a name="example"></a><span data-ttu-id="22566-225">Örnek</span><span class="sxs-lookup"><span data-stu-id="22566-225">Example</span></span>

<span data-ttu-id="22566-226">Aşağıdaki örnek, kod sözleşmeleri kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22566-226">The following example shows the use of code contracts.</span></span>

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
