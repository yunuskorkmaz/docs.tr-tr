---
title: Demetler
description: 'Farklı türlerde olabilecek adlandırılmamış ancak sıralı değerler gruplandırması olan F # Tuple hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 6f4adf7e10e22d8b7a8cf697baee15962adf3630
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720367"
---
# <a name="tuples"></a><span data-ttu-id="7d20d-103">Demetler</span><span class="sxs-lookup"><span data-stu-id="7d20d-103">Tuples</span></span>

<span data-ttu-id="7d20d-104">*Kayıt düzeni* , farklı türlerde olabilecek adlandırılmamış ancak sıralanmış değerlerin bir gruplandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="7d20d-105">Tanımlama grupları başvuru türleri ya da yapılar olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d20d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d20d-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="7d20d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d20d-107">Remarks</span></span>

<span data-ttu-id="7d20d-108">Önceki söz diziminde her *öğe* geçerli bir F # ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="7d20d-109">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7d20d-109">Examples</span></span>

<span data-ttu-id="7d20d-110">Tanımlama gruplarına örnek olarak, aynı veya farklı türlerde çiftler, Üçlü, vb. dahildir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="7d20d-111">Bazı örnekler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="7d20d-112">Ayrı değerler alma</span><span class="sxs-lookup"><span data-stu-id="7d20d-112">Obtaining Individual Values</span></span>

<span data-ttu-id="7d20d-113">Aşağıdaki kodda gösterildiği gibi, kayıt düzeni öğelerine erişmek ve adları atamak için model eşleştirmeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d20d-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="7d20d-114">Ayrıca bağlama yoluyla bir ifadenin dışındaki bir düzeni kullanarak bir tanımlama grubu oluşturabilirsiniz `match`  `let` .</span><span class="sxs-lookup"><span data-stu-id="7d20d-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="7d20d-115">Ya da, diziler üzerinde farklı işlevlere giriş olarak de kalıp eşleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d20d-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="7d20d-116">Kayıt düzeninin yalnızca bir öğesine ihtiyacınız varsa, ihtiyacınız olmayan bir değer için yeni bir ad oluşturmaktan kaçınmak için joker karakter (alt çizgi) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="7d20d-117">Bir başvuru kayıt kümesinden yapı grubu içine öğe kopyalamak de basittir:</span><span class="sxs-lookup"><span data-stu-id="7d20d-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="7d20d-118">İşlevler `fst` ve `snd` (yalnızca başvuru tanımlama grupları), bir başlığın sırasıyla ilk ve ikinci öğelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d20d-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="7d20d-119">Üçlü öğesinin üçüncü öğesini döndüren yerleşik bir işlev yoktur, ancak aşağıdaki gibi kolayca bir tane yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d20d-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="7d20d-120">Genellikle, tek tek demet öğelerine erişmek için model eşleştirmeyi kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="7d20d-121">Tanımlama gruplarını kullanma</span><span class="sxs-lookup"><span data-stu-id="7d20d-121">Using Tuples</span></span>

<span data-ttu-id="7d20d-122">Tanımlama grupları, aşağıdaki örnekte gösterildiği gibi bir işlevden birden çok değer döndürmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d20d-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="7d20d-123">Bu örnek, tam sayı bölümü gerçekleştirir ve bir demet çiftinin ilk üyesi olarak işlemin yuvarlanmış sonucunu ve çiftinin ikinci bir üyesi olarak geri kalanını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d20d-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="7d20d-124">Ayrıca, normal işlev sözdizimi tarafından kapsanan işlev bağımsız değişkenlerinin örtük olarak oluşmasını önlemek istediğinizde, diziler işlev bağımsız değişkeni olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="7d20d-125">İşlevi tanımlamaya yönelik olağan sözdizimi, `let sum a b = a + b` aşağıdaki kodda gösterildiği gibi, işlevin ilk bağımsız değişkeninin kısmi uygulaması olan bir işlev tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d20d-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="7d20d-126">Parametre olarak bir tanımlama grubu kullanmak, currying 'i devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="7d20d-127">Daha fazla bilgi için, bkz. [işlevlerde](./functions/index.md)"bağımsız değişkenlerin kısmi uygulaması".</span><span class="sxs-lookup"><span data-stu-id="7d20d-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="7d20d-128">Demet türlerinin adları</span><span class="sxs-lookup"><span data-stu-id="7d20d-128">Names of Tuple Types</span></span>

