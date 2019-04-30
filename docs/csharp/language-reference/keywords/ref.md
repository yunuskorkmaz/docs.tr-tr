---
title: ref anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 1faebe2ce1a59798621888e3a518900234720be5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660846"
---
# <a name="ref-c-reference"></a><span data-ttu-id="54ea6-102">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="54ea6-102">ref (C# Reference)</span></span>

<span data-ttu-id="54ea6-103">`ref` Anahtar sözcüğü, başvuru tarafından geçirilmediğine bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="54ea6-104">Bu dört farklı bağlamda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="54ea6-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="54ea6-105">Bir yöntem imzası ve bağımsız değişken başvuru ile bir yönteme geçirmek için bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="54ea6-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="54ea6-106">Daha fazla bilgi için [başvuruya göre bağımsız değişken geçirme](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="54ea6-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="54ea6-107">Başvuruya göre çağırana bir değer döndürmek için bir yöntem imzasında.</span><span class="sxs-lookup"><span data-stu-id="54ea6-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="54ea6-108">Daha fazla bilgi için [başvuru dönüş değerleri](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="54ea6-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="54ea6-109">Bir üye gövdesinde çağıran değiştirme amaçlayan bir başvuru olarak yerel veya genel olarak, bir başvuru dönüş değeri depolanır belirtmek için bir yerel değişkeni başka bir değer başvuruya göre erişir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="54ea6-110">Daha fazla bilgi için [Ref yerel ayarlar](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="54ea6-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="54ea6-111">İçinde bir `struct` bildirmek için bildirimi bir `ref struct` veya `ref readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="54ea6-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="54ea6-112">Daha fazla bilgi için [ref struct türlerini](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="54ea6-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="54ea6-113">Başvuruya göre bağımsız değişken geçirme</span><span class="sxs-lookup"><span data-stu-id="54ea6-113">Passing an argument by reference</span></span>

<span data-ttu-id="54ea6-114">Bir yöntemin parametre listesinde kullanıldığında `ref` anahtar sözcüğü gösterir bir bağımsız değişken başvuruya göre değil değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="54ea6-115">`ref` Anahtar sözcüğü bir değişken olmalıdır bağımsız değişkeni için bir diğer ad biçimsel parametre sağlar.</span><span class="sxs-lookup"><span data-stu-id="54ea6-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="54ea6-116">Diğer bir deyişle, herhangi bir işlem parametresinde bağımsız değişken üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="54ea6-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="54ea6-117">Örneğin, çağıran bir yerel değişken ifade veya bir dizi öğe erişimi ifadesi geçerse ve çağrılan yöntemin hangi ref parametresi başvuruyor, sonra çağıran yerel nesne değiştirir değişkeni ya da dizi öğesini şimdi yeni nesneye başvuran olduğunda yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="54ea6-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="54ea6-118">Başvuru türlerinin kavramıyla başvuruya göre geçirme kavramını karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="54ea6-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="54ea6-119">İki konsepti aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-119">The two concepts are not the same.</span></span> <span data-ttu-id="54ea6-120">Bir yöntem parametresi tarafından değiştirilebilir `ref` bir değer türü veya bir başvuru türü olmasına bakılmaksızın.</span><span class="sxs-lookup"><span data-stu-id="54ea6-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="54ea6-121">Başvuruya göre geçildiğinde bir değer türünün hiçbir kutulama yoktur.</span><span class="sxs-lookup"><span data-stu-id="54ea6-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="54ea6-122">Kullanılacak bir `ref` parametresi, yöntem tanımının hem yöntemi çağrılırken açıkça kullanmalıdır `ref` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="54ea6-123">Geçirilen bir bağımsız değişken bir `ref` veya `in` bunu geçirilmeden önce parametresi'nin başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="54ea6-124">Bu farklıdır [kullanıma](out-parameter-modifier.md) parametreleri, bağımsız değişkenleri geçirilen önce açıkça başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="54ea6-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="54ea6-125">Bir sınıfın üyelerinin, yalnızca farklı imzaları olamaz `ref`, `in`, veya `out`.</span><span class="sxs-lookup"><span data-stu-id="54ea6-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="54ea6-126">İki bir türün üyeleri arasındaki tek fark, birinin ise bunları sahip bir derleyici hatası oluşur. bir `ref` parametresi ve diğer bir `out`, veya `in` parametresi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="54ea6-127">Örneğin, aşağıdaki kod, derleme değil.</span><span class="sxs-lookup"><span data-stu-id="54ea6-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="54ea6-128">Bir yöntem olduğunda ancak yöntemler aşırı yüklenebilir bir `ref`, `in`, veya `out` parametresi ve diğer aşağıdaki örnekte gösterildiği gibi bir değer parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="54ea6-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="54ea6-129">Gizleme veya geçersiz kılma, gibi imza eşleştirme gerektiren diğer durumlarda `in`, `ref`, ve `out` imzasının bir parçası olan ve birbiriyle uyuşmuyor.</span><span class="sxs-lookup"><span data-stu-id="54ea6-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="54ea6-130">Özellikler değişkenleri değildir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-130">Properties are not variables.</span></span> <span data-ttu-id="54ea6-131">Yöntemler ve için geçirilemez `ref` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="54ea6-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="54ea6-132">Kullanamazsınız `ref`, `in`, ve `out` yöntemleri aşağıdaki türde için anahtar sözcükler:</span><span class="sxs-lookup"><span data-stu-id="54ea6-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="54ea6-133">Kullanarak tanımladığınız zaman uyumsuz yöntemlerde [zaman uyumsuz](async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="54ea6-134">Yineleyici yöntemleri dahil bir [yield return](yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="54ea6-135">Başvuruya göre bağımsız değişken geçirme: Bir örnek</span><span class="sxs-lookup"><span data-stu-id="54ea6-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="54ea6-136">Önceki örneklerde, değer türleri başvuruya göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="54ea6-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="54ea6-137">Ayrıca `ref` başvuru geçirilecek anahtar sözcüğü türleri başvuruya göre.</span><span class="sxs-lookup"><span data-stu-id="54ea6-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="54ea6-138">Bir başvuru türü başvuruya göre geçirme başvuru parametresi arayanda başvurduğu nesneyi değiştirmek çağrılan yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="54ea6-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="54ea6-139">Nesne depolama konumu yönteme başvuru parametresi değeri olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="54ea6-140">Depolama konumu (yeni bir nesneye işaret edecek şekilde) parametresinin değeri değiştirirseniz, ayrıca çağıran başvurduğu depolama konumunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="54ea6-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="54ea6-141">Aşağıdaki örnek bir başvuru türünün örneğini geçirir bir `ref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="54ea6-142">Başvuru türleri değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="54ea6-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="54ea6-143">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="54ea6-143">Reference return values</span></span>

<span data-ttu-id="54ea6-144">Başvuru dönüş değerleri (veya ref döndürür) başvuru arayana döner değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="54ea6-145">Diğer bir deyişle, arayan bir yöntemi tarafından döndürülen değer değiştirebilirsiniz ve bu değişiklik yöntemi içeren nesneyi durumda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="54ea6-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="54ea6-146">Başvuru dönüş değeri kullanılarak tanımlanmış `ref` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="54ea6-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="54ea6-147">Yöntem imzasında.</span><span class="sxs-lookup"><span data-stu-id="54ea6-147">In the method signature.</span></span> <span data-ttu-id="54ea6-148">Örneğin, aşağıdaki yöntem imzasını belirten `GetCurrentPrice` yöntemi döndürür bir <xref:System.Decimal> başvuruya göre değeri.</span><span class="sxs-lookup"><span data-stu-id="54ea6-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="54ea6-149">Arasında `return` belirtecini ve döndürülen değişkeni bir `return` deyiminde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="54ea6-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="54ea6-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="54ea6-151">Nesnenin durumunu değiştirmek arayan için sırada başvuru dönüş değeri depolanan, olarak açıkça tanımlanmış bir değişkene bir [ref yerel](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="54ea6-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="54ea6-152">Çağrılan yöntemin dönüş değeri olarak da bildirebilir `ref readonly` başvuruya göre dönüş değeri ve zorunlu çağıran kod döndürülen değeri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="54ea6-152">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="54ea6-153">Döndürülen değer yerel depolayarak değerli kopyalama yöntemi çağrılırken kaçınabilirsiniz [ref salt okunur](#ref-readonly-locals) değişkeni.</span><span class="sxs-lookup"><span data-stu-id="54ea6-153">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="54ea6-154">Bir örnek için bkz. [A ref dönüşler ve ref yerel örnek](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="54ea6-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="54ea6-155">Ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="54ea6-155">Ref locals</span></span>

<span data-ttu-id="54ea6-156">Bir ref yerel değişken başvuru ile döndürülen değerleri için kullanılan `return ref`.</span><span class="sxs-lookup"><span data-stu-id="54ea6-156">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="54ea6-157">Bir ref yerel değişken başvuru olmayan dönüş değeri için başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="54ea6-157">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="54ea6-158">Diğer bir deyişle, sağ taraftaki başlatma bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54ea6-158">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="54ea6-159">Yerel başvurunun değeri herhangi bir değişiklik durumunda, yöntem döndürülen değer nesnesinin başvuruya göre yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="54ea6-159">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="54ea6-160">Bir ref yerel kullanarak tanımladığınız `ref` anahtar sözcüğü Değişken bildiriminde önce yanı sıra hemen önce başvuruya göre değeri döndüren yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="54ea6-160">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="54ea6-161">Örneğin, aşağıdaki deyim adlı bir yöntem tarafından döndürülen bir ref yerel değer tanımlar `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="54ea6-161">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="54ea6-162">Başvuruya göre bir değer aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54ea6-162">You can access a value by reference in the same way.</span></span> <span data-ttu-id="54ea6-163">Bazı durumlarda, bir değere Başvuruya göre erişmeden performansı büyük olasılıkla pahalı kopyalama işlemi tarafından artırır.</span><span class="sxs-lookup"><span data-stu-id="54ea6-163">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="54ea6-164">Örneğin, aşağıdaki ifade bir değer başvurmak için kullanılan bir ref yerel değer nasıl tanımlayabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-164">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="54ea6-165">Her iki örneklerde unutmayın `ref` anahtar sözcüğü her iki yerde de kullanılması gerekir ya da derleyici hata CS8172, "bir başvuruya göre değişken bir değer ile başlatılamaz." oluşturur</span><span class="sxs-lookup"><span data-stu-id="54ea6-165">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="54ea6-166">İle başlayarak C# 7.3, yineleme değişkeninin `foreach` ref yerel öğesi veya ref salt okunur yerel değişkenin bildirimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-166">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="54ea6-167">Daha fazla bilgi için [foreach deyimi](foreach-in.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-167">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="54ea6-168">ref salt okunur yerel öğeler</span><span class="sxs-lookup"><span data-stu-id="54ea6-168">Ref readonly locals</span></span>

<span data-ttu-id="54ea6-169">Yerel başvuru salt okunur olan özelliği ve yöntemi tarafından döndürülen değerler başvurmak için kullanılan `ref readonly` kullanır ve imza `return ref`.</span><span class="sxs-lookup"><span data-stu-id="54ea6-169">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="54ea6-170">A `ref readonly` değişkeni özelliklerini birleştiren bir `ref` yerel bir değişken bir `readonly` değişkeni: bir diğer addır depolama alanına atanır ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="54ea6-170">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="54ea6-171">Bir ref dönüşler ve ref yerel örneği</span><span class="sxs-lookup"><span data-stu-id="54ea6-171">A ref returns and ref locals example</span></span>

<span data-ttu-id="54ea6-172">Aşağıdaki örnekte tanımlayan bir `Book` iki sınıf <xref:System.String> alanları `Title` ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="54ea6-172">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="54ea6-173">Ayrıca tanımlar bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="54ea6-173">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="54ea6-174">Tek tek kitap nesneleri çağırarak başvuru ile döndürülür kendi `GetBookByTitle` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54ea6-174">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="54ea6-175">Çağıran tarafından döndürülen değeri, zaman depolar `GetBookByTitle` yöntemi bir ref yerel olarak çağırana döndürülen değeri yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="54ea6-175">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="54ea6-176">Ref struct türleri</span><span class="sxs-lookup"><span data-stu-id="54ea6-176">Ref struct types</span></span>

<span data-ttu-id="54ea6-177">Ekleme `ref` değiştiriciyi bir `struct` bildirimi tanımlar, türün örneklerinin yığını ayrılan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54ea6-177">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="54ea6-178">Diğer bir deyişle, bu tür örnekleri hiçbir zaman yığın üzerinde başka bir sınıf üyesi olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="54ea6-178">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="54ea6-179">Bu özellik için birincil motivasyon olan <xref:System.Span%601> ve ilişkili yapıları.</span><span class="sxs-lookup"><span data-stu-id="54ea6-179">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="54ea6-180">Amacı tutarken, bir `ref struct` yazın, tüm derleyici zorlayan çeşitli kurallar bir yığın ayırma değişken tanıtan `ref struct` türleri.</span><span class="sxs-lookup"><span data-stu-id="54ea6-180">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="54ea6-181">Kutusunda edilemez bir `ref struct`.</span><span class="sxs-lookup"><span data-stu-id="54ea6-181">You can't box a `ref struct`.</span></span> <span data-ttu-id="54ea6-182">Atama yapılamaz bir `ref struct` türünde bir değişkene `object`, `dynamic`, veya herhangi bir arabirim türü.</span><span class="sxs-lookup"><span data-stu-id="54ea6-182">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="54ea6-183">`ref struct` türleri, arabirimleri uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="54ea6-183">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="54ea6-184">Bildirip bir `ref struct` bir sınıf veya normal yapı üyesi olarak.</span><span class="sxs-lookup"><span data-stu-id="54ea6-184">You can't declare a `ref struct` as a member of a class or a normal struct.</span></span>
- <span data-ttu-id="54ea6-185">Yerel değişkenler bildiremezsiniz `ref struct` zaman uyumsuz yöntemlerde türleri.</span><span class="sxs-lookup"><span data-stu-id="54ea6-185">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="54ea6-186">Döndüren zaman uyumlu yöntemleri bildirebilirsiniz <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> veya `Task`-türleri ister.</span><span class="sxs-lookup"><span data-stu-id="54ea6-186">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="54ea6-187">Bildirip `ref struct` yineleyiciler yerel değişkenler.</span><span class="sxs-lookup"><span data-stu-id="54ea6-187">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="54ea6-188">Yakalama gerçekleştiremez `ref struct` değişkenleri lambda ifadeleri veya yerel işlevler.</span><span class="sxs-lookup"><span data-stu-id="54ea6-188">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="54ea6-189">Bu kısıtlamalar yanlışlıkla kullanmayın emin olun. bir `ref struct` bir şekilde yönetilen yığınla Yükselt.</span><span class="sxs-lookup"><span data-stu-id="54ea6-189">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="54ea6-190">Bir yapı olarak bildirmek için değiştiriciler birleştirebilirsiniz `readonly ref`.</span><span class="sxs-lookup"><span data-stu-id="54ea6-190">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="54ea6-191">A `readonly ref struct` avantajları ve kısıtlamaları birleştirir `ref struct` ve `readonly struct` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="54ea6-191">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="54ea6-192">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="54ea6-192">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54ea6-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54ea6-193">See also</span></span>

- [<span data-ttu-id="54ea6-194">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="54ea6-194">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="54ea6-195">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="54ea6-195">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="54ea6-196">Ref koşullu ifadesi</span><span class="sxs-lookup"><span data-stu-id="54ea6-196">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="54ea6-197">başvuru atama işleci</span><span class="sxs-lookup"><span data-stu-id="54ea6-197">ref assignment operator</span></span>](../operators/assignment-operator.md#ref-assignment-operator)
- [<span data-ttu-id="54ea6-198">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="54ea6-198">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="54ea6-199">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="54ea6-199">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="54ea6-200">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="54ea6-200">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="54ea6-201">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="54ea6-201">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="54ea6-202">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="54ea6-202">C# Keywords</span></span>](index.md)
