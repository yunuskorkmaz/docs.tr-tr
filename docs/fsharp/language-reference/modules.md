---
title: Modüller (F#)
description: Bir F# modül değerleri, türleri ve işlev değerleri olarak F# programında gibi F# kodu, bir gruplandırma nasıl olduğunu öğrenin.
ms.date: 04/24/2017
ms.openlocfilehash: fb0aa1d508d1141933b4fbdf10633f67ed078dc7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45528532"
---
# <a name="modules"></a><span data-ttu-id="60f73-103">Modüller</span><span class="sxs-lookup"><span data-stu-id="60f73-103">Modules</span></span>

<span data-ttu-id="60f73-104">F# dili, bağlamında bir *Modülü* F# kodu, değerleri, türleri ve işlev değerleri olarak F# programında gibi bir gruplandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="60f73-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="60f73-105">Kod modüllerinde gruplandırma ilgili kod bir arada tutmaya yardımcı olur ve programınızdaki ad çakışmalarını önlemek yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="60f73-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="60f73-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60f73-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="60f73-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60f73-107">Remarks</span></span>

<span data-ttu-id="60f73-108">Bir F# modül türleri, değerleri, işlev değerleri ve kodda gibi kod yapıları F# gruplandırmasıdır `do` bağlar.</span><span class="sxs-lookup"><span data-stu-id="60f73-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="60f73-109">Bu, yalnızca statik üyeleri olan ortak dil çalışma zamanı (CLR) sınıfı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="60f73-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="60f73-110">Modül bildirimlerinde'olup tüm dosya modülüne dahil edilen bağlı olarak, iki tür vardır: üst düzey modül bildirimi ve bir yerel modül bildirimi.</span><span class="sxs-lookup"><span data-stu-id="60f73-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="60f73-111">Üst düzey modül bildirimi modülünde dosyanın tamamını içerir.</span><span class="sxs-lookup"><span data-stu-id="60f73-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="60f73-112">Üst düzey modül bildirimi yalnızca bir dosyadaki ilk bildirimi olarak görünebilir.</span><span class="sxs-lookup"><span data-stu-id="60f73-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="60f73-113">İsteğe bağlı üst düzey modül bildirimi için sözdiziminde *nitelenmiş ad* modülü içeren iç içe geçmiş ad alanı adları dizisidir.</span><span class="sxs-lookup"><span data-stu-id="60f73-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="60f73-114">Daha önce belirtilecek tam ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="60f73-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="60f73-115">Üst düzey bir modül bildirimlerinde Girintile gerekmez.</span><span class="sxs-lookup"><span data-stu-id="60f73-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="60f73-116">Tüm yerel modülleri bildirimlerinde Girintile gerekir.</span><span class="sxs-lookup"><span data-stu-id="60f73-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="60f73-117">Bir yerel modül bildirimine yalnızca bu modül bildirimi altında girintili bildirimleri modülü bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="60f73-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="60f73-118">Bir kod dosyası, bir üst düzey modül bildirimi ya da bir ad alanı bildirimi başlamazsa, yerel modüllerin de dahil olmak üzere dosyanın tüm içeriğini uzantısı olmadan bir dosyayla aynı ada sahip bir örtük olarak oluşturulan üst düzey modülü bir parçası olur, ilk harfi büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="60f73-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="60f73-119">Örneğin, aşağıdaki dosya göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="60f73-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="60f73-120">Bu dosya bu şekilde yazılmışlar gibi derlenmesi:</span><span class="sxs-lookup"><span data-stu-id="60f73-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="60f73-121">Birden çok modül bir dosya varsa, her modül için bir yerel modül bildirimi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60f73-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="60f73-122">Bir kapsayan ad uzayı bildirirse, bu modülleri kapsayan ad uzayı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="60f73-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="60f73-123">Modüller, kapsayan bir ad alanında bildirilmedi, örtük olarak oluşturulan üst düzey modülü bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="60f73-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="60f73-124">Aşağıdaki kod örneği, birden çok modül içeren bir kod dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="60f73-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="60f73-125">Derleyici örtük olarak adlı en üst düzey bir modül oluşturur `Multiplemodules`, ve `MyModule1` ve `MyModule2` , üst düzey modülü iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="60f73-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="60f73-126">Birden çok dosya bir proje veya tek bir derleme varsa veya bir kitaplık oluşturuyorsanız, ad alanı bildirimini veya modül bildirimi dosyasının üst eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="60f73-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="60f73-127">F# derleyicisi yalnızca bir modül adı örtük olarak bir proje veya derleme komut satırı yalnızca bir dosya olduğunda ve bir uygulama oluşturuyorsanız belirler.</span><span class="sxs-lookup"><span data-stu-id="60f73-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="60f73-128">*Erişilebilirlik değiştiricisi* aşağıdakilerden biri olabilir: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="60f73-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="60f73-129">Daha fazla bilgi için [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="60f73-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="60f73-130">Genel varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="60f73-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="60f73-131">Kod modüllerinde başvurma</span><span class="sxs-lookup"><span data-stu-id="60f73-131">Referencing Code in Modules</span></span>

<span data-ttu-id="60f73-132">İşlevleri, türleri ve değerleri başka bir modülden başvuruda bulunduğunuzda bir tam adı kullanın veya modül açmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="60f73-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="60f73-133">Bir tam adı kullanırsanız, ad alanları modülü ve istediğiniz program öğesi için tanımlayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="60f73-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="60f73-134">Tam yolun her bölümü bir nokta (.), aşağıdaki gibi ayırır.</span><span class="sxs-lookup"><span data-stu-id="60f73-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="60f73-135">Modülün veya bir veya daha fazla ad alanları kodu basitleştirmek için açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60f73-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="60f73-136">Açılış ad alanları ve modüller hakkında daha fazla bilgi için bkz. [içeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="60f73-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="60f73-137">Aşağıdaki kod örneği, dosyanın sonuna kadar tüm kodu içeren bir üst düzey modülü gösterir.</span><span class="sxs-lookup"><span data-stu-id="60f73-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="60f73-138">Aynı projede başka bir dosyadan bu kodu kullanmak için ya da nitelikli adlar kullanın veya İşlevler, kullanmadan önce modül aşağıdaki örneklerde gösterildiği gibi açın.</span><span class="sxs-lookup"><span data-stu-id="60f73-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="60f73-139">İç içe geçmiş modülleri</span><span class="sxs-lookup"><span data-stu-id="60f73-139">Nested Modules</span></span>

<span data-ttu-id="60f73-140">Modülleri içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="60f73-140">Modules can be nested.</span></span> <span data-ttu-id="60f73-141">İç modülleri iç modülleri değil yeni modüller olduğunu belirtmek için dış modül bildirimlerinde sunulan ürünün kendinde girintili gerekir.</span><span class="sxs-lookup"><span data-stu-id="60f73-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="60f73-142">Örneğin, aşağıdaki iki örnek ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="60f73-142">For example, compare the following two examples.</span></span> <span data-ttu-id="60f73-143">Modül `Z` aşağıdaki kodda iç bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="60f73-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="60f73-144">Ancak Modülü `Z` modülü eşdüzeye olduğu `Y` aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="60f73-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="60f73-145">Modül `Z` diğer modül bildirimlerinde sunulan ürünün kendinde girintili değil de bir eşdüzey Modülü aşağıdaki kodda, çünkü `Y`.</span><span class="sxs-lookup"><span data-stu-id="60f73-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="60f73-146">Son olarak, dış modül yok bildirimler içeriyor ve başka bir modül bildirimi tarafından hemen ardından, yeni modül bildirimi bir iç modül olarak kabul edilir, ancak derleyici ikinci modül tanımı farther daha girintili değil durumunda uyaracak ilk.</span><span class="sxs-lookup"><span data-stu-id="60f73-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="60f73-147">Uyarıyı ortadan kaldırmak için iç modül girinti.</span><span class="sxs-lookup"><span data-stu-id="60f73-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="60f73-148">Tüm kodu dosyasında tek bir dış modülde olmasını istiyorsanız ve iç modülleri istediğiniz dış modül eşittir işareti gerektirmez ve dış modüle gidecek herhangi bir iç modül bildirimlerinde de dahil olmak üzere, bildirimleri girintili gerekmez.</span><span class="sxs-lookup"><span data-stu-id="60f73-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="60f73-149">Bildirimi içinde iç modül bildirimlerinde girintili olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60f73-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="60f73-150">Aşağıdaki kod, bu durumda gösterir.</span><span class="sxs-lookup"><span data-stu-id="60f73-150">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="60f73-151">Özyinelemeli modülleri</span><span class="sxs-lookup"><span data-stu-id="60f73-151">Recursive modules</span></span>

<span data-ttu-id="60f73-152">F# 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu tanıyan modülleri kavramını sunar.</span><span class="sxs-lookup"><span data-stu-id="60f73-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="60f73-153">Bu aracılığıyla yapılır `module rec`.</span><span class="sxs-lookup"><span data-stu-id="60f73-153">This is done via `module rec`.</span></span>  <span data-ttu-id="60f73-154">Kullanım `module rec` türler ve modüller arasında karşılıklı başvurusal kod yazmak boyutlandırılmamışsa, bazı sorunlar hafifletmek.</span><span class="sxs-lookup"><span data-stu-id="60f73-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="60f73-155">Bunun bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60f73-155">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
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

<span data-ttu-id="60f73-156">Unutmayın özel durum `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="60f73-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="60f73-157">Buna ek olarak, modül `BananaHelpers` ve sınıf `Banana` ayrıca birbirine bakın.</span><span class="sxs-lookup"><span data-stu-id="60f73-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="60f73-158">Bu F#'ta kaldırdıysanız express mümkün olmazdı `rec` from anahtar sözcüğü `RecursiveModule` modülü.</span><span class="sxs-lookup"><span data-stu-id="60f73-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="60f73-159">Bu özellik ayrıca mümkün [ad alanları](namespaces.md) ile F# 4.1.</span><span class="sxs-lookup"><span data-stu-id="60f73-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="60f73-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60f73-160">See also</span></span>

- [<span data-ttu-id="60f73-161">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="60f73-161">F# Language Reference</span></span>](index.md)  
- [<span data-ttu-id="60f73-162">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="60f73-162">Namespaces</span></span>](namespaces.md)  
- [<span data-ttu-id="60f73-163">F# RFC FS-1009 - karşılıklı başvurusal türler ve modüller daha büyük dosyaları kapsamlarda üzerinden izin ver</span><span class="sxs-lookup"><span data-stu-id="60f73-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
