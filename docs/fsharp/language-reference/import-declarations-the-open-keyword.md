---
title: 'İçeri aktarma bildirimleri: Open anahtar sözcüğü'
description: Hakkında bilgi edinin F# bildirimleri ve bir modülde veya öğeleri bir tam adı kullanmadan başvuru ad alanı nasıl belirlediği içeri aktarın.
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937507"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="c26a7-103">İçeri aktarma bildirimleri: `open` Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c26a7-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="c26a7-104">Bu makaledeki API başvuru bağlantıları için MSDN sürer.</span><span class="sxs-lookup"><span data-stu-id="c26a7-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="c26a7-105">Docs.microsoft.com API başvuru tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="c26a7-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="c26a7-106">Bir *bildirim alma* bir modülde veya öğeleri bir tam adı kullanmadan başvuru ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="c26a7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c26a7-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="c26a7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c26a7-108">Remarks</span></span>

<span data-ttu-id="c26a7-109">Tam ad alanında veya modülde yolunu kullanarak kod başvuran her yazma, okunması ve düzenlenmesi zor kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c26a7-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="c26a7-110">Bunun yerine kullanabileceğiniz `open` anahtar sözcüğü için sık kullanılan modüller ve ad alanları böylece, modül veya isim uzayı üyesi başvurduğunuzda adının kısa formunu yerine tam adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c26a7-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="c26a7-111">Bu anahtar sözcük benzer `using` C# anahtar sözcüğü `using namespace` Visual C++ ' ta ve `Imports` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="c26a7-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="c26a7-112">Modülün veya sağlanan ad alanı, aynı projede veya başvurulan proje ya da derleme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c26a7-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="c26a7-113">Yüklü değilse, projeye bir başvuru ekleyin, veya kullanın `-reference` komut`-`satırı seçeneğini (veya eşlememiz `-r`).</span><span class="sxs-lookup"><span data-stu-id="c26a7-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="c26a7-114">Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="c26a7-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="c26a7-115">İçeri aktarma bildirimi, ad kapsayan ad alanı, modül veya dosya sonuna kadar bildirimi, aşağıdaki kod kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="c26a7-116">Birden çok içeri aktarma bildirimleri kullandığınızda, ayrı satırlarda görünmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="c26a7-117">Aşağıdaki kod kullanımını gösterir `open` kodu basitleştirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c26a7-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="c26a7-118">F# Derleyici ktıları bir hata veya uyarı belirsizlikleri aynı adlı birden fazla açık bir modülde veya ad alanı içinde oluştuğunda meydana geldiğinde.</span><span class="sxs-lookup"><span data-stu-id="c26a7-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="c26a7-119">Belirsizlikler meydana geldiğinde F# tercihi daha açık bir modülde veya ad alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c26a7-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="c26a7-120">Örneğin, aşağıdaki kodda, `empty` anlamına gelir `Seq.empty`rağmen `empty` her ikisinde de bulunuyorsa `List` ve `Seq` modüller.</span><span class="sxs-lookup"><span data-stu-id="c26a7-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="c26a7-121">Modüllerde veya ad gibi açtığınızda, bu nedenle dikkatli olun `List` veya `Seq` aynı adlara sahip; bunun yerine, nitelikli adlar kullanmayı üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="c26a7-122">Kod üzerinde içeri aktarma bildirimleri sırasını bağımlı olduğu tüm durumlarda kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="c26a7-123">Varsayılan olarak açık olan ad alanları</span><span class="sxs-lookup"><span data-stu-id="c26a7-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="c26a7-124">Bazı ad alanları, sık sık kullanılır F# kod, örtük olarak açık içeri aktarma bildirimi gerek kalmadan açılmadı.</span><span class="sxs-lookup"><span data-stu-id="c26a7-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="c26a7-125">Aşağıdaki tabloda, varsayılan olarak açık olan ad alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="c26a7-126">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="c26a7-126">Namespace</span></span>|<span data-ttu-id="c26a7-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c26a7-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="c26a7-128">Temel içeren F# yerleşik türleri için tanımları gibi yazın `int` ve `float`.</span><span class="sxs-lookup"><span data-stu-id="c26a7-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="c26a7-129">Temel aritmetik işlemleri gibi içeren `+` ve `*`.</span><span class="sxs-lookup"><span data-stu-id="c26a7-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="c26a7-130">Değişmez koleksiyon sınıfları içeren `List` ve `Array`.</span><span class="sxs-lookup"><span data-stu-id="c26a7-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="c26a7-131">Geç değerlendirme ve zaman uyumsuz iş akışları gibi denetim yapıları için türler içerir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="c26a7-132">Biçimlendirilmiş g/ç için gibi işlevler içeren `printf` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c26a7-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="c26a7-133">AutoOpen özniteliği</span><span class="sxs-lookup"><span data-stu-id="c26a7-133">AutoOpen Attribute</span></span>

<span data-ttu-id="c26a7-134">Uygulayabileceğiniz `AutoOpen` derlemeye başvurulduğundan, otomatik olarak bir ad alanında veya modülde açmak isteyip istemediğiniz bir bütünleştirilmiş kod özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c26a7-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="c26a7-135">Ayrıca uygulayabilirsiniz `AutoOpen` öznitelik üst modülde veya ad alanı açıldığında otomatik olarak bu modülü açmak için bir modül.</span><span class="sxs-lookup"><span data-stu-id="c26a7-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="c26a7-136">Daha fazla bilgi için [Core.AutoOpenAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="c26a7-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="c26a7-137">RequireQualifiedAccess özniteliği</span><span class="sxs-lookup"><span data-stu-id="c26a7-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="c26a7-138">Bazı modüller, kayıtlar veya birleşim türleri belirtebilir `RequireQualifiedAccess` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c26a7-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="c26a7-139">Bu modüller, kayıtlar ve birleşimler öğeleri başvurduğunuzda, içeri aktarma bildirimi içerip bağımsız olarak bir tam adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c26a7-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="c26a7-140">Bu öznitelik stratejik üzerinde kullanırsanız, yaygın olarak tanımlayan türler kullanılan adları, ad çakışmalarını önlemek ve böylece kod daha dayanıklı kitaplıkları değişiklikler yapmak yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c26a7-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="c26a7-141">Daha fazla bilgi için [Core.RequireQualifiedAccessAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="c26a7-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="c26a7-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c26a7-142">See also</span></span>

- [<span data-ttu-id="c26a7-143">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c26a7-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c26a7-144">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="c26a7-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="c26a7-145">Modüller</span><span class="sxs-lookup"><span data-stu-id="c26a7-145">Modules</span></span>](modules.md)
