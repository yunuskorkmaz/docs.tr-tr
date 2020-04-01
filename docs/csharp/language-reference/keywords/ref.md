---
title: ref anahtar kelime - C# Referans
ms.date: 03/19/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 8d04f888befae2cad815c88a0d27bd836f458c63
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523785"
---
# <a name="ref-c-reference"></a><span data-ttu-id="06921-102">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="06921-102">ref (C# Reference)</span></span>

<span data-ttu-id="06921-103">Anahtar `ref` kelime, başvuru yla geçirilen bir değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="06921-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="06921-104">Dört farklı bağlamda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="06921-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="06921-105">Bir yöntem imza ve bir yöntem arama, başvuru ile bir yönteme bir argüman geçmek için.</span><span class="sxs-lookup"><span data-stu-id="06921-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="06921-106">Daha fazla bilgi için [bkz.](#passing-an-argument-by-reference)</span><span class="sxs-lookup"><span data-stu-id="06921-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="06921-107">Bir yöntem imzasında, başvuru ile arayana bir değer döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="06921-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="06921-108">Daha fazla bilgi için [Bkz. Başvuru iade değerleri.](#reference-return-values)</span><span class="sxs-lookup"><span data-stu-id="06921-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="06921-109">Bir üye gövdesinde, bir referans dönüş değerinin, arayanın değiştirmek istediği bir başvuru olarak yerel olarak depolandığını veya genel olarak yerel bir değişkenin başvuru yla başka bir değere eriştiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="06921-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="06921-110">Daha fazla bilgi için Ref [yerel bilgilerine](#ref-locals)bakın.</span><span class="sxs-lookup"><span data-stu-id="06921-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="06921-111">Bir `struct` veya bir `ref struct` `readonly ref struct`beyanda .</span><span class="sxs-lookup"><span data-stu-id="06921-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="06921-112">Daha fazla bilgi için [ref struct türlerine](#ref-struct-types)bakın.</span><span class="sxs-lookup"><span data-stu-id="06921-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="06921-113">Bir bağımsız değişkeni başvuruyla geçirme</span><span class="sxs-lookup"><span data-stu-id="06921-113">Passing an argument by reference</span></span>

