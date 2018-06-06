---
title: ref (C# Başvurusu)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: a4d5719bccd240658880cc5c6e549e8c912ca1b9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696400"
---
# <a name="ref-c-reference"></a><span data-ttu-id="7627a-102">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7627a-102">ref (C# Reference)</span></span>

<span data-ttu-id="7627a-103">`ref` Anahtar sözcüğü başvuruya göre geçirilen bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="7627a-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="7627a-104">Üç farklı bağlamlarda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="7627a-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="7627a-105">Bir yöntem imzası ve bir yönteme başvuruya göre bağımsız değişken geçirmek için bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="7627a-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="7627a-106">Bkz: [başvuruya göre bağımsız değişken geçirme](#passing-an-argument-by-reference) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="7627a-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="7627a-107">Başvuruya göre çağırana bir değer döndürmek için bir yöntem imza ile.</span><span class="sxs-lookup"><span data-stu-id="7627a-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="7627a-108">Bkz: [başvuru dönüş değerleri](#reference-return-values) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="7627a-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="7627a-109">Üye gövdesinde bir başvuru dönüş değeri çağıran değiştirme amaçlayan bir başvuru olarak yerel veya genel olarak, depolanan belirtmek için bir yerel değişken başka bir değer başvuruya göre erişir.</span><span class="sxs-lookup"><span data-stu-id="7627a-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="7627a-110">Bkz: [Ref Yereller](#ref-locals) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="7627a-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="7627a-111">Başvuruya göre bağımsız değişken geçirme</span><span class="sxs-lookup"><span data-stu-id="7627a-111">Passing an argument by reference</span></span>

<span data-ttu-id="7627a-112">Bir yöntemin parametre listesinde kullanıldığında `ref` anahtar sözcüğü gösterir bağımsız değişken değeri tarafından başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7627a-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="7627a-113">Başvuruya göre geçirme çağrılan yöntemin değişkeninde herhangi bir değişiklik arama yönteminde yansıtılır etkisidir.</span><span class="sxs-lookup"><span data-stu-id="7627a-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="7627a-114">Örneğin, yerel bir değişken ifadesi veya bir dizi öğesi erişim ifadesi çağıran geçerse ve çağrılan yöntemin hangi ref parametresi gösterir, ardından çağıran yerel nesnenin yerini değişken veya dizi öğesi artık yeni bir nesneye başvuruyor olduğunda yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7627a-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="7627a-115">Başvuru türleri kavramı ile başvuruya göre geçirme kavramı karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="7627a-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="7627a-116">İki kavramları aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="7627a-116">The two concepts are not the same.</span></span> <span data-ttu-id="7627a-117">Yöntem parametresi tarafından değiştirilebilir `ref` bir değer türü veya bir başvuru türü olmasından bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="7627a-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="7627a-118">Başvuruya göre geçirildiğinde hiçbir kutulama değer türü yok.</span><span class="sxs-lookup"><span data-stu-id="7627a-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="7627a-119">Kullanılacak bir `ref` parametresi, yöntem tanımı ve arama yöntemi açıkça kullanmalıdır `ref` aşağıdaki örnekte gösterildiği gibi anahtar.</span><span class="sxs-lookup"><span data-stu-id="7627a-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="7627a-120">Geçirilen bağımsız değişken bir `ref` veya `in` parametresi, geçirilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7627a-120">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="7627a-121">Bu farklıdır [çıkışı](out-parameter-modifier.md) parametreleri olan bağımsız değişkenler bunlar geçirilmeden önce açıkça başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7627a-121">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="7627a-122">Sınıf üyeleri yalnızca farklı imzalar olamaz `ref`, `in`, veya `out`.</span><span class="sxs-lookup"><span data-stu-id="7627a-122">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="7627a-123">Bir türün iki üyeleri arasındaki tek fark, biri olduğunda bunları sahip bir derleyici hatası oluşursa bir `ref` parametre ve diğer sahip bir `out`, veya `in` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7627a-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="7627a-124">Aşağıdaki kod, örneğin, derleme değil.</span><span class="sxs-lookup"><span data-stu-id="7627a-124">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
<span data-ttu-id="7627a-125">Bir yöntemi varsa ancak yöntemlerini aşırı yüklenebilir bir `ref`, `in`, veya `out` parametre ve diğer aşağıdaki örnekte gösterildiği gibi bir değer parametresine sahip.</span><span class="sxs-lookup"><span data-stu-id="7627a-125">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="7627a-126">İmza eşleştirme gizleme veya geçersiz kılma, gibi gerektiren diğer durumlarda `in`, `ref`, ve `out` imza parçası olan ve birbirlerine eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="7627a-126">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="7627a-127">Özellikler değişkenleri değildir.</span><span class="sxs-lookup"><span data-stu-id="7627a-127">Properties are not variables.</span></span> <span data-ttu-id="7627a-128">Bunlar yöntemleri ve için geçirilemez `ref` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7627a-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="7627a-129">Diziler geçirmek hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="7627a-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="7627a-130">Kullanamazsınız `ref`, `in`, ve `out` yöntemleri şu tür için anahtar sözcükleri:</span><span class="sxs-lookup"><span data-stu-id="7627a-130">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="7627a-131">Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="7627a-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
- <span data-ttu-id="7627a-132">Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7627a-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="7627a-133">Başvuruya göre bağımsız değişken geçirme: örneği</span><span class="sxs-lookup"><span data-stu-id="7627a-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="7627a-134">Önceki örneklerde değer türleri başvuruya göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="7627a-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="7627a-135">Aynı zamanda `ref` başvuru geçirmek için anahtar sözcüğü türleri başvuruya göre.</span><span class="sxs-lookup"><span data-stu-id="7627a-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="7627a-136">Bir başvuru türü başvuruya göre geçirme başvuru parametresi çağrı yapan başvurduğu nesneyi değiştirmek çağrılan yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="7627a-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="7627a-137">Nesne depolama konumunu yönteme başvurusu parametre değeri olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7627a-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="7627a-138">Depolama konumu (yeni bir nesneye işaret edecek şekilde) parametresinin değeri değiştirirseniz, aynı zamanda çağıran başvurduğu depolama konumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7627a-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="7627a-139">Aşağıdaki örnek başvuru türünde bir örneğini geçirmeden bir `ref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7627a-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="7627a-140">Başvuru türleri değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7627a-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="7627a-141">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="7627a-141">Reference return values</span></span>

<span data-ttu-id="7627a-142">Başvuru dönüş değerleri (veya ref döndürür) çağırana başvuruya göre bir yöntem döndüren değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7627a-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="7627a-143">Diğer bir deyişle, arayan bir yöntemi tarafından döndürülen değer değiştirebilirsiniz ve bu değişikliği yöntemi içeren nesneyi durumda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="7627a-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="7627a-144">Bir başvuru dönüş değeri kullanılarak tanımlanmış `ref` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="7627a-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="7627a-145">Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="7627a-145">In the method signature.</span></span> <span data-ttu-id="7627a-146">Örneğin, aşağıdaki yöntemi imza inidicates, `GetCurrentPrice` yöntemi döndürür bir <xref:System.Decimal> başvuruya değeri.</span><span class="sxs-lookup"><span data-stu-id="7627a-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="7627a-147">Arasında `return` belirteci ve döndürülen değişken bir `return` yöntemi deyiminde.</span><span class="sxs-lookup"><span data-stu-id="7627a-147">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="7627a-148">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7627a-148">For example:</span></span>
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

<span data-ttu-id="7627a-149">Nesnenin durumu değiştirmek çağıran için sırayla başvuru dönüş değeri depolanan, olarak açıkça tanımlanmış bir değişken için bir [ref yerel](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="7627a-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="7627a-150">Bir örnek için bkz: [bir başvuru döndürür ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="7627a-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="7627a-151">Ref Yereller</span><span class="sxs-lookup"><span data-stu-id="7627a-151">Ref locals</span></span>

<span data-ttu-id="7627a-152">Ref yerel değişken değerleri kullanarak döndürülen başvurmak için kullanılan `return ref`.</span><span class="sxs-lookup"><span data-stu-id="7627a-152">A ref local variable is used to refer to values returned using `return ref`.</span></span>  <span data-ttu-id="7627a-153">Ref yerel değişken başlatılmalı ve ref dönüş değerine atanmış.</span><span class="sxs-lookup"><span data-stu-id="7627a-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="7627a-154">Değer yapılan tüm değişiklikler yerel ref, değeri olan yöntemi döndürülen nesnenin durumda başvuruya göre yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="7627a-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="7627a-155">Kullanarak yerel bir ref tanımlayın `ref` değişken bildirimi önce yanı sıra hemen başvuruya göre değeri döndüren yöntemi çağırmadan önce anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7627a-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="7627a-156">Örneğin, aşağıdaki deyim adlı bir yöntemi tarafından döndürülen ref yerel değerin tanımlar `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="7627a-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="7627a-157">Başvuruya göre bir değer aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7627a-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="7627a-158">Bazı durumlarda, bir değer başvuruya göre erişme, performans'potansiyel olarak pahalı kopyalama işlemi kaçınarak artırır.</span><span class="sxs-lookup"><span data-stu-id="7627a-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="7627a-159">Örneğin, aşağıdaki deyim bir değer başvurmak için kullanılan bir ref yerel değerin nasıl tanımlayabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="7627a-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="7627a-160">Her iki örneklerde unutmayın `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır ya da derleyici hatası "değerine sahip bir başvuru tarafından değişken başlatılamıyor." CS8172 oluşturur</span><span class="sxs-lookup"><span data-stu-id="7627a-160">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="7627a-161">Bir başvuru döndürür ve ref Yereller örneği</span><span class="sxs-lookup"><span data-stu-id="7627a-161">A ref returns and ref locals example</span></span>

<span data-ttu-id="7627a-162">Aşağıdaki örnek tanımlayan bir `Book` iki olan sınıfı <xref:System.String> alanları `Title` ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="7627a-162">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="7627a-163">Ayrıca tanımlayan bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7627a-163">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="7627a-164">Tek tek defteri nesneleri çağırarak başvuruya göre döndürülür, `GetBookByTitle` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7627a-164">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="7627a-165">Ne zaman çağıran depolar tarafından döndürülen değer `GetBookByTitle` yöntemi ref yerel olarak çağıran dönüş değerini yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="7627a-165">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="7627a-166">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7627a-166">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7627a-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7627a-167">See also</span></span>  
 [<span data-ttu-id="7627a-168">Değer türleri ile başvuru semantiği</span><span class="sxs-lookup"><span data-stu-id="7627a-168">Reference semantics with value types</span></span>](../../reference-semantics-with-value-types.md)  
 [<span data-ttu-id="7627a-169">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="7627a-169">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="7627a-170">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="7627a-170">Method Parameters</span></span>](method-parameters.md)  
 [<span data-ttu-id="7627a-171">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7627a-171">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="7627a-172">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7627a-172">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="7627a-173">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7627a-173">C# Keywords</span></span>](index.md)
