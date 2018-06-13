---
title: Modüller (F#)
description: 'Nasıl bir F # modülün F # kodunda değerler, türleri ve F # programında işlevi değerleri gibi grubudur öğrenin.'
ms.date: 04/24/2017
ms.openlocfilehash: 9a1416321e392f7a06551b4a7e3429e3a2d023bd
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483529"
---
# <a name="modules"></a><span data-ttu-id="6f9a4-103">Modüller</span><span class="sxs-lookup"><span data-stu-id="6f9a4-103">Modules</span></span>

<span data-ttu-id="6f9a4-104">F # dili bağlamında bir *Modülü* F # kodunda değerler, türleri ve F # programında işlevi değerleri gibi bir gruplandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="6f9a4-105">Modüllerinde kodu gruplandırma ilgili kod birlikte tutmaya yardımcı olur ve ad çakışmalarını programınızdaki önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f9a4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f9a4-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="6f9a4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f9a4-107">Remarks</span></span>
<span data-ttu-id="6f9a4-108">F # modülün F # kod yapılarını türleri, değerleri, işlev değerlerini ve kodda gibi bir gruplandırmasıdır `do` bağlar.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="6f9a4-109">Yalnızca statik üyeleri olan bir ortak dil çalışma zamanı (CLR) sınıfı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="6f9a4-110">Modül bildirimleri, dosyanın tamamını modülünde olup olmadığı dahil bağlı olarak iki tür vardır: bir üst düzey modül bildirimi ve bir yerel modül bildirimi.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="6f9a4-111">Bir üst düzey modül bildirimi modülünde dosyanın tamamını içerir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="6f9a4-112">Bir üst düzey modül bildirimi yalnızca bir dosya ilk bildirimde olarak yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="6f9a4-113">İsteğe bağlı en üst düzey modülü bildiriminin sözdiziminde *nitelenmiş ad* modülü içeren iç içe geçmiş ad alanı adları sırasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="6f9a4-114">Daha önce bildirilmesi tam ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="6f9a4-115">Üst düzey bir modül bildirimlerinde girinti gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="6f9a4-116">Tüm yerel modülleri bildirimlerinde girinti zorunda.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="6f9a4-117">Bir yerel modül bildiriminde yalnızca modülü bildirim altında girintili bildirimlerine modülü bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="6f9a4-118">Bir kod dosyası bir en üst düzey modül bildiriminde ya da bir ad alanı bildirimi ile başlamıyorsa, herhangi bir yerel modül dahil olmak üzere dosyanın tüm içeriğini uzantısı olmadan dosya aynı ada sahip bir örtük olarak oluşturulmuş en üst düzey modülün parçası haline gelir, ilk harfi büyük harfe dönüştürülmüş.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="6f9a4-119">Örneğin, aşağıdaki dosya göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="6f9a4-120">Bu şekilde yazılmışsa gibi bu dosyayı derlenmiş:</span><span class="sxs-lookup"><span data-stu-id="6f9a4-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="6f9a4-121">Birden fazla modülü bir dosyanız varsa, her modül için bir yerel modül bildirimi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="6f9a4-122">Kapsayan bir ad alanı bildirilirse, bu modülleri kapsayan ad alanını bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="6f9a4-123">Kapsayan bir ad alanı bildirilmedi, modüller örtük olarak oluşturulmuş en üst düzey modülü parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="6f9a4-124">Aşağıdaki kod örneğinde birden fazla modülü içeren bir kod dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="6f9a4-125">Derleyici örtük olarak adlı en üst düzey bir modül oluşturur `Multiplemodules`, ve `MyModule1` ve `MyModule2` , üst düzey modülü iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="6f9a4-126">Birden çok proje veya tek bir derleme dosyalarınız varsa veya bir kitaplık oluşturuluyorsa, bir ad alanı bildirimini veya modül bildirimi dosyanın üst eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="6f9a4-127">F # Derleyici yalnızca modül adı örtük olarak bir proje veya derleme komut satırında yalnızca bir dosya olduğunda ve bir uygulama oluşturmaya belirler.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="6f9a4-128">*Erişim değiştiricisi* şunlardan biri olabilir: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="6f9a4-129">Daha fazla bilgi için bkz: [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="6f9a4-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="6f9a4-130">Ortak varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-130">The default is public.</span></span>


## <a name="referencing-code-in-modules"></a><span data-ttu-id="6f9a4-131">Kod modülleri içinde başvurma</span><span class="sxs-lookup"><span data-stu-id="6f9a4-131">Referencing Code in Modules</span></span>
<span data-ttu-id="6f9a4-132">Başka bir modülden işlevleri, türleri ve değerleri başvuru yaptığınızda, bir tam ad kullanın veya modülü açmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="6f9a4-133">Bir tam ad kullanıyorsanız, ad alanları modülü ve istediğiniz program öğesi için tanımlayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="6f9a4-134">Tam yolu her bir parçasını bir nokta (.), aşağıdaki gibi ayırır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="6f9a4-135">Modül veya bir veya daha fazla kodu basitleştirmek için ad alanları açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="6f9a4-136">Açılış ad alanları ve modülleri hakkında daha fazla bilgi için bkz: [içeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="6f9a4-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="6f9a4-137">Aşağıdaki kod örneğinde dosyasının sonuna kadar olan tüm kodları içeren üst düzey bir modülü gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="6f9a4-138">Bu kodu aynı projede başka bir dosyadan kullanmak için ya da nitelikli adlar kullanın veya İşlevler, kullanmadan önce Modülü aşağıdaki örneklerde gösterildiği gibi açın.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="6f9a4-139">İç içe geçmiş modülleri</span><span class="sxs-lookup"><span data-stu-id="6f9a4-139">Nested Modules</span></span>
<span data-ttu-id="6f9a4-140">Modülleri içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-140">Modules can be nested.</span></span> <span data-ttu-id="6f9a4-141">İç modülleri iç modülleri, değil yeni modüller olduğunu belirtmek için dış modülü bildirimleri durum girintili gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="6f9a4-142">Örneğin, aşağıdaki iki örnek karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-142">For example, compare the following two examples.</span></span> <span data-ttu-id="6f9a4-143">Modül `Z` aşağıdaki kodda iç modülüdür.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="6f9a4-144">Ancak Modülü `Z` modülü bir eşdüzeyi olan `Y` aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="6f9a4-145">Modül `Z` modülü diğer bildirimlerinde durum girintili değil de bir eşdüzey Modülü aşağıdaki kodda, çünkü `Y`.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="6f9a4-146">Son olarak, dış modülü hiçbir bildirimleri varsa ve başka bir modül bildirimi hemen ardından, yeni modül bildiriminde bir iç modül olarak kabul edilir, ancak derleyici ikinci modül tanım farther daha girintili değil durumunda uyaracak ilk.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="6f9a4-147">Uyarı ortadan kaldırmak için iç modül girinti.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="6f9a4-148">Bir dosyanın tek bir dış modülünde olması için tüm kodda istiyorsanız ve iç modülleri istediğiniz dış modülü eşittir işaretinden gerektirmez ve dış modülünde gidecek tüm iç modül bildirimleri de dahil olmak üzere bu bildirimleri girintili gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="6f9a4-149">Bildirimler iç modül bildirimleri içinde girintili olmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="6f9a4-150">Aşağıdaki kod bu durumda gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-150">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="6f9a4-151">Özyinelemeli modülleri</span><span class="sxs-lookup"><span data-stu-id="6f9a4-151">Recursive modules</span></span>

<span data-ttu-id="6f9a4-152">F # 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu sağlayan modüller kavramını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="6f9a4-153">Bu aracılığıyla yapılır `module rec`.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-153">This is done via `module rec`.</span></span>  <span data-ttu-id="6f9a4-154">Kullanımı `module rec` türleri ve modülleri arasında karşılıklı başvuru kod yazmaya yazdıramama içinde bazı sorunlar hafifletmek.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="6f9a4-155">Bunun bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6f9a4-155">The following is an example of this:</span></span>

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

<span data-ttu-id="6f9a4-156">Unutmayın özel `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="6f9a4-157">Ayrıca, modül `BananaHelpers` ve sınıf `Banana` de birbirine bakın.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="6f9a4-158">Bu kaldırdıysanız F # express kurulamaz `rec` anahtar sözcüğünün `RecursiveModule` modülü.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="6f9a4-159">Bu özellik ayrıca mümkündür [ad alanları](namespaces.md) F # 4.1 ile.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f9a4-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f9a4-160">See also</span></span>

[<span data-ttu-id="6f9a4-161">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6f9a4-161">F# Language Reference</span></span>](index.md)  
[<span data-ttu-id="6f9a4-162">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="6f9a4-162">Namespaces</span></span>](namespaces.md)  
[<span data-ttu-id="6f9a4-163">F # RFC FS-1009 - birbirini başvuru türleri ve modülleri dosyaları büyük kapsamlarında üzerinden izin ver</span><span class="sxs-lookup"><span data-stu-id="6f9a4-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
