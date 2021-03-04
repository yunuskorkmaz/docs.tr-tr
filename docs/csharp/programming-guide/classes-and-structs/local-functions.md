---
title: Yerel işlevler-C# Programlama Kılavuzu
description: C# ' deki yerel işlevler, başka bir üyede iç içe yerleştirilmiş ve kendi kapsayıcı üyelerinden çağrılabilecek özel yöntemlerdir.
ms.date: 10/16/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 1c0cd1b8122f9069e5d6385d698f0ff8278912dd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103250"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="d4098-103">Yerel işlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d4098-103">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="d4098-104">C# 7,0 ' den başlayarak, c# *Yerel Işlevleri* destekler.</span><span class="sxs-lookup"><span data-stu-id="d4098-104">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="d4098-105">Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="d4098-105">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="d4098-106">Yalnızca kendi kapsayıcı üyelerinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-106">They can only be called from their containing member.</span></span> <span data-ttu-id="d4098-107">Yerel işlevler içinde bildirilebilecek ve şuradan çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="d4098-107">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="d4098-108">Yöntemler, özellikle Yineleyici yöntemleri ve zaman uyumsuz yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4098-108">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="d4098-109">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d4098-109">Constructors</span></span>
- <span data-ttu-id="d4098-110">Özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="d4098-110">Property accessors</span></span>
- <span data-ttu-id="d4098-111">Olay erişimcileri</span><span class="sxs-lookup"><span data-stu-id="d4098-111">Event accessors</span></span>
- <span data-ttu-id="d4098-112">Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4098-112">Anonymous methods</span></span>
- <span data-ttu-id="d4098-113">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d4098-113">Lambda expressions</span></span>
- <span data-ttu-id="d4098-114">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="d4098-114">Finalizers</span></span>
- <span data-ttu-id="d4098-115">Diğer yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="d4098-115">Other local functions</span></span>

<span data-ttu-id="d4098-116">Ancak, yerel işlevler ifade-Bodied üyesi içinde bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="d4098-116">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="d4098-117">Bazı durumlarda, bir yerel işlev tarafından desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4098-117">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="d4098-118">Bir karşılaştırma için bkz [. yerel işlevler ve lambda ifadeleri](#local-functions-vs-lambda-expressions).</span><span class="sxs-lookup"><span data-stu-id="d4098-118">For a comparison, see [Local functions vs. lambda expressions](#local-functions-vs-lambda-expressions).</span></span>

<span data-ttu-id="d4098-119">Yerel işlevler, kodunuzun amacını açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d4098-119">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="d4098-120">Kodunuzu okuyan herkes, yöntemin kapsayan Yöntem dışında çağrılabilir olmadığını görebilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-120">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="d4098-121">Ekip projeleri için, başka bir geliştiricinin yöntemi doğrudan sınıf veya yapı içinde başka bir yerde çağırmak olanaksız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d4098-121">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="d4098-122">Yerel işlev sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4098-122">Local function syntax</span></span>

