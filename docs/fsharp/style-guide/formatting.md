---
title: F# kod biçimlendirme yönergeleri
description: 'F # kodunu biçimlendirmeye yönelik yönergeleri öğrenin.'
ms.date: 11/04/2019
ms.openlocfilehash: a65600a6c685929aef8582e49caded6340fb09e2
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309709"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="73220-103">F# kod biçimlendirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="73220-103">F# code formatting guidelines</span></span>

<span data-ttu-id="73220-104">Bu makalede, F # kodunuzun olması için kodunuzu biçimlendirme yönergeleri sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="73220-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="73220-105">Daha okunaklı</span><span class="sxs-lookup"><span data-stu-id="73220-105">More legible</span></span>
* <span data-ttu-id="73220-106">Visual Studio ve diğer düzenleyicilerde biçimlendirme araçları tarafından uygulanan kurallara uygun olarak</span><span class="sxs-lookup"><span data-stu-id="73220-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="73220-107">Çevrimiçi diğer koda benzer</span><span class="sxs-lookup"><span data-stu-id="73220-107">Similar to other code online</span></span>

<span data-ttu-id="73220-108">Bu yönergeler, [Anh-Dung Phan](https://github.com/dungpa)tarafından oluşturulan [F # biçimlendirme kurallarına yönelik kapsamlı bir kılavuza](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) dayanır.</span><span class="sxs-lookup"><span data-stu-id="73220-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="73220-109">Girintileme için genel kurallar</span><span class="sxs-lookup"><span data-stu-id="73220-109">General rules for indentation</span></span>

<span data-ttu-id="73220-110">F # varsayılan olarak önemli boşluk kullanır.</span><span class="sxs-lookup"><span data-stu-id="73220-110">F# uses significant white space by default.</span></span> <span data-ttu-id="73220-111">Aşağıdaki kılavuzlar, bu, uygulayabileceğine dair bazı güçlüklerin nasıl ele alınacağını gösteren yönergeler sağlamaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="73220-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="73220-112">Boşluk kullanma</span><span class="sxs-lookup"><span data-stu-id="73220-112">Using spaces</span></span>

<span data-ttu-id="73220-113">Girintileme gerekli olduğunda, sekmeler değil, boşluk kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73220-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="73220-114">En az bir alan gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73220-114">At least one space is required.</span></span> <span data-ttu-id="73220-115">Kuruluşunuz, girintileme için kullanılacak boşluk sayısını belirtmek için kodlama standartları oluşturabilir; her düzeyde girintileme her zamanki iki, üç veya dört boşluk.</span><span class="sxs-lookup"><span data-stu-id="73220-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="73220-116">**Girintileme başına dört boşluk önerilir.**</span><span class="sxs-lookup"><span data-stu-id="73220-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="73220-117">Bu şekilde, programların girintileme öznel bir önemi olur.</span><span class="sxs-lookup"><span data-stu-id="73220-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="73220-118">Çeşitlemeler Tamam, ancak izlemeniz gereken ilk kural *girintileme tutarlılığından*oluşur.</span><span class="sxs-lookup"><span data-stu-id="73220-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="73220-119">Genellikle kabul edilen bir girintileme stili seçin ve kod tabanınızın tamamında sistematik olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="73220-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="73220-120">Boşluk biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-120">Formatting white space</span></span>

<span data-ttu-id="73220-121">F #, boşluk duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-121">F# is white space sensitive.</span></span> <span data-ttu-id="73220-122">Beyaz boşluktan çok sayıda anlambilim doğru girintileme kapsamında olmakla birlikte göz önünde bulundurmanız gereken bazı şeyler vardır.</span><span class="sxs-lookup"><span data-stu-id="73220-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="73220-123">Aritmetik İfadelerdeki biçimlendirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="73220-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="73220-124">Her zaman ikili aritmetik ifadelerin etrafında boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="73220-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="73220-125">Birli `-` işleçler her zaman, yoksayıdıkları değer tarafından hemen izlenir:</span><span class="sxs-lookup"><span data-stu-id="73220-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="73220-126">İşleçten sonra bir boşluk karakteri eklemek, `-` Diğerlerinin karışıklığına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="73220-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="73220-127">Özetle, her zaman için önemlidir:</span><span class="sxs-lookup"><span data-stu-id="73220-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="73220-128">Boşluk ile ikili işleçler çevreleme</span><span class="sxs-lookup"><span data-stu-id="73220-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="73220-129">Birli işleçten sonra hiç bir sondaki boşluk yok</span><span class="sxs-lookup"><span data-stu-id="73220-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="73220-130">İkili aritmetik işleç Kılavuzu özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="73220-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="73220-131">`-`Belirli biçimlendirme seçenekleriyle birleştirildiğinde ikili bir işlecin sarlamaması, tek bir birli olarak yorumlanmasına neden olabilir `-` .</span><span class="sxs-lookup"><span data-stu-id="73220-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="73220-132">Bir özel operatör tanımını boşluk ile çevreleyin</span><span class="sxs-lookup"><span data-stu-id="73220-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="73220-133">Her zaman bir operatör tanımını çevrelemek için boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="73220-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="73220-134">İle başlayan ve birden fazla karakter içeren herhangi bir özel operatör için `*` , bir derleyici belirsizliğini önlemek için tanımın başlangıcına boşluk eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="73220-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="73220-135">Bu nedenle, tek bir boşluk karakteriyle tüm işleçlerin tanımlarını çevrelemeyi öneririz.</span><span class="sxs-lookup"><span data-stu-id="73220-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="73220-136">Boşluk işlevi parametre okları boşluk ile</span><span class="sxs-lookup"><span data-stu-id="73220-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="73220-137">Bir işlevin imzasını tanımlarken, simgenin etrafında boşluk kullanın `->` :</span><span class="sxs-lookup"><span data-stu-id="73220-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="73220-138">Boşluk ile çevreleme işlevi bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="73220-138">Surround function arguments with white space</span></span>

<span data-ttu-id="73220-139">Bir işlevi tanımlarken, her bağımsız değişken etrafında boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="73220-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a><span data-ttu-id="73220-140">Uzun üye tanımları için parametreleri yeni bir satıra yerleştir</span><span class="sxs-lookup"><span data-stu-id="73220-140">Place parameters on a new line for long member definitions</span></span>

<span data-ttu-id="73220-141">Çok uzun bir üye tanımınız varsa, parametreleri yeni satırlara yerleştirip sonraki parametrenin girintileme düzeyiyle eşleşecek şekilde Girintile.</span><span class="sxs-lookup"><span data-stu-id="73220-141">If you have a very long member definition, place the parameters on new lines and indent them to match the indentation level of the subsequent parameter.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(aVeryLongType: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="73220-142">Bu, oluşturucular için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="73220-142">This also applies to constructors:</span></span>

```fsharp
type C(aVeryLongType: AVeryLongTypeThatYouNeedToUse,
       aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse,
       aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

<span data-ttu-id="73220-143">Açık bir dönüş türü ek açıklaması varsa, ya da `)` öncesinde `=` veya yeni bir satırda olabilir.</span><span class="sxs-lookup"><span data-stu-id="73220-143">If there is an explicit return type annotation, it can either be at the end of the `)` and before the `=`, or on a new line.</span></span> <span data-ttu-id="73220-144">Dönüş türünün da uzun bir adı varsa, ikinci durum tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="73220-144">If the return type also has a long name, the latter might be preferable:</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(aVeryLongType: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse)
                                            : AVeryLongReturnType =
        // ... the body of the method follows
```

