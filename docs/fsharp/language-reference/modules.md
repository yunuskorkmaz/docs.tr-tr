---
title: Modüller
description: Bir F# modülün bir F# F# programdaki değerler, türler ve işlev değerleri gibi bir kod gruplandırması olduğunu öğrenin.
ms.date: 04/24/2017
ms.openlocfilehash: fbde0c8b001d88614ba2de49c4aa7bfa098c6945
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425061"
---
# <a name="modules"></a><span data-ttu-id="314d2-103">Modüller</span><span class="sxs-lookup"><span data-stu-id="314d2-103">Modules</span></span>

<span data-ttu-id="314d2-104">Dil bağlamında *Modül* , bir F# programdaki değerler, türler ve işlev değerleri gibi F# bir kod gruplandırmasıdır. F#</span><span class="sxs-lookup"><span data-stu-id="314d2-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="314d2-105">Modüllerde kod gruplandırma, ilgili kodu birlikte tutmaya yardımcı olur ve programınızda ad çakışmalarını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="314d2-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="314d2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="314d2-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="314d2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="314d2-107">Remarks</span></span>

<span data-ttu-id="314d2-108">F# Modül, `do` bağlamalardaki türler F# , değerler, işlev değerleri ve kod gibi kod yapılarının bir gruplandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="314d2-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="314d2-109">Yalnızca statik üyelere sahip ortak dil çalışma zamanı (CLR) sınıfı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="314d2-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="314d2-110">Tüm dosyanın modüle dahil edilip edilmeyeceğini bağlı olarak iki tür modül bildirimi vardır: en üst düzey modül bildirimi ve yerel bir modül bildirimi.</span><span class="sxs-lookup"><span data-stu-id="314d2-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="314d2-111">Üst düzey modül bildirimi, modülün tüm dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="314d2-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="314d2-112">En üst düzey modül bildirimi, yalnızca bir dosyadaki ilk bildirim olarak görünebilir.</span><span class="sxs-lookup"><span data-stu-id="314d2-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="314d2-113">Üst düzey modül bildiriminin sözdiziminde, isteğe bağlı *nitelikli ad alanı* , modülünü içeren iç içe ad alanı adlarının sırasıdır.</span><span class="sxs-lookup"><span data-stu-id="314d2-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="314d2-114">Nitelenmiş ad alanının önceden bildirilmesine izin yoktur.</span><span class="sxs-lookup"><span data-stu-id="314d2-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="314d2-115">Üst düzey modüldeki bildirimleri girintilemek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="314d2-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="314d2-116">Yerel modüllerdeki tüm bildirimlerin girintisini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="314d2-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="314d2-117">Yerel bir modül bildiriminde, yalnızca söz konusu modül bildiriminde girintili olan bildirimler modülün bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="314d2-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="314d2-118">Bir kod dosyası en üst düzey modül bildirimiyle veya bir ad alanı bildirimiyle başlamamışsa, tüm yerel modüller dahil olmak üzere dosyanın tüm içerikleri, uzantısı olmadan dosya ile aynı ada sahip örtük olarak oluşturulmuş bir üst düzey modülün bir parçası haline gelir. ilk harfle büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="314d2-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="314d2-119">Örneğin, aşağıdaki dosyayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="314d2-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="314d2-120">Bu dosya bu şekilde yazılmış gibi derlenir:</span><span class="sxs-lookup"><span data-stu-id="314d2-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="314d2-121">Bir dosyada birden çok modülünüz varsa, her modül için yerel bir modül bildirimi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="314d2-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="314d2-122">Kapsayan bir ad alanı bildirilirse, bu modüller kapsayan ad alanının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="314d2-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="314d2-123">Kapsayan bir ad alanı bildirilmemiş ise, modüller örtük olarak oluşturulan en üst düzey modülün bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="314d2-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="314d2-124">Aşağıdaki kod örneği, birden çok modül içeren bir kod dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="314d2-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="314d2-125">Derleyici örtük olarak `Multiplemodules`adlı bir üst düzey modül oluşturur ve `MyModule1` ve `MyModule2` bu üst düzey modülde iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="314d2-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="314d2-126">Bir projede veya tek bir derlemede birden çok dosya varsa veya bir kitaplık oluşturuyorsanız, dosyanın üst kısmına bir ad alanı bildirimi veya modül bildirimi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="314d2-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="314d2-127">F# Derleyici yalnızca bir proje veya derleme komut satırında yalnızca bir dosya olduğunda ve bir uygulama oluşturuyorsanız bir modül adını örtülü olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="314d2-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="314d2-128">*Erişilebilirlik-değiştirici* aşağıdakilerden biri olabilir: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="314d2-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="314d2-129">Daha fazla bilgi için bkz. [Access Control](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="314d2-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="314d2-130">Varsayılan değer geneldir.</span><span class="sxs-lookup"><span data-stu-id="314d2-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="314d2-131">Modüllerde koda başvurma</span><span class="sxs-lookup"><span data-stu-id="314d2-131">Referencing Code in Modules</span></span>

