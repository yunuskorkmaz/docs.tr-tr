---
title: F# kod biçimlendirme yönergeleri
description: F# kodunu biçimlendirme yönergelerini öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 2086b515b8ec9b69a44e2e65ca06fb320670dff2
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278944"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="e7fd3-103">F# kod biçimlendirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e7fd3-103">F# code formatting guidelines</span></span>

<span data-ttu-id="e7fd3-104">Bu makalede, F# kodunuzu şu şekilde biçimlendirecek şekilde kodunuzu biçimlendirecek yönergeler sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="e7fd3-105">Genellikle daha okunaklı olarak görülüyor</span><span class="sxs-lookup"><span data-stu-id="e7fd3-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="e7fd3-106">Visual Studio ve diğer editörlerde biçimlendirme araçları tarafından uygulanan kurallara uygun mudur</span><span class="sxs-lookup"><span data-stu-id="e7fd3-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="e7fd3-107">Çevrimiçi diğer kodlara benzer</span><span class="sxs-lookup"><span data-stu-id="e7fd3-107">Similar to other code online</span></span>

<span data-ttu-id="e7fd3-108">Bu yönergeler, [Anh-Dung Phan'ın](https://github.com/dungpa) [F# Biçimlendirme Sözleşmeleri için kapsamlı bir kılavuza](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="e7fd3-109">Girintinasyon için genel kurallar</span><span class="sxs-lookup"><span data-stu-id="e7fd3-109">General rules for indentation</span></span>

<span data-ttu-id="e7fd3-110">F# varsayılan olarak önemli beyaz boşluk kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-110">F# uses significant white space by default.</span></span> <span data-ttu-id="e7fd3-111">Aşağıdaki yönergeler, bunun dayatabileceği bazı zorlukların nasıl ele aldayılabildiği konusunda rehberlik sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="e7fd3-112">Boşlukları kullanma</span><span class="sxs-lookup"><span data-stu-id="e7fd3-112">Using spaces</span></span>

<span data-ttu-id="e7fd3-113">Girintisi gerektiğinde, sekmeleri değil boşlukları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="e7fd3-114">En az bir boşluk gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-114">At least one space is required.</span></span> <span data-ttu-id="e7fd3-115">Kuruluşunuz girintisi için kullanılacak alan sayısını belirtmek için kodlama standartları oluşturabilir; girintinin oluştuğu her düzeyde iki, üç veya dört girintin boşluk tipiktir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="e7fd3-116">**Girintinasyon başına 4 boşluk öneririz.**</span><span class="sxs-lookup"><span data-stu-id="e7fd3-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="e7fd3-117">Bununla ilgili olarak, programların girintisi öznel bir konudur.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="e7fd3-118">Varyasyonlar tamam, ancak izlemeniz gereken ilk kural *girintinin tutarlılığıdır.*</span><span class="sxs-lookup"><span data-stu-id="e7fd3-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="e7fd3-119">Genel olarak kabul görmüş bir girintin stili seçin ve kod tabanınız boyunca sistematik olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="e7fd3-120">Beyaz alanı biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-120">Formatting white space</span></span>

<span data-ttu-id="e7fd3-121">F# beyaz alana duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-121">F# is white space sensitive.</span></span> <span data-ttu-id="e7fd3-122">Beyaz uzaydan en semantik uygun girinti ile kaplı olmasına rağmen, göz önünde bulundurulması gereken bazı diğer şeyler vardır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="e7fd3-123">İşleçleri aritmetik ifadelerde biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="e7fd3-124">Her zaman ikili aritmetik ifadeler etrafında beyaz boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="e7fd3-125">Unary `-` işleçleri her zaman hemen izleyin negating değeri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="e7fd3-126">Işleci sonra `-` bir beyaz boşluk karakteri ekleme diğerleri için karışıklığa yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="e7fd3-127">Özetle, her zaman önemlidir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="e7fd3-128">İkili operatörleri beyaz alana surround</span><span class="sxs-lookup"><span data-stu-id="e7fd3-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="e7fd3-129">Bir unary işlecinden sonra asla beyaz boşluk yok</span><span class="sxs-lookup"><span data-stu-id="e7fd3-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="e7fd3-130">İkili aritmetik işleç kılavuzu özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="e7fd3-131">Belirli biçimlendirme `-` seçenekleriyle birleştirildiğinde, bir ikili işlecinin çevrelenmemesi, `-`onu unary olarak yorumlamaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="e7fd3-132">Özel bir operatör tanımını beyaz alanla çevrele</span><span class="sxs-lookup"><span data-stu-id="e7fd3-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="e7fd3-133">Operatör tanımını çevreleyen beyaz alanı her zaman kullanın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="e7fd3-134">Birden fazla karakterle `*` başlayan ve birden fazla karaktere sahip olan herhangi bir özel işleç için, derleyici belirsizliğini önlemek için tanımın başına beyaz bir boşluk eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="e7fd3-135">Bu nedenle, tüm operatörlerin tanımlarını tek bir beyaz boşluk karakteriyle çevrelemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="e7fd3-136">Surround fonksiyon parametre okları ile beyaz boşluk</span><span class="sxs-lookup"><span data-stu-id="e7fd3-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="e7fd3-137">Bir işlevin imzasını tanımlarken, sembolün `->` etrafındaki beyaz boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="e7fd3-138">Beyaz boşluklu surround işlev bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e7fd3-138">Surround function arguments with white space</span></span>

<span data-ttu-id="e7fd3-139">Bir işlev tanımlarken, her bağımsız değişkenin etrafında beyaz boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-very-long-member-definitions"></a><span data-ttu-id="e7fd3-140">Çok uzun üye tanımları için parametreleri yeni bir satıra yerleştirin</span><span class="sxs-lookup"><span data-stu-id="e7fd3-140">Place parameters on a new line for very long member definitions</span></span>

<span data-ttu-id="e7fd3-141">Çok uzun bir üye tanımınız varsa, parametreleri yeni satırlara yerleştirin ve bunları bir kapsam girin.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="e7fd3-142">Bu, yapıcılar için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="e7fd3-143">Ek açıklamalar yazın</span><span class="sxs-lookup"><span data-stu-id="e7fd3-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="e7fd3-144">Sağ pad işlev bağımsız değişken türü ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="e7fd3-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="e7fd3-145">Tür ek açıklamaları ile bağımsız değişkenleri tanımlarken, simgeden `:` sonra beyaz boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="e7fd3-146">Beyaz boşluklu surround dönüş türü ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="e7fd3-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="e7fd3-147">Let-bound işleviveya değer türü ek açıklama (bir işlev durumunda dönüş türü), `:` önce ve sonra sembol beyaz boşluk kullanın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="e7fd3-148">Boş satırları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-148">Formatting blank lines</span></span>

* <span data-ttu-id="e7fd3-149">Üst düzey işlevi ve sınıf tanımlarını iki boş satırla ayırın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="e7fd3-150">Bir sınıf içindeki yöntem tanımları tek bir boş satırla ayrılır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="e7fd3-151">İlgili işlev gruplarını ayırmak için ekstra boş satırlar (seyrek) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="e7fd3-152">Boş satırlar, bir grup ilgili tek gömlekli (örneğin, bir dizi kukla uygulama) arasında atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="e7fd3-153">Mantıksal bölümleri belirtmek için işlevlerde boş çizgiler kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="e7fd3-154">Açıklamaları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-154">Formatting comments</span></span>

<span data-ttu-id="e7fd3-155">Genellikle ML tarzı blok yorumlar üzerinde birden fazla çift eğik çizgi yorum tercih edin.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="e7fd3-156">Satır satırlı yorumlar ilk harfi büyük harfle yazmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="e7fd3-157">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e7fd3-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="e7fd3-158">Sınıfa bağlı, ifadeye bağlı ve desene bağlı değerler ve işlevler için camelCase'i kullanın</span><span class="sxs-lookup"><span data-stu-id="e7fd3-158">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="e7fd3-159">Yerel değişkenler olarak bağlanan tüm adlar için veya desen eşleşmeleri ve işlev tanımlarında camelCase kullanmak yaygın ve kabul edilen F# stilidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="e7fd3-160">Sınıflarda yerel olarak bağlanan fonksiyonlar da camelCase kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-160">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="e7fd3-161">Modüle bağlı ortak işlevler için camelCase'i kullanın</span><span class="sxs-lookup"><span data-stu-id="e7fd3-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="e7fd3-162">Modüle bağlı bir işlev genel API'nin bir parçasıysa, camelCase'i kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="e7fd3-163">Dahili ve özel modüle bağlı değerler ve fonksiyonlar için camelCase'i kullanın</span><span class="sxs-lookup"><span data-stu-id="e7fd3-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="e7fd3-164">Aşağıdakiler de dahil olmak üzere özel modüle bağlı değerler için camelCase'i kullanın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="e7fd3-165">Komut dosyalarındaki geçici işlevler</span><span class="sxs-lookup"><span data-stu-id="e7fd3-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="e7fd3-166">Bir modülün veya türün iç uygulamasını oluşturan değerler</span><span class="sxs-lookup"><span data-stu-id="e7fd3-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="e7fd3-167">Parametreler için camelCase'i kullanın</span><span class="sxs-lookup"><span data-stu-id="e7fd3-167">Use camelCase for parameters</span></span>

<span data-ttu-id="e7fd3-168">Tüm parametreler .NET adlandırma kurallarına uygun olarak camelCase kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="e7fd3-169">Modüller için PascalCase'i kullanma</span><span class="sxs-lookup"><span data-stu-id="e7fd3-169">Use PascalCase for modules</span></span>

<span data-ttu-id="e7fd3-170">Tüm modüller (üst düzey, iç, özel, iç içe) PascalCase kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="e7fd3-171">Tür bildirimleri, üyeler ve etiketler için PascalCase'i kullanın</span><span class="sxs-lookup"><span data-stu-id="e7fd3-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="e7fd3-172">Sınıflar, arabirimler, structs, sayısallaştırmalar, temsilciler, kayıtlar ve ayrımcı sendikalar tüm PascalCase ile adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="e7fd3-173">Kayıtlar ve ayrımcı sendikalar için tür ve etiketler deki üyeler de PascalCase kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="e7fd3-174">.NET'e özgü yapılar için PascalCase'i kullanın</span><span class="sxs-lookup"><span data-stu-id="e7fd3-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="e7fd3-175">Ad alanları, özel durumlar, olaylar`.dll` ve proje/ adlar da PascalCase kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="e7fd3-176">Bu, diğer .NET dillerinden gelen tüketimi tüketiciler için daha doğal hale getirmekle kalmıyor, aynı zamanda karşılaşma olasılığınız olan .NET adlandırma kurallarıyla da tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="e7fd3-177">Adlarda alt çizerlerden kaçının</span><span class="sxs-lookup"><span data-stu-id="e7fd3-177">Avoid underscores in names</span></span>

<span data-ttu-id="e7fd3-178">Tarihsel olarak, bazı F# kitaplıkları adlarda alt çizerler kullanabilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="e7fd3-179">Ancak, kısmen .NET adlandırma kurallarıyla çakıştığı için bu artık yaygın olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="e7fd3-180">Bununla ilgili olarak, bazı F# programcıları kısmen tarihsel nedenlerden dolayı vurguları yoğun bir şekilde kullanırlar ve hoşgörü ve saygı önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="e7fd3-181">Ancak, stilgenellikle kullanmak için bir seçim var başkaları tarafından sevilmeyen olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="e7fd3-182">Bazı özel durumlar, alt çizlerin çok yaygın olduğu yerel bileşenlerle birlikte çalışmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-182">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="e7fd3-183">Standart F# işleçlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="e7fd3-183">Use standard F# operators</span></span>

<span data-ttu-id="e7fd3-184">Aşağıdaki işleçler F# standart kitaplığında tanımlanır ve eşdeğerleri tanımlamak yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="e7fd3-185">Kodu daha okunabilir ve deyimsel hale getirme eğiliminde olduğundan, bu işleçlerin kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="e7fd3-186">OCaml veya diğer işlevsel programlama dilinde bir arka plan geliştiriciler farklı deyimler alışkın olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="e7fd3-187">Aşağıdaki liste önerilen F# işleçlerini özetler.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="e7fd3-188">Genel ek sözdizimi (`Foo<T>`) için önek sözdizimini (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="e7fd3-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="e7fd3-189">F# hem genel adlandırma nın ML postfix stilini `int list`(örneğin,) hem de .NET stilini (örneğin) `list<int>`devralır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="e7fd3-190">Beş özel tür dışında .NET stilini tercih edin:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="e7fd3-191">F# Listeleri için, postfix `int list` formunu `list<int>`kullanın: yerine .</span><span class="sxs-lookup"><span data-stu-id="e7fd3-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="e7fd3-192">F# Seçenekleri için, postfix `int option` formunu `option<int>`kullanın: yerine .</span><span class="sxs-lookup"><span data-stu-id="e7fd3-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="e7fd3-193">F# Değer Seçenekleri için, postfix `int voption` formunu `voption<int>`kullanın: yerine .</span><span class="sxs-lookup"><span data-stu-id="e7fd3-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="e7fd3-194">F# dizileri için, sintaktik adı `int[]` kullanmak yerine `int array` veya `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="e7fd3-195">Referans Hücreler için, `ref<int>` yerine `Ref<int>`kullanın `int ref` veya .</span><span class="sxs-lookup"><span data-stu-id="e7fd3-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="e7fd3-196">Diğer tüm türler için önek formunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="e7fd3-197">Biçimlendirme tuples</span><span class="sxs-lookup"><span data-stu-id="e7fd3-197">Formatting tuples</span></span>

<span data-ttu-id="e7fd3-198">Bir tuple instantiation parantez ve içinde delimiting virgül tek bir boşluk tarafından takip `(1, 2)` `(x, y, z)`edilmelidir, örneğin: , .</span><span class="sxs-lookup"><span data-stu-id="e7fd3-198">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="e7fd3-199">Tuples desen eşleşen parantez atlamak için yaygın olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="e7fd3-200">Tuple bir fonksiyonun geri dönüş değeri ise, parantez ibareleri atlamak da yaygın olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="e7fd3-201">Özetle, parantez anlık değerlerini tercih edin, ancak desen eşleştirmesi veya geri dönüş değeri için tuples kullanırken, parantezlerden kaçınmak iyi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="e7fd3-202">Ayrımcı birlik bildirimlerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="e7fd3-203">4 boşlukla tür tanımında girintis: `|`</span><span class="sxs-lookup"><span data-stu-id="e7fd3-203">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="e7fd3-204">Ayrımcı sendikaları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-204">Formatting discriminated unions</span></span>

<span data-ttu-id="e7fd3-205">Birden çok satıra bölünmüş anında Ayrılmış Ayırmalı Sendikalar, içerdiği verileri girintisi içeren yeni bir kapsam vermelidir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="e7fd3-206">Kapanış parantezi de yeni bir satırda olabilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="e7fd3-207">Kayıt bildirimlerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-207">Formatting record declarations</span></span>

<span data-ttu-id="e7fd3-208">4 boşluk `{` la tür tanımı girintisi ve aynı satırda alan listesini başlatın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-208">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="e7fd3-209">Açıkara belirteci yeni bir satıra, kapanış jetonunu da yeni bir satıra yerleştirme, arabirim uygulamalarını veya üyeleri kayda dahil ediyorsanız tercih edilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

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

## <a name="formatting-records"></a><span data-ttu-id="e7fd3-210">Kayıtları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-210">Formatting records</span></span>

<span data-ttu-id="e7fd3-211">Kısa kayıtlar tek satırda yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="e7fd3-212">Daha uzun olan kayıtlar etiketler için yeni satırlar kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="e7fd3-213">Açılış belirteci yeni bir satıra yerleştirilme, içeriği tek bir kapsam üzerinde sekmeli ve yeni bir satırdaki kapanış belirteci aşağıdakiler varsa tercih edilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="e7fd3-214">Kayıtları farklı girinti kapsamları ile kod içinde taşıma</span><span class="sxs-lookup"><span data-stu-id="e7fd3-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="e7fd3-215">Onları bir fonksiyona dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-215">Piping them into a function</span></span>

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

<span data-ttu-id="e7fd3-216">Liste ve dizi öğeleri için de aynı kurallar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="e7fd3-217">Kayıt ifadelerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="e7fd3-218">Kopyala ve güncelleştir kayıt ifadesi hala bir kayıttır, bu nedenle benzer yönergeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="e7fd3-219">Kısa ifadeler tek bir satıra sığabilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="e7fd3-220">Daha uzun ifadeler yeni satırlar kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="e7fd3-221">Ve kayıt kılavuzunda olduğu gibi, ayraçlar için ayrı satırlar ayırmak isteyebilirsiniz ve girinti bir kapsam ifade ile sağa.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="e7fd3-222">Bazı özel durumlarda, örneğin bir değeri parantez olmadan isteğe bağlı olarak sarmalamak gibi, bir ayraç'ı tek bir satırda tutmanız gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-222">Note that in some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="e7fd3-223">Listeleri ve dizileri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-223">Formatting lists and arrays</span></span>

<span data-ttu-id="e7fd3-224">Işlecinin `x :: l` `::` etrafındaki boşluklarla yazın (bir`::` infix işlecidir, dolayısıyla boşluklarla çevrilidir).</span><span class="sxs-lookup"><span data-stu-id="e7fd3-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="e7fd3-225">Tek bir satırda bildirilen liste ve dizilerin açılış ayracından sonra ve kapanış ayracından önce bir boşluk olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="e7fd3-226">Her zaman iki farklı ayraç benzeri işleçler arasında en az bir boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="e7fd3-227">Örneğin, bir ve bir `[` `{`arasında bir boşluk bırakın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="e7fd3-228">Aynı kılavuz listeler veya tuples dizileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="e7fd3-229">Birden çok satıra bölünmüş listeler ve diziler, kayıtlar gibi benzer bir kural izler:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="e7fd3-230">Ve kayıtlarda olduğu gibi, açma ve kapama parantezini kendi satırlarında bildirmek kodu niçin hareket ettireceğini ve işlevlerin içine girmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="e7fd3-231">Diziler oluştururken ve programlı listelerken, bir değer her zaman oluşturulduğunda `->` tercih `do ... yield` edin:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

<span data-ttu-id="e7fd3-232">F# dilinin eski sürümlerinde, verilerin koşullu olarak oluşturulabileceği veya değerlendirilecek ardışık ifadeler olabileceği durumlarda belirtilmesi `yield` gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="e7fd3-233">Eski bir F# dili sürümüyle derlemeniz gerekiyorsa, bu `yield` anahtar kelimeleri atlayış etmeyi tercih edin:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

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

<span data-ttu-id="e7fd3-234">Bazı durumlarda, `do...yield` okunabilirlik yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="e7fd3-235">Bu olgular, öznel de olsa, dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="e7fd3-236">İfadeler varsa biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-236">Formatting if expressions</span></span>

<span data-ttu-id="e7fd3-237">Koşullu ların girintisi, onları oluşturan ifadelerin boyutlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="e7fd3-238">Eğer `cond` `e1` , `e2` ve kısa, sadece bir satırda bunları yazın:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="e7fd3-239">Ya `cond`, `e1` `e2` veya uzun, ancak çok satırlı değil:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="e7fd3-240">İfadelerden herhangi biri çok satırlıysa:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="e7fd3-241">Birden fazla koşullu ile `elif` ve `else` aynı kapsamda `if`girintisi:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="e7fd3-242">Desen eşleştirme yapıları</span><span class="sxs-lookup"><span data-stu-id="e7fd3-242">Pattern matching constructs</span></span>

<span data-ttu-id="e7fd3-243">Girintisi olmayan bir eşleşmenin her yan tümcesi için a `|` kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="e7fd3-244">İfade kısaysa, her alt ifade de basitse tek bir satır kullanmayı düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="e7fd3-245">Desen eşleşen okun sağındaki ifade çok büyükse, aşağıdaki satıra taşıyın, girindi bir adım . `match` / `|`</span><span class="sxs-lookup"><span data-stu-id="e7fd3-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="e7fd3-246">Anonim işlevlerin desen eşleştirme, başlayarak `function`, genellikle çok fazla girintisi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="e7fd3-247">Örneğin, bir kapsamı aşağıdaki gibi girintisi gayet iyi:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="e7fd3-248">Anahtar `let` kelime kullanılsa `let rec` `let` `function` bile, başladıktan sonra 4 boşluk tarafından tanımlanan veya girintisi gereken işlevlerde desen eşleştirme:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-248">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="e7fd3-249">Okları hizalamanızı önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="e7fd3-250">Try/with ifadelerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-250">Formatting try/with expressions</span></span>

<span data-ttu-id="e7fd3-251">Özel durum türünde desen eşlemesi `with`.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="e7fd3-252">Biçimlendirme fonksiyonu parametre uygulaması</span><span class="sxs-lookup"><span data-stu-id="e7fd3-252">Formatting function parameter application</span></span>

<span data-ttu-id="e7fd3-253">Genel olarak, çoğu işlev parametre uygulaması aynı satırda yapılır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="e7fd3-254">Parametreleri yeni bir satırdaki bir işleve uygulamak istiyorsanız, bunları tek bir kapsamla girin.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="e7fd3-255">Aynı kurallar işlev bağımsız değişkenleri olarak lambda ifadeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="e7fd3-256">Bir lambda ifadesinin gövdesi ise, vücut başka bir çizgi olabilir, bir kapsam tarafından girintisi</span><span class="sxs-lookup"><span data-stu-id="e7fd3-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="e7fd3-257">Ancak, bir lambda ifadesinin gövdesi birden fazla satırsa, bir işleve tek bir bağımsız değişken olarak uygulanan çok satırlı bir yapı yerine onu ayrı bir işleve ayırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="e7fd3-258">Ekiş işleçlerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-258">Formatting infix operators</span></span>

<span data-ttu-id="e7fd3-259">Boşluklara göre ayrı işleçler.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-259">Separate operators by spaces.</span></span> <span data-ttu-id="e7fd3-260">Bu kuralın bariz `!` istisnaları `.` ve işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="e7fd3-261">Ekek ifadeleri aynı sütunda sıraya tamam:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="e7fd3-262">Boru hattı operatörlerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-262">Formatting pipeline operators</span></span>

<span data-ttu-id="e7fd3-263">Boru `|>` hattı operatörleri üzerinde çalıştıkları ifadelerin altına girmelidir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="e7fd3-264">Modülleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-264">Formatting modules</span></span>

<span data-ttu-id="e7fd3-265">Yerel bir modüldeki kod modüle göre girintisi olmalıdır, ancak üst düzey bir modüldeki kod girintinolmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="e7fd3-266">Ad alanı öğeleri girintisi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-266">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="e7fd3-267">Nesne ifadelerini ve arabirimlerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="e7fd3-268">Nesne ifadeleri ve arabirimleri 4 boşluktan sonra `member` girintilen ile aynı şekilde hizalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="e7fd3-269">İfadelerde beyaz alanı biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-269">Formatting white space in expressions</span></span>

<span data-ttu-id="e7fd3-270">F# ifadelerinde gereksiz beyaz boşluktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="e7fd3-271">Adlandırılmış bağımsız değişkenler de `=`çevreleyen boşluk olmamalıdır:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="e7fd3-272">Öznitelikleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-272">Formatting attributes</span></span>

<span data-ttu-id="e7fd3-273">[Öznitelikler](../language-reference/attributes.md) bir yapının üzerine yerleştirilir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="e7fd3-274">Parametrelere öznitelikleri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="e7fd3-275">Öznitelikler de parametreler üzerinde yer olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-275">Attributes can also be places on parameters.</span></span> <span data-ttu-id="e7fd3-276">Bu durumda, parametre ile aynı satıra ve addan önce yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="e7fd3-277">Birden çok özniteliği biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-277">Formatting multiple attributes</span></span>

<span data-ttu-id="e7fd3-278">Parametre olmayan bir yapıya birden çok öznitelik uygulandığında, satır başına bir öznitelik olacak şekilde yerleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="e7fd3-279">Bir parametreye uygulandığında, aynı satırda olmalı ve `;` ayırıcı ile ayrılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="e7fd3-280">Gerçek anlamları biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fd3-280">Formatting literals</span></span>

<span data-ttu-id="e7fd3-281">Özniteliği kullanan `Literal` [F# literals](../language-reference/literals.md) özniteliği kendi satırına yerleştirmeli ve PascalCase adlandırmasını kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e7fd3-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="e7fd3-282">Özniteliği değerle aynı satıra yerleştirmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="e7fd3-282">Avoid placing the attribute on the same line as the value.</span></span>