### <a name="type-annotations"></a><span data-ttu-id="73220-145">Tür ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="73220-145">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="73220-146">Sağ panel işlevi bağımsız değişken türü ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="73220-146">Right-pad function argument type annotations</span></span>

<span data-ttu-id="73220-147">Tür ek açıklamalarıyla bağımsız değişkenler tanımlarken, simgeden sonra boşluk kullanın `:` :</span><span class="sxs-lookup"><span data-stu-id="73220-147">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="73220-148">Boşluk içeren surround dönüş türü ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="73220-148">Surround return type annotations with white space</span></span>

<span data-ttu-id="73220-149">Bir izin-bağlantılı işlevinde veya değer türü ek açıklamasında (bir işlev durumunda dönüş türü), simgeden önce ve sonra boşluk kullanın `:` :</span><span class="sxs-lookup"><span data-stu-id="73220-149">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="73220-150">Boş satırları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-150">Formatting blank lines</span></span>

* <span data-ttu-id="73220-151">En üst düzey işlev ve sınıf tanımlarını iki boş satır ile ayırın.</span><span class="sxs-lookup"><span data-stu-id="73220-151">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="73220-152">Bir sınıf içindeki yöntem tanımları, tek bir boş satırla ayrılır.</span><span class="sxs-lookup"><span data-stu-id="73220-152">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="73220-153">İlgili işlevlerin gruplarını ayırmak için fazladan boş satırlar kullanılabilir (gelişigüzel).</span><span class="sxs-lookup"><span data-stu-id="73220-153">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="73220-154">Bir arada ilgili tek bir grup (örneğin, bir kukla uygulamalar kümesi) arasında boş satırlar atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="73220-154">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="73220-155">Mantıksal bölümleri göstermek için işlevlerde boş satırları gelişigüzel bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="73220-155">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="73220-156">Biçimlendirme açıklamaları</span><span class="sxs-lookup"><span data-stu-id="73220-156">Formatting comments</span></span>

