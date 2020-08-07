---
title: 'İçeri Aktarma Bildirimleri: open Anahtar Sözcüğü'
description: 'F # içeri aktarma bildirimleri hakkında bilgi edinin ve öğelerin tam nitelikli bir ad kullanmadan başvurdukları bir modül veya ad alanı belirtmeleri hakkında bilgi edinin.'
ms.date: 04/04/2019
ms.openlocfilehash: 2b88427ca92212fb4a7598447dd1a5e12061093a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855094"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="be0cf-103">İçeri aktarma bildirimleri: `open` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="be0cf-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="be0cf-104">*İçeri aktarma bildirimi* , öğelerini tam nitelikli bir ad kullanmadan başvuralabileceğiniz bir modül veya ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="be0cf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="be0cf-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="be0cf-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be0cf-106">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="be0cf-107">F # için docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="be0cf-107">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="be0cf-108">Bozuk bağlantılarla karşılaşırsanız, bunun yerine [F # Çekirdek Kitaplığı belgelerine](https://fsharp.github.io/fsharp-core-docs/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="be0cf-108">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

<span data-ttu-id="be0cf-109">Her seferinde tam nitelikli ad alanı veya modül yolunu kullanarak koda başvurmak, yazmak, okumak ve sürdürmek zor olan kod oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="be0cf-110">Bunun yerine `open` sık kullanılan modüller ve ad alanları için anahtar sözcüğünü kullanarak bu modülün veya ad alanının bir üyesine başvurduğunuzda, tam ad yerine adın kısa formunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0cf-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="be0cf-111">Bu anahtar sözcük `using` , `using namespace` Visual C++ ve Visual Basic içindeki C# anahtar sözcüğüne benzerdir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="be0cf-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="be0cf-112">Belirtilen modül veya ad alanı aynı projede veya başvurulan bir proje ya da derlemede olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="be0cf-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="be0cf-113">Yoksa, projeye bir başvuru ekleyebilir veya `-reference` komut satırı seçeneğini (ya da kısaltmasının `-r` ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0cf-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="be0cf-114">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="be0cf-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="be0cf-115">İçeri aktarma bildirimi, kapsayan ad alanı, modül veya dosyanın sonuna kadar, bildirimi izleyen koddaki adları kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="be0cf-116">Çoklu içeri aktarma bildirimleri kullandığınızda, bunlar ayrı satırlarda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="be0cf-117">Aşağıdaki kod, `open` kodu basitleştirmek için anahtar sözcüğünün kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="be0cf-118">Aynı ad birden fazla açık modülde veya ad alanında gerçekleştiğinde, F # derleyicisi bir hata veya uyarı göstermez.</span><span class="sxs-lookup"><span data-stu-id="be0cf-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="be0cf-119">Belirsizlikleri gerçekleştiğinde, F # daha yeni açılan modüle veya ad alanına tercih verir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="be0cf-120">Örneğin, aşağıdaki kodda hem hem de `empty` `Seq.empty` `empty` `List` modüllerinde bulunur `Seq` .</span><span class="sxs-lookup"><span data-stu-id="be0cf-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="be0cf-121">Bu nedenle, ya da gibi özdeş adlara sahip üyeler içeren veya gibi modülleri veya ad alanlarını açtığınızda dikkatli olun `List` `Seq` ; bunun yerine nitelikli adları kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="be0cf-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="be0cf-122">Kodun içeri aktarma bildirimlerinin sırasına bağlı olduğu herhangi bir durumu kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="be0cf-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="be0cf-123">Varsayılan olarak açık olan ad alanları</span><span class="sxs-lookup"><span data-stu-id="be0cf-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="be0cf-124">Bazı ad alanları, F # kodunda açık bir içeri aktarma bildirimine gerek kalmadan örtük olarak açıldıkları sıklıkla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be0cf-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="be0cf-125">Aşağıdaki tabloda varsayılan olarak açık olan ad alanları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="be0cf-126">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="be0cf-126">Namespace</span></span>|<span data-ttu-id="be0cf-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be0cf-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="be0cf-128">Ve gibi yerleşik türler için temel F # tür tanımlarını içerir `int` `float` .</span><span class="sxs-lookup"><span data-stu-id="be0cf-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="be0cf-129">Ve gibi temel aritmetik işlemleri içerir `+` `*` .</span><span class="sxs-lookup"><span data-stu-id="be0cf-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="be0cf-130">Ve gibi sabit koleksiyon sınıflarını içerir `List` `Array` .</span><span class="sxs-lookup"><span data-stu-id="be0cf-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="be0cf-131">Yavaş değerlendirme ve zaman uyumsuz iş akışları gibi denetim yapıları için türler içerir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="be0cf-132">İşlev gibi, biçimlendirilen GÇ işlevleri içerir `printf` .</span><span class="sxs-lookup"><span data-stu-id="be0cf-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="be0cf-133">Oto aç özniteliği</span><span class="sxs-lookup"><span data-stu-id="be0cf-133">AutoOpen Attribute</span></span>

<span data-ttu-id="be0cf-134">`AutoOpen`Derlemeye başvuruluyorsa bir ad alanını veya modülü otomatik olarak açmak istiyorsanız, özniteliği bir derlemeye uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0cf-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="be0cf-135">`AutoOpen`Üst modül veya ad alanı açıldığında bu modülü otomatik olarak açmak için bir modüle özniteliği de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0cf-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="be0cf-136">Daha fazla bilgi için bkz. [Core. oto Openattribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="be0cf-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="be0cf-137">RequireQualifiedAccess özniteliği</span><span class="sxs-lookup"><span data-stu-id="be0cf-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="be0cf-138">Bazı modüller, kayıtlar veya birleşim türleri `RequireQualifiedAccess` özniteliği belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="be0cf-139">Bu modüllerin, kayıtların veya birleşimlerin öğelerine başvurduğunuzda, bir içeri aktarma bildirimi eklenip eklenmeyeceğini fark etmeksizin nitelikli bir ad kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="be0cf-140">Bu özniteliği yaygın olarak kullanılan adları tanımlayan türler üzerinde stratejik olarak kullanırsanız, ad çakışmalarını önlemeyi ve bu sayede kodu kitaplıklarda değişikliklere daha dayanıklı hale getirmenize yardımcı olursunuz.</span><span class="sxs-lookup"><span data-stu-id="be0cf-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="be0cf-141">Daha fazla bilgi için bkz. [Core. RequireQualifiedAccessAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="be0cf-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="be0cf-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be0cf-142">See also</span></span>

- [<span data-ttu-id="be0cf-143">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="be0cf-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="be0cf-144">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="be0cf-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="be0cf-145">Modüller</span><span class="sxs-lookup"><span data-stu-id="be0cf-145">Modules</span></span>](modules.md)
