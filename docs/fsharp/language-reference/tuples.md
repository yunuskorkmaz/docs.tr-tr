---
title: Demetler
description: Hakkında bilgi edinin F# tanımlama grubu, farklı türlerde adlandırılmamış ancak sıralı değerleri gruplandırmasıdır.
ms.date: 05/16/2016
ms.openlocfilehash: a1fc31d4dc97c0921545e53b91dcde0547002006
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755343"
---
# <a name="tuples"></a><span data-ttu-id="6219a-103">Demetler</span><span class="sxs-lookup"><span data-stu-id="6219a-103">Tuples</span></span>

<span data-ttu-id="6219a-104">A *demet* farklı türlerde adlandırılmamış ancak sıralı değerleri bir gruplandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6219a-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="6219a-105">Diziler, başvuru türleri veya yapıları ya da olabilir.</span><span class="sxs-lookup"><span data-stu-id="6219a-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="6219a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6219a-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="6219a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6219a-107">Remarks</span></span>

<span data-ttu-id="6219a-108">Her *öğesi* önceki sözdiziminde herhangi bir geçerli olabilir F# ifade.</span><span class="sxs-lookup"><span data-stu-id="6219a-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="6219a-109">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6219a-109">Examples</span></span>

<span data-ttu-id="6219a-110">Çiftler, Üçlü ve benzeri, aynı veya farklı tür diziler örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="6219a-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="6219a-111">Bazı örnekler, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6219a-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="6219a-112">Tek değer alma</span><span class="sxs-lookup"><span data-stu-id="6219a-112">Obtaining Individual Values</span></span>

<span data-ttu-id="6219a-113">Desen eşleştirme erişmek ve demet öğelerin adlarını atamak için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6219a-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="6219a-114">Ayrıca dışında desen eşleştirme aracılığıyla bir demet ayrıştırma bir `match` ifadesi ile `let` bağlama:</span><span class="sxs-lookup"><span data-stu-id="6219a-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="6219a-115">Veya desen giriş olarak işlevleri demetleri eşleşen:</span><span class="sxs-lookup"><span data-stu-id="6219a-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="6219a-116">Yalnızca bir demet öğesi gerekiyorsa, joker karakter (alt çizgi), ihtiyacınız olmayan bir değer için yeni bir ad oluşturmaktan kaçınmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6219a-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="6219a-117">Öğeleri bir başvuru tanımlama grubundan bir yapı tanımlama grubu kopyalama ayrıca basittir:</span><span class="sxs-lookup"><span data-stu-id="6219a-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="6219a-118">İşlevleri `fst` ve `snd` (başvuru yalnızca başlıkları) ilk geri dönün ve bir dizi öğelerini sırasıyla ikinci.</span><span class="sxs-lookup"><span data-stu-id="6219a-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="6219a-119">Üçüncü bir Üçlü öğesine döndürür hiçbir yerleşik işlevi yoktur, ancak, kolay bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6219a-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="6219a-120">Genellikle, tek bir demet öğelere erişmek için desen eşleştirme kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="6219a-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="6219a-121">Demetlerin kullanılmasını sağlayan</span><span class="sxs-lookup"><span data-stu-id="6219a-121">Using Tuples</span></span>