<span data-ttu-id="d4098-123">Yerel bir işlev, kapsayan bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d4098-123">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="d4098-124">Tanımı aşağıdaki sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d4098-124">Its definition has the following syntax:</span></span>

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="d4098-125">Aşağıdaki değiştiricileri yerel bir işlevle kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d4098-125">You can use the following modifiers with a local function:</span></span>

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- <span data-ttu-id="d4098-126">[`static`](../../language-reference/keywords/static.md) (C# 8,0 ve üzeri sürümlerde).</span><span class="sxs-lookup"><span data-stu-id="d4098-126">[`static`](../../language-reference/keywords/static.md) (in C# 8.0 and later).</span></span> <span data-ttu-id="d4098-127">Statik bir yerel işlev yerel değişkenler veya örnek durumu yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="d4098-127">A static local function can't capture local variables or instance state.</span></span>
- <span data-ttu-id="d4098-128">[`extern`](../../language-reference/keywords/extern.md) (C# 9,0 ve üzeri sürümlerde).</span><span class="sxs-lookup"><span data-stu-id="d4098-128">[`extern`](../../language-reference/keywords/extern.md) (in C# 9.0 and later).</span></span> <span data-ttu-id="d4098-129">Dış yerel işlev olmalıdır `static` .</span><span class="sxs-lookup"><span data-stu-id="d4098-129">An external local function must be `static`.</span></span>

<span data-ttu-id="d4098-130">Yöntem parametreleri de dahil olmak üzere, kapsayan üyede tanımlanan tüm yerel değişkenlere statik olmayan bir yerel işlevde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-130">All local variables that are defined in the containing member, including its method parameters, are accessible in a non-static local function.</span></span>

<span data-ttu-id="d4098-131">Bir yöntem tanımının aksine, yerel bir işlev tanımı üye erişim değiştiricisini içeremez.</span><span class="sxs-lookup"><span data-stu-id="d4098-131">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="d4098-132">Tüm yerel işlevler özel olduğundan, anahtar sözcüğü gibi bir erişim değiştiricisi de dahil olmak üzere, `private` "özel ' değiştiricisi Bu öğe için geçerli değil."</span><span class="sxs-lookup"><span data-stu-id="d4098-132">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

<span data-ttu-id="d4098-133">Aşağıdaki örnek adlı bir yerel işlevi tanımlar `AppendPathSeparator` `GetText` :</span><span class="sxs-lookup"><span data-stu-id="d4098-133">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

<span data-ttu-id="d4098-134">C# 9,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, bir yerel işleve, parametreleri ve tür parametrelerine öznitelikler uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d4098-134">Beginning with C# 9.0, you can apply attributes to a local function, its parameters and type parameters, as the following example shows:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

<span data-ttu-id="d4098-135">Önceki örnek, null olabilen bir bağlamda statik çözümlemede derleyiciye yardım etmek için [özel bir öznitelik](../../language-reference/attributes/nullable-analysis.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4098-135">The preceding example uses a [special attribute](../../language-reference/attributes/nullable-analysis.md) to assist the compiler in static analysis in a nullable context.</span></span>

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="d4098-136">Yerel işlevler ve özel durumlar</span><span class="sxs-lookup"><span data-stu-id="d4098-136">Local functions and exceptions</span></span>

<span data-ttu-id="d4098-137">Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeyine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-137">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="d4098-138">Yöntem yineleyiciler için, özel durumlar yalnızca döndürülen dizi numaralandırıldıktan sonra, yineleyici alındığında değil, ortaya çıkacak.</span><span class="sxs-lookup"><span data-stu-id="d4098-138">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="d4098-139">Zaman uyumsuz metotlar için, bir zaman uyumsuz yöntemde oluşturulan özel durumlar, döndürülen görev beklendiğinde gözlemlenir.</span><span class="sxs-lookup"><span data-stu-id="d4098-139">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="d4098-140">Aşağıdaki örnek, `OddSequence` belirtilen aralıktaki tek sayıları numaralandırır bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4098-140">The following example defines an `OddSequence` method that enumerates odd numbers in a specified range.</span></span> <span data-ttu-id="d4098-141">Numaralandırıcı yöntemine 100 ' den büyük bir sayı geçirdiğinden `OddSequence` , yöntemi bir oluşturur <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="d4098-141">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="d4098-142">Örneğin çıkışının gösterdiği gibi, özel durum yalnızca sayıları tekrarladığı zaman, numaralandırıcıyı alırken değil, yüzeyleri.</span><span class="sxs-lookup"><span data-stu-id="d4098-142">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

<span data-ttu-id="d4098-143">Yineleyici mantığını yerel bir işleve yerleştirirseniz, aşağıdaki örnekte gösterildiği gibi, Numaralandırıcı aldığınızda bağımsız değişken doğrulama özel durumları atılır.</span><span class="sxs-lookup"><span data-stu-id="d4098-143">If you put iterator logic into a local function, argument validation exceptions are thrown when you retrieve the enumerator, as the following example shows:</span></span>

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a><span data-ttu-id="d4098-144">Yerel işlevler ve lambda ifadeleri karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="d4098-144">Local functions vs. lambda expressions</span></span>

<span data-ttu-id="d4098-145">İlk bakışta, yerel işlevler ve [lambda ifadeleri](../../language-reference/operators/lambda-expressions.md) çok benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d4098-145">At first glance, local functions and [lambda expressions](../../language-reference/operators/lambda-expressions.md) are very similar.</span></span> <span data-ttu-id="d4098-146">Birçok durumda, lambda ifadeleri ve yerel işlevler kullanma arasında seçim stili ve kişisel tercihlerden bağımsız olur.</span><span class="sxs-lookup"><span data-stu-id="d4098-146">In many cases, the choice between using lambda expressions and local functions is a matter of style and personal preference.</span></span> <span data-ttu-id="d4098-147">Ancak, dikkat etmeniz gereken bir veya diğerini kullanabileceğiniz gerçek farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="d4098-147">However, there are real differences in where you can use one or the other that you should be aware of.</span></span>

<span data-ttu-id="d4098-148">Bu, yerel işlev ve çarpınımı algoritmasının lambda ifadesi uygulamaları arasındaki farkları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="d4098-148">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="d4098-149">Yerel bir işlev kullanan sürümü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d4098-149">Here's the version using a local function:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

<span data-ttu-id="d4098-150">Bu sürüm lambda ifadeleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="d4098-150">This version uses lambda expressions:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

### <a name="naming"></a><span data-ttu-id="d4098-151">Adlandırma</span><span class="sxs-lookup"><span data-stu-id="d4098-151">Naming</span></span>

<span data-ttu-id="d4098-152">Yerel işlevler, yöntemler gibi açıkça adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d4098-152">Local functions are explicitly named like methods.</span></span> <span data-ttu-id="d4098-153">Lambda ifadeleri anonim yöntemlerdir ve `delegate` genellikle veya türler türünde bir türün değişkenlerine atanması gerekir `Action` `Func` .</span><span class="sxs-lookup"><span data-stu-id="d4098-153">Lambda expressions are anonymous methods and need to be assigned to variables of a `delegate` type, typically either `Action` or `Func` types.</span></span> <span data-ttu-id="d4098-154">Yerel bir işlev bildirdiğinizde, işlem normal bir yöntem yazmak gibidir; bir dönüş türü ve bir işlev imzası bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4098-154">When you declare a local function, the process is like writing a normal method; you declare a return type and a function signature.</span></span>

### <a name="function-signatures-and-lambda-expression-types"></a><span data-ttu-id="d4098-155">İşlev imzaları ve lambda ifadesi türleri</span><span class="sxs-lookup"><span data-stu-id="d4098-155">Function signatures and lambda expression types</span></span>

<span data-ttu-id="d4098-156">Lambda ifadeleri, `Action` / `Func` bağımsız değişkenini ve dönüş türlerini belirlemekte atanan değişkenin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4098-156">Lambda expressions rely on the type of the `Action`/`Func` variable that they're assigned to determine the argument and return types.</span></span> <span data-ttu-id="d4098-157">Yerel işlevlerde, söz dizimi normal bir yöntemi yazarken çok benzer olduğundan, bağımsız değişken türleri ve dönüş türü zaten işlev bildiriminin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d4098-157">In local functions, since the syntax is much like writing a normal method, argument types and return type are already part of the function declaration.</span></span>

### <a name="definite-assignment"></a><span data-ttu-id="d4098-158">Kesin atama</span><span class="sxs-lookup"><span data-stu-id="d4098-158">Definite assignment</span></span>

<span data-ttu-id="d4098-159">Lambda ifadeleri, çalışma zamanında bildirildiği ve atanan nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="d4098-159">Lambda expressions are objects that are declared and assigned at runtime.</span></span> <span data-ttu-id="d4098-160">Bir lambda ifadesinin kullanılabilmesi için, kesinlikle atanması gerekir: kendisine `Action` / `Func` atanacak olan değişken bildirilmelidir ve kendisine atanmış lambda ifadesi.</span><span class="sxs-lookup"><span data-stu-id="d4098-160">In order for a lambda expression to be used, it needs to be definitely assigned: the `Action`/`Func` variable that it will be assigned to must be declared and the lambda expression assigned to it.</span></span> <span data-ttu-id="d4098-161">`LambdaFactorial`Tanımlanmadan önce lambda ifadesini bildirmelidir ve başlatmalıdır `nthFactorial` .</span><span class="sxs-lookup"><span data-stu-id="d4098-161">Notice that `LambdaFactorial` must declare and initialize the lambda expression `nthFactorial` before defining it.</span></span> <span data-ttu-id="d4098-162">Bu nedenle, atamadan önce başvurmak için derleme zamanı hatasına neden `nthFactorial` olur.</span><span class="sxs-lookup"><span data-stu-id="d4098-162">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>

<span data-ttu-id="d4098-163">Yerel işlevler, derleme zamanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d4098-163">Local functions are defined at compile time.</span></span> <span data-ttu-id="d4098-164">Değişkenlere atanmadığından, bunlara **kapsamda olduğu** herhangi bir kod konumundan başvurulabilirler; ilk örneğimizde `LocalFunctionFactorial` , deyimin üzerinde veya altında `return` olan ve herhangi bir derleyici hatası tetiklemeyen yerel işlevimizi bildirebiliriz.</span><span class="sxs-lookup"><span data-stu-id="d4098-164">As they're not assigned to variables, they can be referenced from any code location **where it is in scope**; in our first example `LocalFunctionFactorial`, we could declare our local function either above or below the `return` statement and not trigger any compiler errors.</span></span>

<span data-ttu-id="d4098-165">Bu farklılıklar özyinelemeli algoritmaların yerel işlevler kullanılarak oluşturulması daha kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="d4098-165">These differences mean that recursive algorithms are easier to create using local functions.</span></span> <span data-ttu-id="d4098-166">Kendisini çağıran bir yerel işlev tanımlayabilir ve tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4098-166">You can declare and define a local function that calls itself.</span></span> <span data-ttu-id="d4098-167">Lambda ifadeleri, aynı lambda ifadesine başvuran bir gövdeye yeniden atanabilmeleri için bildirilmelidir ve varsayılan bir değer atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4098-167">Lambda expressions must be declared, and assigned a default value before they can be re-assigned to a body that references the same lambda expression.</span></span>

### <a name="implementation-as-a-delegate"></a><span data-ttu-id="d4098-168">Temsilci olarak uygulama</span><span class="sxs-lookup"><span data-stu-id="d4098-168">Implementation as a delegate</span></span>

<span data-ttu-id="d4098-169">Lambda ifadeleri, bildirildiği zaman temsilcilere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d4098-169">Lambda expressions are converted to delegates when they're declared.</span></span> <span data-ttu-id="d4098-170">Yerel işlevler geleneksel bir yöntem *veya* temsilci olarak yazabildiği için daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="d4098-170">Local functions are more flexible in that they can be written like a traditional method *or* as a delegate.</span></span> <span data-ttu-id="d4098-171">Yerel işlevler yalnızca temsilci olarak ***kullanıldığında*** temsilcilere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d4098-171">Local functions are only converted to delegates when ***used*** as a delegate.</span></span>

<span data-ttu-id="d4098-172">Yerel bir işlev bildirirseniz ve yalnızca bir yöntem gibi çağırarak buna başvurmanız durumunda, bir temsilciye dönüştürülmez.</span><span class="sxs-lookup"><span data-stu-id="d4098-172">If you declare a local function and only reference it by calling it like a method, it will not be converted to a delegate.</span></span>

### <a name="variable-capture"></a><span data-ttu-id="d4098-173">Değişken yakalama</span><span class="sxs-lookup"><span data-stu-id="d4098-173">Variable capture</span></span>

<span data-ttu-id="d4098-174">[Kesin atamanın](../../../../_csharplang/spec/variables.md#definite-assignment) kuralları, yerel işlev veya lambda ifadesi tarafından yakalanan tüm değişkenleri de etkiler.</span><span class="sxs-lookup"><span data-stu-id="d4098-174">The rules of [definite assignment](../../../../_csharplang/spec/variables.md#definite-assignment) also affect any variables that are captured by the local function or lambda expression.</span></span> <span data-ttu-id="d4098-175">Derleyici, yerel işlevlerin kapsayan kapsamda kesin olarak yakalanan değişkenleri atamasını sağlayan statik analizler gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-175">The compiler can perform static analysis that enables local functions to definitely assign captured variables in the enclosing scope.</span></span> <span data-ttu-id="d4098-176">Bu örneği ele alalım:</span><span class="sxs-lookup"><span data-stu-id="d4098-176">Consider this example:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="d4098-177">Derleyici, `LocalFunction` çağrıldığında kesinlikle atayıp atamayacağını tespit edebilir `y` .</span><span class="sxs-lookup"><span data-stu-id="d4098-177">The compiler can determine that `LocalFunction` definitely assigns `y` when called.</span></span> <span data-ttu-id="d4098-178">, `LocalFunction` Deyimden önce çağrıldığı için `return` , `y` ifadeye kesin olarak atanır `return` .</span><span class="sxs-lookup"><span data-stu-id="d4098-178">Because `LocalFunction` is called before the `return` statement, `y` is definitely assigned at the `return` statement.</span></span>

<span data-ttu-id="d4098-179">Yerel bir işlev kapsayan kapsamdaki değişkenleri yakaladığında, yerel işlevin temsilci türü olarak uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4098-179">Note that when a local function captures variables in the enclosing scope, the local function is implemented as a delegate type.</span></span>

### <a name="heap-allocations"></a><span data-ttu-id="d4098-180">Yığın ayırmaları</span><span class="sxs-lookup"><span data-stu-id="d4098-180">Heap allocations</span></span>

<span data-ttu-id="d4098-181">Yerel işlevler, kullanım amaçlarına bağlı olarak, lambda ifadeleri için her zaman gerekli olan yığın ayırmalara engel olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-181">Depending on their use, local functions can avoid heap allocations that are always necessary for lambda expressions.</span></span> <span data-ttu-id="d4098-182">Yerel bir işlev hiçbir şekilde bir temsilciye dönüştürülürse ve yerel işlev tarafından yakalanan değişkenlerden hiçbiri, başka Lambdalar veya temsilcilere dönüştürülen yerel işlevler tarafından yakalanmazsa, derleyici yığın ayırmalara engel olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-182">If a local function is never converted to a delegate, and none of the variables captured by the local function are captured by other lambdas or local functions that are converted to delegates, the compiler can avoid heap allocations.</span></span>

<span data-ttu-id="d4098-183">Bu zaman uyumsuz örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d4098-183">Consider this async example:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

<span data-ttu-id="d4098-184">Bu lambda ifadesinin kapanışı `address` , `index` ve `name` değişkenlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d4098-184">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="d4098-185">Yerel işlevler söz konusu olduğunda, kapanışı uygulayan nesne bir `struct` tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-185">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="d4098-186">Bu yapı türü yerel işleve başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-186">That struct type would be passed by reference to the local function.</span></span> <span data-ttu-id="d4098-187">Uygulamadaki bu fark bir ayırmaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d4098-187">This difference in implementation would save on an allocation.</span></span>

<span data-ttu-id="d4098-188">Lambda ifadeleri için gereken örnek oluşturma, zaman açısından kritik kod yollarındaki bir performans faktörü olabilecek fazladan bellek ayırmaları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d4098-188">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time-critical code paths.</span></span> <span data-ttu-id="d4098-189">Yerel işlevler bu ek yüke neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="d4098-189">Local functions do not incur this overhead.</span></span> <span data-ttu-id="d4098-190">Yukarıdaki örnekte, yerel işlevlerin sürümünde lambda ifadesi sürümünden daha az sayıda ayırma vardır.</span><span class="sxs-lookup"><span data-stu-id="d4098-190">In the example above, the local functions version has two fewer allocations than the lambda expression version.</span></span>

<span data-ttu-id="d4098-191">Yerel işlevinizin bir temsilciye dönüştürülemediğini ve tarafından yakalanan değişkenlerden hiçbirinin, temsilcilere dönüştürülen başka Lambdalar veya yerel işlevler tarafından yakalanıp yakalanmayacağını biliyorsanız, yerel işlevinizin yığın üzerinde yerel bir işlev olarak bildirerek ayrılmasının önleneceğini garanti edebilirsiniz `static` .</span><span class="sxs-lookup"><span data-stu-id="d4098-191">If you know that your local function won't be converted to a delegate and none of the variables captured by it are captured by other lambdas or local functions that are converted to delegates, you can guarantee that your local function avoids being allocated on the heap by declaring it as a `static` local function.</span></span> <span data-ttu-id="d4098-192">Bu özelliğin C# 8,0 ve daha yeni sürümlerde kullanılabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4098-192">Note that this feature is available in C# 8.0 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="d4098-193">Bu yöntemin yerel işlev eşdeğeri, kapanış için bir sınıf de kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4098-193">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="d4098-194">Yerel bir işlev için Kapanışın bir veya olarak uygulanıp uygulanmadığı bir `class` `struct` uygulama ayrıntısı.</span><span class="sxs-lookup"><span data-stu-id="d4098-194">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="d4098-195">Yerel bir işlev bir kullanabilir, `struct` ancak bir lambda her zaman bir kullanır `class` .</span><span class="sxs-lookup"><span data-stu-id="d4098-195">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

### <a name="usage-of-the-yield-keyword"></a><span data-ttu-id="d4098-196">`yield`Anahtar sözcüğünün kullanımı</span><span class="sxs-lookup"><span data-stu-id="d4098-196">Usage of the `yield` keyword</span></span>

<span data-ttu-id="d4098-197">Bu örnekte gösterilmeyen bir son avantaj, yerel işlevlerin yineleyiciler olarak uygulanabilmesinin yanı `yield return` sıra bir değer dizisi oluşturmak için söz dizimini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d4098-197">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="YieldReturn" :::

<span data-ttu-id="d4098-198">`yield return`Lambda ifadelerinde ifadeye izin verilmiyor, bkz. [DERLEYICI hatası CS1621](../../misc/cs1621.md).</span><span class="sxs-lookup"><span data-stu-id="d4098-198">The `yield return` statement is not allowed in lambda expressions, see [compiler error CS1621](../../misc/cs1621.md).</span></span>

<span data-ttu-id="d4098-199">Yerel işlevler Lambda ifadelerinde gereksiz gibi görünse de, bu işlemler aslında farklı amaçlara hizmet eder ve farklı kullanımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4098-199">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span> <span data-ttu-id="d4098-200">Yalnızca başka bir yöntemin bağlamından çağrılan bir işlev yazmak istediğinizde yerel işlevler bu durum için daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="d4098-200">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4098-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4098-201">See also</span></span>

- [<span data-ttu-id="d4098-202">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4098-202">Methods</span></span>](methods.md)