<span data-ttu-id="73220-157">Genellikle, ML stili blok açıklamaları üzerinde birden çok çift eğik açıklama tercih eder.</span><span class="sxs-lookup"><span data-stu-id="73220-157">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="73220-158">Satır içi yorumların ilk harfi büyük harfle yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-158">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="73220-159">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="73220-159">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="73220-160">Sınıf bağlantılı, ifade ile bağlantılı ve kalıp bağlantılı değerler ve işlevler için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-160">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="73220-161">Yerel değişkenler veya kalıp eşleşmeleri ve işlev tanımları ile bağlantılı tüm adlar için camelCase kullanmak için ortak ve kabul edilen F # stili kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73220-161">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="73220-162">Sınıflarda yerel olarak bağlantılı işlevler de camelCase kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-162">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="73220-163">Modül bağlantılı ortak işlevler için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-163">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="73220-164">Modül bağlantılı bir işlev ortak bir API 'nin parçasıysa, camelCase kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="73220-164">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="73220-165">İç ve özel modüle yönelik değerler ve işlevler için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-165">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="73220-166">Aşağıdakiler de dahil olmak üzere, özel modül bağlantılı değerler için camelCase kullanın:</span><span class="sxs-lookup"><span data-stu-id="73220-166">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="73220-167">Betiklerdeki geçici işlevler</span><span class="sxs-lookup"><span data-stu-id="73220-167">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="73220-168">Modül veya türün iç uygulamasını oluşturan değerler</span><span class="sxs-lookup"><span data-stu-id="73220-168">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="73220-169">Parametreler için camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-169">Use camelCase for parameters</span></span>

<span data-ttu-id="73220-170">Tüm parametrelerin, .NET adlandırma kurallarına uygun olarak camelCase kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73220-170">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="73220-171">Modüller için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-171">Use PascalCase for modules</span></span>

<span data-ttu-id="73220-172">Tüm modüller (üst düzey, iç, özel, iç içe) PascalCase kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-172">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="73220-173">Tür bildirimleri, Üyeler ve Etiketler için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-173">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="73220-174">Sınıflar, arabirimler, yapılar, numaralandırmalar, temsilciler, kayıtlar ve ayırt edici birleşimler PascalCase ile adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-174">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="73220-175">Kayıt ve ayrılmış birleşimler için türler ve Etiketler içindeki Üyeler PascalCase de kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-175">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="73220-176">.NET 'e iç yapılar için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-176">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="73220-177">Ad alanları, özel durumlar, olaylar ve proje/ `.dll` adlar PascalCase ' i de kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-177">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="73220-178">Bu, diğer .NET dillerinden gelen tüketimin tüketicilere daha doğal bir fikir sunmasına değil, büyük olasılıkla karşılaşabileceğiniz .NET adlandırma kurallarıyla de tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-178">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="73220-179">Adlarda alt çizgileri önleyin</span><span class="sxs-lookup"><span data-stu-id="73220-179">Avoid underscores in names</span></span>

