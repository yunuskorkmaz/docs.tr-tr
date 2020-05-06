---
title: Ad Alanları
description: 'Bir F # ad alanının, program öğeleri gruplandırmasına bir ad iliştirerek, ilgili işlevlerin bölümlerine kod düzenlemenize nasıl olanak sağladığını öğrenin.'
ms.date: 12/08/2018
ms.openlocfilehash: bf71843349434a1ea91c58dbc0477373dbb0c449
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796138"
---
# <a name="namespaces"></a><span data-ttu-id="61f40-103">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="61f40-103">Namespaces</span></span>

<span data-ttu-id="61f40-104">Bir ad alanı, bir F # program öğesi gruplandırmasına bir ad iliştirmenizi sağlayarak kodu ilgili işlevlerin alanlarıyla düzenlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="61f40-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="61f40-105">Ad alanları genellikle F # dosyalarındaki en üst düzey öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="61f40-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="61f40-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61f40-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="61f40-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61f40-107">Remarks</span></span>

<span data-ttu-id="61f40-108">Bir ad alanına kod koymak istiyorsanız, dosyadaki ilk bildirim ad alanını bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="61f40-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="61f40-109">Dosyanın tamamı daha sonra başka bir ad alanı bildirimi mevcut olmadığından, bu dosyanın içeriği ad alanının bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="61f40-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="61f40-110">Bu durumda, sonraki ad alanı bildirimi ilk ad alanı içinde olduğu Düşünülene kadar tüm kod yukarı.</span><span class="sxs-lookup"><span data-stu-id="61f40-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="61f40-111">Ad alanları doğrudan değer ve işlevleri içeremez.</span><span class="sxs-lookup"><span data-stu-id="61f40-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="61f40-112">Bunun yerine, değerler ve işlevler modüllerde yer almalıdır ve modüller ad alanlarına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="61f40-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="61f40-113">Ad alanlarında türler, modüller bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="61f40-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="61f40-114">XML belge açıklamaları bir ad alanı üzerinde bildirilemez, ancak bunlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="61f40-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="61f40-115">Derleyici yönergeleri Ayrıca bir ad alanı üzerinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="61f40-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="61f40-116">Ad alanları, ad alanı anahtar sözcüğüyle açıkça veya bir modül bildirilirken örtük olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="61f40-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="61f40-117">Bir ad alanını açıkça bildirmek için, ad alanı adını izleyen namespace anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="61f40-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="61f40-118">Aşağıdaki örnek, bir türü ve bu ad alanına dahil olan `Widgets` bir modül içeren bir ad alanı bildiren bir kod dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="61f40-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="61f40-119">Dosyanın tüm içeriği bir modülde ise, `module` anahtar sözcüğü kullanarak ve tam modül adında yeni ad alanı adını sağlayarak ad alanlarını örtülü olarak da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61f40-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="61f40-120">Aşağıdaki örnek, bir işlevi içeren bir ad alanı `Widgets` ve bir modül `WidgetsModule`bildiren bir kod dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="61f40-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="61f40-121">Aşağıdaki kod, önceki koda eşdeğerdir, ancak modül yerel bir modül bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="61f40-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="61f40-122">Bu durumda, ad alanı kendi satırında görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="61f40-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="61f40-123">Aynı dosyada bir veya daha fazla ad alanında birden fazla modül gerekliyse, yerel modül bildirimleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61f40-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="61f40-124">Yerel modül bildirimleri kullandığınızda, modül bildirimlerinde nitelikli ad alanını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61f40-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="61f40-125">Aşağıdaki kod, bir ad alanı bildirimi ve iki yerel modül bildirimi olan bir dosyayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="61f40-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="61f40-126">Bu durumda, modüller doğrudan ad alanında yer alır; dosya ile aynı ada sahip örtük olarak oluşturulmuş bir modül yoktur.</span><span class="sxs-lookup"><span data-stu-id="61f40-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="61f40-127">Dosyadaki bir bağlama gibi başka herhangi bir `do` kod ad alanında yer alan, iç modüllerde değil, modül üyesini `widgetFunction` modül adını kullanarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61f40-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="61f40-128">Bu örneğin çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="61f40-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="61f40-129">Daha fazla bilgi için bkz. [modüller](modules.md).</span><span class="sxs-lookup"><span data-stu-id="61f40-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="61f40-130">İç içe geçmiş ad alanları</span><span class="sxs-lookup"><span data-stu-id="61f40-130">Nested Namespaces</span></span>