<span data-ttu-id="6219a-122">Diziler, aşağıdaki örnekte gösterildiği gibi bir işlevden birden çok değer döndürmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6219a-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="6219a-123">Bu örnek, Tamsayı bölme gerçekleştirir ve işlem olarak bir dizi çifti ilk üyesi ve kalanı çifti ikinci bir üyesi olarak yuvarlatılmış sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6219a-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="6219a-124">Normal işlev sözdizimi tarafından örtük işlev bağımsız değişkenlerinin örtülü currying önlemek istediğinizde diziler de işlev bağımsız değişkenleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6219a-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="6219a-125">İşlevi tanımlayan normal söz dizimi `let sum a b = a + b` kısmi uygulama işlevinin ilk bağımsız değişkenin bir işlev aşağıdaki kodda gösterildiği gibi tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6219a-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="6219a-126">Parametre olarak bir tanımlama grubu kullanımı currying devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6219a-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="6219a-127">Daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevleri](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="6219a-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="6219a-128">Demet türü adları</span><span class="sxs-lookup"><span data-stu-id="6219a-128">Names of Tuple Types</span></span>

<span data-ttu-id="6219a-129">Bir demet türü adını yazdığınızda, kullandığınız `*` öğeleri ayırmak için kullanılan simge.</span><span class="sxs-lookup"><span data-stu-id="6219a-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="6219a-130">Oluşan bir demet için bir `int`, `float`ve `string`, gibi `(10, 10.0, "ten")`, türü şu şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="6219a-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="6219a-131">C# demetleri ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6219a-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="6219a-132">C# 7.0 diziler dili kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="6219a-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="6219a-133">' De tanımlama gruplarına C# birimleridir ve yapı demetleri içinde eşdeğer F#.</span><span class="sxs-lookup"><span data-stu-id="6219a-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="6219a-134">C# ile çalışmak ihtiyacınız varsa, yapı demetleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6219a-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="6219a-135">Bunu yapmak kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="6219a-135">This is easy to do.</span></span>  <span data-ttu-id="6219a-136">Örneğin, C# sınıfı için bir demet geçirin ve ardından bir tanımlama grubu olan sonucunu kullanmak sahip olduğunuz düşünün:</span><span class="sxs-lookup"><span data-stu-id="6219a-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="6219a-137">İçinde F# kod, bir yapı demet parametre olarak geçiriyoruz ve sonucu bir yapı tanımlama grubu olarak kullanma.</span><span class="sxs-lookup"><span data-stu-id="6219a-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="6219a-138">Yapı demetleri başvuru diziler arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6219a-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="6219a-139">Başvuru diziler ve yapı demetleri tamamen farklı bir temel alınan gösterimine sahip olduğundan, bunlar örtük olarak dönüştürülebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="6219a-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="6219a-140">Kod aşağıdaki gibi diğer bir deyişle, derlenemeyecektir:</span><span class="sxs-lookup"><span data-stu-id="6219a-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="6219a-141">Desen gerekir üzerinde bir dizi eşleşmesi ve diğer bağlı bileşenlerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6219a-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="6219a-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6219a-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="6219a-143">Derlenmiş Form başvuru tanımlama grubu</span><span class="sxs-lookup"><span data-stu-id="6219a-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="6219a-144">Bu bölümde, bunlar derlendikleri zaman formun başlık açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6219a-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="6219a-145">Burada yer alan bilgiler .NET Framework 3.5 hedefleniyorsa sürece okumak gerekli ya da düşük değildir.</span><span class="sxs-lookup"><span data-stu-id="6219a-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="6219a-146">Diziler, birkaç genel türler, tüm adlandırılmış birinin nesnelerini derlenen `System.Tuple`, parametre sayısı veya türü parametre sayısı aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6219a-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="6219a-147">Tanımlama grubu türleri, bunları başka bir dilden gibi görüntülediğinizde bu formda görünen C# veya Visual Basic veya farkında değil bir aracı kullanırken F# oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6219a-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="6219a-148">`Tuple` Türleri, .NET Framework 4'te sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="6219a-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="6219a-149">.NET Framework'ün önceki bir sürümü hedefliyorsanız, derleyici sürümleri kullanan [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) 2.0 sürümünden F# çekirdek kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="6219a-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="6219a-150">Bu kitaplıktaki türleri, 2.0, 3.0 ve .NET Framework 3.5 sürümlerini hedefleyen uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6219a-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="6219a-151">.NET Framework 2.0 ve .NET Framework 4 ikili uyumluluğu sağlamak için kullanılan tür iletme F# bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="6219a-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="6219a-152">Yapı demetleri derlenmiş biçimi</span><span class="sxs-lookup"><span data-stu-id="6219a-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="6219a-153">Yapı demetleri (örneğin, `struct (x, y)`), temelde başvuru diziler farklıdır.</span><span class="sxs-lookup"><span data-stu-id="6219a-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="6219a-154">İçine derlenmiş <xref:System.ValueTuple> parametre sayısı veya türü parametre sayısı aşırı türü.</span><span class="sxs-lookup"><span data-stu-id="6219a-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="6219a-155">Eşdeğer oldukları [C# 7.0 diziler](../../csharp/tuples.md) ve [Visual Basic 2017 diziler](../../visual-basic/programming-guide/language-features/data-types/tuples.md)ve çift yönlü çalışmak.</span><span class="sxs-lookup"><span data-stu-id="6219a-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="6219a-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6219a-156">See also</span></span>

- [<span data-ttu-id="6219a-157">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6219a-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6219a-158">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="6219a-158">F# Types</span></span>](fsharp-types.md)