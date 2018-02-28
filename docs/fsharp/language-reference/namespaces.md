---
title: "Ad Alanları (F#)"
description: "F # ad alanı nasıl program öğeleri gruplandırması için bir ad eklemek sağlayarak ilgili işlevselliği alanlarına kodunu düzenlemenizi sağlar öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea42156f-e1b9-4535-9383-b45f46f3f7ca
ms.openlocfilehash: f3f73c4fe2197f1f3f2babbe6691ef6662d8f581
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="namespaces"></a><span data-ttu-id="39fae-104">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="39fae-104">Namespaces</span></span>

<span data-ttu-id="39fae-105">Bir ad alanı, kod ilgili işlevselliği alanlarına program öğeleri gruplandırması için bir ad eklemek sağlayarak düzenlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="39fae-105">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="39fae-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39fae-106">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="39fae-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39fae-107">Remarks</span></span>
<span data-ttu-id="39fae-108">Kod bir ad alanındaki put istiyorsanız, dosyayı ilk bildiriminde ad alanı bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="39fae-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="39fae-109">Tüm dosya içeriğini sonra ad alanının parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="39fae-109">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="39fae-110">Ad alanları doğrudan değerleri ve işlevler içeremez.</span><span class="sxs-lookup"><span data-stu-id="39fae-110">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="39fae-111">Bunun yerine, değerler ve işlevleri modülleri eklenmelidir ve modülleri ad alanları eklenir.</span><span class="sxs-lookup"><span data-stu-id="39fae-111">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="39fae-112">Ad alanları türleri, modüller içerebilir.</span><span class="sxs-lookup"><span data-stu-id="39fae-112">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="39fae-113">Ad alanları açıkça veya ad alanı anahtar sözcüğü ile örtük olarak bir modül bildirirken bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="39fae-113">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="39fae-114">Bir ad alanını açıkça bildirmek için ad alanı adına göre ad alanı anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="39fae-114">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="39fae-115">Aşağıdaki örnek, bir ad alanını bir türde ve bu ad alanına dahil bir modül pencere öğeleri bildiren bir kod dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="39fae-115">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="39fae-116">Dosyanın tüm içeriğini bir modülde varsa, aynı zamanda ad alanları örtük olarak kullanarak bildirebilirsiniz `module` anahtar sözcüğü ve sağlayan yeni ad alanı adı tam modül adı.</span><span class="sxs-lookup"><span data-stu-id="39fae-116">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="39fae-117">Aşağıdaki örnek, bir ad alanını tanımlayan bir kod dosyası gösterir `Widgets` ve bir modülü `WidgetsModule`, bir işlev içeriyor.</span><span class="sxs-lookup"><span data-stu-id="39fae-117">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="39fae-118">Aşağıdaki kod, önceki kod eşdeğerdir, ancak bir yerel modül bildirimi modülüdür.</span><span class="sxs-lookup"><span data-stu-id="39fae-118">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="39fae-119">Bu durumda, ad alanı, kendi satırında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="39fae-119">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="39fae-120">Bir veya daha fazla ad aynı dosyasında birden fazla modülü gerekirse, yerel modül bildirimleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39fae-120">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="39fae-121">Yerel modül bildirimleri kullandığınızda, tam ad modülü bildirimlerinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="39fae-121">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="39fae-122">Aşağıdaki kod, bir ad alanı bildirimi ve iki yerel modül bildirimleri sahip bir dosyayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="39fae-122">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="39fae-123">Bu durumda, modülleri doğrudan ad alanında yer alır; aynı ada sahip dosyayı olarak hiç örtük olarak oluşturulmuş bir modülü vardır.</span><span class="sxs-lookup"><span data-stu-id="39fae-123">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="39fae-124">Diğer kod dosyasında gibi bir `do` modülü üye nitelemek gereken bağlama, ad alanı ancak iç modülleri olduğundan `widgetFunction` modül adı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="39fae-124">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="39fae-125">Bu örnek çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="39fae-125">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="39fae-126">Daha fazla bilgi için bkz: [modülleri](modules.md).</span><span class="sxs-lookup"><span data-stu-id="39fae-126">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="39fae-127">İç içe geçmiş ad alanları</span><span class="sxs-lookup"><span data-stu-id="39fae-127">Nested Namespaces</span></span>
<span data-ttu-id="39fae-128">İç içe geçmiş bir ad alanı oluşturduğunuzda, tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="39fae-128">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="39fae-129">Aksi takdirde, yeni bir üst düzey ad alanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="39fae-129">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="39fae-130">Girinti ad alanı bildirimleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="39fae-130">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="39fae-131">Aşağıdaki örnek, iç içe geçmiş bir ad alanı bildirimini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39fae-131">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="39fae-132">Dosyaları ve derlemeler için ad alanları</span><span class="sxs-lookup"><span data-stu-id="39fae-132">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="39fae-133">Ad alanları projenin ya da derleme birden çok dosya yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="39fae-133">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="39fae-134">Terim *ad parçasını* bir dosyada bulunan bir ad alanının parçası açıklar.</span><span class="sxs-lookup"><span data-stu-id="39fae-134">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="39fae-135">Ad alanları, birden çok derleme da yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="39fae-135">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="39fae-136">Örneğin, `System` ad alanı, çok sayıda derlemeleri yayılan ve pek çok iç içe geçmiş ad alanları içeren tüm .NET Framework, içerir.</span><span class="sxs-lookup"><span data-stu-id="39fae-136">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="39fae-137">Genel Namespace</span><span class="sxs-lookup"><span data-stu-id="39fae-137">Global Namespace</span></span>
<span data-ttu-id="39fae-138">Önceden tanımlanmış ad alanını kullanmak `global` .NET en üst düzey ad alanında adları yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="39fae-138">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="39fae-139">Ayrıca genel kullanabileceğiniz üst düzey .NET ad alanı, örneğin başvurmak için diğer ad ile ad çakışmalarını çözmek için.</span><span class="sxs-lookup"><span data-stu-id="39fae-139">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="39fae-140">Özyinelemeli ad alanları</span><span class="sxs-lookup"><span data-stu-id="39fae-140">Recursive namespaces</span></span>

