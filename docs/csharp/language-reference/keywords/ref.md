---
description: ref anahtar sözcüğü-C# başvurusu
title: ref anahtar sözcüğü-C# başvurusu
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 58a4ce30e11ca023b50e5e53b1f1554a30d44390
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137090"
---
# <a name="ref-c-reference"></a><span data-ttu-id="9e05c-103">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9e05c-103">ref (C# Reference)</span></span>

<span data-ttu-id="9e05c-104">`ref`Anahtar sözcüğü, başvuruya göre geçirilen bir değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-104">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="9e05c-105">Dört farklı bağlamda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="9e05c-105">It is used in four different contexts:</span></span>

- <span data-ttu-id="9e05c-106">Bir yöntem imzasında ve bir yöntem çağrısında, bir bağımsız değişkeni başvuruya göre bir yönteme geçirmek için.</span><span class="sxs-lookup"><span data-stu-id="9e05c-106">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="9e05c-107">Daha fazla bilgi için bkz. [bir bağımsız değişkeni başvuruya göre geçirme](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="9e05c-107">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="9e05c-108">Bir yöntem imzasında, çağıran öğesine başvuruya göre bir değer döndürün.</span><span class="sxs-lookup"><span data-stu-id="9e05c-108">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="9e05c-109">Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="9e05c-109">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="9e05c-110">Bir üye gövdesinde, bir başvuru dönüş değerinin, çağıranın değiştirme amaçladığı bir başvuru olarak yerel olarak depolandığını belirtmek için, yerel bir değişken başvuruya göre başka bir değere erişir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-110">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="9e05c-111">Daha fazla bilgi için bkz. [ref Yereller](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="9e05c-111">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="9e05c-112">Bir veya ' i `struct` bildirmek için bir bildirimde `ref struct` `readonly ref struct` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-112">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="9e05c-113">Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `ref` struct](../builtin-types/struct.md#ref-struct) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9e05c-113">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="9e05c-114">Bir bağımsız değişkeni başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="9e05c-114">Passing an argument by reference</span></span>

<span data-ttu-id="9e05c-115">Bir yöntemin parametre listesinde kullanıldığında, `ref` anahtar sözcüğü bir bağımsız değişkenin değere göre değil başvuruya göre geçtiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-115">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="9e05c-116">`ref`Anahtar sözcüğü, bir değişken olması gereken bağımsız değişken için biçimsel parametreye bir diğer ad getirir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-116">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="9e05c-117">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-117">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="9e05c-118">Örneğin, çağıran bir yerel değişken ifadesi veya bir dizi öğesi erişim ifadesi geçirirse ve çağrılan yöntem Ref parametresinin başvurduğu nesnenin yerini alıyorsa, çağıran yerel değişkeni veya Array öğesi artık yöntem döndürüldüğünde yeni nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="9e05c-118">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="9e05c-119">Başvuru türü kavramıyla başvuruya göre geçirme kavramını karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="9e05c-119">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="9e05c-120">İki kavram aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-120">The two concepts are not the same.</span></span> <span data-ttu-id="9e05c-121">Bir yöntem parametresi `ref` , bir değer türü veya bir başvuru türü olmasına bakılmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-121">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="9e05c-122">Başvuru ile geçirildiğinde bir değer türünün kutulenmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9e05c-122">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="9e05c-123">Bir parametre kullanmak için `ref` , `ref` Aşağıdaki örnekte gösterildiği gibi yöntem tanımı ve çağırma yöntemi anahtar sözcüğünü açıkça kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-123">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="9e05c-124">Bir veya parametresine geçirilen bir bağımsız değişken `ref` `in` geçirilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-124">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="9e05c-125">Bu, bağımsız değişkenlerin geçirilmeden önce açıkça başlatılmış olması gereken [Out](out-parameter-modifier.md) parametrelerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-125">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="9e05c-126">Bir sınıfın üyelerinin yalnızca `ref` ,, veya ile farklı imzaları olamaz `in` `out` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-126">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="9e05c-127">Bir türün iki üyesi arasındaki tek fark, bir `ref` parametre içeriyorsa ve diğeri `out` veya parametresi varsa bir derleyici hatası oluşur `in` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-127">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="9e05c-128">Aşağıdaki kod, örneğin derlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9e05c-128">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="9e05c-129">Ancak, bir yöntem bir `ref` , `in` veya `out` parametresi olduğunda ve diğeri bir değer parametresine sahip olduğunda, aşağıdaki örnekte gösterildiği gibi yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-129">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="9e05c-130">İmza eşleştirmesi gerektiren diğer durumlarda,,, ve,, ve ' ı gizleme veya geçersiz kılma,,, `in` `ref` ve birbirini `out` eşleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="9e05c-130">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="9e05c-131">Özellikler değişken değildir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-131">Properties are not variables.</span></span> <span data-ttu-id="9e05c-132">Bunlar yöntemlerdir ve `ref` parametrelere geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="9e05c-132">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="9e05c-133">`ref` `in` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="9e05c-133">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="9e05c-134">Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="9e05c-134">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="9e05c-135">Bir [yield return](yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-135">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="9e05c-136">Ayrıca, [genişletme yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md) aşağıdaki kısıtlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9e05c-136">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="9e05c-137">`out`Anahtar sözcüğü, bir genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-137">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="9e05c-138">`ref`Anahtar sözcüğü, bağımsız değişken bir struct olmadığında ya da genel bir tür struct olarak kısıtlanmamışsa Genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-138">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="9e05c-139">`in`İlk bağımsız değişken bir struct olmadığı müddetçe anahtar sözcüğü kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-139">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="9e05c-140">`in`Anahtar sözcüğü, bir struct gibi sınırlandırsalar bile herhangi bir genel tür üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-140">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="9e05c-141">Bir bağımsız değişkeni başvuruya göre geçirme: bir örnek</span><span class="sxs-lookup"><span data-stu-id="9e05c-141">Passing an argument by reference: An example</span></span>

<span data-ttu-id="9e05c-142">Önceki örneklerde değer türleri başvuruya göre geçer.</span><span class="sxs-lookup"><span data-stu-id="9e05c-142">The previous examples pass value types by reference.</span></span> <span data-ttu-id="9e05c-143">Başvuru `ref` türlerini başvuruya göre geçirmek için anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-143">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="9e05c-144">Başvuru türü başvuruya göre geçirilme yöntemi, çağrılan yöntemin, başvuru parametresinin çağırıcının başvurduğu nesneyi değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e05c-144">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="9e05c-145">Nesnenin depolama konumu, başvuru parametresi değeri olarak yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-145">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="9e05c-146">Parametresinin depolama konumundaki değeri değiştirirseniz (yeni bir nesneyi işaret etmek için), çağıranın başvurduğu depolama konumunu da değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-146">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="9e05c-147">Aşağıdaki örnek, bir başvuru türünün örneğini bir parametre olarak geçirir `ref` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-147">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="9e05c-148">Başvuru türlerini değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz. [başvuru türü parametrelerini geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9e05c-148">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="9e05c-149">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="9e05c-149">Reference return values</span></span>

<span data-ttu-id="9e05c-150">Başvuru dönüş değerleri (veya ref dönüşler), bir yöntemin çağırana başvuruya göre döndürdüğü değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-150">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="9e05c-151">Diğer bir deyişle, çağıran bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik çağırma yöntemindeki nesnenin durumunda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-151">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="9e05c-152">Bir başvuru dönüş değeri `ref` anahtar sözcüğü kullanılarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="9e05c-152">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="9e05c-153">Metot imzasında.</span><span class="sxs-lookup"><span data-stu-id="9e05c-153">In the method signature.</span></span> <span data-ttu-id="9e05c-154">Örneğin, aşağıdaki yöntem imzası, `GetCurrentPrice` yöntemin başvuruya göre bir değer döndürdüğünü gösterir <xref:System.Decimal> .</span><span class="sxs-lookup"><span data-stu-id="9e05c-154">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="9e05c-155">`return`Belirteç ve `return` yöntemin içindeki bir ifadede döndürülen değişken.</span><span class="sxs-lookup"><span data-stu-id="9e05c-155">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="9e05c-156">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9e05c-156">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="9e05c-157">Çağıranın nesnenin durumunu değiştirmesi için, başvuru dönüş değeri açıkça bir [ref yerel](#ref-locals)olarak tanımlanmış bir değişkene depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-157">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="9e05c-158">Burada hem yöntem imzasını hem de Yöntem gövdesini gösteren daha kapsamlı bir başvuru dönüş örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-158">Here is a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="9e05c-159">Çağrılan yöntem, `ref readonly` değeri başvuruya göre döndürmek için dönüş değerini de bildirebilir ve çağıran kodun döndürülen değeri değiştiremeyeceğini zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-159">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="9e05c-160">Çağırma yöntemi, değeri yerel bir [ref salt okunur](#ref-readonly-locals) değişkeninde depolayarak döndürülen değerli değeri kopyalamayı önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-160">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="9e05c-161">Bir örnek için, bkz. [bir başvuru dönüşleri ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="9e05c-161">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="9e05c-162">Başvuru yerelleri</span><span class="sxs-lookup"><span data-stu-id="9e05c-162">Ref locals</span></span>

<span data-ttu-id="9e05c-163">Kullanılarak döndürülen değerlere başvurmak için bir başvuru yerel değişkeni kullanılır `return ref` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-163">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="9e05c-164">Bir ref yerel değişkeni, ref olmayan bir dönüş değeri olarak başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-164">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="9e05c-165">Diğer bir deyişle, başlatmanın sağ tarafı bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-165">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="9e05c-166">Ref Local değerindeki tüm değişiklikler, metodu, yöntemi başvuruya göre döndürülen nesnenin durumuna yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-166">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="9e05c-167">`ref`Değişken bildiriminden önce anahtar sözcüğünü kullanarak bir ref yerel tanımlayın ve değeri başvuruya göre döndüren yönteme çağrıdan hemen önce.</span><span class="sxs-lookup"><span data-stu-id="9e05c-167">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="9e05c-168">Örneğin, aşağıdaki ifade adlı bir yöntem tarafından döndürülen bir başvuru yerel değeri tanımlar `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="9e05c-168">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="9e05c-169">Başvuruya göre bir değere aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-169">You can access a value by reference in the same way.</span></span> <span data-ttu-id="9e05c-170">Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-170">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="9e05c-171">Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir başvuru yerel değerini nasıl tanımlayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-171">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="9e05c-172">Her iki örnekte, `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır veya derleyici hata CS8172 oluşturuyor, "bir değere sahip bir başvuru değişkeni başlatılamaz."</span><span class="sxs-lookup"><span data-stu-id="9e05c-172">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="9e05c-173">C# 7,3 ' den başlayarak, deyimin yineleme değişkeni `foreach` ref yerel veya ref ReadOnly yerel değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e05c-173">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="9e05c-174">Daha fazla bilgi için [foreach ifadesi](foreach-in.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="9e05c-174">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="9e05c-175">Ayrıca C# 7,3 ' den itibaren, ref [atama işleciyle](../operators/assignment-operator.md#ref-assignment-operator)bir ref yerel veya ref ReadOnly yerel değişkenini yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-175">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="9e05c-176">Ref ReadOnly Yereller</span><span class="sxs-lookup"><span data-stu-id="9e05c-176">Ref readonly locals</span></span>

<span data-ttu-id="9e05c-177">Ref salt okunur yerel değeri, imzası ve kullanımları olan yöntem veya özellik tarafından döndürülen değerleri ifade etmek için kullanılır `ref readonly` `return ref` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-177">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="9e05c-178">`ref readonly`Değişken, yerel bir `ref` değişkenin özelliklerini bir değişkenle birleştirir `readonly` : Bu, atandığı depolamanın diğer adıdır ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="9e05c-178">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="9e05c-179">Bir ref, ve ref Yereller örneği döndürür</span><span class="sxs-lookup"><span data-stu-id="9e05c-179">A ref returns and ref locals example</span></span>

<span data-ttu-id="9e05c-180">Aşağıdaki örnek `Book` , ve iki alanı olan bir sınıfı tanımlar <xref:System.String> `Title` `Author` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-180">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="9e05c-181">Ayrıca `BookCollection` , özel nesne dizisi içeren bir sınıfı tanımlar `Book` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-181">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="9e05c-182">Bağımsız kitap nesneleri, yöntemi çağırarak başvuruya göre döndürülür `GetBookByTitle` .</span><span class="sxs-lookup"><span data-stu-id="9e05c-182">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="9e05c-183">Çağıran, yöntem tarafından döndürülen değeri `GetBookByTitle` bir ref yerel olarak depoladığında, çağıranın dönüş değeri için yaptığı değişiklikler, `BookCollection` Aşağıdaki örnekte gösterildiği gibi nesnesine yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="9e05c-183">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="9e05c-184">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9e05c-184">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e05c-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e05c-185">See also</span></span>

- [<span data-ttu-id="9e05c-186">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="9e05c-186">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="9e05c-187">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="9e05c-187">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="9e05c-188">Koşullu başvuru ifadesi</span><span class="sxs-lookup"><span data-stu-id="9e05c-188">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="9e05c-189">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="9e05c-189">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="9e05c-190">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="9e05c-190">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="9e05c-191">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e05c-191">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9e05c-192">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9e05c-192">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9e05c-193">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9e05c-193">C# Keywords</span></span>](index.md)
