---
title: Dokümantasyon yorumları için önerilen etiketler - C# programlama kılavuzu
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789721"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="4e5ad-102">Dokümantasyon yorumları için önerilen etiketler (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4e5ad-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="4e5ad-103">C# derleyicisi, **/doc** komut satırı seçeneğinde adını belirttiğiniz bir dosyada belgeleri kodunuzdaki belgeleri işler ve XML olarak biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="4e5ad-104">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="4e5ad-105">Etiketler, tür ve tür üyeleri gibi kod yapılarında işlenir.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="4e5ad-106">Belge açıklamaları bir ad alanına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="4e5ad-107">Derleyici, geçerli olan herhangi bir etiketi XML'i işler.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="4e5ad-108">Aşağıdaki etiketler, kullanıcı belgelerinde genel olarak kullanılan işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="4e5ad-109">Etiketler</span><span class="sxs-lookup"><span data-stu-id="4e5ad-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="4e5ad-110">\<c></span><span class="sxs-lookup"><span data-stu-id="4e5ad-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="4e5ad-111">\<para></span><span class="sxs-lookup"><span data-stu-id="4e5ad-111">\<para></span></span>](./para.md)|<span data-ttu-id="4e5ad-112">[\<bkz.>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="4e5ad-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="4e5ad-113">\<değer></span><span class="sxs-lookup"><span data-stu-id="4e5ad-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="4e5ad-114">\<kod></span><span class="sxs-lookup"><span data-stu-id="4e5ad-114">\<code></span></span>](./code.md)|<span data-ttu-id="4e5ad-115">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="4e5ad-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="4e5ad-116">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="4e5ad-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="4e5ad-117">\<örnek></span><span class="sxs-lookup"><span data-stu-id="4e5ad-117">\<example></span></span>](./example.md)|[<span data-ttu-id="4e5ad-118">\<paramref></span><span class="sxs-lookup"><span data-stu-id="4e5ad-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="4e5ad-119">\<özet></span><span class="sxs-lookup"><span data-stu-id="4e5ad-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="4e5ad-120">[\<özel durum>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="4e5ad-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="4e5ad-121">[\<izin>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="4e5ad-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="4e5ad-122">[\<typeparam>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="4e5ad-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="4e5ad-123">[\<>dahil](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="4e5ad-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="4e5ad-124">\<açıklamalar></span><span class="sxs-lookup"><span data-stu-id="4e5ad-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="4e5ad-125">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="4e5ad-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="4e5ad-126">\<liste></span><span class="sxs-lookup"><span data-stu-id="4e5ad-126">\<list></span></span>](./list.md)|[<span data-ttu-id="4e5ad-127">\<kalıtsal doc></span><span class="sxs-lookup"><span data-stu-id="4e5ad-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="4e5ad-128">\<>döndürür</span><span class="sxs-lookup"><span data-stu-id="4e5ad-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="4e5ad-129">(\* derleyicinin sözdizimini doğruladığını gösterir.)</span><span class="sxs-lookup"><span data-stu-id="4e5ad-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="4e5ad-130">Bir belge açıklama metninde açı braketlerinin görünmesini istiyorsanız, html `<` kodlamasını `&lt;` ve `&gt;` `>` sırasıyla ve sırasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="4e5ad-131">Bu kodlama aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="4e5ad-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e5ad-132">See also</span></span>

- [<span data-ttu-id="4e5ad-133">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4e5ad-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4e5ad-134">-doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4e5ad-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="4e5ad-135">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="4e5ad-135">XML documentation comments</span></span>](./index.md)
