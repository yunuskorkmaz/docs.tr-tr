---
title: 'Biçimlendirme yönergelerine F # kodu'
description: 'F # kod biçimlendirme yönergeleri hakkında bilgi edinin.'
ms.date: 05/14/2018
ms.openlocfilehash: 9c6e80509e9a5654e6514674d38c02e2a6b44e37
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734648"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="8ea4e-103">Biçimlendirme yönergelerine F # kodu</span><span class="sxs-lookup"><span data-stu-id="8ea4e-103">F# code formatting guidelines</span></span>

<span data-ttu-id="8ea4e-104">Bu makalede, F # kodu böylece, kodunuzu biçimlendirme için yönergeler sunar:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="8ea4e-105">Genel olarak daha okunaklı görüntülenebilir</span><span class="sxs-lookup"><span data-stu-id="8ea4e-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="8ea4e-106">Visual Studio Araçları ve diğer düzenleyiciler biçimlendirme tarafından uygulanan kuralları uygun olan</span><span class="sxs-lookup"><span data-stu-id="8ea4e-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="8ea4e-107">Benzer şekilde diğer kod çevrimiçi</span><span class="sxs-lookup"><span data-stu-id="8ea4e-107">Similar to other code online</span></span>

<span data-ttu-id="8ea4e-108">Bu kılavuzu temel alan [F # biçimlendirme kuralları kapsamlı bir kılavuz](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) tarafından [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="8ea4e-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="8ea4e-109">Girinti için genel kurallar</span><span class="sxs-lookup"><span data-stu-id="8ea4e-109">General rules for indentation</span></span>

<span data-ttu-id="8ea4e-110">F # önemli boşluk varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-110">F# uses significant white space by default.</span></span> <span data-ttu-id="8ea4e-111">Aşağıdaki yönergeleri Bu getirebilir bazı zorluklar juggle nasıl dair yönergeler sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="8ea4e-112">Alanları kullanma</span><span class="sxs-lookup"><span data-stu-id="8ea4e-112">Using spaces</span></span>

<span data-ttu-id="8ea4e-113">Girinti gerekli olduğunda, boşluk, sekme değil kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="8ea4e-114">En az bir alan gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-114">At least one space is required.</span></span> <span data-ttu-id="8ea4e-115">Kuruluşunuz için Girintileme kullanmak için boşluk sayısını belirtmek için kodlama standartları oluşturabilirsiniz. girinti girinti oluştuğu her düzeyde iki, üç veya dört boşluk tipiktir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="8ea4e-116">**Girinti başına 4 alan öneririz.**</span><span class="sxs-lookup"><span data-stu-id="8ea4e-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="8ea4e-117">Bu, programların girinti öznel bir konudur belirtti.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="8ea4e-118">Değişimleri Tamam, ancak izlemeniz gereken ilk kural *girinti tutarlılığını*.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="8ea4e-119">Genel olarak kabul edilen bir girinti stilini seçin ve kod temelinizde sistematik olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-blank-lines"></a><span data-ttu-id="8ea4e-120">Boş satırlar biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-120">Formatting blank lines</span></span>

* <span data-ttu-id="8ea4e-121">Ayrı en üst düzey işlev ve sınıf tanımları iki boş satırlar.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-121">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="8ea4e-122">Yöntemi tanımları bir sınıf içinde tek bir boş satır tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-122">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="8ea4e-123">Ek boş satırlar (gerektiğinde) ilgili işlev gruplarını birbirinden ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-123">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="8ea4e-124">Boş satırlar bir sürü ilgili one-liners (örneğin, sahte uygulamaları kümesi) arasında atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-124">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="8ea4e-125">Boş satırlar işlevleri'nde gerektiğinde, mantıksal bölümler belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-125">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="8ea4e-126">Açıklamalar Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-126">Formatting comments</span></span>

<span data-ttu-id="8ea4e-127">Genellikle birden çok çift eğik çizgi açıklamalarını derinlikli ML stil bloğu açıklamaları tercih eder.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-127">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="8ea4e-128">Satır içi açıklamalara ilk harfini büyük harfe.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-128">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="8ea4e-129">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="8ea4e-129">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="8ea4e-130">CamelCase sınıfı bağlı, ifade bağlı ve bağlama deseni değerleri ve işlevleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-130">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="8ea4e-131">Genel ve yerel değişkenler olarak veya desen ve işlev tanımları camelCase tüm adlar için kabul edilen F # stili bağlanır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-131">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="8ea4e-132">Yerel olarak bağlı işlevler sınıflardaki camelCase de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-132">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="8ea4e-133">Genel modül bağlı işlevler için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="8ea4e-133">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="8ea4e-134">Bir modül bağlı işlev genel API parçası olduğunda, camelCase kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-134">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="8ea4e-135">İç ve özel modül bağlı değerleri ve işlevleri için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="8ea4e-135">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="8ea4e-136">CamelCase aşağıdakiler dahil olmak üzere özel modül bağlı değerleri için kullanın:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-136">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="8ea4e-137">Komut geçici işlevleri</span><span class="sxs-lookup"><span data-stu-id="8ea4e-137">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="8ea4e-138">Değerleri modülü veya türü iç uygulama yapma</span><span class="sxs-lookup"><span data-stu-id="8ea4e-138">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="8ea4e-139">CamelCase parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-139">Use camelCase for parameters</span></span>

<span data-ttu-id="8ea4e-140">Tüm parametreler camelCase .NET adlandırma kurallarına uygun olarak kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-140">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="8ea4e-141">Modüller için PascalCase kullan</span><span class="sxs-lookup"><span data-stu-id="8ea4e-141">Use PascalCase for modules</span></span>

<span data-ttu-id="8ea4e-142">(Üst düzey, iç, özel, iç içe geçmiş) tüm modülleri PascalCase kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-142">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="8ea4e-143">Tür bildirimleri, üyeleri ve etiketler için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="8ea4e-143">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="8ea4e-144">Sınıfları, arabirimleri, yapılar, numaralandırmalar, temsilciler, kayıtlar ve ayrılmış birleşimler tüm PascalCase ile adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-144">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="8ea4e-145">Üye türleri ve kayıtları ve ayrılmış birleşimler için etiketleri içinde PascalCase de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-145">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="8ea4e-146">.NET için iç yapılar için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="8ea4e-146">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="8ea4e-147">Ad alanları, özel durumlar, olayları ve proje /`.dll` adları PascalCase de kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-147">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="8ea4e-148">Yalnızca bu diğer .NET dilleri tüketicilere daha doğal tüketime yapar, ayrıca karşılaşma olasılığı yüksek olan .NET adlandırma kuralları ile tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-148">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="8ea4e-149">Adları alt çizgi kaçının</span><span class="sxs-lookup"><span data-stu-id="8ea4e-149">Avoid underscores in names</span></span>

<span data-ttu-id="8ea4e-150">Tarihsel olarak, bazı F # kitaplıkları adları alt çizgi kullandınız.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-150">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="8ea4e-151">Kısmen, .NET adlandırma kuralları ile çakışıyor çünkü ancak bu artık yaygın olarak, kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-151">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="8ea4e-152">Bu, bazı F # programcıları alt çizgi yoğun, kısmen geçmiş nedenlerle kullanın ve dayanıklılık ve saygı önemlidir da belirtti.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-152">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="8ea4e-153">Ancak, bir seçeneğiniz mi kullanılacağını hakkında başkaları tarafından stili genellikle yanıtlamadığı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-153">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="8ea4e-154">Bazı özel durumlar, alt çizgi yaygın olduğu yerel bileşenleriyle birlikte içerir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-154">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="8ea4e-155">Standart F # işleçleri kullanma</span><span class="sxs-lookup"><span data-stu-id="8ea4e-155">Use standard F# operators</span></span>

<span data-ttu-id="8ea4e-156">Aşağıdaki işleçleri, F # standart kitaplıkta tanımlanan ve eşdeğerleri tanımlamak yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-156">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="8ea4e-157">Bu kod daha okunabilir ve kullanılan deyimsel bir hale gelir gibi bu işleçleri kullanarak önerilir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-157">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="8ea4e-158">Arka plan OCaml veya işlev başka bir programlama dilinde geliştiricilere, farklı deyimleri için alışkın olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-158">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="8ea4e-159">Aşağıdaki listede, önerilen F # işleçleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-159">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="8ea4e-160">Genel türler için öneki sözdizimini kullanın (`Foo<T>`) sonek söz dizimi yerine (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="8ea4e-160">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="8ea4e-161">F # genel türleri adlandırma iki sonek ML stili devralır (örneğin, `int list`) öneki .NET stili yanı sıra (örneğin, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="8ea4e-161">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="8ea4e-162">.NET stili dört belirli tür dışında tercih et:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-162">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="8ea4e-163">F # listeleri için sonek biçimi kullanın: `int list` yerine `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-163">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="8ea4e-164">F # seçenekleri için sonek biçimi kullanın: `int option` yerine `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-164">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="8ea4e-165">F # diziler için söz dizimi adı kullanmak `int[]` yerine `int array` veya `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-165">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="8ea4e-166">Başvuru hücreleri için kullanmak `int ref` yerine `ref<int>` veya `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-166">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="8ea4e-167">Önek biçimi diğer tüm türleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-167">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="8ea4e-168">Diziler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-168">Formatting tuples</span></span>

<span data-ttu-id="8ea4e-169">Parantez içine alınmış bir tanımlama grubu örneklemesine olmalıdır ve sınırlandırma virgül içinde tek bir boşluk, örneğin gelmelidir: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-169">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="8ea4e-170">Parantez içinde tanımlama desen eşleştirme atlamak için yaygın olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-170">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="8ea4e-171">Ayırt edici birleşim bildirimleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-171">Formatting discriminated union declarations</span></span>

<span data-ttu-id="8ea4e-172">Girinti `|` 4 boşluklarla tür tanımı:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-172">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="8ea4e-173">Ayrılmış birleşimler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-173">Formatting discriminated unions</span></span>

<span data-ttu-id="8ea4e-174">Örneklenen ayrılmış birden çok satırda ayrılmış birleşimler, girinti ile yeni bir kapsam içerdiği veri vermeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-174">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="8ea4e-175">Kapatma parantezinden ayrıca yeni bir satıra olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-175">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="8ea4e-176">Biçimlendirme kayıt bildirimi</span><span class="sxs-lookup"><span data-stu-id="8ea4e-176">Formatting record declarations</span></span>

<span data-ttu-id="8ea4e-177">Girinti `{` türü tanımı tarafından 4 alanları ve alan listesinde aynı satırda başlatın:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-177">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address : string
      City : string
      Zip : string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address : string
    City : string
    Zip : string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
// Unusual in F#
type PostalAddress =
    { 
        Address : string
        City : string
        Zip : string
    }
```

<span data-ttu-id="8ea4e-178">Aynı satırda ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek de ince olmakla birlikte kullanmanız gerektiğini unutmayın [ayrıntılı sözdizimi](../language-reference/verbose-syntax.md) üyelerini tanımlamak için ( `with` anahtar sözcüğü):</span><span class="sxs-lookup"><span data-stu-id="8ea4e-178">Placing the opening token on the same line and the closing token on a new line is also fine, but be aware that you need to use the [verbose syntax](../language-reference/verbose-syntax.md) to define members (the `with` keyword):</span></span>

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address : string
    City : string
    Zip : string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
```

## <a name="formatting-records"></a><span data-ttu-id="8ea4e-179">Kayıtları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-179">Formatting records</span></span>

<span data-ttu-id="8ea4e-180">Kısa kayıtları tek satırda yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-180">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="8ea4e-181">Uzun kayıtları yeni satırlar için etiketleri kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-181">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="8ea4e-182">Aynı satırda ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek da uygundur:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-182">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
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
```

<span data-ttu-id="8ea4e-183">Bu kuralların listesi ve dizi öğeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-183">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="8ea4e-184">Biçimlendirme listeler ve diziler</span><span class="sxs-lookup"><span data-stu-id="8ea4e-184">Formatting lists and arrays</span></span>

<span data-ttu-id="8ea4e-185">Yazma `x :: l` etrafındaki boşlukları ile `::` işleci (`::` dolayısıyla boşluklarla çevrili bir içtakı işleci) ve `[1; 2; 3]` (`;` dolayısıyla ardından bir boşluk, bir sınırlayıcıdır).</span><span class="sxs-lookup"><span data-stu-id="8ea4e-185">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="8ea4e-186">Her zaman en az bir alanı arasında iki farklı küme ayracı gibi işleçler kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-186">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="8ea4e-187">Örneğin, arasına boşluk bırakın bir `[` ve `{`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-187">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="8ea4e-188">Kayıtlar gibi listeler ve birden çok satırda bölme diziler benzer bir kural uygulayın:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-188">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="8ea4e-189">Biçimlendirme IF ifadeleri</span><span class="sxs-lookup"><span data-stu-id="8ea4e-189">Formatting if expressions</span></span>

<span data-ttu-id="8ea4e-190">Koşullular girintilerini bunları oluşturan ifadeler boyutlarını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-190">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="8ea4e-191">Varsa `cond`, `e1` ve `e2` kısa ve basit bunları bir satıra yazın:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-191">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="8ea4e-192">Ya da `cond`, `e1` veya `e2` uzun, ancak çok satırlı değil:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-192">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="8ea4e-193">Herhangi bir ifadenin çok satırlı varsa:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-193">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="8ea4e-194">İle birden çok koşullular `elif` ve `else` aynı kapsamda girintili `if`:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-194">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="8ea4e-195">Desen eşleştirme yapıları</span><span class="sxs-lookup"><span data-stu-id="8ea4e-195">Pattern matching constructs</span></span>

<span data-ttu-id="8ea4e-196">Kullanım bir `|` her bir match yan tümcesinin hiçbir girintilemeli.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-196">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="8ea4e-197">Kısa ifade ise, her alt ifade de basit ise tek bir satırı kullanarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-197">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="8ea4e-198">İfade sağ tarafındaki oka desen çok büyük ise, taşıyabilir girintili bir adımdan aşağıdaki satırı `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-198">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="8ea4e-199">Desen tarafından başlangıç anonim işlev eşleme `function`, genellikle çok Girintile değil.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-199">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="8ea4e-200">Örneğin, bir kapsam şu şekilde girintileme uygundur:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-200">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="8ea4e-201">Desen tarafından tanımlanan İşlevler, `let` veya `let rec` girintili 4 boşluk, başlattıktan sonra olmalıdır `let`bile `function` anahtar sözcüğü kullanılır:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-201">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="8ea4e-202">Oklar hizalama önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-202">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="8ea4e-203">Biçimlendirme bir try / ifadelerle</span><span class="sxs-lookup"><span data-stu-id="8ea4e-203">Formatting try/with expressions</span></span>

<span data-ttu-id="8ea4e-204">Özel durum türüne göre desen girintili aynı düzeyde `with`.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-204">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="8ea4e-205">İşlev parametresi uygulama biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-205">Formatting function parameter application</span></span>

<span data-ttu-id="8ea4e-206">Genel olarak, çoğu işlev parametre uygulama aynı çizgi üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-206">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="8ea4e-207">Yeni bir satıra bir işlev parametreleri uygulamak istiyorsanız, bunları bir kapsama göre Girintile.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-207">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="8ea4e-208">Aynı yönergeleri işlevi bağımsız değişken olarak lambda ifadeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-208">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="8ea4e-209">Bir lambda ifadesinin gövdesi gövdesi başka bir satır varsa bir kapsamla girintili</span><span class="sxs-lookup"><span data-stu-id="8ea4e-209">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="8ea4e-210">Ancak, bir lambda ifadesinin gövdesinin birden fazla satır varsa bunu ayrı bir işleve hesaba katarak göz önünde bulundurun yerine tek bir bağımsız değişken bir işleve uygulanmış bir çok satırlı yapısı vardır.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-210">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="8ea4e-211">Biçimlendirme içtakı işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ea4e-211">Formatting infix operators</span></span>

<span data-ttu-id="8ea4e-212">Boşluklarla ayrı işleçler.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-212">Separate operators by spaces.</span></span> <span data-ttu-id="8ea4e-213">Bu kuralın istisnaları belirgin `!` ve `.` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-213">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="8ea4e-214">İçtakı ifadeler aynı sütunda eklemedir Tamam şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-214">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="8ea4e-215">Ardışık Düzen operatörleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-215">Formatting pipeline operators</span></span>

<span data-ttu-id="8ea4e-216">İşlem hattı `|>` işleçleri, bunlar çalışır ifadeleri altında gitmesini.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-216">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="8ea4e-217">Modüller biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-217">Formatting modules</span></span>

<span data-ttu-id="8ea4e-218">Yerel bir modülde kod göreli modül girintili gerekir, ancak üst düzey bir modülde kod girintili.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-218">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="8ea4e-219">Namespace öğelerini girintili gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-219">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="8ea4e-220">Nesne ifadeleri ve arabirimler biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-220">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="8ea4e-221">Nesne ifadeleri ve arabirimler hizalanmayacak ile aynı şekilde `member` sonra 4 alan girintili.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-221">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="8ea4e-222">Boşluk ifadelerde biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="8ea4e-222">Formatting white space in expressions</span></span>

<span data-ttu-id="8ea4e-223">F # ifadelerini fazlalık bölünemez boşluğu kaçının.</span><span class="sxs-lookup"><span data-stu-id="8ea4e-223">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="8ea4e-224">Adlandırılmış bağımsız değişkenler de olmamalıdır boşluk çevresindeki `=`:</span><span class="sxs-lookup"><span data-stu-id="8ea4e-224">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