<span data-ttu-id="61f40-131">İç içe bir ad alanı oluşturduğunuzda, tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61f40-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="61f40-132">Aksi takdirde, yeni bir üst düzey ad alanı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="61f40-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="61f40-133">Ad alanı bildirimlerinde girintileme yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="61f40-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="61f40-134">Aşağıdaki örnek, iç içe bir ad alanının nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="61f40-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="61f40-135">Dosyalarda ve derlemelerde ad alanları</span><span class="sxs-lookup"><span data-stu-id="61f40-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="61f40-136">Ad alanları, tek bir projede veya derlemede birden çok dosyayı kapsayabilir.</span><span class="sxs-lookup"><span data-stu-id="61f40-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="61f40-137">*Ad alanı parçası* , bir dosyada bulunan bir ad alanının parçasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="61f40-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="61f40-138">Ad alanları birden fazla derlemeye de yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="61f40-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="61f40-139">Örneğin, `System` ad alanı birçok derlemeyi kapsayan ve birçok iç içe ad alanı içeren .NET Framework tamamını içerir.</span><span class="sxs-lookup"><span data-stu-id="61f40-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="61f40-140">Genel ad alanı</span><span class="sxs-lookup"><span data-stu-id="61f40-140">Global Namespace</span></span>

<span data-ttu-id="61f40-141">.NET en üst düzey ad `global` alanına ad koymak için önceden tanımlanmış ad alanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="61f40-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="61f40-142">Ayrıca, üst düzey .NET ad alanına başvurmak için genel ' i de kullanabilirsiniz. Örneğin, diğer ad alanları ile ad çakışmalarını çözmek için.</span><span class="sxs-lookup"><span data-stu-id="61f40-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="61f40-143">Özyinelemeli ad alanları</span><span class="sxs-lookup"><span data-stu-id="61f40-143">Recursive namespaces</span></span>

<span data-ttu-id="61f40-144">Ayrıca, içerilen tüm kodun birbirini karşılıklı olarak özyinelemeli olmasını sağlamak için ad alanları özyinelemeli olarak da bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="61f40-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="61f40-145">Bu, aracılığıyla `namespace rec`yapılır.</span><span class="sxs-lookup"><span data-stu-id="61f40-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="61f40-146">Kullanımı, `namespace rec` ve modülleri arasında karşılıklı başvuru kodu yazamayacak bazı paıns 'leri hafifme edebilir.</span><span class="sxs-lookup"><span data-stu-id="61f40-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="61f40-147">Aşağıda buna bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="61f40-147">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

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

<span data-ttu-id="61f40-148">Özel durumun `DontSqueezeTheBananaException` ve sınıfın `Banana` her ikisi de birbirine başvurmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61f40-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="61f40-149">Ayrıca, modülü `BananaHelpers` ve sınıfı `Banana` birbirini da ifade eder.</span><span class="sxs-lookup"><span data-stu-id="61f40-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="61f40-150">`rec` Anahtar sözcüğü `MutualReferences` ad alanından kaldırdıysanız, bu, F # içinde ifade etmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="61f40-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="61f40-151">Bu özellik, üst düzey [modüller](modules.md)için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61f40-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61f40-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61f40-152">See also</span></span>

- [<span data-ttu-id="61f40-153">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="61f40-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="61f40-154">Modül</span><span class="sxs-lookup"><span data-stu-id="61f40-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="61f40-155">F # RFC FS-1009-dosyalar içindeki daha büyük kapsamlar üzerinde karşılıklı başvuru türleri ve modülleri sağlar</span><span class="sxs-lookup"><span data-stu-id="61f40-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