<span data-ttu-id="73220-180">Tarihsel olarak, bazı F # kitaplıklarında adlarda alt çizgiler kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="73220-180">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="73220-181">Ancak, bu, kısmen kabul edilmez, kısmen de .NET adlandırma kurallarına çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="73220-181">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="73220-182">Yani, bazı F # programcıları büyük ölçüde, kısmen geçmiş nedenlerle alt çizgi kullanır ve tolerans ve saygı önemli öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73220-182">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="73220-183">Bununla birlikte, stilin genellikle onu kullanıp kullanmayacağınızı belirten bir seçeneğe sahip olan diğerlerinin beğenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="73220-183">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="73220-184">Bir özel durum, yerel bileşenlerle birlikte çalışmaya dahildir ve alt çizgilerin ortak olduğu durumdur.</span><span class="sxs-lookup"><span data-stu-id="73220-184">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="73220-185">Standart F # işleçlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-185">Use standard F# operators</span></span>

<span data-ttu-id="73220-186">Aşağıdaki işleçler F # standart kitaplığı 'nda tanımlanmıştır ve eşdeğerleri tanımlamak yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-186">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="73220-187">Bu işleçlerin kullanılması, kodun daha okunaklı ve farklı hale getirme eğilimi için önerilir.</span><span class="sxs-lookup"><span data-stu-id="73220-187">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="73220-188">OCaml veya diğer işlevsel programlama dilinde arka plan içeren geliştiriciler farklı ıoms 'ye alışkın olabilir.</span><span class="sxs-lookup"><span data-stu-id="73220-188">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="73220-189">Aşağıdaki listede önerilen F # işleçleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="73220-189">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="73220-190">`Foo<T>`Tercihe sonek sözdizimi () içinde genel türler () için önek sözdizimini `T Foo` kullanın</span><span class="sxs-lookup"><span data-stu-id="73220-190">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="73220-191">F #, genel türleri (örneğin, `int list` ) ve önek .net stili (örneğin,) adlandırmanın SONEK ml stilini devralır `list<int>` .</span><span class="sxs-lookup"><span data-stu-id="73220-191">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="73220-192">Beş özel tür hariç .NET stilini tercih edin:</span><span class="sxs-lookup"><span data-stu-id="73220-192">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="73220-193">F # listeleri için sonek biçimini kullanın: `int list` yerine `list<int>` .</span><span class="sxs-lookup"><span data-stu-id="73220-193">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="73220-194">F # seçenekleri için sonek biçimini kullanın: `int option` yerine `option<int>` .</span><span class="sxs-lookup"><span data-stu-id="73220-194">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="73220-195">F # değer seçenekleri için sonek biçimini kullanın: `int voption` yerine `voption<int>` .</span><span class="sxs-lookup"><span data-stu-id="73220-195">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="73220-196">F # dizileri için veya yerine sözdizimsel adı kullanın `int[]` `int array` `array<int>` .</span><span class="sxs-lookup"><span data-stu-id="73220-196">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="73220-197">Başvuru hücreleri için `int ref` veya yerine kullanın `ref<int>` `Ref<int>` .</span><span class="sxs-lookup"><span data-stu-id="73220-197">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="73220-198">Diğer tüm türler için önek formunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="73220-198">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="73220-199">Tanımlama gruplarını biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-199">Formatting tuples</span></span>

<span data-ttu-id="73220-200">Tanımlama grubu örneklemesi parantez içine alınmalıdır ve içindeki sınırlandırma virgüller tek bir boşluk gelmelidir, örneğin: `(1, 2)` , `(x, y, z)` .</span><span class="sxs-lookup"><span data-stu-id="73220-200">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="73220-201">Tanımlama gruplarının düzeniyle eşleştirilirken parantezleri atlamak için genellikle kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="73220-201">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="73220-202">Kayıt düzeni bir işlevin dönüş değeri ise ayraçları atlamak için de kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="73220-202">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="73220-203">Özet ' te, parantez içine alınmış demet örneklemeleri tercih eder, ancak kalıp eşleme veya dönüş değeri için tanımlama grupları kullanıldığında, ayraçları önlemek için ince olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="73220-203">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="73220-204">Ayırt edici birleşim bildirimlerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-204">Formatting discriminated union declarations</span></span>

