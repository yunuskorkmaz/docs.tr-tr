---
title: Ad Alanları
description: Bilgi nasıl bir F# ad alanı, program öğeleri gruplandırması için bir ad eklemek sağlayarak ilgili işlevleri alanlarına kodunu düzenlemenize olanak sağlar.
ms.date: 12/08/2018
ms.openlocfilehash: 526d7a07e4804751811c15fa91b0c74c1954d591
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666397"
---
# <a name="namespaces"></a><span data-ttu-id="28dfb-103">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="28dfb-103">Namespaces</span></span>

<span data-ttu-id="28dfb-104">Bir ad alanı gruplandırması için bir ad eklemek sağlayarak, ilgili işlevleri alanlarına kod düzenlemenize olanak tanır F# program öğeleri.</span><span class="sxs-lookup"><span data-stu-id="28dfb-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="28dfb-105">Ad alanları, genellikle üst düzey öğe içinde F# dosyaları.</span><span class="sxs-lookup"><span data-stu-id="28dfb-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="28dfb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28dfb-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="28dfb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28dfb-107">Remarks</span></span>

<span data-ttu-id="28dfb-108">Bir ad alanında kod koymak istiyorsanız, ilk bildirimi dosyasındaki ad alanı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="28dfb-109">Tüm dosya içeriğini, ad alanı bir parçası haline gelir, diğer ad bildirimi var sağlanan dosyasında daha fazla.</span><span class="sxs-lookup"><span data-stu-id="28dfb-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="28dfb-110">Bu durumda, sonraki ad alanı bildirimi gönderinizi tüm kod ilk ad alanı içinde olacak şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="28dfb-111">Ad alanları, doğrudan değerleri ve işlevler içeremez.</span><span class="sxs-lookup"><span data-stu-id="28dfb-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="28dfb-112">Bunun yerine, değerleri ve işlevleri modüllerde eklenmelidir, ve modülleri ad alanlarında yer alır.</span><span class="sxs-lookup"><span data-stu-id="28dfb-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="28dfb-113">Ad alanlarını, türleri, modülleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="28dfb-114">XML belge açıklamaları bir ad alanı bildirilebilir, ancak bunlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="28dfb-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="28dfb-115">Derleyici yönergeleri bir ad alanı da bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="28dfb-116">Ad alanları açıkça ad alanı anahtar sözcüğüyle veya örtük olarak bir modül bildirirken bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="28dfb-117">Bir ad alanını açıkça bildirmek için ad alanı adından önce gelen ad alanı anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="28dfb-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="28dfb-118">Aşağıdaki örnek, bir ad alanını tanımlayan bir kod dosyası gösterir. `Widgets` ile ve o ad alanında bulunan bir modül türü.</span><span class="sxs-lookup"><span data-stu-id="28dfb-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="28dfb-119">Dosyanın tüm içeriğini bir modülde varsa, ayrıca ad alanlarında örtülü olarak kullanarak bildirebilirsiniz `module` anahtar sözcüğü ve tam modül adı yeni ad alanı adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="28dfb-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="28dfb-120">Aşağıdaki örnek, bir ad alanını tanımlayan bir kod dosyası gösterir. `Widgets` ve modül `WidgetsModule`, bir işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="28dfb-121">Aşağıdaki kod, önceki koda eşdeğerdir, ancak bir yerel modül bildirimi modülüdür.</span><span class="sxs-lookup"><span data-stu-id="28dfb-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="28dfb-122">Bu durumda, ad alanı, kendi satırında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="28dfb-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="28dfb-123">Aynı dosyada bir veya daha fazla ad alanlarında birden fazla modülü gerekiyorsa, yerel modül bildirimlerinde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="28dfb-124">Yerel modül bildirimlerinde kullandığınızda, tam ad alanı, modül bildirimlerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="28dfb-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="28dfb-125">Aşağıdaki kod, bir ad alanı bildirimi ve iki yerel modül bildirimi içeren bir dosya gösterir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="28dfb-126">Bu durumda, modülleri doğrudan ad alanında bulunan; dosyayla aynı ada sahip hiçbir örtük olarak oluşturulmuş modülü yoktur.</span><span class="sxs-lookup"><span data-stu-id="28dfb-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="28dfb-127">Diğer kod dosyasında aşağıdaki gibi bir `do` modülü üye nitelemek gereken bağlama, ad alanında ancak iç modülleri olduğundan `widgetFunction` kullanarak modül adı.</span><span class="sxs-lookup"><span data-stu-id="28dfb-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="28dfb-128">Bu örnek çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="28dfb-129">Daha fazla bilgi için [modülleri](modules.md).</span><span class="sxs-lookup"><span data-stu-id="28dfb-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="28dfb-130">İç içe geçmiş ad alanları</span><span class="sxs-lookup"><span data-stu-id="28dfb-130">Nested Namespaces</span></span>

