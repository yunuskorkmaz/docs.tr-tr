---
title: Yerel işlevler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 24b7d6f98e331110ddcd971d0d0b21003dbe023d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736842"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="c1e5b-102">Yerel işlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c1e5b-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="c1e5b-103">7,0 ile C# başlayarak C# *Yerel işlevleri*destekler.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="c1e5b-104">Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="c1e5b-105">Yalnızca kendi kapsayıcı üyelerinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-105">They can only be called from their containing member.</span></span> <span data-ttu-id="c1e5b-106">Yerel işlevler içinde bildirilebilecek ve şuradan çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="c1e5b-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="c1e5b-107">Yöntemler, özellikle Yineleyici yöntemleri ve zaman uyumsuz yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1e5b-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="c1e5b-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="c1e5b-108">Constructors</span></span>
- <span data-ttu-id="c1e5b-109">Özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="c1e5b-109">Property accessors</span></span>
- <span data-ttu-id="c1e5b-110">Olay erişimcileri</span><span class="sxs-lookup"><span data-stu-id="c1e5b-110">Event accessors</span></span>
- <span data-ttu-id="c1e5b-111">Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1e5b-111">Anonymous methods</span></span>
- <span data-ttu-id="c1e5b-112">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c1e5b-112">Lambda expressions</span></span>
- <span data-ttu-id="c1e5b-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="c1e5b-113">Finalizers</span></span>
- <span data-ttu-id="c1e5b-114">Diğer yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="c1e5b-114">Other local functions</span></span>

<span data-ttu-id="c1e5b-115">Ancak, yerel işlevler ifade-Bodied üyesi içinde bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="c1e5b-116">Bazı durumlarda, bir yerel işlev tarafından desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="c1e5b-117">Bir karşılaştırma için bkz. [Yerel Işlevler lambda ifadelerine kıyasla](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="c1e5b-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="c1e5b-118">Yerel işlevler, kodunuzun amacını açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="c1e5b-119">Kodunuzu okuyan herkes, yöntemin kapsayan Yöntem dışında çağrılabilir olmadığını görebilir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="c1e5b-120">Ekip projeleri için, başka bir geliştiricinin yöntemi doğrudan sınıf veya yapı içinde başka bir yerde çağırmak olanaksız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="c1e5b-121">Yerel işlev sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1e5b-121">Local function syntax</span></span>

<span data-ttu-id="c1e5b-122">Yerel bir işlev, kapsayan bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="c1e5b-123">Tanımı aşağıdaki sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c1e5b-123">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="c1e5b-124">Yerel işlevler, [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvenli olmayan](../../language-reference/keywords/unsafe.md) değiştiriciler kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="c1e5b-125">Kendi Yöntem parametreleri de dahil olmak üzere, kapsayan üyede tanımlanan tüm yerel değişkenlerin yerel işlevde erişilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="c1e5b-126">Bir yöntem tanımının aksine, yerel bir işlev tanımı üye erişim değiştiricisini içeremez.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-126">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="c1e5b-127">Tüm yerel işlevler özel olduğundan, `private` anahtar sözcüğü gibi bir erişim değiştiricisi de dahil olmak üzere, "özel ' değiştiricisi Bu öğe için geçerli değil."</span><span class="sxs-lookup"><span data-stu-id="c1e5b-127">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="c1e5b-128">C# 8,0 ' den önce yerel işlevler `static` değiştiricisini içeremez.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-128">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="c1e5b-129">`static` anahtar sözcüğünü içeren derleyici hatası CS0106, "' static ' değiştiricisi Bu öğe için geçerli değil."</span><span class="sxs-lookup"><span data-stu-id="c1e5b-129">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="c1e5b-130">Ayrıca, öznitelikler yerel işleve veya parametrelerine ve parametre türüne uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-130">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="c1e5b-131">Aşağıdaki örnek, `GetText`adlı bir yönteme özel `AppendPathSeparator` adlı yerel bir işlevi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="c1e5b-131">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="c1e5b-132">Yerel işlevler ve özel durumlar</span><span class="sxs-lookup"><span data-stu-id="c1e5b-132">Local functions and exceptions</span></span>

<span data-ttu-id="c1e5b-133">Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeyine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-133">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="c1e5b-134">Yöntem yineleyiciler için, özel durumlar yalnızca döndürülen dizi numaralandırıldıktan sonra, yineleyici alındığında değil, ortaya çıkacak.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-134">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="c1e5b-135">Zaman uyumsuz metotlar için, bir zaman uyumsuz yöntemde oluşturulan özel durumlar, döndürülen görev beklendiğinde gözlemlenir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-135">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="c1e5b-136">Aşağıdaki örnek, belirtilen bir Aralık arasındaki tek sayıları numaralandırır `OddSequence` yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-136">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="c1e5b-137">`OddSequence` Numaralandırıcı yöntemine 100 ' den büyük bir sayı geçirdiğinden, yöntem bir <xref:System.ArgumentOutOfRangeException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-137">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="c1e5b-138">Örneğin çıkışının gösterdiği gibi, özel durum yalnızca sayıları tekrarladığı zaman, numaralandırıcıyı alırken değil, yüzeyleri.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-138">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="c1e5b-139">Bunun yerine, aşağıdaki örnekte gösterildiği gibi, bir yerel işlevden Yineleyici döndürerek, doğrulama gerçekleştirirken ve yineleyici almadan önce bir özel durum oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-139">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="c1e5b-140">Yerel işlevler, zaman uyumsuz işlem dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-140">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="c1e5b-141">Genellikle, zaman uyumsuz yöntemde oluşturulan özel durumlar, bir <xref:System.AggregateException>iç özel durumlarını incelemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-141">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="c1e5b-142">Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasına olanak tanır ve özel durumun hem zaman uyumlu olarak hem de aynı şekilde gözlemlenip</span><span class="sxs-lookup"><span data-stu-id="c1e5b-142">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="c1e5b-143">Aşağıdaki örnek, belirtilen saniye sayısını duraklatmak için `GetMultipleAsync` adlı zaman uyumsuz bir yöntem kullanır ve bu kadar saniye rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-143">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="c1e5b-144">En fazla gecikme 5 saniyedir; değer 5 ' ten büyükse bir <xref:System.ArgumentOutOfRangeException> sonuç elde edilir.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-144">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="c1e5b-145">Aşağıdaki örnekte gösterildiği gibi, `GetMultipleAsync` yöntemine 6 değeri geçirildiğinde oluşturulan özel durum, `GetMultipleAsync` yöntemi yürütülmeye başladıktan sonra bir <xref:System.AggregateException> sarmalanır.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-145">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="c1e5b-146">Yöntem yineleyicisi ile yaptığımız gibi, zaman uyumsuz metodu çağırmadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-146">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="c1e5b-147">Aşağıdaki örnekteki Çıktının gösterdiği gibi, <xref:System.ArgumentOutOfRangeException> bir <xref:System.AggregateException>sarmalanmamış.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-147">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="c1e5b-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1e5b-148">See also</span></span>

- [<span data-ttu-id="c1e5b-149">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1e5b-149">Methods</span></span>](methods.md)
