---
title: "ref (C# Başvurusu)"
ms.date: 05/30/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0be0eee67b507e2a209c9caaa3eb14cc60e8a763
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ref-c-reference"></a><span data-ttu-id="8afcd-102">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8afcd-102">ref (C# Reference)</span></span>

<span data-ttu-id="8afcd-103">`ref` Anahtar sözcüğü başvuruya göre geçirilen bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="8afcd-104">Üç farklı bağlamlarda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="8afcd-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="8afcd-105">Bir yöntem imzası ve bir yönteme başvuruya göre bağımsız değişken geçirmek için bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="8afcd-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="8afcd-106">Bkz: [başvuruya göre bağımsız değişken geçirme](#passing-an-argument-by-reference) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8afcd-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="8afcd-107">Başvuruya göre çağırana bir değer döndürmek için bir yöntem imza ile.</span><span class="sxs-lookup"><span data-stu-id="8afcd-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="8afcd-108">Bkz: [başvuru dönüş değerleri](#reference-return-values) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8afcd-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="8afcd-109">Bir başvuru dönüş değeri çağıran değiştirme amaçlayan bir başvuru olarak yerel olarak depolanan belirtmek için bir üye gövdesine.</span><span class="sxs-lookup"><span data-stu-id="8afcd-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="8afcd-110">Bkz: [Ref Yereller](#ref-locals) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8afcd-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="8afcd-111">Başvuruya göre bağımsız değişken geçirme</span><span class="sxs-lookup"><span data-stu-id="8afcd-111">Passing an argument by reference</span></span>

<span data-ttu-id="8afcd-112">Bir yöntemin parametre listesinde kullanıldığında `ref` anahtar sözcüğü gösterir bağımsız değişken değeri tarafından başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="8afcd-113">Başvuruya göre geçirme çağrılan yöntemin değişkeninde herhangi bir değişiklik arama yönteminde yansıtılır etkisidir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="8afcd-114">Örneğin, yerel bir değişken ifadesi veya bir dizi öğesi erişim ifadesi çağıran geçerse ve çağrılan yöntemin hangi ref parametresi gösterir, ardından çağıran yerel nesnenin yerini değişken veya dizi öğesi artık yeni bir nesneye başvuruyor olduğunda yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8afcd-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="8afcd-115">Başvuru türleri kavramı ile başvuruya göre geçirme kavramı karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="8afcd-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="8afcd-116">İki kavramları aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-116">The two concepts are not the same.</span></span> <span data-ttu-id="8afcd-117">Yöntem parametresi tarafından değiştirilebilir `ref` bir değer türü veya bir başvuru türü olmasından bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="8afcd-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="8afcd-118">Başvuruya göre geçirildiğinde hiçbir kutulama değer türü yok.</span><span class="sxs-lookup"><span data-stu-id="8afcd-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="8afcd-119">Kullanılacak bir `ref` parametresi, yöntem tanımı ve arama yöntemi açıkça kullanmalıdır `ref` aşağıdaki örnekte gösterildiği gibi anahtar.</span><span class="sxs-lookup"><span data-stu-id="8afcd-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

<span data-ttu-id="8afcd-120">Geçirilen bağımsız değişken bir `ref` parametresi, geçirilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8afcd-120">An argument that is passed to a `ref` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="8afcd-121">Bu farklıdır [çıkışı](out.md) parametreleri olan bağımsız değişkenler bunlar geçirilmeden önce açıkça başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8afcd-121">This differs from [out](out.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="8afcd-122">Sınıf üyeleri yalnızca farklı imzalar olamaz `ref` ve `out`.</span><span class="sxs-lookup"><span data-stu-id="8afcd-122">Members of a class can't have signatures that differ only by `ref` and `out`.</span></span> <span data-ttu-id="8afcd-123">Bir türün iki üyeleri arasındaki tek fark, biri olduğunda bunları sahip bir derleyici hatası oluşursa bir `ref` parametre ve diğer sahip bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8afcd-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out` parameter.</span></span> <span data-ttu-id="8afcd-124">Aşağıdaki kod, örneğin, derleme değil.</span><span class="sxs-lookup"><span data-stu-id="8afcd-124">The following code, for example, doesn't compile.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 <span data-ttu-id="8afcd-125">Bir yöntemi varsa ancak yöntemlerini aşırı yüklenebilir bir `ref` veya `out` parametre ve diğer aşağıdaki örnekte gösterildiği gibi bir değer parametresine sahip.</span><span class="sxs-lookup"><span data-stu-id="8afcd-125">However, methods can be overloaded when one method has a `ref` or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
 [!code-csharp[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 <span data-ttu-id="8afcd-126">İmza eşleştirme gizleme veya geçersiz kılma, gibi gerektiren diğer durumlarda `ref` ve `out` imza parçası olan ve birbirlerine eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="8afcd-126">In other situations that require signature matching, such as hiding or overriding, `ref` and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="8afcd-127">Özellikler değişkenleri değildir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-127">Properties are not variables.</span></span> <span data-ttu-id="8afcd-128">Bunlar yöntemleri ve için geçirilemez `ref` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="8afcd-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="8afcd-129">Diziler geçirmek hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="8afcd-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="8afcd-130">Kullanamazsınız `ref` ve `out` yöntemleri şu tür için anahtar sözcükleri:</span><span class="sxs-lookup"><span data-stu-id="8afcd-130">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="8afcd-131">Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="8afcd-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="8afcd-132">Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8afcd-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  
  
## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="8afcd-133">Başvuruya göre bağımsız değişken geçirme: örneği</span><span class="sxs-lookup"><span data-stu-id="8afcd-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="8afcd-134">Önceki örneklerde değer türleri başvuruya göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="8afcd-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="8afcd-135">Aynı zamanda `ref` başvuru geçirmek için anahtar sözcüğü türleri başvuruya göre.</span><span class="sxs-lookup"><span data-stu-id="8afcd-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="8afcd-136">Bir başvuru türü başvuruya göre geçirme başvuru parametresi çağrı yapan başvurduğu nesneyi değiştirmek çağrılan yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8afcd-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="8afcd-137">Nesne depolama konumunu yönteme başvurusu parametre değeri olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="8afcd-138">Depolama konumu (yeni bir nesneye işaret edecek şekilde) parametresinin değeri değiştirirseniz, aynı zamanda çağıran başvurduğu depolama konumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8afcd-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="8afcd-139">Aşağıdaki örnek başvuru türünde bir örneğini geçirmeden bir `ref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8afcd-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
 [!code-csharp[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

<span data-ttu-id="8afcd-140">Başvuru türleri değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8afcd-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="8afcd-141">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="8afcd-141">Reference return values</span></span>

<span data-ttu-id="8afcd-142">Başvuru dönüş değerleri (veya ref döndürür) çağırana başvuruya göre bir yöntem döndüren değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="8afcd-143">Diğer bir deyişle, arayan bir yöntemi tarafından döndürülen değer değiştirebilirsiniz ve bu değişikliği yöntemi içeren nesneyi durumda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="8afcd-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="8afcd-144">Bir başvuru dönüş değeri kullanılarak tanımlanmış `ref` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="8afcd-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="8afcd-145">Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="8afcd-145">In the method signature.</span></span> <span data-ttu-id="8afcd-146">Örneğin, aşağıdaki yöntemi imza inidicates, `GetCurrentPrice` yöntemi döndürür bir <xref:System.Decimal> başvuruya değeri.</span><span class="sxs-lookup"><span data-stu-id="8afcd-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="8afcd-147">Her önce `return` yöntemi deyiminde.</span><span class="sxs-lookup"><span data-stu-id="8afcd-147">Before each `return` statement in the method.</span></span> <span data-ttu-id="8afcd-148">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8afcd-148">For example:</span></span>
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

<span data-ttu-id="8afcd-149">Nesnenin durumu değiştirmek çağıran için sırayla başvuru dönüş değeri depolanan, olarak açıkça tanımlanmış bir değişken için bir [ref yerel](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="8afcd-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="8afcd-150">Bir örnek için bkz: [bir başvuru döndürür ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="8afcd-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="8afcd-151">Ref Yereller</span><span class="sxs-lookup"><span data-stu-id="8afcd-151">Ref locals</span></span>

<span data-ttu-id="8afcd-152">Ref yerel değişken değerleri kullanarak döndürülen başvurmak için kullanılan `ref return`.</span><span class="sxs-lookup"><span data-stu-id="8afcd-152">A ref local variable is used to refer to values returned using `ref return`.</span></span>  <span data-ttu-id="8afcd-153">Ref yerel değişken başlatılmalı ve ref dönüş değerine atanmış.</span><span class="sxs-lookup"><span data-stu-id="8afcd-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="8afcd-154">Değer yapılan tüm değişiklikler yerel ref, değeri olan yöntemi döndürülen nesnenin durumda başvuruya göre yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="8afcd-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="8afcd-155">Kullanarak yerel bir ref tanımlayın `ref` değişken bildirimi önce yanı sıra hemen başvuruya göre değeri döndüren yöntemi çağırmadan önce anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8afcd-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="8afcd-156">Örneğin, aşağıdaki deyim adlı bir yöntemi tarafından döndürülen ref yerel değerin tanımlar `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="8afcd-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="8afcd-157">Unutmayın `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır ya da derleyici hatası "değerine sahip bir başvuru tarafından değişken başlatılamıyor." CS8172 oluşturur</span><span class="sxs-lookup"><span data-stu-id="8afcd-157">Note that the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="8afcd-158">Bir başvuru döndürür ve ref Yereller örneği</span><span class="sxs-lookup"><span data-stu-id="8afcd-158">A ref returns and ref locals example</span></span>

<span data-ttu-id="8afcd-159">Aşağıdaki örnek tanımlayan bir `Book` iki olan sınıfı <xref:System.String> alanları `Title` ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="8afcd-159">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="8afcd-160">Ayrıca tanımlayan bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8afcd-160">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="8afcd-161">Tek tek defteri nesneleri çağırarak başvuruya göre döndürülür, `GetBookByTitle` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8afcd-161">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

<span data-ttu-id="8afcd-162">Ne zaman çağıran depolar tarafından döndürülen değer `GetBookByTitle` yöntemi ref yerel olarak çağıran dönüş değerini yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="8afcd-162">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a><span data-ttu-id="8afcd-163">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8afcd-163">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8afcd-164">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8afcd-164">See Also</span></span>  
 [<span data-ttu-id="8afcd-165">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8afcd-165">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8afcd-166">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8afcd-166">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8afcd-167">Parametreleri geçirme</span><span class="sxs-lookup"><span data-stu-id="8afcd-167">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="8afcd-168">Yöntem parametreleri</span><span class="sxs-lookup"><span data-stu-id="8afcd-168">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="8afcd-169">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8afcd-169">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