<span data-ttu-id="73220-205">`|`Tür tanımında dört boşlukla Girintile:</span><span class="sxs-lookup"><span data-stu-id="73220-205">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="73220-206">Ayırt edici birleşimleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-206">Formatting discriminated unions</span></span>

<span data-ttu-id="73220-207">Birden çok satıra bölünen oluşturulmuş ayrılmış birleşimler, içerilen verileri girintileme ile yeni bir kapsam olarak vermelidir:</span><span class="sxs-lookup"><span data-stu-id="73220-207">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="73220-208">Kapanış parantezi de yeni bir satır üzerinde olabilir:</span><span class="sxs-lookup"><span data-stu-id="73220-208">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="73220-209">Kayıt bildirimlerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-209">Formatting record declarations</span></span>

<span data-ttu-id="73220-210">`{`Tür tanımında dört boşlukla girinti yapın ve alan listesini aynı satırda başlatın:</span><span class="sxs-lookup"><span data-stu-id="73220-210">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="73220-211">Kayıt üzerinde arabirim uygulamaları veya Üyeler bildirirken, açma belirtecinin yeni bir satıra yerleştirilmesi ve yeni bir satırdaki kapatma belirteci tercih edilir:</span><span class="sxs-lookup"><span data-stu-id="73220-211">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="73220-212">Kayıtları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-212">Formatting records</span></span>

<span data-ttu-id="73220-213">Kısa kayıtlar tek bir satırda yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="73220-213">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="73220-214">Daha uzun olan kayıtlar, Etiketler için yeni satırları kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="73220-214">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="73220-215">Açma belirtecinin yeni bir satıra yerleştirilmesi, bir kapsam üzerinde sekmeli içerikler ve yeni bir satırdaki kapatma belirteci, şu durumlarda tercih edilir:</span><span class="sxs-lookup"><span data-stu-id="73220-215">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="73220-216">Farklı girintileme kapsamları ile koddaki kayıtları taşıma</span><span class="sxs-lookup"><span data-stu-id="73220-216">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="73220-217">Bir işleve boru oluşturma</span><span class="sxs-lookup"><span data-stu-id="73220-217">Piping them into a function</span></span>

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

<span data-ttu-id="73220-218">Liste ve dizi öğeleri için aynı kurallar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="73220-218">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="73220-219">Copy ve Update kayıt ifadelerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-219">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="73220-220">Bir kopyalama ve güncelleştirme kayıt ifadesi hala bir kayıt olduğundan benzer yönergeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="73220-220">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="73220-221">Kısa ifadeler tek bir satıra uygun olabilir:</span><span class="sxs-lookup"><span data-stu-id="73220-221">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="73220-222">Daha uzun ifadeler yeni satırları kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="73220-222">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="73220-223">Kayıt kılavuzunda olduğu gibi, küme ayraçları için ayrı satırlar atamak ve bir kapsamın sağına doğru bir kapsamını girintilemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73220-223">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="73220-224">Parantez olmadan isteğe bağlı bir değeri sarmalama gibi bazı özel durumlarda, bir satır için bir küme ayracı tutmanız gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="73220-224">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="73220-225">Listeleri ve dizileri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-225">Formatting lists and arrays</span></span>

