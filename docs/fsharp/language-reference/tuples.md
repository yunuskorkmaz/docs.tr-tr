---
title: Demetler (F#)
description: 'F # tanımlama hakkında farklı türlerde adlandırılmamış ancak sıralı değerler gruplandırması öğrenin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: e0a5e5eb08e13bd5cbe9f88a47d4cf4bba19ea22
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="tuples"></a><span data-ttu-id="7ca71-104">Demetler</span><span class="sxs-lookup"><span data-stu-id="7ca71-104">Tuples</span></span>

<span data-ttu-id="7ca71-105">A *tanımlama grubu* farklı türlerde adlandırılmamış ancak sıralı değerler grubudur.</span><span class="sxs-lookup"><span data-stu-id="7ca71-105">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="7ca71-106">Tanımlama grubu ya da başvuru türleri veya yapılar olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-106">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ca71-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ca71-107">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="7ca71-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ca71-108">Remarks</span></span>
<span data-ttu-id="7ca71-109">Her *öğesi* önceki sözdiziminde herhangi geçerli F # ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-109">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="7ca71-110">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7ca71-110">Examples</span></span>
<span data-ttu-id="7ca71-111">Diziler örnekleri çiftleri, Üçlü vb., aynı veya farklı türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-111">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="7ca71-112">Bazı örnekler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-112">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="7ca71-113">Tek tek değerleri alma</span><span class="sxs-lookup"><span data-stu-id="7ca71-113">Obtaining Individual Values</span></span>
<span data-ttu-id="7ca71-114">Desen eşleştirme erişmek ve tanımlama grubu öğelerin adları atamak için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ca71-114">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="7ca71-115">Bir tanımlama grubu dışında desen eşleştirme aracılığıyla deconstruct bir `match` ifadesi aracılığıyla `let` bağlama:</span><span class="sxs-lookup"><span data-stu-id="7ca71-115">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="7ca71-116">Or deseni giriş olarak işlevleri tanımlama grupları üzerinde eşleşen:</span><span class="sxs-lookup"><span data-stu-id="7ca71-116">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="7ca71-117">Yalnızca tek bir öğe kayıt gerekiyorsa, joker karakter (alt çizgi) ihtiyacınız olmayan bir değer için yeni bir ad oluşturmamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-117">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="7ca71-118">Öğeleri bir başvuru tanımlama grubundan bir yapı tanımlama grubu kopyalama ayrıca basittir:</span><span class="sxs-lookup"><span data-stu-id="7ca71-118">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="7ca71-119">İşlevler `fst` ve `snd` (başvuru yalnızca başlıkları) ilk dönün ve bir tanımlama grubu öğeleri sırasıyla ikinci.</span><span class="sxs-lookup"><span data-stu-id="7ca71-119">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="7ca71-120">Bir Üçlü üçüncü öğeyi döndürür hiçbir yerleşik işlevi yoktur, ancak, kolay bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ca71-120">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="7ca71-121">Genellikle, tek tek başlığın öğeleri erişmek için desen eşleştirme kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-121">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="7ca71-122">Tanımlama gruplarını kullanma</span><span class="sxs-lookup"><span data-stu-id="7ca71-122">Using Tuples</span></span>
<span data-ttu-id="7ca71-123">Diziler, aşağıdaki örnekte gösterildiği gibi bir işlevden birden çok değer döndürmek için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="7ca71-123">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="7ca71-124">Bu örnek tamsayı bölme gerçekleştirir ve işlem bir tanımlama grubu çifti ilk üye olarak ve geri kalan çift ikinci bir üyesi olarak yuvarlatılmış sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ca71-124">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="7ca71-125">Normal işlevi sözdizimi tarafından kapsanan işlev bağımsız değişkenleri örtülü currying engellemek istediğinizde diziler işlevi bağımsız değişken olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-125">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="7ca71-126">İşlev tanımlamak için normal sözdizimi `let sum a b = a + b` aşağıdaki kodda gösterildiği gibi kısmi uygulama işlevinin ilk bağımsız değişkenin bir işlev tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ca71-126">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="7ca71-127">Parametre olarak bir tanımlama grubu kullanarak currying devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="7ca71-127">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="7ca71-128">Daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevler](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ca71-128">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="7ca71-129">Tuple türlerinin adlarını</span><span class="sxs-lookup"><span data-stu-id="7ca71-129">Names of Tuple Types</span></span>
<span data-ttu-id="7ca71-130">Bir tanımlama grubu olan bir türü adını yazdığınızda, kullandığınız `*` öğeleri ayırmak için kullanılan simge.</span><span class="sxs-lookup"><span data-stu-id="7ca71-130">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="7ca71-131">Oluşan bir tanımlama grubu için bir `int`, `float`ve bir `string`, gibi `(10, 10.0, "ten")`, türü şu şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="7ca71-131">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="7ca71-132">C# başlıkları ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="7ca71-132">Interoperation with C# Tuples</span></span>

<span data-ttu-id="7ca71-133">C# 7.0 diziler diline kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="7ca71-133">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="7ca71-134">C# diziler yapılar ve F # yapısı diziler eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-134">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="7ca71-135">C# ile çalışmanız gerekiyorsa, yapı dizilerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-135">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="7ca71-136">Bunu yapmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="7ca71-136">This is easy to do.</span></span>  <span data-ttu-id="7ca71-137">Örneğin, C# sınıfına bir tanımlama grubu geçirmek ve aynı zamanda bir tanımlama grubu olan sonucunu kullanmak zorunda düşünün:</span><span class="sxs-lookup"><span data-stu-id="7ca71-137">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="7ca71-138">F # kodu, ardından yapısı tanımlama grubu parametre olarak geçirmek ve sonucu bir yapı tanımlama grubu olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-138">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="7ca71-139">Başvuru başlıkları ve yapı diziler arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7ca71-139">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="7ca71-140">Başvuru başlıkları ve yapı diziler tamamen farklı bir temel alınan gösterimi olduğundan, bunlar örtük olarak dönüştürülebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-140">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="7ca71-141">Diğer bir deyişle, aşağıdaki gibi kod derleme olmaz:</span><span class="sxs-lookup"><span data-stu-id="7ca71-141">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="7ca71-142">Desen gereken diğer bağlı bölümlerle oluşturmak ve bir tanımlama grubu üzerinde eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="7ca71-142">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="7ca71-143">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7ca71-143">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="7ca71-144">Başvuru başlık derlenmiş formu</span><span class="sxs-lookup"><span data-stu-id="7ca71-144">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="7ca71-145">Bu bölümde, derlenmiş zaman formun başlık açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7ca71-145">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="7ca71-146">Burada yer alan bilgiler, .NET Framework 3.5 hedeflediğiniz sürece okumak gerekli veya alt değil.</span><span class="sxs-lookup"><span data-stu-id="7ca71-146">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="7ca71-147">Diziler birkaç genel türlerden birinde, tüm adlandırılmış nesnelerine derlenmiş `System.Tuple`, bu aşırı parametre sayısı veya türü parametre sayısı.</span><span class="sxs-lookup"><span data-stu-id="7ca71-147">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="7ca71-148">Dizi türleri, bunları C# veya Visual Basic gibi başka bir dilden görüntülediğinizde veya F # yapılarını tanımaz bir aracı kullanırken bu formda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7ca71-148">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="7ca71-149">`Tuple` Türleri, .NET Framework 4'te sunulmuştu.</span><span class="sxs-lookup"><span data-stu-id="7ca71-149">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="7ca71-150">.NET Framework'ün önceki bir sürümünü hedefliyorsanız, derleyici sürümlerini kullanan [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) F # Core kitaplık 2.0 sürümünden.</span><span class="sxs-lookup"><span data-stu-id="7ca71-150">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="7ca71-151">Bu kitaplıktaki türleri 2.0, 3.0 ve .NET Framework 3.5 sürümlerini hedefleyen uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ca71-151">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="7ca71-152">Tür iletme, .NET Framework 2.0 ve .NET Framework 4 F # bileşenleri arasında ikili uyumluluğu sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ca71-152">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="7ca71-153">Yapı başlık derlenmiş formu</span><span class="sxs-lookup"><span data-stu-id="7ca71-153">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="7ca71-154">Yapı diziler (örneğin, `struct (x, y)`), başvuru diziler temelde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7ca71-154">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="7ca71-155">İçine derlenmiş <xref:System.ValueTuple> parametre sayısı veya türü parametre sayısı aşırı türü.</span><span class="sxs-lookup"><span data-stu-id="7ca71-155">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="7ca71-156">Eşdeğer [C# 7.0 diziler](../../csharp/tuples.md) ve [Visual Basic 2017 diziler](../../visual-basic/programming-guide/language-features/data-types/tuples.md)ve çift yönlü onunla birlikte çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="7ca71-156">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ca71-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ca71-157">See Also</span></span>
[<span data-ttu-id="7ca71-158">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7ca71-158">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="7ca71-159">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="7ca71-159">F# Types</span></span>](fsharp-types.md)
