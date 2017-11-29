---
title: "Yerel işlevler (C# programlama Kılavuzu)"
ms.date: 06/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b4e95d48e451038f0f7004d0901f329b2c57fe5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="a7dc4-102">Yerel işlevler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a7dc4-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="a7dc4-103">C# 7, C# destekler'ile başlayan *yerel işlevler*.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-103">Starting with C# 7, C# supports *local functions*.</span></span> <span data-ttu-id="a7dc4-104">Başka bir üye iç içe geçmiş özel bir tür yöntemlerinin yerel işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="a7dc4-105">Kendi içeren üyeden yalnızca çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-105">They can only be called from their containing member.</span></span> <span data-ttu-id="a7dc4-106">Yerel işlevler içinde bildirilen ve çağrılır:</span><span class="sxs-lookup"><span data-stu-id="a7dc4-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="a7dc4-107">Yöntemleri, özellikle Yineleyici ve zaman uyumsuz yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a7dc4-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="a7dc4-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a7dc4-108">Constructors</span></span>
- <span data-ttu-id="a7dc4-109">Özellik erişimcisi</span><span class="sxs-lookup"><span data-stu-id="a7dc4-109">Property accessors</span></span>
- <span data-ttu-id="a7dc4-110">Olay erişimcileri</span><span class="sxs-lookup"><span data-stu-id="a7dc4-110">Event accessors</span></span>
- <span data-ttu-id="a7dc4-111">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7dc4-111">Anonymous methods</span></span>
- <span data-ttu-id="a7dc4-112">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a7dc4-112">Lambda expressions</span></span>
- <span data-ttu-id="a7dc4-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="a7dc4-113">Finalizers</span></span>
- <span data-ttu-id="a7dc4-114">Diğer yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="a7dc4-114">Other local functions</span></span>

<span data-ttu-id="a7dc4-115">Ancak, yerel işlevler bir ifade bodied üye iç bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="a7dc4-116">Bazı durumlarda, ayrıca yerel bir işlev tarafından desteklenen işlevleri uygulamak için bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="a7dc4-117">Bir karşılaştırması için bkz: [Lambda ifadeleri karşılaştırma yerel işlevler](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="a7dc4-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="a7dc4-118">Yerel işlevler kodunuzu Temizle amacı olun.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="a7dc4-119">Herkes okuma yöntemi içeren yöntemi tarafından çağrılabilir dışında değil, kodunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="a7dc4-120">Takım projeleri için de, yanlışlıkla doğrudan başka bir yerden yöntemini çağırmak başka bir geliştirici mümkün yaptıkları sınıfı ya da stuct.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or stuct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="a7dc4-121">Yerel işlev sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7dc4-121">Local function syntax</span></span>

<span data-ttu-id="a7dc4-122">Yerel bir işlev içeren bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="a7dc4-123">Tanımına sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a7dc4-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="a7dc4-124">Yerel işlevler kullanabileceğiniz [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvensiz](../../language-reference/keywords/unsafe.md) değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="a7dc4-125">Kendi yöntem parametreleri de dahil olmak üzere içeren üye içinde tanımlanan tüm yerel değişkenler yerel işlevde erişilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="a7dc4-126">Bir yöntemin tanımı yerel işlev tanımı aşağıdaki öğeleri içeremez:</span><span class="sxs-lookup"><span data-stu-id="a7dc4-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="a7dc4-127">Üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-127">The member access modifier.</span></span> <span data-ttu-id="a7dc4-128">Tüm yerel işlevler özel olduğundan, bir erişim değiştiricisi gibi dahil `private` anahtar sözcüğü oluşturur Derleyici Hatası CS0106, "'özel' değiştiricisi bu öğe için geçerli değil."</span><span class="sxs-lookup"><span data-stu-id="a7dc4-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="a7dc4-129">[Statik](../../language-reference/keywords/static.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="a7dc4-130">Dahil olmak üzere `static` anahtar sözcüğü Derleyici Hatası CS0106 oluşturur, "'static' değiştiricisi bu öğe için geçerli değil."</span><span class="sxs-lookup"><span data-stu-id="a7dc4-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="a7dc4-131">Ayrıca, öznitelikler yerel işlevi veya parametrelerini uygulanamaz ve parametreleri yazın.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="a7dc4-132">Aşağıdaki örnek adlı bir yerel işlevi tanımlar `AppendPathSeparator` adlı bir yönteme özel olan `GetText`:</span><span class="sxs-lookup"><span data-stu-id="a7dc4-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="a7dc4-133">Yerel işlevler ve özel durumlar</span><span class="sxs-lookup"><span data-stu-id="a7dc4-133">Local functions and exceptions</span></span>

<span data-ttu-id="a7dc4-134">Yerel işlevler yararlı özelliklerini hemen yüzey için özel durumlar izin verebilir biridir.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="a7dc4-135">Yöntemi yineleyiciler için özel durumlar, yalnızca döndürülen dizi numaralandırıldığı zaman ve değil yineleyici alındığında çıkmış.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="a7dc4-136">Döndürülen görev beklemenin zaman zaman uyumsuz yöntemleri için bir zaman uyumsuz yöntem karşılaşılan özel durumlar gözetilir.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="a7dc4-137">Aşağıdaki örnek tanımlayan bir `OddSequence` belirli bir aralık arasında tek sayıları numaralandırır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="a7dc4-138">Bir sayı 100'den büyük atladığı için `OddSequence` yöntemi Numaralandırıcı yöntemi atar bir <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="a7dc4-139">Örneğin çıktısını gösterildiği gibi özel durum yalnızca sayıları yinelemek ve Numaralandırıcı almama zamanı ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="a7dc4-140">Bunun yerine, doğrulama yapılırken bir özel durum ve yerel bir işleve yineleyici döndürerek yineleyici almadan önce aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="a7dc4-141">Yerel İşlevler, zaman uyumsuz işlemi dışında özel durumları işlemek için benzer bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="a7dc4-142">Normalde, iç özel durumları inceleyin async yöntemi içinde oluşturulan özel durumları gerektiren bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="a7dc4-143">Yerel işlevler hızlı başarısız ve hem oluşturulur ve zaman uyumlu olarak gözlenen özel izin vermek kodunuzu izin verir.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="a7dc4-144">Aşağıdaki örnek adlı zaman uyumsuz bir yöntem kullanır `GetMultipleAsync` belirtilen sayıda saniye için Duraklat ve o saniye sayısını rastgele birden fazla olan bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="a7dc4-145">En büyük gecikme 5 saniyedir; bir <xref:System.ArgumentOutOfRangeException> değer 5'ten büyük olduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="a7dc4-146">Aşağıdaki örnekte gösterildiği gibi bir değer 6'ın zaman oluşturulur özel durum sınıfına `GetMultipleAsync` yöntemi kaydırılır bir <xref:System.AggregateException> sonra `GetMultipleAsync` yöntemi yürütülmesine başlar.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="a7dc4-147">İle yöntemi yineleyici yaptığımız gibi biz zaman uyumsuz bir yöntemini çağırmadan önce doğrulama gerçekleştirmek için bu örnek kodu yeniden.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="a7dc4-148">Aşağıdaki örnekte gösterildiği çıktısı olarak <xref:System.ArgumentOutOfRangeException> < x:System.AggregateException > içinde sarmalanmamış.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <x:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="a7dc4-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7dc4-149">See also</span></span>
[<span data-ttu-id="a7dc4-150">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a7dc4-150">Methods</span></span>](methods.md)
