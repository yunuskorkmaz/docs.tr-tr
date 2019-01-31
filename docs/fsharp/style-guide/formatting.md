---
title: F#kod biçimlendirme yönergeleri
description: Biçimlendirme kuralları bilgi F# kod.
ms.date: 11/26/2018
ms.openlocfilehash: b80a66f582d9fb8a2ec940ab565823483e7e4eea
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254836"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="760bf-103">F#kod biçimlendirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="760bf-103">F# code formatting guidelines</span></span>

<span data-ttu-id="760bf-104">Bu makalede kod biçimlendirme için yönergeler sunar. böylece, F# kodu:</span><span class="sxs-lookup"><span data-stu-id="760bf-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="760bf-105">Genel olarak daha okunaklı görüntülenebilir</span><span class="sxs-lookup"><span data-stu-id="760bf-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="760bf-106">Visual Studio Araçları ve diğer düzenleyiciler biçimlendirme tarafından uygulanan kuralları uygun olan</span><span class="sxs-lookup"><span data-stu-id="760bf-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="760bf-107">Benzer şekilde diğer kod çevrimiçi</span><span class="sxs-lookup"><span data-stu-id="760bf-107">Similar to other code online</span></span>

<span data-ttu-id="760bf-108">Bu kılavuzu temel alan [kapsamlı bir kılavuz F# biçimlendirme kuralları](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) tarafından [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="760bf-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="760bf-109">Girinti için genel kurallar</span><span class="sxs-lookup"><span data-stu-id="760bf-109">General rules for indentation</span></span>

<span data-ttu-id="760bf-110">F#önemli boşluk, varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="760bf-110">F# uses significant white space by default.</span></span> <span data-ttu-id="760bf-111">Aşağıdaki yönergeleri Bu getirebilir bazı zorluklar juggle nasıl dair yönergeler sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="760bf-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="760bf-112">Alanları kullanma</span><span class="sxs-lookup"><span data-stu-id="760bf-112">Using spaces</span></span>

<span data-ttu-id="760bf-113">Girinti gerekli olduğunda, boşluk, sekme değil kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="760bf-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="760bf-114">En az bir alan gereklidir.</span><span class="sxs-lookup"><span data-stu-id="760bf-114">At least one space is required.</span></span> <span data-ttu-id="760bf-115">Kuruluşunuz için Girintileme kullanmak için boşluk sayısını belirtmek için kodlama standartları oluşturabilirsiniz. girinti girinti oluştuğu her düzeyde iki, üç veya dört boşluk tipiktir.</span><span class="sxs-lookup"><span data-stu-id="760bf-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="760bf-116">**Girinti başına 4 alan öneririz.**</span><span class="sxs-lookup"><span data-stu-id="760bf-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="760bf-117">Bu, programların girinti öznel bir konudur belirtti.</span><span class="sxs-lookup"><span data-stu-id="760bf-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="760bf-118">Değişimleri Tamam, ancak izlemeniz gereken ilk kural *girinti tutarlılığını*.</span><span class="sxs-lookup"><span data-stu-id="760bf-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="760bf-119">Genel olarak kabul edilen bir girinti stilini seçin ve kod temelinizde sistematik olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="760bf-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="760bf-120">Boşluk biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-120">Formatting white space</span></span>

<span data-ttu-id="760bf-121">F#boşluk büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="760bf-121">F# is white space sensitive.</span></span> <span data-ttu-id="760bf-122">Çoğu semantiğe boşluk tarafından uygun girintisini ele alınmaktadır ancak dikkate alınması gereken bazı hususlar vardır.</span><span class="sxs-lookup"><span data-stu-id="760bf-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="760bf-123">Biçimlendirme işleçleri aritmetik ifadelerde</span><span class="sxs-lookup"><span data-stu-id="760bf-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="760bf-124">Her zaman ikili aritmetik ifadeler beyaz boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="760bf-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="760bf-125">Birli `-` işleçleri negating değeri her zaman olmalıdır hemen izleyin:</span><span class="sxs-lookup"><span data-stu-id="760bf-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="760bf-126">Sonra bir boşluk karakteri ekleme `-` işleci diğerleri için Kafa karışıklığına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="760bf-127">Özet olarak, her zaman önemlidir:</span><span class="sxs-lookup"><span data-stu-id="760bf-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="760bf-128">İkili işleçler boşluk ile çevreleyen</span><span class="sxs-lookup"><span data-stu-id="760bf-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="760bf-129">Hiçbir zaman bir birli işleç sonra boşluk sahip</span><span class="sxs-lookup"><span data-stu-id="760bf-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="760bf-130">İkili aritmetik işleç kılavuz özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="760bf-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="760bf-131">Bir ikili kapsamak başarısız olan `-` bazı biçimlendirme seçeneklerini ile birleştirildiğinde işleci, bir tekil yorumlanması için açabilir `-`.</span><span class="sxs-lookup"><span data-stu-id="760bf-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="760bf-132">Boşluk içeren bir özel işleç tanımını çevreleyen</span><span class="sxs-lookup"><span data-stu-id="760bf-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="760bf-133">Her zaman bir işleç tanımını kapsamak için boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="760bf-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="760bf-134">İle başlayan herhangi bir özel işleç için `*`, derleyici belirsizlik önlemek için tanım başlangıcına bir beyaz alanı eklemeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="760bf-134">For any custom operator that starts with `*`, you'll need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="760bf-135">Bu nedenle, yalnızca tek bir boşluk karakteri ile tüm işleçleri tanımlarını çevreleyen önerilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-135">Because of this, it's recommended that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="760bf-136">İşlev parametresi oklar boşluk ile çevreleyen</span><span class="sxs-lookup"><span data-stu-id="760bf-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="760bf-137">Bir işlev imzası tanımlarken, beyaz boşluk kullanmak `->` sembol:</span><span class="sxs-lookup"><span data-stu-id="760bf-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="760bf-138">Boş satırlar biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-138">Formatting blank lines</span></span>

* <span data-ttu-id="760bf-139">Ayrı en üst düzey işlev ve sınıf tanımları iki boş satırlar.</span><span class="sxs-lookup"><span data-stu-id="760bf-139">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="760bf-140">Yöntemi tanımları bir sınıf içinde tek bir boş satır tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="760bf-140">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="760bf-141">Ek boş satırlar (gerektiğinde) ilgili işlev gruplarını birbirinden ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-141">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="760bf-142">Boş satırlar bir sürü ilgili one-liners (örneğin, sahte uygulamaları kümesi) arasında atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-142">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="760bf-143">Boş satırlar işlevleri'nde gerektiğinde, mantıksal bölümler belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="760bf-143">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="760bf-144">Açıklamalar Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-144">Formatting comments</span></span>

<span data-ttu-id="760bf-145">Genellikle birden çok çift eğik çizgi açıklamalarını derinlikli ML stil bloğu açıklamaları tercih eder.</span><span class="sxs-lookup"><span data-stu-id="760bf-145">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="760bf-146">Satır içi açıklamalara ilk harfini büyük harfe.</span><span class="sxs-lookup"><span data-stu-id="760bf-146">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="760bf-147">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="760bf-147">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="760bf-148">CamelCase sınıfı bağlı, ifade bağlı ve bağlama deseni değerleri ve işlevleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="760bf-148">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="760bf-149">Sık karşılaşılan ve kabul edilen F# tüm adları desen veya yerel değişkenler olarak bağlı ve işlev tanımları camelCase stili.</span><span class="sxs-lookup"><span data-stu-id="760bf-149">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="760bf-150">Yerel olarak bağlı işlevler sınıflardaki camelCase de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="760bf-150">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="760bf-151">Genel modül bağlı işlevler için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="760bf-151">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="760bf-152">Bir modül bağlı işlev genel API parçası olduğunda, camelCase kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="760bf-152">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="760bf-153">İç ve özel modül bağlı değerleri ve işlevleri için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="760bf-153">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="760bf-154">CamelCase aşağıdakiler dahil olmak üzere özel modül bağlı değerleri için kullanın:</span><span class="sxs-lookup"><span data-stu-id="760bf-154">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="760bf-155">Komut geçici işlevleri</span><span class="sxs-lookup"><span data-stu-id="760bf-155">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="760bf-156">Değerleri modülü veya türü iç uygulama yapma</span><span class="sxs-lookup"><span data-stu-id="760bf-156">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="760bf-157">CamelCase parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="760bf-157">Use camelCase for parameters</span></span>

<span data-ttu-id="760bf-158">Tüm parametreler camelCase .NET adlandırma kurallarına uygun olarak kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="760bf-158">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="760bf-159">Modüller için PascalCase kullan</span><span class="sxs-lookup"><span data-stu-id="760bf-159">Use PascalCase for modules</span></span>

<span data-ttu-id="760bf-160">(Üst düzey, iç, özel, iç içe geçmiş) tüm modülleri PascalCase kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="760bf-160">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="760bf-161">Tür bildirimleri, üyeleri ve etiketler için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="760bf-161">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="760bf-162">Sınıfları, arabirimleri, yapılar, numaralandırmalar, temsilciler, kayıtlar ve ayrılmış birleşimler tüm PascalCase ile adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="760bf-162">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="760bf-163">Üye türleri ve kayıtları ve ayrılmış birleşimler için etiketleri içinde PascalCase de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="760bf-163">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="760bf-164">.NET için iç yapılar için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="760bf-164">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="760bf-165">Ad alanları, özel durumlar, olayları ve proje /`.dll` adları PascalCase de kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="760bf-165">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="760bf-166">Yalnızca bu diğer .NET dilleri tüketicilere daha doğal tüketime yapar, ayrıca karşılaşma olasılığı yüksek olan .NET adlandırma kuralları ile tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="760bf-166">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="760bf-167">Adları alt çizgi kaçının</span><span class="sxs-lookup"><span data-stu-id="760bf-167">Avoid underscores in names</span></span>

<span data-ttu-id="760bf-168">Tarihsel olarak, bazı F# kitaplıkları adları alt çizgi kullanılan.</span><span class="sxs-lookup"><span data-stu-id="760bf-168">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="760bf-169">Kısmen, .NET adlandırma kuralları ile çakışıyor çünkü ancak bu artık yaygın olarak, kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-169">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="760bf-170">Bununla birlikte, bazı F# programcılar kullanın alt çizgi yoğun, kısmen geçmiş nedenlerle ve dayanıklılık ve saygı önemlidir.</span><span class="sxs-lookup"><span data-stu-id="760bf-170">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="760bf-171">Ancak, bir seçeneğiniz mi kullanılacağını hakkında başkaları tarafından stili genellikle yanıtlamadığı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="760bf-171">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="760bf-172">Bazı özel durumlar, alt çizgi yaygın olduğu yerel bileşenleriyle birlikte içerir.</span><span class="sxs-lookup"><span data-stu-id="760bf-172">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="760bf-173">Kullanım standart F# işleçleri</span><span class="sxs-lookup"><span data-stu-id="760bf-173">Use standard F# operators</span></span>

<span data-ttu-id="760bf-174">Aşağıdaki işleçleri tanımlanan F# standart kitaplığı ve tanımlama eşdeğerleri yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="760bf-174">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="760bf-175">Bu kod daha okunabilir ve kullanılan deyimsel bir hale gelir gibi bu işleçleri kullanarak önerilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-175">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="760bf-176">Arka plan OCaml veya işlev başka bir programlama dilinde geliştiricilere, farklı deyimleri için alışkın olabilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-176">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="760bf-177">Aşağıdaki liste önerilen özetler F# işleçleri.</span><span class="sxs-lookup"><span data-stu-id="760bf-177">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="760bf-178">Genel türler için öneki sözdizimini kullanın (`Foo<T>`) sonek söz dizimi yerine (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="760bf-178">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="760bf-179">F#genel türler adlandırma iki sonek ML stili devralır (örneğin, `int list`) öneki .NET stili yanı sıra (örneğin, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="760bf-179">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="760bf-180">.NET stili dört belirli tür dışında tercih et:</span><span class="sxs-lookup"><span data-stu-id="760bf-180">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="760bf-181">İçin F# listeleri, sonek biçimi kullanın: `int list` yerine `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="760bf-181">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="760bf-182">İçin F# seçenekleri, sonek biçimi kullanın: `int option` yerine `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="760bf-182">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="760bf-183">İçin F# diziler, söz dizimi adı kullanın `int[]` yerine `int array` veya `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="760bf-183">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="760bf-184">Başvuru hücreleri için kullanmak `int ref` yerine `ref<int>` veya `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="760bf-184">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="760bf-185">Önek biçimi diğer tüm türleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="760bf-185">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="760bf-186">Diziler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-186">Formatting tuples</span></span>

<span data-ttu-id="760bf-187">Parantez içine alınmış bir tanımlama grubu örneklemesine olmalıdır ve sınırlandırma virgül içinde tek bir boşluk, örneğin gelmelidir: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="760bf-187">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="760bf-188">Parantez içinde tanımlama desen eşleştirme atlamak için yaygın olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="760bf-188">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="760bf-189">Tanımlama grubu işlevinin dönüş değerini ise parantez atlamak için yaygın olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="760bf-189">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```
<span data-ttu-id="760bf-190">Özet olarak, parantez içine alınmış demet örneklemeleri tercih eder, ancak tanımlama grubu desen eşleştirme veya bir dönüş değeri için kullanılırken, parantez önlemek ince değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-190">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="760bf-191">Ayırt edici birleşim bildirimleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-191">Formatting discriminated union declarations</span></span>

<span data-ttu-id="760bf-192">Girinti `|` 4 boşluklarla tür tanımı:</span><span class="sxs-lookup"><span data-stu-id="760bf-192">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="760bf-193">Ayrılmış birleşimler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-193">Formatting discriminated unions</span></span>

<span data-ttu-id="760bf-194">Örneklenen ayrılmış birden çok satırda ayrılmış birleşimler, girinti ile yeni bir kapsam içerdiği veri vermeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="760bf-194">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="760bf-195">Kapatma parantezinden ayrıca yeni bir satıra olabilir:</span><span class="sxs-lookup"><span data-stu-id="760bf-195">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="760bf-196">Biçimlendirme kayıt bildirimi</span><span class="sxs-lookup"><span data-stu-id="760bf-196">Formatting record declarations</span></span>

<span data-ttu-id="760bf-197">Girinti `{` türü tanımı tarafından 4 alanları ve alan listesinde aynı satırda başlatın:</span><span class="sxs-lookup"><span data-stu-id="760bf-197">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
// Unusual in F#
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="760bf-198">Yeni bir satır ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek arabirim uygulamaları veya üyeleri kaydında bildiriyorsanız preferrable:</span><span class="sxs-lookup"><span data-stu-id="760bf-198">Placing the opening token on a new line and the closing token on a new line is preferrable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="760bf-199">Kayıtları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-199">Formatting records</span></span>

<span data-ttu-id="760bf-200">Kısa kayıtları tek satırda yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="760bf-200">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="760bf-201">Uzun kayıtları yeni satırlar için etiketleri kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="760bf-201">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="760bf-202">Açılış yerleştirme belirteci yeni bir satıra içerikleri üzerinde bir kapsam sekmeli ve yeni bir satıra kapatma belirteci kullanıyorsanız preferrable:</span><span class="sxs-lookup"><span data-stu-id="760bf-202">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferrable if you are:</span></span>

* <span data-ttu-id="760bf-203">Kod girintileme farklı kapsamlarla kayıtları dolaşma</span><span class="sxs-lookup"><span data-stu-id="760bf-203">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="760bf-204">Bir işleve öğesine ekleyerek sorgularınızı</span><span class="sxs-lookup"><span data-stu-id="760bf-204">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }
    
type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="760bf-205">Bu kuralların listesi ve dizi öğeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="760bf-205">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="760bf-206">Biçimlendirme listeler ve diziler</span><span class="sxs-lookup"><span data-stu-id="760bf-206">Formatting lists and arrays</span></span>

<span data-ttu-id="760bf-207">Yazma `x :: l` etrafındaki boşlukları ile `::` işleci (`::` dolayısıyla boşluklarla çevrili bir içtakı işleci).</span><span class="sxs-lookup"><span data-stu-id="760bf-207">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="760bf-208">Liste ve tek bir satıra bildirilen diziler boşlukla ayraç sonra ve kapatma köşeli ayraç önce sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="760bf-208">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="760bf-209">Her zaman en az bir alanı arasında iki farklı küme ayracı gibi işleçler kullanın.</span><span class="sxs-lookup"><span data-stu-id="760bf-209">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="760bf-210">Örneğin, arasına boşluk bırakın bir `[` ve `{`.</span><span class="sxs-lookup"><span data-stu-id="760bf-210">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="760bf-211">Aynı kılavuz listeler veya diziler dizileri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="760bf-211">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="760bf-212">Kayıtlar gibi listeler ve birden çok satırda bölme diziler benzer bir kural uygulayın:</span><span class="sxs-lookup"><span data-stu-id="760bf-212">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="760bf-213">Ve kayıtlarla olduğu gibi açılış ve kapanış köşeli ayraçlar kendi satırında bildirme taşıma kodda gezinmeye ve İşlevler halinde yöneltme kolaylaştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="760bf-213">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="760bf-214">Biçimlendirme IF ifadeleri</span><span class="sxs-lookup"><span data-stu-id="760bf-214">Formatting if expressions</span></span>

<span data-ttu-id="760bf-215">Koşullular girintilerini bunları oluşturan ifadeler boyutlarını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="760bf-215">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="760bf-216">Varsa `cond`, `e1` ve `e2` kısa ve basit bunları bir satıra yazın:</span><span class="sxs-lookup"><span data-stu-id="760bf-216">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="760bf-217">Ya da `cond`, `e1` veya `e2` uzun, ancak çok satırlı değil:</span><span class="sxs-lookup"><span data-stu-id="760bf-217">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="760bf-218">Herhangi bir ifadenin çok satırlı varsa:</span><span class="sxs-lookup"><span data-stu-id="760bf-218">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="760bf-219">İle birden çok koşullular `elif` ve `else` aynı kapsamda girintili `if`:</span><span class="sxs-lookup"><span data-stu-id="760bf-219">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="760bf-220">Desen eşleştirme yapıları</span><span class="sxs-lookup"><span data-stu-id="760bf-220">Pattern matching constructs</span></span>

<span data-ttu-id="760bf-221">Kullanım bir `|` her bir match yan tümcesinin hiçbir girintilemeli.</span><span class="sxs-lookup"><span data-stu-id="760bf-221">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="760bf-222">Kısa ifade ise, her alt ifade de basit ise tek bir satırı kullanarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="760bf-222">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="760bf-223">İfade sağ tarafındaki oka desen çok büyük ise, taşıyabilir girintili bir adımdan aşağıdaki satırı `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="760bf-223">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="760bf-224">Desen tarafından başlangıç anonim işlev eşleme `function`, genellikle çok Girintile değil.</span><span class="sxs-lookup"><span data-stu-id="760bf-224">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="760bf-225">Örneğin, bir kapsam şu şekilde girintileme uygundur:</span><span class="sxs-lookup"><span data-stu-id="760bf-225">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="760bf-226">Desen tarafından tanımlanan İşlevler, `let` veya `let rec` girintili 4 boşluk, başlattıktan sonra olmalıdır `let`bile `function` anahtar sözcüğü kullanılır:</span><span class="sxs-lookup"><span data-stu-id="760bf-226">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="760bf-227">Oklar hizalama önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="760bf-227">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="760bf-228">Biçimlendirme bir try / ifadelerle</span><span class="sxs-lookup"><span data-stu-id="760bf-228">Formatting try/with expressions</span></span>

<span data-ttu-id="760bf-229">Özel durum türüne göre desen girintili aynı düzeyde `with`.</span><span class="sxs-lookup"><span data-stu-id="760bf-229">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="760bf-230">İşlev parametresi uygulama biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-230">Formatting function parameter application</span></span>

<span data-ttu-id="760bf-231">Genel olarak, çoğu işlev parametre uygulama aynı çizgi üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-231">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="760bf-232">Yeni bir satıra bir işlev parametreleri uygulamak istiyorsanız, bunları bir kapsama göre Girintile.</span><span class="sxs-lookup"><span data-stu-id="760bf-232">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="760bf-233">Aynı yönergeleri işlevi bağımsız değişken olarak lambda ifadeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="760bf-233">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="760bf-234">Bir lambda ifadesinin gövdesi gövdesi başka bir satır varsa bir kapsamla girintili</span><span class="sxs-lookup"><span data-stu-id="760bf-234">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="760bf-235">Ancak, bir lambda ifadesinin gövdesinin birden fazla satır varsa bunu ayrı bir işleve hesaba katarak göz önünde bulundurun yerine tek bir bağımsız değişken bir işleve uygulanmış bir çok satırlı yapısı vardır.</span><span class="sxs-lookup"><span data-stu-id="760bf-235">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="760bf-236">Biçimlendirme içtakı işleçleri</span><span class="sxs-lookup"><span data-stu-id="760bf-236">Formatting infix operators</span></span>

<span data-ttu-id="760bf-237">Boşluklarla ayrı işleçler.</span><span class="sxs-lookup"><span data-stu-id="760bf-237">Separate operators by spaces.</span></span> <span data-ttu-id="760bf-238">Bu kuralın istisnaları belirgin `!` ve `.` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="760bf-238">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="760bf-239">İçtakı ifadeler aynı sütunda eklemedir Tamam şunlardır:</span><span class="sxs-lookup"><span data-stu-id="760bf-239">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="760bf-240">Ardışık Düzen operatörleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-240">Formatting pipeline operators</span></span>

<span data-ttu-id="760bf-241">İşlem hattı `|>` işleçleri, bunlar çalışır ifadeleri altında gitmesini.</span><span class="sxs-lookup"><span data-stu-id="760bf-241">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="760bf-242">Modüller biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-242">Formatting modules</span></span>

<span data-ttu-id="760bf-243">Yerel bir modülde kod göreli modül girintili gerekir, ancak üst düzey bir modülde kod girintili.</span><span class="sxs-lookup"><span data-stu-id="760bf-243">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="760bf-244">Namespace öğelerini girintili gerekmez.</span><span class="sxs-lookup"><span data-stu-id="760bf-244">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="760bf-245">Nesne ifadeleri ve arabirimler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-245">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="760bf-246">Nesne ifadeleri ve arabirimler hizalanmayacak ile aynı şekilde `member` sonra 4 alan girintili.</span><span class="sxs-lookup"><span data-stu-id="760bf-246">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="760bf-247">Boşluk ifadelerde biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-247">Formatting white space in expressions</span></span>

<span data-ttu-id="760bf-248">Gereksiz boşluk önlemek F# ifadeler.</span><span class="sxs-lookup"><span data-stu-id="760bf-248">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="760bf-249">Adlandırılmış bağımsız değişkenler de olmamalıdır boşluk çevresindeki `=`:</span><span class="sxs-lookup"><span data-stu-id="760bf-249">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="760bf-250">Biçimlendirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="760bf-250">Formatting attributes</span></span>

<span data-ttu-id="760bf-251">[Öznitelikleri](../language-reference/attributes.md) bir yapısı yerleştirilir:</span><span class="sxs-lookup"><span data-stu-id="760bf-251">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="760bf-252">Parametreleri biçimlendirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="760bf-252">Formatting attributes on parameters</span></span>

<span data-ttu-id="760bf-253">Öznitelikleri parametreleri yerde de olabilir.</span><span class="sxs-lookup"><span data-stu-id="760bf-253">Attributes can also be places on parameters.</span></span> <span data-ttu-id="760bf-254">Bu durumda, aynı satırda parametre adından önce ve sonra yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="760bf-254">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="760bf-255">Birden çok öznitelik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="760bf-255">Formatting multiple attributes</span></span>

<span data-ttu-id="760bf-256">Bir parametre değil bir yapı için birden çok öznitelik uygulandığında, bunlar yok her satıra bir öznitelik olduğunu yerleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="760bf-256">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="760bf-257">Bir parametre uygulandığında, bunlar aynı satırda olmalıdır ve ayrılmış bir `;` ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="760bf-257">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="760bf-258">Biçimlendirme değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="760bf-258">Formatting literals</span></span>

<span data-ttu-id="760bf-259">[F#değişmez değerler](../language-reference/literals.md) kullanarak `Literal` özniteliği öznitelik kendi satırına yerleştirin ve camelCase adlandırma kullanın:</span><span class="sxs-lookup"><span data-stu-id="760bf-259">[F# literals](../language-reference/literals.md) using the `Literal` attribute should should place the attribute on its own line and use camelCase naming:</span></span>

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="760bf-260">Öznitelik değeri ile aynı satırda yerleştirmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="760bf-260">Avoid placing the attribute on the same line as the value.</span></span>
