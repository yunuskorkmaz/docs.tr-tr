---
title: ref anahtar sözcüğü (C# Başvurusu)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 689b61bb79718f4185e22a53bc669e7d67765ba0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746895"
---
# <a name="ref-c-reference"></a><span data-ttu-id="93017-102">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="93017-102">ref (C# Reference)</span></span>

<span data-ttu-id="93017-103">`ref` Anahtar sözcüğü, başvuru tarafından geçirilmediğine bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="93017-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="93017-104">Bu dört farklı bağlamda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="93017-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="93017-105">Bir yöntem imzası ve bağımsız değişken başvuru ile bir yönteme geçirmek için bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="93017-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="93017-106">Bkz: [başvuruya göre bağımsız değişken geçirme](#passing-an-argument-by-reference) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="93017-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>
- <span data-ttu-id="93017-107">Başvuruya göre çağırana bir değer döndürmek için bir yöntem imzasında.</span><span class="sxs-lookup"><span data-stu-id="93017-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="93017-108">Bkz: [başvuru dönüş değerleri](#reference-return-values) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="93017-108">See [Reference return values](#reference-return-values) for more information.</span></span>
- <span data-ttu-id="93017-109">Bir üye gövdesinde çağıran değiştirme amaçlayan bir başvuru olarak yerel veya genel olarak, bir başvuru dönüş değeri depolanır belirtmek için bir yerel değişkeni başka bir değer başvuruya göre erişir.</span><span class="sxs-lookup"><span data-stu-id="93017-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="93017-110">Bkz: [Ref yerel ayarlar](#ref-locals) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="93017-110">See [Ref locals](#ref-locals) for more information.</span></span>
- <span data-ttu-id="93017-111">İçinde bir `struct` bildirmek için bildirimi bir `ref struct` veya `ref readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="93017-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="93017-112">Daha fazla bilgi için [başvuru semantiği ile değer türleri](../../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="93017-112">For more information, see [Reference semantics with value types](../../reference-semantics-with-value-types.md).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="93017-113">Başvuruya göre bağımsız değişken geçirme</span><span class="sxs-lookup"><span data-stu-id="93017-113">Passing an argument by reference</span></span>

<span data-ttu-id="93017-114">Bir yöntemin parametre listesinde kullanıldığında `ref` anahtar sözcüğü gösterir bir bağımsız değişken başvuruya göre değil değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="93017-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="93017-115">Başvuruya göre geçirme çağrılan yöntem değişkeninde herhangi bir değişiklik çağıran yöntemin yansıtılır etkisidir.</span><span class="sxs-lookup"><span data-stu-id="93017-115">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="93017-116">Örneğin, çağıran bir yerel değişken ifade veya bir dizi öğe erişimi ifadesi geçerse ve çağrılan yöntemin hangi ref parametresi başvuruyor, sonra çağıran yerel nesne değiştirir değişkeni ya da dizi öğesini şimdi yeni nesneye başvuran olduğunda yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="93017-116">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="93017-117">Başvuru türlerinin kavramıyla başvuruya göre geçirme kavramını karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="93017-117">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="93017-118">İki konsepti aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="93017-118">The two concepts are not the same.</span></span> <span data-ttu-id="93017-119">Bir yöntem parametresi tarafından değiştirilebilir `ref` bir değer türü veya bir başvuru türü olmasına bakılmaksızın.</span><span class="sxs-lookup"><span data-stu-id="93017-119">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="93017-120">Başvuruya göre geçildiğinde bir değer türünün hiçbir kutulama yoktur.</span><span class="sxs-lookup"><span data-stu-id="93017-120">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="93017-121">Kullanılacak bir `ref` parametresi, yöntem tanımının hem yöntemi çağrılırken açıkça kullanmalıdır `ref` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="93017-121">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="93017-122">Geçirilen bir bağımsız değişken bir `ref` veya `in` bunu geçirilmeden önce parametresi'nin başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="93017-122">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="93017-123">Bu farklıdır [kullanıma](out-parameter-modifier.md) parametreleri, bağımsız değişkenleri geçirilen önce açıkça başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="93017-123">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="93017-124">Bir sınıfın üyelerinin, yalnızca farklı imzaları olamaz `ref`, `in`, veya `out`.</span><span class="sxs-lookup"><span data-stu-id="93017-124">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="93017-125">İki bir türün üyeleri arasındaki tek fark, birinin ise bunları sahip bir derleyici hatası oluşur. bir `ref` parametresi ve diğer bir `out`, veya `in` parametresi.</span><span class="sxs-lookup"><span data-stu-id="93017-125">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="93017-126">Örneğin, aşağıdaki kod, derleme değil.</span><span class="sxs-lookup"><span data-stu-id="93017-126">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="93017-127">Bir yöntem olduğunda ancak yöntemler aşırı yüklenebilir bir `ref`, `in`, veya `out` parametresi ve diğer aşağıdaki örnekte gösterildiği gibi bir değer parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="93017-127">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="93017-128">Gizleme veya geçersiz kılma, gibi imza eşleştirme gerektiren diğer durumlarda `in`, `ref`, ve `out` imzasının bir parçası olan ve birbiriyle uyuşmuyor.</span><span class="sxs-lookup"><span data-stu-id="93017-128">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="93017-129">Özellikler değişkenleri değildir.</span><span class="sxs-lookup"><span data-stu-id="93017-129">Properties are not variables.</span></span> <span data-ttu-id="93017-130">Yöntemler ve için geçirilemez `ref` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="93017-130">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="93017-131">Ona nasıl iletileceğini dizileri hakkında daha fazla bilgi için bkz [kullanarak dizileri geçirme ref ve out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="93017-131">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="93017-132">Kullanamazsınız `ref`, `in`, ve `out` yöntemleri aşağıdaki türde için anahtar sözcükler:</span><span class="sxs-lookup"><span data-stu-id="93017-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="93017-133">Kullanarak tanımladığınız zaman uyumsuz yöntemlerde [zaman uyumsuz](async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="93017-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="93017-134">Yineleyici yöntemleri dahil bir [yield return](yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="93017-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="93017-135">Başvuruya göre bağımsız değişken geçirme: örneği</span><span class="sxs-lookup"><span data-stu-id="93017-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="93017-136">Önceki örneklerde, değer türleri başvuruya göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="93017-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="93017-137">Ayrıca `ref` başvuru geçirilecek anahtar sözcüğü türleri başvuruya göre.</span><span class="sxs-lookup"><span data-stu-id="93017-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="93017-138">Bir başvuru türü başvuruya göre geçirme başvuru parametresi arayanda başvurduğu nesneyi değiştirmek çağrılan yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="93017-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="93017-139">Nesne depolama konumu yönteme başvuru parametresi değeri olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="93017-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="93017-140">Depolama konumu (yeni bir nesneye işaret edecek şekilde) parametresinin değeri değiştirirseniz, ayrıca çağıran başvurduğu depolama konumunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="93017-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="93017-141">Aşağıdaki örnek bir başvuru türünün örneğini geçirir bir `ref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="93017-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="93017-142">Başvuru türleri değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="93017-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="93017-143">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="93017-143">Reference return values</span></span>

<span data-ttu-id="93017-144">Başvuru dönüş değerleri (veya ref döndürür) başvuru arayana döner değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="93017-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="93017-145">Diğer bir deyişle, arayan bir yöntemi tarafından döndürülen değer değiştirebilirsiniz ve bu değişiklik yöntemi içeren nesneyi durumda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="93017-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="93017-146">Başvuru dönüş değeri kullanılarak tanımlanmış `ref` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="93017-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="93017-147">Yöntem imzasında.</span><span class="sxs-lookup"><span data-stu-id="93017-147">In the method signature.</span></span> <span data-ttu-id="93017-148">Örneğin, aşağıdaki yöntem imzasını belirten `GetCurrentPrice` yöntemi döndürür bir <xref:System.Decimal> başvuruya göre değeri.</span><span class="sxs-lookup"><span data-stu-id="93017-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="93017-149">Arasında `return` belirtecini ve döndürülen değişkeni bir `return` deyiminde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93017-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="93017-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="93017-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="93017-151">Nesnenin durumunu değiştirmek arayan için sırada başvuru dönüş değeri depolanan, olarak açıkça tanımlanmış bir değişkene bir [ref yerel](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="93017-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="93017-152">Bir örnek için bkz [A ref dönüşler ve ref yerel örneği](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="93017-152">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="93017-153">Ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="93017-153">Ref locals</span></span>

<span data-ttu-id="93017-154">Bir ref yerel değişken başvuru ile döndürülen değerleri için kullanılan `return ref`.</span><span class="sxs-lookup"><span data-stu-id="93017-154">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="93017-155">Bir ref yerel değişken başvuru olmayan dönüş değeri için başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="93017-155">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="93017-156">Diğer bir deyişle, sağ taraftaki başlatma bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="93017-156">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="93017-157">Yerel başvurunun değeri herhangi bir değişiklik durumunda, yöntem döndürülen değer nesnesinin başvuruya göre yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="93017-157">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="93017-158">Bir ref yerel kullanarak tanımladığınız `ref` anahtar sözcüğü Değişken bildiriminde önce yanı sıra hemen önce başvuruya göre değeri döndüren yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="93017-158">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="93017-159">Örneğin, aşağıdaki deyim adlı bir yöntem tarafından döndürülen bir ref yerel değer tanımlar `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="93017-159">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="93017-160">Başvuruya göre bir değer aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93017-160">You can access a value by reference in the same way.</span></span> <span data-ttu-id="93017-161">Bazı durumlarda, bir değere Başvuruya göre erişmeden performansı büyük olasılıkla pahalı kopyalama işlemi tarafından artırır.</span><span class="sxs-lookup"><span data-stu-id="93017-161">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="93017-162">Örneğin, aşağıdaki ifade bir değer başvurmak için kullanılan bir ref yerel değer nasıl tanımlayabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="93017-162">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="93017-163">Her iki örneklerde unutmayın `ref` anahtar sözcüğü her iki yerde de kullanılması gerekir ya da derleyici hata CS8172, "bir başvuruya göre değişken bir değer ile başlatılamaz." oluşturur</span><span class="sxs-lookup"><span data-stu-id="93017-163">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="93017-164">Bir ref dönüşler ve ref yerel örneği</span><span class="sxs-lookup"><span data-stu-id="93017-164">A ref returns and ref locals example</span></span>

<span data-ttu-id="93017-165">Aşağıdaki örnekte tanımlayan bir `Book` iki sınıf <xref:System.String> alanları `Title` ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="93017-165">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="93017-166">Ayrıca tanımlar bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="93017-166">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="93017-167">Tek tek kitap nesneleri çağırarak başvuru ile döndürülür kendi `GetBookByTitle` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93017-167">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="93017-168">Çağıran tarafından döndürülen değeri, zaman depolar `GetBookByTitle` yöntemi bir ref yerel olarak çağırana döndürülen değeri yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="93017-168">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="93017-169">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="93017-169">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="93017-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93017-170">See also</span></span>

- [<span data-ttu-id="93017-171">Değer türleri ile başvuru semantiği</span><span class="sxs-lookup"><span data-stu-id="93017-171">Reference semantics with value types</span></span>](../../reference-semantics-with-value-types.md)  
- [<span data-ttu-id="93017-172">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="93017-172">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)  
- [<span data-ttu-id="93017-173">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="93017-173">Method Parameters</span></span>](method-parameters.md)  
- [<span data-ttu-id="93017-174">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="93017-174">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="93017-175">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="93017-175">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="93017-176">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="93017-176">C# Keywords</span></span>](index.md)