<span data-ttu-id="06921-114">Bir yöntemin `ref` parametre listesinde kullanıldığında, anahtar kelime bir bağımsız değişkenin değere göre değil, başvuru yla geçirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06921-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="06921-115">Anahtar `ref` kelime, resmi parametreyi bağımsız değişken için bir diğer ad yapar ve bu da değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06921-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="06921-116">Başka bir deyişle, parametre üzerinde herhangi bir işlem bağımsız değişken üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="06921-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="06921-117">Örneğin, arayan yerel bir değişken ifadesini veya dizi öğesi erişim ifadesini geçerse ve çağrılan yöntem ref parametrenin başvurulduğu nesnenin yerini alırsa, arayanın yerel değişkeni veya dizi öğesi yöntem döndüğünde şimdi yeni nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="06921-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="06921-118">Referans la geçme kavramını başvuru türleri kavramıyla karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="06921-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="06921-119">İki kavram aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="06921-119">The two concepts are not the same.</span></span> <span data-ttu-id="06921-120">Yöntem parametresi, değer `ref` türü veya başvuru türü olup olmadığına bakılmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="06921-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="06921-121">Başvuru yla geçirildiğinde değer türünün kutulamayoktur.</span><span class="sxs-lookup"><span data-stu-id="06921-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="06921-122">Bir `ref` parametre kullanmak için, hem yöntem tanımı hem de `ref` arama yöntemi, aşağıdaki örnekte gösterildiği gibi anahtar kelimeyi açıkça kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06921-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="06921-123">Bir `ref` veya `in` parametreye geçirilen bir bağımsız değişken geçirilmeden önce başharfe atılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06921-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="06921-124">Bu, bağımsız değişkenleri geçirilmeden önce açıkça başlatılması gerekmeyen [dış](out-parameter-modifier.md) parametrelerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="06921-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="06921-125">Bir sınıfın üyeleri yalnızca `ref`, `in`veya `out`.</span><span class="sxs-lookup"><span data-stu-id="06921-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="06921-126">Bir türiki üye arasındaki tek fark, birinin `ref` parametresi, diğerinin ise bir `out`parametresi `in` veya parametresi olması ysa derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="06921-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="06921-127">Örneğin, aşağıdaki kod derlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="06921-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="06921-128">Ancak, yöntemlerden biri `ref`, , `in`parametresi `out` ve diğer bir değer parametresi varsa, aşağıdaki örnekte gösterildiği gibi aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="06921-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="06921-129">Gizleme veya geçersiz kılma `in` `ref`gibi imza eşleştirmegerektiren ve imzanın bir parçası olan ve `out` birbiriyle eşleşmeyen diğer durumlarda.</span><span class="sxs-lookup"><span data-stu-id="06921-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="06921-130">Özellikler değişken değildir.</span><span class="sxs-lookup"><span data-stu-id="06921-130">Properties are not variables.</span></span> <span data-ttu-id="06921-131">Bunlar yöntemdir ve parametrelere `ref` geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="06921-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="06921-132">Aşağıdaki yöntem türleri `ref`için `in`, `out` ve anahtar kelimeleri kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="06921-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="06921-133">Async değiştirici kullanarak tanımladığınız [async](async.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="06921-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="06921-134">[Verim getirisi](yield.md) veya `yield break` deyimi içeren yineleyici yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="06921-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="06921-135">Buna ek olarak, [uzantı yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md) aşağıdaki kısıtlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="06921-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="06921-136">Anahtar `out` kelime, bir uzantı yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="06921-136">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="06921-137">Anahtar `ref` kelime, bağımsız değişken bir yapı olmadığında veya yapı olarak sınırlandırılmamış genel bir tür olduğunda, uzantı yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="06921-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="06921-138">İlk `in` bağımsız değişken bir yapı olmadığı sürece anahtar sözcük kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="06921-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="06921-139">Anahtar `in` kelime, yapı olarak sınırlandırılsa bile, herhangi bir genel türde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="06921-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="06921-140">Bir bağımsız değişkeni başvuruyla geçirme: Bir örnek</span><span class="sxs-lookup"><span data-stu-id="06921-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="06921-141">Önceki örnekler referansa göre değer türlerini geçer.</span><span class="sxs-lookup"><span data-stu-id="06921-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="06921-142">Referans türlerini `ref` başvuruya göre geçirmek için anahtar sözcüğü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="06921-143">Başvuru türünü referansla geçmek, başvuru parametresinin arayanda başvururolduğu nesneyi değiştirmek için çağrılan yöntemin değiştirilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="06921-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="06921-144">Nesnenin depolama konumu, başvuru parametresi değeri olarak yönteme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="06921-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="06921-145">Parametrenin depolama konumundaki değeri değiştirirseniz (yeni bir nesneye işaret etmek için), arayanın başvurulması gereken depolama konumunu da değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="06921-146">Aşağıdaki örnek, `ref` parametre olarak bir başvuru türü örneğini geçer.</span><span class="sxs-lookup"><span data-stu-id="06921-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="06921-147">Referans türlerinin değere ve başvuruya göre nasıl geçirilen hakkında daha fazla bilgi için [Bkz.](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="06921-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="06921-148">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="06921-148">Reference return values</span></span>

<span data-ttu-id="06921-149">Başvuru iade değerleri (veya ref returns) bir yöntemin arayana başvuruyla döndürdettiği değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="06921-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="06921-150">Diğer bir deyişle, arayan bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik yöntemi içeren nesnenin durumuna yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="06921-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="06921-151">Bir referans iade değeri anahtar `ref` sözcüğü kullanılarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="06921-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="06921-152">Yöntem imzasında.</span><span class="sxs-lookup"><span data-stu-id="06921-152">In the method signature.</span></span> <span data-ttu-id="06921-153">Örneğin, aşağıdaki yöntem imzası yöntemin `GetCurrentPrice` başvuru <xref:System.Decimal> tarafından bir değer döndürür gösterir.</span><span class="sxs-lookup"><span data-stu-id="06921-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="06921-154">Belirteç `return` ve değişken arasında `return` yöntemde bir ifade döndürülür.</span><span class="sxs-lookup"><span data-stu-id="06921-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="06921-155">Örnek:</span><span class="sxs-lookup"><span data-stu-id="06921-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="06921-156">Arayanın nesnenin durumunu değiştirebilmesi için, başvuru iade değerinin ref [yerel](#ref-locals)olarak açıkça tanımlanan bir değişkene depolanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06921-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="06921-157">Çağrılan yöntem, iade değerini başvuru `ref readonly` yla değeri döndürecek şekilde bildirebilir ve arama kodunun döndürülen değeri değiştiremeyeceğini zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="06921-157">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="06921-158">Arama yöntemi, değeri yerel bir [ref readonly](#ref-readonly-locals) değişkeninde depolayarak döndürülen değeri kopyalamaktan kaçınabilir.</span><span class="sxs-lookup"><span data-stu-id="06921-158">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="06921-159">Örneğin, [bkz.](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="06921-159">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="06921-160">Ref yerlileri</span><span class="sxs-lookup"><span data-stu-id="06921-160">Ref locals</span></span>

<span data-ttu-id="06921-161">Ref yerel değişkeni kullanılarak `return ref`döndürülen değerlere başvurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06921-161">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="06921-162">Bir ref yerel değişkeni, ref olmayan bir geri dönüş değerine başolarak başlılamaz.</span><span class="sxs-lookup"><span data-stu-id="06921-162">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="06921-163">Başka bir deyişle, başlaştırmanın sağ tarafı bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06921-163">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="06921-164">Ref yerel değeri herhangi bir değişiklik yöntemi referans tarafından değeri döndürülen nesnenin durumuna yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="06921-164">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="06921-165">Değişken bildiriminden `ref` önce anahtar sözcüğü kullanarak ve başvuru değeri döndüren yönteme çağrıdan hemen önce bir ref yerel tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="06921-165">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="06921-166">Örneğin, aşağıdaki deyim, adlı `GetEstimatedValue`bir yöntemle döndürülen bir ref yerel değerini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="06921-166">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="06921-167">Bir değere aynı şekilde başvuru yla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-167">You can access a value by reference in the same way.</span></span> <span data-ttu-id="06921-168">Bazı durumlarda, bir değere referans la erişmek, pahalı olabilecek bir kopyalama işleminden kaçınarak performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="06921-168">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="06921-169">Örneğin, aşağıdaki deyim, bir değere başvurmak için kullanılan bir ref yerel değerini nasıl tanımlayabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06921-169">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="06921-170">Her iki örnekte `ref` de anahtar kelimenin her iki yerde de kullanılması gerektiğini veya derleyicinin CS8172 hatası oluşturduğunu unutmayın: "Bir değerle bir yan referans değişkenini başharfe düşüremezsin."</span><span class="sxs-lookup"><span data-stu-id="06921-170">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="06921-171">C# 7.3 ile başlayarak, ifadenin `foreach` yineleme değişkeni ref lokal veya ref readonlyonly local değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="06921-171">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="06921-172">Daha fazla bilgi için [foreach deyimi](foreach-in.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="06921-172">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="06921-173">Ayrıca C# 7.3 ile başlayarak, [ref atama işleci](../operators/assignment-operator.md#ref-assignment-operator)ile bir ref yerel veya ref readonlyonly local değişken yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-173">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="06921-174">Ref sadece yerlileri okuyor</span><span class="sxs-lookup"><span data-stu-id="06921-174">Ref readonly locals</span></span>

<span data-ttu-id="06921-175">Bir ref readonly yerel imzası ve kullandığı `ref readonly` `return ref`yöntem veya özellik tarafından döndürülen değerleri başvurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06921-175">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="06921-176">Bir `ref readonly` değişken yerel değişkenin `ref` özelliklerini bir `readonly` değişkenle birleştirir: atandığı depolamanın diğer adıdır ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="06921-176">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="06921-177">Bir ref döner ve ref locals örneği</span><span class="sxs-lookup"><span data-stu-id="06921-177">A ref returns and ref locals example</span></span>

<span data-ttu-id="06921-178">Aşağıdaki örnekte iki `Book` <xref:System.String> alanı olan bir `Title` `Author`sınıf tanımlanır ve .</span><span class="sxs-lookup"><span data-stu-id="06921-178">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="06921-179">Ayrıca, özel `BookCollection` bir `Book` nesne dizisi içeren bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06921-179">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="06921-180">Tek tek kitap nesneleri, `GetBookByTitle` yöntemini çağırarak referans la döndürülür.</span><span class="sxs-lookup"><span data-stu-id="06921-180">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="06921-181">Arayan `GetBookByTitle` yöntem tarafından döndürülen değeri bir ref yerel olarak depoladığında, aşağıdaki örnekte görüldüğü `BookCollection` gibi, arayanın return value'a yaptığı değişiklikler nesneye yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="06921-181">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="06921-182">Ref yapı tipleri</span><span class="sxs-lookup"><span data-stu-id="06921-182">Ref struct types</span></span>

<span data-ttu-id="06921-183">`struct` Bir bildirime `ref` değiştirici nin eklenmesi, bu tür örneklerin yığın ayrılması gerektiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06921-183">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="06921-184">Başka bir deyişle, bu tür örnekler başka bir sınıfın bir üyesi olarak yığın üzerinde oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="06921-184">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="06921-185">Bu özelliğin temel <xref:System.Span%601> motivasyonu ve ilgili yapılardır.</span><span class="sxs-lookup"><span data-stu-id="06921-185">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="06921-186">Bir `ref struct` türü yığın ayrılmış değişken olarak tutma hedefi, derleyicinin tüm `ref struct` türler için uyguladığı çeşitli kurallar sunar.</span><span class="sxs-lookup"><span data-stu-id="06921-186">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="06921-187">Bir `ref struct`şey için boks yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="06921-187">You can't box a `ref struct`.</span></span> <span data-ttu-id="06921-188">Bir tür, `ref struct` tür `object`, `dynamic`veya herhangi bir arabirim türü değişkenine atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="06921-188">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="06921-189">`ref struct`türler arabirimleri uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="06921-189">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="06921-190">Bir `ref struct` sınıfın alan üyesi veya normal bir yapı olarak beyan edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-190">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="06921-191">Bu, derleyici oluşturulan destek alanı oluşturan otomatik olarak uygulanan bir özelliği bildirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="06921-191">This includes declaring an auto-implemented property, which creates a compiler generated backing field.</span></span>
- <span data-ttu-id="06921-192">Async yöntemleri `ref struct` türleri yerel değişkenler bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-192">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="06921-193">Bunları döndüren <xref:System.Threading.Tasks.Task>eşzamanlı yöntemlerle <xref:System.Threading.Tasks.Task%601> veya `Task`-benzer türlerde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-193">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="06921-194">Yineleyicilerde `ref struct` yerel değişkenleri bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-194">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="06921-195">Lambda `ref struct` ifadelerinde veya yerel işlevlerde değişkenleri yakalayamamazsınız.</span><span class="sxs-lookup"><span data-stu-id="06921-195">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="06921-196">Bu kısıtlamalar, yanlışlıkla yönetilen yığına tanıtacak şekilde kullanmamanızı `ref struct` sağlar.</span><span class="sxs-lookup"><span data-stu-id="06921-196">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="06921-197">Bir yapıyı " olarak `readonly ref`bildirmek için değiştiricileri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06921-197">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="06921-198">A `readonly ref struct` yararları ve kısıtlamaları `ref struct` ve `readonly struct` bildirimleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="06921-198">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="06921-199">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="06921-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="06921-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06921-200">See also</span></span>

- [<span data-ttu-id="06921-201">Güvenli verimli kod yazın</span><span class="sxs-lookup"><span data-stu-id="06921-201">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="06921-202">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="06921-202">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="06921-203">Koşullu ref ekspresyonu</span><span class="sxs-lookup"><span data-stu-id="06921-203">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="06921-204">Geçme Parametreleri</span><span class="sxs-lookup"><span data-stu-id="06921-204">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="06921-205">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="06921-205">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="06921-206">C# Referans</span><span class="sxs-lookup"><span data-stu-id="06921-206">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="06921-207">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="06921-207">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="06921-208">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="06921-208">C# Keywords</span></span>](index.md)
