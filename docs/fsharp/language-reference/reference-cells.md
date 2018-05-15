---
title: Başvuru Hücreleri (F#)
description: 'F # başvuru hücreleri değişebilir değerleri başvuru semantiği ile oluşturmanıza olanak sağlaması depolama konumları ne olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 3a632425356a250f07e5babd2751b9923eec6552
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2018
---
# <a name="reference-cells"></a><span data-ttu-id="483bf-103">Başvuru Hücreleri</span><span class="sxs-lookup"><span data-stu-id="483bf-103">Reference Cells</span></span>

<span data-ttu-id="483bf-104">*Başvuru hücreleri* değişebilir değerleri başvuru semantiği ile oluşturmanıza olanak sağlaması depolama konumlarının.</span><span class="sxs-lookup"><span data-stu-id="483bf-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="483bf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="483bf-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="483bf-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="483bf-106">Remarks</span></span>
<span data-ttu-id="483bf-107">Kullandığınız `ref` değeri yalıtan yeni bir başvuru hücre oluşturmak için işlecinden önce bir değer.</span><span class="sxs-lookup"><span data-stu-id="483bf-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="483bf-108">Ardından, temeldeki değer değişebilir olduğundan değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="483bf-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="483bf-109">Başvuru hücresi gerçek bir değer taşır; yalnızca adres değildir.</span><span class="sxs-lookup"><span data-stu-id="483bf-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="483bf-110">Kullanarak bir başvuru hücresi oluşturduğunuzda `ref` işleci, temel alınan değeri kapsüllenmiş değişmez değer olarak bir kopyasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="483bf-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="483bf-111">Kullanarak bir başvuru hücresine başvurur `!` (performansı) işleci.</span><span class="sxs-lookup"><span data-stu-id="483bf-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="483bf-112">Aşağıdaki kod örneği başvuru hücrelerinin bildirim ve kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="483bf-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="483bf-113">Çıktı `50`.</span><span class="sxs-lookup"><span data-stu-id="483bf-113">The output is `50`.</span></span>

<span data-ttu-id="483bf-114">Başvuru hücreleri örnekleridir `Ref` gibi bildirilmiş genel kayıt türü.</span><span class="sxs-lookup"><span data-stu-id="483bf-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="483bf-115">Türü `'a ref` eşanlamlısı olduğu `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="483bf-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="483bf-116">Derleyici ve IDE içindeki IntelliSense, bu tür için ilkini görüntüler fakat temeldeki tanım ikincisidir.</span><span class="sxs-lookup"><span data-stu-id="483bf-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="483bf-117">`ref` İşleci yeni bir başvuru hücresi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="483bf-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="483bf-118">Aşağıdaki kodu bildirimi: `ref` işleci.</span><span class="sxs-lookup"><span data-stu-id="483bf-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="483bf-119">Aşağıdaki tablo başvuru hücresindeki mevcut özellikleri göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="483bf-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="483bf-120">İşleç, üye veya alan</span><span class="sxs-lookup"><span data-stu-id="483bf-120">Operator, member, or field</span></span>|<span data-ttu-id="483bf-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="483bf-121">Description</span></span>|<span data-ttu-id="483bf-122">Tür</span><span class="sxs-lookup"><span data-stu-id="483bf-122">Type</span></span>|<span data-ttu-id="483bf-123">Tanım</span><span class="sxs-lookup"><span data-stu-id="483bf-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="483bf-124">`!` (işleci başvuru)</span><span class="sxs-lookup"><span data-stu-id="483bf-124">`!` (dereference operator)</span></span>|<span data-ttu-id="483bf-125">Temeldeki değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="483bf-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="483bf-126">`:=` (atama işleci)</span><span class="sxs-lookup"><span data-stu-id="483bf-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="483bf-127">Temeldeki değeri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="483bf-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="483bf-128">`ref` (işleç)</span><span class="sxs-lookup"><span data-stu-id="483bf-128">`ref` (operator)</span></span>|<span data-ttu-id="483bf-129">Yeni bir başvuru hücresine bir değer kapsüller.</span><span class="sxs-lookup"><span data-stu-id="483bf-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="483bf-130">`Value` (özellik)</span><span class="sxs-lookup"><span data-stu-id="483bf-130">`Value` (property)</span></span>|<span data-ttu-id="483bf-131">Temeldeki değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="483bf-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="483bf-132">`contents` (kayıt alanı)</span><span class="sxs-lookup"><span data-stu-id="483bf-132">`contents` (record field)</span></span>|<span data-ttu-id="483bf-133">Temeldeki değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="483bf-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="483bf-134">Temeldeki değere erişmek için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="483bf-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="483bf-135">Başvuru işleci tarafından döndürülen değer (`!`) atanabilen bir değer değil.</span><span class="sxs-lookup"><span data-stu-id="483bf-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="483bf-136">Bu nedenle, temeldeki değer değiştiriyorsanız atama işleci kullanmanız gerekir (`:=`) yerine.</span><span class="sxs-lookup"><span data-stu-id="483bf-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="483bf-137">Her iki `Value` özelliği ve `contents` alan atanabilir değerleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="483bf-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="483bf-138">Bu nedenle, bunları temeldeki değere ulaşmak ya da onu değiştirmek için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="483bf-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="483bf-139">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="483bf-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="483bf-140">Alan `contents` diğer ML sürümleri ile uyumluluk için sağlanır ve derleme sırasında bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="483bf-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="483bf-141">Uyarıyı devre dışı bırakmak için `--mlcompatibility` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="483bf-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="483bf-142">Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="483bf-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="483bf-143">Aşağıdaki kod, başvuru hücrelerinin parametre geçişlerinde kullanımını örneklendirmektedir.</span><span class="sxs-lookup"><span data-stu-id="483bf-143">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="483bf-144">Artırıcı türü bir yöntem byref parametre türü içeren bir parametre alan artışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="483bf-144">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="483bf-145">Parametre türü byref arayanlar başvuru hücre veya belirtilen türün tipik değişkenin adresini bu büyük tamsayı geçmesi gerektiğini gösterir Kalan kod artırma hem de bu tür bağımsız değişkenleri ile çağırmak nasıl gösterir ve başvuru hücre (ref myDelta1) oluşturmak için bir değişken ref işleci kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="483bf-145">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="483bf-146">Address-of işleci kullanımını ardından gösterir (&amp;) uygun bir bağımsız değişken oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="483bf-146">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="483bf-147">Son olarak, Increment yöntemi yeniden let bağlama kullanarak bildirilmiş bir başvuru hücresi kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="483bf-147">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="483bf-148">Kodu son satırının kullanımını gösteren!</span><span class="sxs-lookup"><span data-stu-id="483bf-148">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="483bf-149">yazdırma için başvuru hücresi başvurulacak işleci.</span><span class="sxs-lookup"><span data-stu-id="483bf-149">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="483bf-150">Başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [parametreler ve bağımsız değişkenler](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="483bf-150">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="483bf-151">C# programcıları C# ' ta göründüğünden bu ref farklı F # içinde çalıştığını bilmeniz.</span><span class="sxs-lookup"><span data-stu-id="483bf-151">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="483bf-152">C# ' ta aksine Örneğin, bir bağımsız değişken geçirdiğinizde ref kullanımını aynı etkiye F #'ta yok.</span><span class="sxs-lookup"><span data-stu-id="483bf-152">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

>[!NOTE]
<span data-ttu-id="483bf-153">`mutable` değişkenleri otomatik olarak tanıtılması için `'a ref` tarafından kapatma; yakalanan olup [değerleri](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="483bf-153">`mutable` variables may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="483bf-154">C# tüketme `ref` döndürür</span><span class="sxs-lookup"><span data-stu-id="483bf-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="483bf-155">F # 4.1 ile başlayarak, size tüketebileceği `ref` C# ' de oluşturulan döndürür.</span><span class="sxs-lookup"><span data-stu-id="483bf-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="483bf-156">Bu tür bir çağrının sonucu olan bir `byref<_>` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="483bf-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="483bf-157">Aşağıdaki C# yöntemi:</span><span class="sxs-lookup"><span data-stu-id="483bf-157">The following C# method:</span></span>

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

<span data-ttu-id="483bf-158">Saydam F # kullanarak özel bir sözdizimi ile çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="483bf-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="483bf-159">Ele geçirebilir işlevlerini de bildirebilirsiniz bir `ref` giriş olarak örneğin döndürür:</span><span class="sxs-lookup"><span data-stu-id="483bf-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="483bf-160">Şu anda oluşturmak için bir yolu yoktur bir `ref` F, C# dilinde kullanılabilecek # dönüş.</span><span class="sxs-lookup"><span data-stu-id="483bf-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="483bf-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="483bf-161">See Also</span></span>
[<span data-ttu-id="483bf-162">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="483bf-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="483bf-163">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="483bf-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="483bf-164">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="483bf-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)

[<span data-ttu-id="483bf-165">Değerler</span><span class="sxs-lookup"><span data-stu-id="483bf-165">Values</span></span>](values/index.md)