<span data-ttu-id="7d20d-129">Tanımlama grubu olan bir türün adını yazdığınızda, `*` öğeleri ayırmak için simgesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d20d-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="7d20d-130">, Gibi bir,, ve içeren bir tanımlama grubu için, `int` `float` `string` `(10, 10.0, "ten")` tür şöyle yazılır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="7d20d-131">C# tanımlama grupları ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="7d20d-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="7d20d-132">C# 7,0, tanımlama gruplarını dile sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="7d20d-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="7d20d-133">C# ' deki diziler yapılar ve F # ' daki yapı tanımlama grupları ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="7d20d-134">C# ile birlikte çalışmanız gerekiyorsa struct tanımlama gruplarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="7d20d-135">Bu kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-135">This is easy to do.</span></span>  <span data-ttu-id="7d20d-136">Örneğin, bir tanımlama grubunu C# sınıfına geçirmeniz ve sonra da bir tanımlama grubu olan sonucunu tüketmeniz gerektiğini düşünün:</span><span class="sxs-lookup"><span data-stu-id="7d20d-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="7d20d-137">F # kodunuzda, bir yapı tanımlama grubunu parametre olarak geçirebilir ve sonucu bir struct demet olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d20d-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="7d20d-138">Başvuru tanımlama grupları ve yapı tanımlama grupları arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7d20d-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="7d20d-139">Başvuru başlıkları ve yapı tanımlama gruplarının tamamen farklı bir temel temsili olduğundan, bunlar örtülü olarak dönüştürülebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="7d20d-140">Diğer bir deyişle, aşağıdaki gibi bir kod derlenmez:</span><span class="sxs-lookup"><span data-stu-id="7d20d-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="7d20d-141">Tek bir kayıt düzeninde kalıp eşleşmesi gerekir ve diğer bileşenleri oluşturan parçalar ile oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d20d-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="7d20d-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7d20d-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="7d20d-143">Başvuru tanımlama gruplarının derlenmiş formu</span><span class="sxs-lookup"><span data-stu-id="7d20d-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="7d20d-144">Bu bölüm, derlendikleri zaman başlıkların biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d20d-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="7d20d-145">.NET Framework 3,5 veya daha düşük bir sürüm hedeflenmediğiniz müddetçe buradaki bilgiler okunmanıza gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="7d20d-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="7d20d-146">Tanımlama grupları, birden fazla genel türden biri olan, `System.Tuple` parametre sayısı üzerinde aşırı yüklenmiş olan tüm adlandırılmış nesneler veya tür parametrelerinin sayısıyla derlenir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="7d20d-147">Bu formda, C# veya Visual Basic gibi başka bir dilde görüntülediğinizde ya da F # yapıları farkında olmayan bir araç kullanırken demet türleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="7d20d-148">`Tuple`Türler .NET Framework 4 ' te tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="7d20d-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="7d20d-149">.NET Framework önceki bir sürümünü hedefliyorsanız, derleyici `System.Tuple` F # Çekirdek kitaplığının 2,0 sürümündeki sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-149">If you are targeting an earlier version of .NET Framework, the compiler uses versions of `System.Tuple` from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="7d20d-150">Bu kitaplıktaki türler yalnızca .NET Framework 2,0, 3,0 ve 3,5 sürümlerini hedefleyen uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of .NET Framework.</span></span> <span data-ttu-id="7d20d-151">Tür iletme, .NET Framework 2,0 ve .NET Framework 4 F # bileşenleri arasında ikili uyumluluk sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="7d20d-152">Yapı tanımlama gruplarının derlenmiş formu</span><span class="sxs-lookup"><span data-stu-id="7d20d-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="7d20d-153">Yapı tanımlama grupları (örneğin, `struct (x, y)` ), başvuru dizklarından temelde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="7d20d-154">Bunlar <xref:System.ValueTuple> türü, parametre sayısına göre aşırı yüklendi veya tür parametrelerinin sayısı olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="7d20d-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="7d20d-155">[C# 7,0 tanımlama](../../csharp/language-reference/builtin-types/value-tuples.md) gruplarına ve [Visual Basic 2017 tanımlama](../../visual-basic/programming-guide/language-features/data-types/tuples.md)gruplarına eşdeğerdir ve birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d20d-155">They are equivalent to [C# 7.0 Tuples](../../csharp/language-reference/builtin-types/value-tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d20d-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d20d-156">See also</span></span>

- [<span data-ttu-id="7d20d-157">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="7d20d-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7d20d-158">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="7d20d-158">F# Types</span></span>](fsharp-types.md)
