---
title: Yerel işlevler - C# Programlama Kılavuzu
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: b6924b8981af5115a474eeb6b2e5376dd1b17ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170241"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="6e6b4-102">Yerel işlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6e6b4-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="6e6b4-103">C# 7.0 ile başlayarak, C# *yerel işlevleri*destekler.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="6e6b4-104">Yerel işlevler, başka bir üyede iç içe olan bir türdeki özel yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="6e6b4-105">Yalnızca kendi üyelerinden çağrılabilirler.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-105">They can only be called from their containing member.</span></span> <span data-ttu-id="6e6b4-106">Yerel işlevler bildirilebilir ve şu andan itibaren çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="6e6b4-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="6e6b4-107">Yöntemler, özellikle reeratör yöntemleri ve async yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6e6b4-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="6e6b4-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="6e6b4-108">Constructors</span></span>
- <span data-ttu-id="6e6b4-109">Özellik erişime girenler</span><span class="sxs-lookup"><span data-stu-id="6e6b4-109">Property accessors</span></span>
- <span data-ttu-id="6e6b4-110">Etkinlik erişime girenler</span><span class="sxs-lookup"><span data-stu-id="6e6b4-110">Event accessors</span></span>
- <span data-ttu-id="6e6b4-111">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e6b4-111">Anonymous methods</span></span>
- <span data-ttu-id="6e6b4-112">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6e6b4-112">Lambda expressions</span></span>
- <span data-ttu-id="6e6b4-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="6e6b4-113">Finalizers</span></span>
- <span data-ttu-id="6e6b4-114">Diğer yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="6e6b4-114">Other local functions</span></span>

<span data-ttu-id="6e6b4-115">Ancak, yerel işlevler ifade gövdeli bir üye içinde bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="6e6b4-116">Bazı durumlarda, yerel bir işlev tarafından da desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="6e6b4-117">Karşılaştırma için, [Lambda ifadeleri ile karşılaştırıldığında Yerel işlevler](../../local-functions-vs-lambdas.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="6e6b4-118">Yerel işlevler, kodunuzu açıkça ortaya kovar.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="6e6b4-119">Kodunuzu okuyan herkes, içeren yöntem dışında yöntemin çağrılabilir olmadığını görebilir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="6e6b4-120">Takım projeleri için, başka bir geliştiricinin yöntemi yanlışlıkla sınıfın veya yapının başka bir yerinden yanlışlıkla aramasını da imkansız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="6e6b4-121">Yerel işlev sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e6b4-121">Local function syntax</span></span>

<span data-ttu-id="6e6b4-122">Yerel bir işlev, iç içe bir üyenin içinde iç içe bir yöntem olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="6e6b4-123">Tanımıaşağıdaki sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6e6b4-123">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="6e6b4-124">Yerel işlevler [async](../../language-reference/keywords/async.md) ve [güvensiz](../../language-reference/keywords/unsafe.md) değiştiriciler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

<span data-ttu-id="6e6b4-125">Yöntem parametreleri de dahil olmak üzere, ilgili üyede tanımlanan tüm yerel değişkenlere yerel işlevde erişilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span>

<span data-ttu-id="6e6b4-126">Yöntem tanımının aksine, yerel işlev tanımı üye erişim değiştiriciyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-126">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="6e6b4-127">`private` Anahtar kelime gibi bir erişim değiştirici de dahil olmak üzere tüm yerel işlevler özel olduğundan, cs0106 derleyici hatası oluşturur, "Değiştirici 'özel' bu öğe için geçerli değildir."</span><span class="sxs-lookup"><span data-stu-id="6e6b4-127">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="6e6b4-128">C# 8.0'dan önce yerel `static` işlevler değiştiriciyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-128">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="6e6b4-129">`static` Anahtar kelime de dahil olmak üzere derleyici hatası CS0106 oluşturur, "Değiştirici 'statik' bu öğe için geçerli değildir."</span><span class="sxs-lookup"><span data-stu-id="6e6b4-129">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="6e6b4-130">Ayrıca, öznitelikler yerel işleve veya parametrelerine ve tür parametrelerine uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-130">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span>

<span data-ttu-id="6e6b4-131">Aşağıdaki örnek, adlı bir `AppendPathSeparator` yönteme özel olan `GetText`yerel bir işlev tanımlar:</span><span class="sxs-lookup"><span data-stu-id="6e6b4-131">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="6e6b4-132">Yerel işlevler ve özel durumlar</span><span class="sxs-lookup"><span data-stu-id="6e6b4-132">Local functions and exceptions</span></span>

<span data-ttu-id="6e6b4-133">Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeye çıkmasına izin verebilmeleridir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-133">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="6e6b4-134">Yöntem yineleyicileri için, özel durumlar yalnızca döndürülen sıra numaralandırıldığında su yüzüne çıkar, yineleyici alındığında değil.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-134">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="6e6b4-135">Async yöntemleri için, döndürülen görev bekleniyor zaman bir async yöntemi atılan tüm özel durumlar gözlenir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-135">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="6e6b4-136">Aşağıdaki örnek, belirli `OddSequence` bir aralık arasında tek sayılar numaralandırmak bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-136">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="6e6b4-137">Numaralandırma yöntemine 100'den `OddSequence` büyük bir sayı geçtiği için, yöntem <xref:System.ArgumentOutOfRangeException>bir .</span><span class="sxs-lookup"><span data-stu-id="6e6b4-137">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="6e6b4-138">Örnekteki çıktının gösterdiği gibi, özel durum yalnızca sayıyı kaydettiğinizde değil, sayıları yinelediğinizde ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-138">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

<span data-ttu-id="6e6b4-139">Bunun yerine, doğrulama gerçekleştirirken ve aşağıdaki örnekte görüldüğü gibi, yineleyiciyi yerel bir işlevden döndürerek yineleyiciyi almadan önce bir özel durum atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-139">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="6e6b4-140">Yerel işlevler, asynchronous işleminin dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-140">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="6e6b4-141">Normalde, async yönteminde atılan özel durumlar, bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-141">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="6e6b4-142">Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasını ve özel durumlarınızın hem atılmasına hem de eşzamanlı olarak gözlenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-142">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="6e6b4-143">Aşağıdaki örnek, belirli bir saniye `GetMultipleAsync` sayısı için duraklatmak ve bu saniye sayısının rasgele bir katını döndürecek bir değer döndürmek için adlandırılmış bir eşzamanlı yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-143">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="6e6b4-144">Maksimum gecikme 5 saniyedir; değeri <xref:System.ArgumentOutOfRangeException> 5'ten büyükse sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-144">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="6e6b4-145">Aşağıdaki örnekte de görüldüğü gibi, `GetMultipleAsync` <xref:System.AggregateException> `GetMultipleAsync` yönteme 6 değeri geçirildiğinde atılan özel durum, yöntem yürütmeye başladıktan sonra bir şekilde sarılır.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-145">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

<span data-ttu-id="6e6b4-146">Yöntem yineleyicide yaptığımız gibi, asynchronous yöntemini aramadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden değerlendirebiliriz.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-146">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="6e6b4-147">Aşağıdaki örnekteki çıktının gösterdiği <xref:System.ArgumentOutOfRangeException> gibi, bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-147">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="see-also"></a><span data-ttu-id="6e6b4-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e6b4-148">See also</span></span>

- [<span data-ttu-id="6e6b4-149">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e6b4-149">Methods</span></span>](methods.md)
