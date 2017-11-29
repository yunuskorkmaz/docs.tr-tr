---
title: "İçeri Aktarma Bildirimleri: open Anahtar Sözcüğü (F#)"
description: "F # içeri aktarma bildirimleri ve bunların nasıl bir modül veya ad alanı belirtin bir tam ad kullanmadan başvuru öğeleri öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1e98e48c-52e9-4314-8954-85d5583125f0
ms.openlocfilehash: a6d79bed3dd202657d06956edf9499a9b21a5f03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="a6ca9-104">İçeri aktarma bildirimleri: `open` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a6ca9-104">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="a6ca9-105">Bu makalede API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="a6ca9-106">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="a6ca9-107">Bir *bildirimi almak* bir modüle ya da öğeleri bir tam ad kullanmadan başvuru isim belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-107">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="a6ca9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6ca9-108">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="a6ca9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6ca9-109">Remarks</span></span>
<span data-ttu-id="a6ca9-110">Tam ad veya modülü yolunu kullanarak kod başvuran her yazma, okuma ve Bakım sabit kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-110">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="a6ca9-111">Bunun yerine, kullanabileceğiniz `open` anahtar sözcüğü için sık kullanılan modülleri ve ad alanlarını böylece, modül veya ad alanı üyesi başvurduğunuzda tam adı yerine kısa formun adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-111">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="a6ca9-112">Bu anahtar sözcük benzer `using` C# anahtar sözcüğü `using namespace` Visual C++ ' ta ve `Imports` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-112">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="a6ca9-113">Modüle ya da sağlanan ad alanı aynı projede veya başvurulan proje ya da derleme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-113">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="a6ca9-114">Değilse, projesine bir başvuru ekleyin, veya kullanın `-reference` komutu`-`satır seçeneği (ya da kendi kısaltmayı `-r`).</span><span class="sxs-lookup"><span data-stu-id="a6ca9-114">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="a6ca9-115">Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a6ca9-115">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="a6ca9-116">Alma bildirimi adlarını kapsayan ad alanı, modül veya dosya sonuna kadar bildirimi aşağıdaki kodda kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-116">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="a6ca9-117">Birden çok içeri aktarma bildirimleri kullandığınızda, ayrı satırlara görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-117">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="a6ca9-118">Aşağıdaki kod kullanımı gösterilmiştir `open` kodu basitleştirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-118">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="a6ca9-119">Aynı adlı birden fazla açık modülü veya ad alanı oluştuğunda belirsizlikleri oluştuğunda F # derleyici bir hata veya uyarı yayma değil.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-119">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="a6ca9-120">Belirsizlikleri gerçekleştiğinde, F # tercih daha yakın zamanda açılan modülü veya ad alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-120">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="a6ca9-121">Örneğin, aşağıdaki kodda, `empty` anlamına gelir `Seq.empty`rağmen `empty` ikisinde bulunan `List` ve `Seq` modüller.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-121">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="a6ca9-122">Modülleri veya ad alanları gibi açtığınızda, bu nedenle dikkatli olun `List` veya `Seq` aynı adlara sahip; bunun yerine, tam ad kullanmayı deneyin üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-122">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="a6ca9-123">Kod içeri aktarma bildirimleri sırasını bağımlı olduğu tüm durumlarda kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-123">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="a6ca9-124">Varsayılan olarak açık olan ad alanları</span><span class="sxs-lookup"><span data-stu-id="a6ca9-124">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="a6ca9-125">Bazı ad alanlarının, bunlar örtük olarak bir açık alma bildirimi gerek olmadan açıldığından F # kodunda çok sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-125">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="a6ca9-126">Aşağıdaki tabloda, varsayılan olarak açık olan ad alanları gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-126">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="a6ca9-127">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a6ca9-127">Namespace</span></span>|<span data-ttu-id="a6ca9-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6ca9-128">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="a6ca9-129">Temel F # için tür tanımları yerleşik türleri gibi içeren `int` ve `float`.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-129">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="a6ca9-130">Temel aritmetik işlemler gibi içeren `+` ve `*`.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-130">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="a6ca9-131">Değişmez koleksiyon sınıfları içerir `List` ve `Array`.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-131">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="a6ca9-132">Denetim yapıları geç değerlendirme ve zaman uyumsuz iş akışları gibi türler içerir.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-132">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="a6ca9-133">Biçimlendirilmiş g/ç için gibi işlevler içeren `printf` işlevi.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-133">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="a6ca9-134">AutoOpen özniteliği</span><span class="sxs-lookup"><span data-stu-id="a6ca9-134">AutoOpen Attribute</span></span>
<span data-ttu-id="a6ca9-135">Uygulayabileceğiniz `AutoOpen` derleme başvurulduğunda bir ad alanı veya modülü otomatik olarak açmak istiyorsanız, bir derlemede özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-135">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="a6ca9-136">Ayrıca uygulayabilirsiniz `AutoOpen` öznitelik üst modüle ya da ad alanı açıldığında otomatik olarak bu modülü açmak için bir modül.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-136">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="a6ca9-137">Daha fazla bilgi için bkz: [Core.AutoOpenAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="a6ca9-137">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="a6ca9-138">RequireQualifiedAccess özniteliği</span><span class="sxs-lookup"><span data-stu-id="a6ca9-138">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="a6ca9-139">Bazı modüller, kayıtları ya da birleşim türlerini belirtmek `RequireQualifiedAccess` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-139">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="a6ca9-140">Bu modüller, kayıtları veya birleşimler öğeleri başvuru yaptığınızda, bir içeri aktarma bildirimi içerip bağımsız olarak bir tam ad kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-140">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="a6ca9-141">Bu öznitelik stratejik üzerinde kullanıyorsanız, yaygın olarak tanımlayan türler kullanılan adları, ad çakışmaları önlemek ve böylece kodu daha esnektir kitaplıklarında değişiklikler yapmak yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-141">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="a6ca9-142">Daha fazla bilgi için bkz: [Core.RequireQualifiedAccessAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="a6ca9-142">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="a6ca9-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6ca9-143">See Also</span></span>
[<span data-ttu-id="a6ca9-144"># Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a6ca9-144"># Language Reference</span></span>](index.md)

[<span data-ttu-id="a6ca9-145">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="a6ca9-145">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="a6ca9-146">Modülleri</span><span class="sxs-lookup"><span data-stu-id="a6ca9-146">Modules</span></span>](modules.md)

