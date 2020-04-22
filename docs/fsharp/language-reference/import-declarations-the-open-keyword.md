---
title: 'İçeri Aktarma Bildirimleri: open Anahtar Sözcüğü'
description: F# alma bildirimleri ve tam nitelikli bir ad kullanmadan başvuruda bulunabileceğiniz bir modülü veya ad alanını nasıl belirttikleri hakkında bilgi edinin.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021536"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="fa230-103">İthalat Bildirimleri: `open` Anahtar Kelime</span><span class="sxs-lookup"><span data-stu-id="fa230-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="fa230-104">Bu makaledeki API başvuru bağlantıları sizi MSDN'ye götürür.</span><span class="sxs-lookup"><span data-stu-id="fa230-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="fa230-105">docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="fa230-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="fa230-106">*Alma bildirimi,* tam nitelikli bir ad kullanmadan öğelerine başvuruyapabileceğiniz bir modül veya ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa230-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa230-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa230-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="fa230-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa230-108">Remarks</span></span>

<span data-ttu-id="fa230-109">Kodu, her seferinde tam nitelikli ad alanı veya modül yolunu kullanarak başvurmak, yazması, okunması ve bakımı zor kodlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="fa230-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="fa230-110">Bunun yerine, sık `open` kullanılan modüller ve ad alanları için anahtar sözcüğü kullanabilirsiniz, böylece bu modülün veya ad alanının bir üyesine başvuruyaptığınızda, tam nitelikli ad yerine adın kısa biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa230-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="fa230-111">Bu anahtar kelime C#, `using` `using namespace` Visual C++'daki ve `Imports` Visual Basic'teki anahtar kelimeye benzer.</span><span class="sxs-lookup"><span data-stu-id="fa230-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="fa230-112">Sağlanan modül veya ad alanı aynı projede veya başvurulan proje veya derlemede olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa230-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="fa230-113">Değilse, projeye bir başvuru ekleyebilir veya `-reference` komut satırı seçeneğini (veya kısaltmasını) `-r`kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa230-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="fa230-114">Daha fazla bilgi için [Derleyici Seçenekleri'ne](compiler-options.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fa230-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="fa230-115">Alma bildirimi, adları, çevreleyen ad alanının, modülün veya dosyanın sonuna kadar, bildirimi izleyen kodda kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fa230-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="fa230-116">Birden çok alma bildirimi kullandığınızda, bunlar ayrı satırlarda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa230-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="fa230-117">Aşağıdaki kod, kodu basitleştirmek için `open` anahtar kelimenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa230-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="fa230-118">F# derleyicisi, aynı ad birden fazla açık modülveya ad alanında oluştuğunda belirsizlikler oluştuğunda bir hata veya uyarı yayar.</span><span class="sxs-lookup"><span data-stu-id="fa230-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="fa230-119">Belirsizlikler oluştuğunda, F# daha yeni açılan modülü veya ad alanını tercih verir.</span><span class="sxs-lookup"><span data-stu-id="fa230-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="fa230-120">Örneğin, aşağıdaki kodda, `empty` `Seq.empty`hem `empty` `Seq` modüllerde hem de `List` modüllerde bulunmasına rağmen , anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fa230-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="fa230-121">Bu nedenle, modülleri veya aynı adlara `List` `Seq` sahip üyeler içeren ad alanlarını açtığınızda dikkatli olun; bunun yerine, nitelikli adları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fa230-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="fa230-122">Kodun alma bildirimlerinin sırasına bağlı olduğu herhangi bir durumdan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="fa230-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="fa230-123">Varsayılan Olarak Açık Olan Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="fa230-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="fa230-124">Bazı ad alanları F# kodunda o kadar sık kullanılır ki, açık bir alma bildirimine gerek kalmadan örtülü olarak açılırlar.</span><span class="sxs-lookup"><span data-stu-id="fa230-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="fa230-125">Aşağıdaki tablo, varsayılan olarak açık olan ad alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa230-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="fa230-126">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="fa230-126">Namespace</span></span>|<span data-ttu-id="fa230-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa230-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="fa230-128">Dahili türleri için temel F# türü `int` tanımları içerir ve. `float`</span><span class="sxs-lookup"><span data-stu-id="fa230-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="fa230-129">Gibi temel aritmetik `+` işlemleri `*`içerir ve.</span><span class="sxs-lookup"><span data-stu-id="fa230-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="fa230-130">Gibi değişmez toplama sınıfları `List` `Array`içerir ve.</span><span class="sxs-lookup"><span data-stu-id="fa230-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="fa230-131">Tembel değerlendirme ve eşzamanlı iş akışları gibi denetim yapıları için türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fa230-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="fa230-132">İşlev gibi biçimlendirilmiş IO `printf` işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fa230-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="fa230-133">OtomatikAçık Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa230-133">AutoOpen Attribute</span></span>

<span data-ttu-id="fa230-134">Derleme başvurulduğunda bir ad alanı veya modülü otomatik olarak açmak istiyorsanız özniteliği bir derlemeye uygulayabilirsiniz. `AutoOpen`</span><span class="sxs-lookup"><span data-stu-id="fa230-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="fa230-135">Ana modül veya `AutoOpen` ad alanı açıldığında bu modülü otomatik olarak açmak için bir modüle özniteliği de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa230-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="fa230-136">Daha fazla bilgi için [Core.AutoOpenAttribute Class'a](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)bakın.</span><span class="sxs-lookup"><span data-stu-id="fa230-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="fa230-137">Kalifiye Erişim Özniteliği Gerektirir</span><span class="sxs-lookup"><span data-stu-id="fa230-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="fa230-138">Bazı modüller, kayıtlar veya birleşim türleri özniteliği belirtebilir. `RequireQualifiedAccess`</span><span class="sxs-lookup"><span data-stu-id="fa230-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="fa230-139">Bu modüllerin, kayıtların veya birliş öğelerine başvururken, bir alma bildirimi ekleyip eklemediğinize bakılmaksızın nitelikli bir ad kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa230-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="fa230-140">Bu özniteliği, yaygın olarak kullanılan adları tanımlayan türler üzerinde stratejik olarak kullanırsanız, ad çakışmalarını önlemeye yardımcı olur ve böylece kodu kitaplıktaki değişikliklere karşı daha esnek hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa230-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="fa230-141">Daha fazla bilgi için [Core.RequireQualifiedAccessAttribute Class'a](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)bakın.</span><span class="sxs-lookup"><span data-stu-id="fa230-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa230-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa230-142">See also</span></span>

- [<span data-ttu-id="fa230-143">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="fa230-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="fa230-144">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="fa230-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="fa230-145">Modüller</span><span class="sxs-lookup"><span data-stu-id="fa230-145">Modules</span></span>](modules.md)
