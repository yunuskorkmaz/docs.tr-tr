---
title: Yerel işlevler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e91069c25ebe6c2a22927391734e5030a908e4ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646234"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="e8bfa-102">Yerel işlevler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e8bfa-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="e8bfa-103">C# 7.0, C# destekleyen'ile başlayan *yerel işlevler*.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="e8bfa-104">Yerel işlevler başka bir üye iç içe geçmiş özel bir tür yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="e8bfa-105">Bunlar, yalnızca kendi kapsayan üyeden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-105">They can only be called from their containing member.</span></span> <span data-ttu-id="e8bfa-106">Yerel işlevler içinde bildirilen ve çağrılır:</span><span class="sxs-lookup"><span data-stu-id="e8bfa-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="e8bfa-107">Yöntemler, özellikle Yineleyici ve zaman uyumsuz yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e8bfa-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="e8bfa-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e8bfa-108">Constructors</span></span>
- <span data-ttu-id="e8bfa-109">Özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="e8bfa-109">Property accessors</span></span>
- <span data-ttu-id="e8bfa-110">Olay erişimcileri</span><span class="sxs-lookup"><span data-stu-id="e8bfa-110">Event accessors</span></span>
- <span data-ttu-id="e8bfa-111">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="e8bfa-111">Anonymous methods</span></span>
- <span data-ttu-id="e8bfa-112">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e8bfa-112">Lambda expressions</span></span>
- <span data-ttu-id="e8bfa-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="e8bfa-113">Finalizers</span></span>
- <span data-ttu-id="e8bfa-114">Diğer yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="e8bfa-114">Other local functions</span></span>

<span data-ttu-id="e8bfa-115">Ancak, yerel işlevler bir ifade gövdeli üyenin içinde bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="e8bfa-116">Bazı durumlarda, bir lambda ifadesi, ayrıca yerel bir işlev tarafından desteklenen işlevselliği uygulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="e8bfa-117">Bir karşılaştırması için bkz. [Lambda ifadeleri karşılaştırma yerel işlevler](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="e8bfa-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="e8bfa-118">Yerel işlevler Temizle, kodun amacı olun.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="e8bfa-119">Herkes okuma, kod yöntemi içeren yöntemi tarafından çağrılabilir dışında olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="e8bfa-120">Takım projeleri için bunlar da yanlışlıkla doğrudan yerlerden yöntemini çağırmak başka bir geliştirici imkansız hale sınıf veya yapı içinde.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="e8bfa-121">Yerel işlev sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8bfa-121">Local function syntax</span></span>

<span data-ttu-id="e8bfa-122">Yerel bir işlev içeren bir üye iç içe geçmiş bir yöntemde olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="e8bfa-123">Tanımı sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e8bfa-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="e8bfa-124">Yerel işlevler kullanabileceğiniz [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvenli](../../language-reference/keywords/unsafe.md) değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="e8bfa-125">Yöntem parametreleri içeren üyesinde tanımlanan tüm yerel değişkenlerin yerel işlevde erişilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="e8bfa-126">Bir yöntem tanımını bir yerel işlev tanımı aşağıdaki öğeleri içeremez:</span><span class="sxs-lookup"><span data-stu-id="e8bfa-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="e8bfa-127">Üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-127">The member access modifier.</span></span> <span data-ttu-id="e8bfa-128">Tüm yerel işlevler özel olduğundan, bir erişim değiştiricisidir gibi `private` anahtar sözcüğü, Derleyici Hatası CS0106, "'private' değiştiricisi bu öğe için geçerli değil." oluşturur</span><span class="sxs-lookup"><span data-stu-id="e8bfa-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="e8bfa-129">[Statik](../../language-reference/keywords/static.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="e8bfa-130">Dahil olmak üzere `static` anahtar sözcüğü, Derleyici Hatası CS0106 oluşturur, "'static' değiştiricisi bu öğe için geçerli değil."</span><span class="sxs-lookup"><span data-stu-id="e8bfa-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="e8bfa-131">Ayrıca, öznitelikler, yerel bir işlev veya parametrelerini uygulanamaz ve tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="e8bfa-132">Aşağıdaki örnek adlı bir yerel işlev tanımlar `AppendPathSeparator` adlı bir yöntem özel olan `GetText`:</span><span class="sxs-lookup"><span data-stu-id="e8bfa-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="e8bfa-133">Yerel işlevler ve özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e8bfa-133">Local functions and exceptions</span></span>

<span data-ttu-id="e8bfa-134">Yerel işlevler yararlı özelliklerini hemen yüzey özel durumlara izin verebilirsiniz biridir.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="e8bfa-135">Yöntemi yineleyiciler için özel durumlar döndürülen dizi yalnızca numaralandırılana zaman ve yineleyici alınamaz zaman takip edilir.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="e8bfa-136">Döndürülen görevin bekletildiğinde zaman uyumsuz yöntemler için zaman uyumsuz bir yöntem içinde oluşturulan özel durumlar gözlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="e8bfa-137">Aşağıdaki örnekte tanımlayan bir `OddSequence` tek sayıları belirtilen bir aralıktaki arasında numaralandırır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="e8bfa-138">Bir sayı için 100'den büyük geçirdiği için `OddSequence` Numaralandırıcı yöntemi çağırılıyorsa yöntem bir <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="e8bfa-139">Örneğin çıktısında gösterildiği gibi özel durum sayıları yalnızca yineleme yapmak ve Numaralandırıcı alamaz zamanı ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="e8bfa-140">Bunun yerine, doğrulama yapılırken bir özel durum oluşturabilecek ve yerel bir işlevden yineleyici döndürerek yineleyici almadan önce aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="e8bfa-141">Yerel İşlevler, zaman uyumsuz işlemi dışında özel durumları işlemek için benzer bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="e8bfa-142">Normalde, zaman uyumsuz yöntemde oluşan özel durum iç özel durumları incelemeniz gerektiren bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="e8bfa-143">Yerel işlevler hızlı başarısız olma ve özel durum hem zaman uyumlu olarak gözlemlenen izin vermek kodunuzu izin verir.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="e8bfa-144">Aşağıdaki örnekte adlı bir zaman uyumsuz yöntem `GetMultipleAsync` belirtilen sayıda saniye için Duraklat ve o saniye sayısını rastgele katları olan bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="e8bfa-145">En büyük gecikme değeri 5 saniyedir; bir <xref:System.ArgumentOutOfRangeException> değer 5'ten büyük olduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="e8bfa-146">Aşağıdaki örnekte gösterildiği gibi 6 değeri olduğunda oluşturulan özel durum geçirilen `GetMultipleAsync` yöntemi içinde kaydırılır bir <xref:System.AggregateException> sonra `GetMultipleAsync` yöntemi yürütülmesine başlar.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="e8bfa-147">İle yöntemi yineleyici yaptığımız gibi Biz bu örnekte, zaman uyumsuz yöntemi çağırmadan önce doğrulamayı gerçekleştirmek için kodu yeniden düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="e8bfa-148">Aşağıdaki örnekte gösterildiği çıktısı olarak <xref:System.ArgumentOutOfRangeException> , sarmalanmamış bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="e8bfa-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8bfa-149">See also</span></span>

- [<span data-ttu-id="e8bfa-150">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e8bfa-150">Methods</span></span>](methods.md)
