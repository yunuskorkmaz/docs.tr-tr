---
title: Ara değerli dizeler
description: 'Doğrudan içerdikleri F # ifadelerini gömmeyi sağlayan özel bir dize biçimi olan, enterpolasyonlu dizeler hakkında bilgi edinin.'
ms.date: 11/12/2020
ms.openlocfilehash: a49d4e743306fd9bdabb1e019ec4e6c77e0e1f5a
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688610"
---
# <a name="interpolated-strings"></a><span data-ttu-id="aa715-103">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="aa715-103">Interpolated strings</span></span>

<span data-ttu-id="aa715-104">Enterpolasyonlu dizeler, bunlara F # ifadeleri eklemenize olanak sağlayan [dizelerdir](strings.md) .</span><span class="sxs-lookup"><span data-stu-id="aa715-104">Interpolated strings are [strings](strings.md) that allow you to embed F# expressions into them.</span></span> <span data-ttu-id="aa715-105">Bir dizenin değerinin bir değer veya ifadenin sonucuna göre değiştirebildiği çok çeşitli senaryolarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa715-105">They are helpful in a wide range of scenarios where the value of a string may change based on the result of a value or expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa715-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa715-106">Syntax</span></span>

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a><span data-ttu-id="aa715-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa715-107">Remarks</span></span>

<span data-ttu-id="aa715-108">Enterpolasyonlu dizeler, bir dize sabit değerinin içindeki "delikler" içinde kod yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa715-108">Interpolated strings let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="aa715-109">Basit bir örnek verelim:</span><span class="sxs-lookup"><span data-stu-id="aa715-109">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="aa715-110">Her `{}` küme ayracı çifti arasındaki içerikler herhangi bir F # ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="aa715-110">The contents in between each `{}` brace pair can be any F# expression.</span></span>

<span data-ttu-id="aa715-111">Bir `{}` küme ayracı çiftini atlamak için, bunların ikisini de şöyle yazın:</span><span class="sxs-lookup"><span data-stu-id="aa715-111">To escape a `{}` brace pair, write two of them like so:</span></span>

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a><span data-ttu-id="aa715-112">Türü belirlenmiş dizeler</span><span class="sxs-lookup"><span data-stu-id="aa715-112">Typed interpolated strings</span></span>

<span data-ttu-id="aa715-113">Enterpolasyonlu dizeler, türü safey zorlamak için F # biçim belirticilerine de sahiptir.</span><span class="sxs-lookup"><span data-stu-id="aa715-113">Interpolated strings can also have F# format specifiers to enforce type safey.</span></span>

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="aa715-114">Önceki örnekte, kod yanlışlıkla `age` olması gereken değeri yanlışlıkla geçirir `name` ve tam tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aa715-114">In the previous example, the code mistakenly passes the `age` value where `name` should be, and vice/versa.</span></span> <span data-ttu-id="aa715-115">Enterpolasyonlu dizeler biçim belirticileri kullandığından, bu, hafif bir çalışma zamanı hatası yerine bir derleme hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="aa715-115">Because the interpolated strings use format specifiers, this is a compile error instead of a subtle runtime bug.</span></span>

<span data-ttu-id="aa715-116">[Düz metin biçimlendirmesi](plaintext-formatting.md) kapsamındaki tüm biçim belirticileri, enterpolasyonlu bir dizenin içinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aa715-116">All format specifiers covered in [plaintext formatting](plaintext-formatting.md) are valid inside of an interpolated string.</span></span>

## <a name="verbatim-interpolated-strings"></a><span data-ttu-id="aa715-117">Harfine enterpolasyonlu dizeler</span><span class="sxs-lookup"><span data-stu-id="aa715-117">Verbatim interpolated strings</span></span>

<span data-ttu-id="aa715-118">F #, dize sabit değerlerini katıştırabilmeniz için üçlü tırnaklarla birlikte bulunan dizeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="aa715-118">F# supports verbatim interpolated strings with triple quotes so that you can embed string literals.</span></span>

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a><span data-ttu-id="aa715-119">Enterpolasyonlu dizelerde ifadeleri hizalama</span><span class="sxs-lookup"><span data-stu-id="aa715-119">Aligning expressions in interpolated strings</span></span>

<span data-ttu-id="aa715-120">Enterpolasyonlu dizelerin içindeki ifadeleri `|` ve kaç boşluk olduğunu bir belirtim ile sola hizalayabilirsiniz veya sağa hizalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa715-120">You can left-align or right-align expressions inside interpolated strings with `|` and a specification of how many spaces.</span></span> <span data-ttu-id="aa715-121">Aşağıdaki enterpolasyonlu dize sol ve sağ ifadeleri sırasıyla 7 boşlukla sola ve sağa hizalar.</span><span class="sxs-lookup"><span data-stu-id="aa715-121">The following interpolated string aligns the left and right expressions to the left and right, respectively, by 7  spaces.</span></span>

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a><span data-ttu-id="aa715-122">Enterpolasyonlu dizeler ve `FormattableString` biçimlendirmeler</span><span class="sxs-lookup"><span data-stu-id="aa715-122">Interpolated strings and `FormattableString` formatting</span></span>

<span data-ttu-id="aa715-123">Ayrıca, için kurallara uygun biçimlendirme uygulayabilirsiniz <xref:System.FormattableString> :</span><span class="sxs-lookup"><span data-stu-id="aa715-123">You can also apply formatting that adheres to the rules for <xref:System.FormattableString>:</span></span>

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

<span data-ttu-id="aa715-124">Ayrıca, enterpolasyonlu bir dize bir <xref:System.FormattableString> tür ek açıklaması aracılığıyla bir olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="aa715-124">Additionally, an interpolated string can also be typechecked as a <xref:System.FormattableString> via a type annotation:</span></span>

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

<span data-ttu-id="aa715-125">Tür ek açıklamanın, enterpolasyonlu dize ifadesinin kendisinde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aa715-125">Note that the type annotation must be on the interpolated string expression itself.</span></span> <span data-ttu-id="aa715-126">F #, bir enterpolasyonlu dizeyi örtük olarak bir öğesine dönüştürmez <xref:System.FormattableString> .</span><span class="sxs-lookup"><span data-stu-id="aa715-126">F# does not implicitly convert an interpolated string into a <xref:System.FormattableString>.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa715-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa715-127">See also</span></span>

* [<span data-ttu-id="aa715-128">Dizeler</span><span class="sxs-lookup"><span data-stu-id="aa715-128">Strings</span></span>](strings.md)