<span data-ttu-id="73220-226">`x :: l`İşlecin etrafında boşluk ile yazın `::` ( `::` Bu nedenle boşluklarla çevrelenmiş bir işleçtir).</span><span class="sxs-lookup"><span data-stu-id="73220-226">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="73220-227">Tek bir satırda tanımlanan liste ve diziler, açma köşeli ayracından sonra ve kapatma parantezinden önce bir boşluk içermelidir:</span><span class="sxs-lookup"><span data-stu-id="73220-227">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="73220-228">Her zaman iki farklı küme ayracı benzeri işleç arasında en az bir boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="73220-228">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="73220-229">Örneğin, ve arasında bir boşluk bırakın `[` `{` .</span><span class="sxs-lookup"><span data-stu-id="73220-229">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="73220-230">Aynı kılavuz, tanımlama gruplarının listeleri veya dizileri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="73220-230">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="73220-231">Birden çok satıra bölünen listeler ve diziler, kayıt olarak benzer bir kuralı izler:</span><span class="sxs-lookup"><span data-stu-id="73220-231">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="73220-232">Kayıtlarda olduğu gibi, açılış ve kapanış köşeli ayracını kendi satırlarıyla birlikte bildirmek, kodun etrafında ve boru işlevlerine daha kolay bir şekilde sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="73220-232">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="73220-233">Program aracılığıyla diziler ve listeler oluştururken, `->` `do ... yield` her zaman bir değer oluşturulduğunda tercih edin:</span><span class="sxs-lookup"><span data-stu-id="73220-233">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="73220-234">F # dilinin, `yield` verilerin koşullu olarak üretilebileceği durumlarda belirtilmesi gerekir veya değerlendirilecek ardışık ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="73220-234">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="73220-235">`yield`Daha eski bir F # dil sürümüyle derlemeniz gerekmedikçe bu anahtar sözcüklerin atlanması tercih edin:</span><span class="sxs-lookup"><span data-stu-id="73220-235">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="73220-236">Bazı durumlarda okunabilirlik konusunda `do...yield` yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="73220-236">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="73220-237">Bu durumlarda, öznel, dikkate alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73220-237">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="73220-238">İfadeleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-238">Formatting if expressions</span></span>

<span data-ttu-id="73220-239">Koşullular girintileme, bunları yapan ifadelerin boyutlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-239">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="73220-240">`cond`, `e1` Ve kısaysa, `e2` bunları tek bir satıra yazmanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="73220-240">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="73220-241">Ya da `cond` `e1` `e2` daha uzunsa ve çok satırlı ise:</span><span class="sxs-lookup"><span data-stu-id="73220-241">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="73220-242">Deyimlerden herhangi biri çok satırlıdır:</span><span class="sxs-lookup"><span data-stu-id="73220-242">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="73220-243">Ve ile birden çok `elif` koşul `else` , ile aynı kapsamda girintilenir `if` :</span><span class="sxs-lookup"><span data-stu-id="73220-243">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="73220-244">Model eşleştirme yapıları</span><span class="sxs-lookup"><span data-stu-id="73220-244">Pattern matching constructs</span></span>

<span data-ttu-id="73220-245">Bir `|` eşleşmenin for each yan tümcesini girintileme olmadan kullanın.</span><span class="sxs-lookup"><span data-stu-id="73220-245">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="73220-246">İfade kısaysa, her alt ifade da basit olduğunda tek bir satır kullanmayı düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73220-246">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="73220-247">Bir düzenin sağ tarafındaki ifade çok büyükse, bu satırı aşağıdaki satıra taşıyın ve ' den bir adım girintilenir `match` / `|` .</span><span class="sxs-lookup"><span data-stu-id="73220-247">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="73220-248">Tarafından başlayan anonim işlevlerin örüntüme göre `function` , genellikle çok uzakta girintisiz.</span><span class="sxs-lookup"><span data-stu-id="73220-248">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="73220-249">Örneğin, bir kapsamı aşağıda gösterildiği gibi girintileme iyi bir şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="73220-249">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="73220-250">Ya da tarafından tanımlanan işlevlerde desenler `let` eşleştirmesi `let rec` `let` , `function` anahtar sözcüğünün kullanılsa bile, başlatıldıktan sonra dört boşluk olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="73220-250">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="73220-251">Okları hizalamayı önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="73220-251">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="73220-252">Try/with ifadelerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-252">Formatting try/with expressions</span></span>

<span data-ttu-id="73220-253">Özel durum türünde model eşleştirme, ile aynı düzeyde girintili olmalıdır `with` .</span><span class="sxs-lookup"><span data-stu-id="73220-253">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="73220-254">İşlev parametresi uygulamasını biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-254">Formatting function parameter application</span></span>

