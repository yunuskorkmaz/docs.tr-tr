---
title: Başvuru Hücreleri (F#)
description: 'F # başvuru hücreleri başvuru semantiğiyle değişebilir değerler oluşturmanıza olanak tanıyan depolama konumları nasıl olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 133aec6b162a13306a05c9afa172f859890565eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892433"
---
# <a name="reference-cells"></a><span data-ttu-id="1830b-103">Başvuru Hücreleri</span><span class="sxs-lookup"><span data-stu-id="1830b-103">Reference Cells</span></span>

<span data-ttu-id="1830b-104">*Başvuru hücreleri* , başvuru semantiğiyle değişebilir değerler oluşturmanıza olanak sağlayan depolama yerleridir.</span><span class="sxs-lookup"><span data-stu-id="1830b-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="1830b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1830b-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="1830b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1830b-106">Remarks</span></span>

<span data-ttu-id="1830b-107">Kullandığınız `ref` değeri kapsülleyen yeni bir başvuru hücresi oluşturmak için bir değer önce işleci.</span><span class="sxs-lookup"><span data-stu-id="1830b-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="1830b-108">Ardından, temeldeki değer değişebilir olduğundan değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1830b-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="1830b-109">Başvuru hücresi gerçek bir değer taşır; yalnızca adres değildir.</span><span class="sxs-lookup"><span data-stu-id="1830b-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="1830b-110">Kullanarak bir başvuru hücresi oluşturduğunuzda `ref` işleci, kapsüllenmiş bir değişmez değer olarak temeldeki değerin bir kopyasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1830b-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="1830b-111">Kullanarak bir başvuru hücresi başvuru `!` (bang) işlecini.</span><span class="sxs-lookup"><span data-stu-id="1830b-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="1830b-112">Aşağıdaki kod örneği başvuru hücrelerinin bildirim ve kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1830b-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="1830b-113">Çıktı `50`.</span><span class="sxs-lookup"><span data-stu-id="1830b-113">The output is `50`.</span></span>

<span data-ttu-id="1830b-114">Başvuru hücreleri örnekleridir `Ref` genel kayıt türü, şu şekilde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="1830b-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="1830b-115">Türü `'a ref` eşanlamlıdır `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="1830b-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="1830b-116">Derleyici ve IDE içindeki IntelliSense, bu tür için ilkini görüntüler fakat temeldeki tanım ikincisidir.</span><span class="sxs-lookup"><span data-stu-id="1830b-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="1830b-117">`ref` İşleci yeni bir başvuru hücresi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1830b-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="1830b-118">Aşağıdaki kod bildirimidir `ref` işleci.</span><span class="sxs-lookup"><span data-stu-id="1830b-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="1830b-119">Aşağıdaki tablo başvuru hücresindeki mevcut özellikleri göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1830b-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="1830b-120">İşleç, üye veya alan</span><span class="sxs-lookup"><span data-stu-id="1830b-120">Operator, member, or field</span></span>|<span data-ttu-id="1830b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1830b-121">Description</span></span>|<span data-ttu-id="1830b-122">Tür</span><span class="sxs-lookup"><span data-stu-id="1830b-122">Type</span></span>|<span data-ttu-id="1830b-123">Tanım</span><span class="sxs-lookup"><span data-stu-id="1830b-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="1830b-124">`!` (başvuru işleci)</span><span class="sxs-lookup"><span data-stu-id="1830b-124">`!` (dereference operator)</span></span>|<span data-ttu-id="1830b-125">Temeldeki değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1830b-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="1830b-126">`:=` (atama işleci)</span><span class="sxs-lookup"><span data-stu-id="1830b-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="1830b-127">Temeldeki değeri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="1830b-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="1830b-128">`ref` (işleç)</span><span class="sxs-lookup"><span data-stu-id="1830b-128">`ref` (operator)</span></span>|<span data-ttu-id="1830b-129">Yeni bir başvuru hücresine bir değer kapsüller.</span><span class="sxs-lookup"><span data-stu-id="1830b-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="1830b-130">`Value` (özelliği)</span><span class="sxs-lookup"><span data-stu-id="1830b-130">`Value` (property)</span></span>|<span data-ttu-id="1830b-131">Temeldeki değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1830b-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="1830b-132">`contents` (kayıt alanı)</span><span class="sxs-lookup"><span data-stu-id="1830b-132">`contents` (record field)</span></span>|<span data-ttu-id="1830b-133">Temeldeki değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1830b-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="1830b-134">Temeldeki değere erişmek için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="1830b-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="1830b-135">Başvuru işleci tarafından döndürülen değer (`!`) atanabilir bir değer değil.</span><span class="sxs-lookup"><span data-stu-id="1830b-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="1830b-136">Bu nedenle, temeldeki değeri değiştiriyorsanız, atama işlecini kullanmanız gerekir (`:=`) bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="1830b-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="1830b-137">Her iki `Value` özelliği ve `contents` alanı atanabilir değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="1830b-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="1830b-138">Bu nedenle, bunları temeldeki değere ulaşmak ya da onu değiştirmek için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1830b-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="1830b-139">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1830b-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="1830b-140">Alan `contents` diğer ML sürümleriyle uyumluluk için sağlanır ve derleme sırasında bir uyarı üretecektir.</span><span class="sxs-lookup"><span data-stu-id="1830b-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="1830b-141">Uyarı devre dışı bırakmak için `--mlcompatibility` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="1830b-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="1830b-142">Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="1830b-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="1830b-143">Aşağıdaki kod, başvuru hücrelerinin parametre geçişlerinde kullanımını örneklendirmektedir.</span><span class="sxs-lookup"><span data-stu-id="1830b-143">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="1830b-144">Byref parametre türü içeren bir parametre alan artışı yöntemi Incrementor türü vardır.</span><span class="sxs-lookup"><span data-stu-id="1830b-144">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="1830b-145">Byref parametre türü, Arayanların bir başvuru hücresini veya belirtilen türün tipik değişkenin adresini bu büyük bir tamsayı geçmesi gerektiğini gösterir Geri kalan kod artırma hem de bu tür bağımsız değişkenleri ile çağırmak nasıl gösterir ve (ref myDelta1) başvuru hücresini oluşturmak için bir değişken başvuru işleci kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1830b-145">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="1830b-146">Ardından adres işlecini kullanımını gösterir (&amp;) uygun bir bağımsız değişken oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1830b-146">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="1830b-147">Son olarak, Increment yöntemi yeniden let bağlama kullanılarak bildirilen bir başvuru hücresi kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1830b-147">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="1830b-148">Son kod satırının kullanımını gösteren!</span><span class="sxs-lookup"><span data-stu-id="1830b-148">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="1830b-149">yazdırma için başvuru hücresine başvuran işleci.</span><span class="sxs-lookup"><span data-stu-id="1830b-149">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="1830b-150">Başvuruya göre hakkında daha fazla bilgi için bkz. [parametreler ve bağımsız değişkenler](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="1830b-150">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="1830b-151">C# programcıları, C# dilinde sağladığından, başvuru farklı F #'de çalışır bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1830b-151">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="1830b-152">C# içinde çalıştığı gibi örneğin, bir bağımsız değişken geçirdiğinizde ref kullanımını aynı etkiyi F #'ta yok.</span><span class="sxs-lookup"><span data-stu-id="1830b-152">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

>[!NOTE]
<span data-ttu-id="1830b-153">`mutable` değişkenleri otomatik olarak yükseltilerek için `'a ref` kapanım; tarafından yakalanan olup [değerleri](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="1830b-153">`mutable` variables may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="1830b-154">C# tüketme `ref` döndürür</span><span class="sxs-lookup"><span data-stu-id="1830b-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="1830b-155">F # 4.1 ile başlayarak, raporlarını kullanabilirsiniz `ref` oluşturulan C# dilinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="1830b-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="1830b-156">Böyle bir çağrının sonucu bir `byref<_>` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1830b-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="1830b-157">Aşağıdaki C# yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1830b-157">The following C# method:</span></span>

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

<span data-ttu-id="1830b-158">Şeffaf bir şekilde F # tarafından hiçbir özel sözdizimi ile çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="1830b-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="1830b-159">Ayrıca sürebilir işlevleri bildirebilirsiniz bir `ref` giriş olarak örneğin döndürür:</span><span class="sxs-lookup"><span data-stu-id="1830b-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="1830b-160">Şu anda oluşturma olanağı, bir `ref` dönüş F #'de, C# ' de kullanılabilecek.</span><span class="sxs-lookup"><span data-stu-id="1830b-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="1830b-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1830b-161">See also</span></span>

- [<span data-ttu-id="1830b-162">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1830b-162">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1830b-163">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1830b-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="1830b-164">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1830b-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="1830b-165">Değerler</span><span class="sxs-lookup"><span data-stu-id="1830b-165">Values</span></span>](values/index.md)
