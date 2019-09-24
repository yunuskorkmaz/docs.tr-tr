---
title: Başvuru Hücreleri
description: Başvuru semantiğine sahip kesilebilir değerler oluşturmanıza olanak sağlayan depolama konumları olan başvuru hücrelerinin nasıl F# olduğunu öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 2bca7797b272c0e7d5bf54df07041dc08e33709a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216773"
---
# <a name="reference-cells"></a><span data-ttu-id="f9a81-103">Başvuru Hücreleri</span><span class="sxs-lookup"><span data-stu-id="f9a81-103">Reference Cells</span></span>

<span data-ttu-id="f9a81-104">*Başvuru hücreleri* , başvuru semantiğinin değişebilir değerler oluşturmanızı sağlayan depolama konumlarıdır.</span><span class="sxs-lookup"><span data-stu-id="f9a81-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9a81-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9a81-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="f9a81-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9a81-106">Remarks</span></span>

<span data-ttu-id="f9a81-107">Değeri kapsülleyen yeni `ref` bir başvuru hücresi oluşturmak için bir değerden önce işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f9a81-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="f9a81-108">Ardından, temeldeki değer değişebilir olduğundan değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9a81-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="f9a81-109">Başvuru hücresi gerçek bir değer taşır; yalnızca adres değildir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="f9a81-110">`ref` İşlecini kullanarak bir başvuru hücresi oluşturduğunuzda, temeldeki değerin bir kopyasını kapsüllenmiş kesilebilir değer olarak oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f9a81-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="f9a81-111">`!` (Bankg) işlecini kullanarak bir başvuru hücresine başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9a81-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="f9a81-112">Aşağıdaki kod örneği başvuru hücrelerinin bildirim ve kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="f9a81-113">Çıktı `50`.</span><span class="sxs-lookup"><span data-stu-id="f9a81-113">The output is `50`.</span></span>

<span data-ttu-id="f9a81-114">Başvuru hücreleri, aşağıdaki şekilde tanımlanan `Ref` genel kayıt türünün örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="f9a81-115">Tür `'a ref` için`Ref<'a>`bir eş anlamlı.</span><span class="sxs-lookup"><span data-stu-id="f9a81-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="f9a81-116">Derleyici ve IDE içindeki IntelliSense, bu tür için ilkini görüntüler fakat temeldeki tanım ikincisidir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="f9a81-117">`ref` İşleci yeni bir başvuru hücresi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9a81-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="f9a81-118">Aşağıdaki kod, `ref` işlecinin bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="f9a81-119">Aşağıdaki tablo başvuru hücresindeki mevcut özellikleri göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="f9a81-120">İşleç, üye veya alan</span><span class="sxs-lookup"><span data-stu-id="f9a81-120">Operator, member, or field</span></span>|<span data-ttu-id="f9a81-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9a81-121">Description</span></span>|<span data-ttu-id="f9a81-122">Tür</span><span class="sxs-lookup"><span data-stu-id="f9a81-122">Type</span></span>|<span data-ttu-id="f9a81-123">Tanım</span><span class="sxs-lookup"><span data-stu-id="f9a81-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="f9a81-124">`!`(başvuru işleci)</span><span class="sxs-lookup"><span data-stu-id="f9a81-124">`!` (dereference operator)</span></span>|<span data-ttu-id="f9a81-125">Temeldeki değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9a81-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="f9a81-126">`:=`(atama işleci)</span><span class="sxs-lookup"><span data-stu-id="f9a81-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="f9a81-127">Temeldeki değeri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="f9a81-128">`ref`işlecinde</span><span class="sxs-lookup"><span data-stu-id="f9a81-128">`ref` (operator)</span></span>|<span data-ttu-id="f9a81-129">Yeni bir başvuru hücresine bir değer kapsüller.</span><span class="sxs-lookup"><span data-stu-id="f9a81-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="f9a81-130">`Value`özelliði</span><span class="sxs-lookup"><span data-stu-id="f9a81-130">`Value` (property)</span></span>|<span data-ttu-id="f9a81-131">Temeldeki değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f9a81-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="f9a81-132">`contents`(kayıt alanı)</span><span class="sxs-lookup"><span data-stu-id="f9a81-132">`contents` (record field)</span></span>|<span data-ttu-id="f9a81-133">Temeldeki değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f9a81-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|

<span data-ttu-id="f9a81-134">Temeldeki değere erişmek için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="f9a81-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="f9a81-135">Başvuru işleci (`!`) tarafından döndürülen değer atanabilir bir değer değil.</span><span class="sxs-lookup"><span data-stu-id="f9a81-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="f9a81-136">Bu nedenle, temel alınan değeri değiştiriyorsanız bunun yerine atama işlecini (`:=`) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="f9a81-137">`Value` Hem özelliği `contents` hem de alanı atanabilir değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="f9a81-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="f9a81-138">Bu nedenle, bunları temeldeki değere ulaşmak ya da onu değiştirmek için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9a81-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="f9a81-139">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f9a81-139">The output is as follows.</span></span>

```console
10
10
11
12
```

<span data-ttu-id="f9a81-140">Alan `contents` , diğer ml sürümleriyle uyumluluk için sağlanır ve derleme sırasında bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9a81-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="f9a81-141">Uyarıyı devre dışı bırakmak için `--mlcompatibility` derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9a81-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="f9a81-142">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="f9a81-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="f9a81-143">C#programcılar `ref` ' de C# ile aynı şeyi `ref` olmadığını bilmelidir. F#</span><span class="sxs-lookup"><span data-stu-id="f9a81-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="f9a81-144">' Deki F# eşdeğer yapılar, başvuru hücrelerinden farklı bir kavram olan [ByRef referanslardır](byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="f9a81-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="f9a81-145">Olarak `mutable`işaretlenen değerler `'a ref` , bir kapanış tarafından yakalanarak otomatik olarak yükseltilebilir; [değerlere](./values/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f9a81-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](./values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9a81-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9a81-146">See also</span></span>

- [<span data-ttu-id="f9a81-147">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9a81-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f9a81-148">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f9a81-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="f9a81-149">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9a81-149">Symbol and Operator Reference</span></span>](./symbol-and-operator-reference/index.md)
- [<span data-ttu-id="f9a81-150">Değerler</span><span class="sxs-lookup"><span data-stu-id="f9a81-150">Values</span></span>](./values/index.md)