<span data-ttu-id="28dfb-131">Bir iç içe geçmiş ad alanı oluşturduğunuzda, tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="28dfb-132">Aksi takdirde, yeni bir üst düzey ad alanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28dfb-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="28dfb-133">Girinti ad alanı bildirimi göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="28dfb-134">Aşağıdaki örnek, bir iç içe geçmiş ad alanı bildirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="28dfb-135">Dosyaları ve derlemeleri ad alanları</span><span class="sxs-lookup"><span data-stu-id="28dfb-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="28dfb-136">Ad alanları, birden çok dosyayı tek bir proje veya derleme yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="28dfb-137">Terim *ad alanı parça* bir dosyada bulunan bir ad alanı parçası açıklar.</span><span class="sxs-lookup"><span data-stu-id="28dfb-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="28dfb-138">Ad alanları, birden çok bütünleştirilmiş koda da yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="28dfb-139">Örneğin, `System` çoğu derleme yayılan ve çoğu iç içe ad alanlarını içeren tüm .NET Framework, ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="28dfb-140">Genel Namespace</span><span class="sxs-lookup"><span data-stu-id="28dfb-140">Global Namespace</span></span>

<span data-ttu-id="28dfb-141">Önceden tanımlanmış ad alanını kullanacak `global` adları .NET en üst düzey ad alanında yerleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="28dfb-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="28dfb-142">Ayrıca genel kullanabileceğiniz üst düzey .NET ad alanı, örneğin başvurmak için diğer ad alanları ile ad çakışmalarını çözmek için.</span><span class="sxs-lookup"><span data-stu-id="28dfb-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="28dfb-143">Özyinelemeli ad alanları</span><span class="sxs-lookup"><span data-stu-id="28dfb-143">Recursive namespaces</span></span>

<span data-ttu-id="28dfb-144">Ad alanları, aynı zamanda karşılıklı özyinelemeli olarak tüm kapsanan kodunu izin vermek için özyinelemeli olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="28dfb-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="28dfb-145">Bu aracılığıyla yapılır `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="28dfb-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="28dfb-146">Kullanım `namespace rec` türler ve modüller arasında karşılıklı başvurusal kod yazmak boyutlandırılmamışsa, bazı sorunlar hafifletmek.</span><span class="sxs-lookup"><span data-stu-id="28dfb-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="28dfb-147">Bunun bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="28dfb-147">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="28dfb-148">Unutmayın özel durum `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="28dfb-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="28dfb-149">Buna ek olarak, modül `BananaHelpers` ve sınıf `Banana` ayrıca birbirine bakın.</span><span class="sxs-lookup"><span data-stu-id="28dfb-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="28dfb-150">Bu, express mümkün olmazdı F# kaldırdıysanız `rec` from anahtar sözcüğü `MutualReferences` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="28dfb-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="28dfb-151">Bu özellik için de kullanılabilir olan en üst düzey [modülleri](modules.md).</span><span class="sxs-lookup"><span data-stu-id="28dfb-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28dfb-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28dfb-152">See also</span></span>

- [<span data-ttu-id="28dfb-153">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="28dfb-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="28dfb-154">Modüller</span><span class="sxs-lookup"><span data-stu-id="28dfb-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="28dfb-155">F#RFC FS-1009 - karşılıklı başvurusal türler ve modüller daha büyük dosyaları kapsamlarda üzerinden izin ver</span><span class="sxs-lookup"><span data-stu-id="28dfb-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)