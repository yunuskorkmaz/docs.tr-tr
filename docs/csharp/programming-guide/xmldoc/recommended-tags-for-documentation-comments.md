---
title: Belge açıklamaları için önerilen Etiketler- C# Programlama Kılavuzu
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789721"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="e210d-102">Belge açıklamaları için önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e210d-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="e210d-103">C# Derleyici kodunuzda belge açıklamalarını işler ve adı **/doc** komut satırı SEÇENEĞINDE belirttiğiniz bir dosyada xml olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="e210d-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="e210d-104">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e210d-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="e210d-105">Etiketler, türler ve tür üyeleri gibi kod yapıları üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="e210d-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="e210d-106">Belge açıklamaları bir ad alanına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="e210d-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="e210d-107">Derleyici geçerli XML olan herhangi bir etiketi işleyecek.</span><span class="sxs-lookup"><span data-stu-id="e210d-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="e210d-108">Aşağıdaki Etiketler kullanıcı belgelerinde genel olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e210d-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="e210d-109">Etiketler</span><span class="sxs-lookup"><span data-stu-id="e210d-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="e210d-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="e210d-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="e210d-111">\<paragraf ></span><span class="sxs-lookup"><span data-stu-id="e210d-111">\<para></span></span>](./para.md)|<span data-ttu-id="e210d-112">[\<bkz. >](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="e210d-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="e210d-113">\<value></span><span class="sxs-lookup"><span data-stu-id="e210d-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="e210d-114">\<kodu ></span><span class="sxs-lookup"><span data-stu-id="e210d-114">\<code></span></span>](./code.md)|<span data-ttu-id="e210d-115">[\<param >](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="e210d-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="e210d-116">[\<seede >](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="e210d-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="e210d-117">\<örnek ></span><span class="sxs-lookup"><span data-stu-id="e210d-117">\<example></span></span>](./example.md)|[<span data-ttu-id="e210d-118">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="e210d-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="e210d-119">\<summary></span><span class="sxs-lookup"><span data-stu-id="e210d-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="e210d-120">[\<özel durum >](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="e210d-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="e210d-121">[\<izin >](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="e210d-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="e210d-122">[\<typeparam >](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="e210d-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="e210d-123">[\<> ekleme](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="e210d-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="e210d-124">\<açıklamalar ></span><span class="sxs-lookup"><span data-stu-id="e210d-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="e210d-125">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="e210d-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="e210d-126">\<listesi ></span><span class="sxs-lookup"><span data-stu-id="e210d-126">\<list></span></span>](./list.md)|[<span data-ttu-id="e210d-127">\<devralma belgesi ></span><span class="sxs-lookup"><span data-stu-id="e210d-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="e210d-128">\<returns></span><span class="sxs-lookup"><span data-stu-id="e210d-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="e210d-129">(\* derleyicinin söz dizimini doğruladığını gösterir.)</span><span class="sxs-lookup"><span data-stu-id="e210d-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="e210d-130">Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, `<` ve `>` HTML kodlamasını kullanın `&lt;` ve `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="e210d-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="e210d-131">Bu kodlama aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e210d-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="e210d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e210d-132">See also</span></span>

- [<span data-ttu-id="e210d-133">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e210d-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e210d-134">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e210d-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="e210d-135">XML belge açıklamaları</span><span class="sxs-lookup"><span data-stu-id="e210d-135">XML documentation comments</span></span>](./index.md)
