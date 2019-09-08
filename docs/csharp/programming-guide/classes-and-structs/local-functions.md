---
title: Yerel işlevler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f572f683511fe90951f841c80eae448a9cb6054b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785083"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="0633f-102">Yerel işlevler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0633f-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="0633f-103">7,0 ile C# başlayarak C# *Yerel işlevleri*destekler.</span><span class="sxs-lookup"><span data-stu-id="0633f-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="0633f-104">Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="0633f-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="0633f-105">Yalnızca kendi kapsayıcı üyelerinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0633f-105">They can only be called from their containing member.</span></span> <span data-ttu-id="0633f-106">Yerel işlevler içinde bildirilebilecek ve şuradan çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="0633f-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="0633f-107">Yöntemler, özellikle Yineleyici yöntemleri ve zaman uyumsuz yöntemler</span><span class="sxs-lookup"><span data-stu-id="0633f-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="0633f-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0633f-108">Constructors</span></span>
- <span data-ttu-id="0633f-109">Özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="0633f-109">Property accessors</span></span>
- <span data-ttu-id="0633f-110">Olay erişimcileri</span><span class="sxs-lookup"><span data-stu-id="0633f-110">Event accessors</span></span>
- <span data-ttu-id="0633f-111">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="0633f-111">Anonymous methods</span></span>
- <span data-ttu-id="0633f-112">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0633f-112">Lambda expressions</span></span>
- <span data-ttu-id="0633f-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="0633f-113">Finalizers</span></span>
- <span data-ttu-id="0633f-114">Diğer yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="0633f-114">Other local functions</span></span>

<span data-ttu-id="0633f-115">Ancak, yerel işlevler ifade-Bodied üyesi içinde bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="0633f-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="0633f-116">Bazı durumlarda, bir yerel işlev tarafından desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0633f-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="0633f-117">Bir karşılaştırma için bkz. [Yerel Işlevler lambda ifadelerine kıyasla](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="0633f-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="0633f-118">Yerel işlevler, kodunuzun amacını açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0633f-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="0633f-119">Kodunuzu okuyan herkes, yöntemin kapsayan Yöntem dışında çağrılabilir olmadığını görebilir.</span><span class="sxs-lookup"><span data-stu-id="0633f-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="0633f-120">Ekip projeleri için, başka bir geliştiricinin yöntemi doğrudan sınıf veya yapı içinde başka bir yerde çağırmak olanaksız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0633f-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="0633f-121">Yerel işlev sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0633f-121">Local function syntax</span></span>

<span data-ttu-id="0633f-122">Yerel bir işlev, kapsayan bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0633f-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="0633f-123">Tanımı aşağıdaki sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0633f-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="0633f-124">Yerel işlevler, [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvenli olmayan](../../language-reference/keywords/unsafe.md) değiştiriciler kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0633f-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="0633f-125">Kendi Yöntem parametreleri de dahil olmak üzere, kapsayan üyede tanımlanan tüm yerel değişkenlerin yerel işlevde erişilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0633f-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="0633f-126">Bir yöntem tanımının aksine, yerel bir işlev tanımı aşağıdaki öğeleri içeremez:</span><span class="sxs-lookup"><span data-stu-id="0633f-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="0633f-127">Üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0633f-127">The member access modifier.</span></span> <span data-ttu-id="0633f-128">Tüm yerel işlevler özel olduğundan, `private` anahtar sözcüğü gibi bir erişim değiştiricisi de dahil olmak üzere, "özel ' değiştiricisi Bu öğe için geçerli değil."</span><span class="sxs-lookup"><span data-stu-id="0633f-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="0633f-129">[Static](../../language-reference/keywords/static.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0633f-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="0633f-130">"Static ' değiştiricisi Bu öğe için geçerli değil, anahtarsözcüğünüCS0106derleyicihatasıoluşturuyor."`static`</span><span class="sxs-lookup"><span data-stu-id="0633f-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="0633f-131">Ayrıca, öznitelikler yerel işleve veya parametrelerine ve parametre türüne uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="0633f-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="0633f-132">Aşağıdaki örnek adlı bir yerel işlevi `AppendPathSeparator` `GetText`tanımlar:</span><span class="sxs-lookup"><span data-stu-id="0633f-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="0633f-133">Yerel işlevler ve özel durumlar</span><span class="sxs-lookup"><span data-stu-id="0633f-133">Local functions and exceptions</span></span>

<span data-ttu-id="0633f-134">Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeyine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="0633f-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="0633f-135">Yöntem yineleyiciler için, özel durumlar yalnızca döndürülen dizi numaralandırıldıktan sonra, yineleyici alındığında değil, ortaya çıkacak.</span><span class="sxs-lookup"><span data-stu-id="0633f-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="0633f-136">Zaman uyumsuz metotlar için, bir zaman uyumsuz yöntemde oluşturulan özel durumlar, döndürülen görev beklendiğinde gözlemlenir.</span><span class="sxs-lookup"><span data-stu-id="0633f-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="0633f-137">Aşağıdaki örnek, belirtilen bir `OddSequence` Aralık arasındaki tek sayıları numaralandırır bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0633f-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="0633f-138">`OddSequence` Numaralandırıcı yöntemine 100 ' den büyük bir sayı geçirdiğinden, yöntemi bir <xref:System.ArgumentOutOfRangeException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0633f-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="0633f-139">Örneğin çıkışının gösterdiği gibi, özel durum yalnızca sayıları tekrarladığı zaman, numaralandırıcıyı alırken değil, yüzeyleri.</span><span class="sxs-lookup"><span data-stu-id="0633f-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="0633f-140">Bunun yerine, aşağıdaki örnekte gösterildiği gibi, bir yerel işlevden Yineleyici döndürerek, doğrulama gerçekleştirirken ve yineleyici almadan önce bir özel durum oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0633f-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="0633f-141">Yerel işlevler, zaman uyumsuz işlem dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0633f-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="0633f-142">Genellikle, zaman uyumsuz yöntemde oluşturulan özel durumlar, öğesinin <xref:System.AggregateException>iç özel durumlarını incelemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0633f-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="0633f-143">Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasına olanak tanır ve özel durumun hem zaman uyumlu olarak hem de aynı şekilde gözlemlenip</span><span class="sxs-lookup"><span data-stu-id="0633f-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="0633f-144">Aşağıdaki örnek, belirtilen saniye sayısını duraklatmak için `GetMultipleAsync` adlı zaman uyumsuz bir yöntem kullanır ve bu sayıda saniyeden oluşan rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="0633f-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="0633f-145">En fazla gecikme 5 saniyedir; değer <xref:System.ArgumentOutOfRangeException> 5 ' ten büyükse bir sonuç elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0633f-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="0633f-146">Aşağıdaki örnekte gösterildiği gibi, `GetMultipleAsync` yöntemine 6 değeri geçirildiğinde oluşturulan özel durum, `GetMultipleAsync` Yöntem yürütmeye başladıktan sonra bir <xref:System.AggregateException> öğesine kaydırılır.</span><span class="sxs-lookup"><span data-stu-id="0633f-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="0633f-147">Yöntem yineleyicisi ile yaptığımız gibi, zaman uyumsuz metodu çağırmadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0633f-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="0633f-148">Aşağıdaki örnekteki Çıktının gösterdiği gibi, ' <xref:System.ArgumentOutOfRangeException> a <xref:System.AggregateException>sarmalanmaz.</span><span class="sxs-lookup"><span data-stu-id="0633f-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="0633f-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0633f-149">See also</span></span>

- [<span data-ttu-id="0633f-150">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0633f-150">Methods</span></span>](methods.md)