<span data-ttu-id="314d2-132">Başka bir modülden işlevlere, türlere ve değerlere başvuru yaptığınızda tam adı kullanmanız veya modülünü açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="314d2-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="314d2-133">Nitelikli bir ad kullanırsanız, istediğiniz program öğesi için ad alanlarını, modülü ve tanımlayıcıyı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="314d2-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="314d2-134">Tam yolun her bölümünü aşağıdaki gibi bir nokta (.) ile ayırın.</span><span class="sxs-lookup"><span data-stu-id="314d2-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="314d2-135">Kodu basitleştirmek için modülü veya bir veya daha fazla ad alanını açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="314d2-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="314d2-136">Ad alanlarını ve modülleri açma hakkında daha fazla bilgi için bkz. [Içeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="314d2-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="314d2-137">Aşağıdaki kod örneğinde, dosyanın sonuna kadar olan tüm kodu içeren bir üst düzey modül gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="314d2-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="314d2-138">Aynı projedeki başka bir dosyadan bu kodu kullanmak için, aşağıdaki örneklerde gösterildiği gibi, işlevleri kullanmadan önce nitelikli adları kullanırsınız veya modülü açarsınız.</span><span class="sxs-lookup"><span data-stu-id="314d2-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="314d2-139">İç içe modüller</span><span class="sxs-lookup"><span data-stu-id="314d2-139">Nested Modules</span></span>

<span data-ttu-id="314d2-140">Modüller iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="314d2-140">Modules can be nested.</span></span> <span data-ttu-id="314d2-141">İç modüller, yeni modüller değil, iç modüller olduğunu göstermek için dış modül bildirimlerinin en çok olarak girintilenmelidir.</span><span class="sxs-lookup"><span data-stu-id="314d2-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="314d2-142">Örneğin, aşağıdaki iki örneği karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="314d2-142">For example, compare the following two examples.</span></span> <span data-ttu-id="314d2-143">Modül `Z`, aşağıdaki koddaki bir iç modüldür.</span><span class="sxs-lookup"><span data-stu-id="314d2-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="314d2-144">Ancak modül `Z` aşağıdaki kodda `Y` modül eşdüzey bir eşdir.</span><span class="sxs-lookup"><span data-stu-id="314d2-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="314d2-145">Modül `Z` Ayrıca aşağıdaki kodda bir eşdüzey modüldür, çünkü modül `Y`diğer bildirimlerin olduğu kadar girintilenir.</span><span class="sxs-lookup"><span data-stu-id="314d2-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="314d2-146">Son olarak, dış modülün bildirimi yoksa ve daha sonra başka bir modül bildirimi tarafından hemen ardından, yeni modül bildiriminin bir iç modül olduğu varsayılır, ancak ikinci modül tanımı adı.</span><span class="sxs-lookup"><span data-stu-id="314d2-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="314d2-147">Uyarıyı ortadan kaldırmak için, iç modülün girintisini artırın.</span><span class="sxs-lookup"><span data-stu-id="314d2-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="314d2-148">Bir dosyadaki tüm kodun tek bir dış modülde olmasını ve iç modüller olmasını istiyorsanız, dıştaki modül eşittir işaretine gerek yoktur ve dış modülün içindeki tüm iç modül bildirimleri de dahil olmak üzere, bu bildirimlerin girintileneceği bir girinti olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="314d2-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="314d2-149">İç modül bildirimlerinin içindeki bildirimlerin girintili olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="314d2-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="314d2-150">Aşağıdaki kod bu durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="314d2-150">The following code shows this case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="314d2-151">Özyinelemeli modüller</span><span class="sxs-lookup"><span data-stu-id="314d2-151">Recursive modules</span></span>

<span data-ttu-id="314d2-152">F#4,1, içerilen tüm kodların birbirini karşılıklı olarak özyinelemeli olmasını sağlayan modül kavramını sunar.</span><span class="sxs-lookup"><span data-stu-id="314d2-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="314d2-153">Bu, `module rec`aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="314d2-153">This is done via `module rec`.</span></span>  <span data-ttu-id="314d2-154">`module rec` kullanımı, bazı paıns 'leri türler ve modüller arasında karşılıklı başvuru kodu yazamayacak şekilde giderebiliyor.</span><span class="sxs-lookup"><span data-stu-id="314d2-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="314d2-155">Aşağıda buna bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="314d2-155">The following is an example of this:</span></span>

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

<span data-ttu-id="314d2-156">Özel durum `DontSqueezeTheBananaException` ve sınıf `Banana` her ikisi de birbirine başvurmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="314d2-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="314d2-157">Ayrıca, modül `BananaHelpers` ve sınıf `Banana` aynı zamanda birbirini da ifade eder.</span><span class="sxs-lookup"><span data-stu-id="314d2-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="314d2-158">`RecursiveModule` modülünden `rec` anahtar sözcüğünü kaldırdıysanız, bu F# , ' ın içinde ifade edilmez.</span><span class="sxs-lookup"><span data-stu-id="314d2-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="314d2-159">Bu özellik [ad alanlarında](namespaces.md) 4,1 ile F# de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="314d2-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="314d2-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="314d2-160">See also</span></span>

- [<span data-ttu-id="314d2-161">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="314d2-161">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="314d2-162">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="314d2-162">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="314d2-163">F#RFC FS-1009-dosyalar içindeki daha büyük kapsamlar üzerinde karşılıklı başvuru türleri ve modülleri sağlar</span><span class="sxs-lookup"><span data-stu-id="314d2-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