<span data-ttu-id="39fae-141">F # 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu sağlayan ad alanları kavramını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39fae-141">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="39fae-142">Bu aracılığıyla yapılır `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="39fae-142">This is done via `namespace rec`.</span></span>  <span data-ttu-id="39fae-143">Kullanımı `namespace rec` türleri ve modülleri arasında karşılıklı başvuru kod yazmaya yazdıramama içinde bazı sorunlar hafifletmek.</span><span class="sxs-lookup"><span data-stu-id="39fae-143">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="39fae-144">Bunun bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="39fae-144">The following is an example of this:</span></span>

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
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="39fae-145">Unutmayın özel `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="39fae-145">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="39fae-146">Ayrıca, modül `BananaHelpers` ve sınıf `Banana` de birbirine bakın.</span><span class="sxs-lookup"><span data-stu-id="39fae-146">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="39fae-147">Bu kaldırdıysanız F # express kurulamaz `rec` anahtar sözcüğünün `MutualReferences` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="39fae-147">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="39fae-148">Bu özellik ayrıca kullanılabilir en üst düzey [modülleri](modules.md) F # 4.1 veya daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="39fae-148">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="39fae-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39fae-149">See Also</span></span>
[<span data-ttu-id="39fae-150">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="39fae-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="39fae-151">Modüller</span><span class="sxs-lookup"><span data-stu-id="39fae-151">Modules</span></span>](modules.md)

[<span data-ttu-id="39fae-152">F # RFC FS-1009 - birbirini başvuru türleri ve modülleri dosyaları büyük kapsamlarında üzerinden izin ver</span><span class="sxs-lookup"><span data-stu-id="39fae-152">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