<span data-ttu-id="73220-255">Genellikle, çoğu işlev parametresi uygulaması aynı satırda yapılır.</span><span class="sxs-lookup"><span data-stu-id="73220-255">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="73220-256">Parametreleri yeni bir satırdaki bir işleve uygulamak istiyorsanız, bunları bir kapsama göre girintileyin.</span><span class="sxs-lookup"><span data-stu-id="73220-256">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="73220-257">İşlev bağımsız değişkenleri olarak lambda ifadeleri için de aynı yönergeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="73220-257">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="73220-258">Lambda ifadesinin gövdesi ise, gövde başka bir çizgiye sahip olabilir ve bu da bir kapsama göre girintilenir</span><span class="sxs-lookup"><span data-stu-id="73220-258">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="73220-259">Ancak, bir lambda ifadesinin gövdesi birden fazla satırsa, bir işleve tek bir bağımsız değişken olarak uygulanan çok satırlı bir yapının olması yerine ayrı bir işleve düzenleme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="73220-259">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="73220-260">Hatalı bir şekilde biçimlendirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="73220-260">Formatting infix operators</span></span>

<span data-ttu-id="73220-261">İşleçleri boşluklara göre ayırın.</span><span class="sxs-lookup"><span data-stu-id="73220-261">Separate operators by spaces.</span></span> <span data-ttu-id="73220-262">Bu kuralın belirgin özel durumları `!` ve `.` işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="73220-262">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="73220-263">Indüzeltilme ifadeleri aynı sütundaki sıralama için Tamam:</span><span class="sxs-lookup"><span data-stu-id="73220-263">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="73220-264">Biçimlendirme işlem hattı işleçleri</span><span class="sxs-lookup"><span data-stu-id="73220-264">Formatting pipeline operators</span></span>

<span data-ttu-id="73220-265">`|>`İşlem hattı işleçleri üzerinde çalıştıkları ifadelerin altına gitmelidir.</span><span class="sxs-lookup"><span data-stu-id="73220-265">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="73220-266">Biçimlendirme modülleri</span><span class="sxs-lookup"><span data-stu-id="73220-266">Formatting modules</span></span>

<span data-ttu-id="73220-267">Yerel modüldeki kodun modüle bağlı olması gerekir, ancak üst düzey modüldeki kod girintilenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="73220-267">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="73220-268">Ad alanı öğelerinin girintili olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="73220-268">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="73220-269">Nesne ifadelerini ve arabirimleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-269">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="73220-270">Nesne ifadeleri ve arabirimler, `member` dört boşluktan sonra girintilenmiş şekilde hizalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73220-270">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="73220-271">İfadelerde boşluk biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-271">Formatting white space in expressions</span></span>

<span data-ttu-id="73220-272">F # ifadelerinde gereksiz boşluk kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="73220-272">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="73220-273">Adlandırılmış bağımsız değişkenler de çevreleyen boşluk içermemelidir `=` :</span><span class="sxs-lookup"><span data-stu-id="73220-273">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="73220-274">Biçimlendirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="73220-274">Formatting attributes</span></span>

<span data-ttu-id="73220-275">[Öznitelikler](../language-reference/attributes.md) bir yapının üzerine yerleştirilir:</span><span class="sxs-lookup"><span data-stu-id="73220-275">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="73220-276">Parametrelerde öznitelikleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-276">Formatting attributes on parameters</span></span>

<span data-ttu-id="73220-277">Öznitelikler, parametrelere de yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="73220-277">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="73220-278">Bu durumda, daha sonra parametresiyle aynı satıra ve adından önce yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="73220-278">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="73220-279">Birden çok özniteliği biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-279">Formatting multiple attributes</span></span>

<span data-ttu-id="73220-280">Bir parametre olmayan bir yapı için birden çok öznitelik uygulandığında, her satır için bir öznitelik olması gibi yerleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="73220-280">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="73220-281">Bir parametreye uygulandığında, bunların aynı satırda olmaları ve bir `;` ayırıcıyla ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73220-281">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="73220-282">Sabit değerleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="73220-282">Formatting literals</span></span>

<span data-ttu-id="73220-283">Özniteliği kullanan [F # değişmez değerleri](../language-reference/literals.md) `Literal` özniteliği kendi satırına yerleştirip PascalCase adlandırmayı kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="73220-283">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="73220-284">Özniteliği değeri ile aynı satıra yerleştirmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="73220-284">Avoid placing the attribute on the same line as the value.</span></span>
