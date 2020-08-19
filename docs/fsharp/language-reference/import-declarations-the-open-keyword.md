---
title: 'İçeri Aktarma Bildirimleri: open Anahtar Sözcüğü'
description: 'F # içeri aktarma bildirimleri hakkında bilgi edinin ve öğelerin tam nitelikli bir ad kullanmadan başvurdukları bir modül veya ad alanı belirtmeleri hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: 6420df071f86159c44606c2710331d5f587023cc
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557613"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="5e9d3-103">İçeri aktarma bildirimleri: `open` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="5e9d3-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="5e9d3-104">*İçeri aktarma bildirimi* , öğelerini tam nitelikli bir ad kullanmadan başvuralabileceğiniz bir modül veya ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e9d3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e9d3-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="5e9d3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e9d3-106">Remarks</span></span>

<span data-ttu-id="5e9d3-107">Her seferinde tam nitelikli ad alanı veya modül yolunu kullanarak koda başvurmak, yazmak, okumak ve sürdürmek zor olan kod oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-107">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="5e9d3-108">Bunun yerine `open` sık kullanılan modüller ve ad alanları için anahtar sözcüğünü kullanarak bu modülün veya ad alanının bir üyesine başvurduğunuzda, tam ad yerine adın kısa formunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-108">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="5e9d3-109">Bu anahtar sözcük `using` , `using namespace` Visual C++ ve Visual Basic içindeki C# anahtar sözcüğüne benzerdir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="5e9d3-109">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="5e9d3-110">Belirtilen modül veya ad alanı aynı projede veya başvurulan bir proje ya da derlemede olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-110">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="5e9d3-111">Yoksa, projeye bir başvuru ekleyebilir veya `-reference` komut satırı seçeneğini (ya da kısaltmasının `-r` ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-111">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="5e9d3-112">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="5e9d3-112">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="5e9d3-113">İçeri aktarma bildirimi, kapsayan ad alanı, modül veya dosyanın sonuna kadar, bildirimi izleyen koddaki adları kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-113">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="5e9d3-114">Çoklu içeri aktarma bildirimleri kullandığınızda, bunlar ayrı satırlarda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-114">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="5e9d3-115">Aşağıdaki kod, `open` kodu basitleştirmek için anahtar sözcüğünün kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-115">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="5e9d3-116">Aynı ad birden fazla açık modülde veya ad alanında gerçekleştiğinde, F # derleyicisi bir hata veya uyarı göstermez.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-116">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="5e9d3-117">Belirsizlikleri gerçekleştiğinde, F # daha yeni açılan modüle veya ad alanına tercih verir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-117">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="5e9d3-118">Örneğin, aşağıdaki kodda hem hem de `empty` `Seq.empty` `empty` `List` modüllerinde bulunur `Seq` .</span><span class="sxs-lookup"><span data-stu-id="5e9d3-118">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="5e9d3-119">Bu nedenle, ya da gibi özdeş adlara sahip üyeler içeren veya gibi modülleri veya ad alanlarını açtığınızda dikkatli olun `List` `Seq` ; bunun yerine nitelikli adları kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-119">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="5e9d3-120">Kodun içeri aktarma bildirimlerinin sırasına bağlı olduğu herhangi bir durumu kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-120">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="5e9d3-121">Varsayılan olarak açık olan ad alanları</span><span class="sxs-lookup"><span data-stu-id="5e9d3-121">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="5e9d3-122">Bazı ad alanları, F # kodunda açık bir içeri aktarma bildirimine gerek kalmadan örtük olarak açıldıkları sıklıkla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-122">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="5e9d3-123">Aşağıdaki tabloda varsayılan olarak açık olan ad alanları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-123">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="5e9d3-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5e9d3-124">Namespace</span></span>|<span data-ttu-id="5e9d3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9d3-125">Description</span></span>|
|---------|-----------|
|`FSharp.Core`|<span data-ttu-id="5e9d3-126">Ve gibi yerleşik türler için temel F # tür tanımlarını içerir `int` `float` .</span><span class="sxs-lookup"><span data-stu-id="5e9d3-126">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`FSharp.Core.Operators`|<span data-ttu-id="5e9d3-127">Ve gibi temel aritmetik işlemleri içerir `+` `*` .</span><span class="sxs-lookup"><span data-stu-id="5e9d3-127">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`FSharp.Collections`|<span data-ttu-id="5e9d3-128">Ve gibi sabit koleksiyon sınıflarını içerir `List` `Array` .</span><span class="sxs-lookup"><span data-stu-id="5e9d3-128">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`FSharp.Control`|<span data-ttu-id="5e9d3-129">Yavaş değerlendirme ve zaman uyumsuz iş akışları gibi denetim yapıları için türler içerir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-129">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`FSharp.Text`|<span data-ttu-id="5e9d3-130">İşlev gibi, biçimlendirilen GÇ işlevleri içerir `printf` .</span><span class="sxs-lookup"><span data-stu-id="5e9d3-130">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="5e9d3-131">Oto aç özniteliği</span><span class="sxs-lookup"><span data-stu-id="5e9d3-131">AutoOpen Attribute</span></span>

<span data-ttu-id="5e9d3-132">`AutoOpen`Derlemeye başvuruluyorsa bir ad alanını veya modülü otomatik olarak açmak istiyorsanız, özniteliği bir derlemeye uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-132">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="5e9d3-133">`AutoOpen`Üst modül veya ad alanı açıldığında bu modülü otomatik olarak açmak için bir modüle özniteliği de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-133">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="5e9d3-134">Daha fazla bilgi için bkz. [oto Openattribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span><span class="sxs-lookup"><span data-stu-id="5e9d3-134">For more information, see [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="5e9d3-135">RequireQualifiedAccess özniteliği</span><span class="sxs-lookup"><span data-stu-id="5e9d3-135">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="5e9d3-136">Bazı modüller, kayıtlar veya birleşim türleri `RequireQualifiedAccess` özniteliği belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-136">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="5e9d3-137">Bu modüllerin, kayıtların veya birleşimlerin öğelerine başvurduğunuzda, bir içeri aktarma bildirimi eklenip eklenmeyeceğini fark etmeksizin nitelikli bir ad kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-137">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="5e9d3-138">Bu özniteliği yaygın olarak kullanılan adları tanımlayan türler üzerinde stratejik olarak kullanırsanız, ad çakışmalarını önlemeyi ve bu sayede kodu kitaplıklarda değişikliklere daha dayanıklı hale getirmenize yardımcı olursunuz.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-138">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="5e9d3-139">Daha fazla bilgi için bkz. [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span><span class="sxs-lookup"><span data-stu-id="5e9d3-139">For more information, see [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e9d3-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e9d3-140">See also</span></span>

- [<span data-ttu-id="5e9d3-141">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="5e9d3-141">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5e9d3-142">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="5e9d3-142">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="5e9d3-143">Modül</span><span class="sxs-lookup"><span data-stu-id="5e9d3-143">Modules</span></span>](modules.md)
