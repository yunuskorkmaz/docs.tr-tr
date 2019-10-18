---
title: Belge açıklamaları için önerilen Etiketler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: d17ff0b78d8ae40916447e8e12da7948a21e5717
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523360"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="15aca-102">Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="15aca-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="15aca-103">C# Derleyici kodunuzda belge açıklamalarını işler ve adı **/doc** komut satırı SEÇENEĞINDE belirttiğiniz bir dosyada xml olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="15aca-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="15aca-104">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15aca-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="15aca-105">Etiketler, türler ve tür üyeleri gibi kod yapıları üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="15aca-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15aca-106">Belge açıklamaları bir ad alanına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="15aca-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="15aca-107">Derleyici geçerli XML olan herhangi bir etiketi işleyecek.</span><span class="sxs-lookup"><span data-stu-id="15aca-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="15aca-108">Aşağıdaki Etiketler kullanıcı belgelerinde genel olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="15aca-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="15aca-109">Etiketler</span><span class="sxs-lookup"><span data-stu-id="15aca-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="15aca-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="15aca-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="15aca-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="15aca-111">\<para></span></span>](./para.md)|<span data-ttu-id="15aca-112">[\<see >](./see.md) \*</span><span class="sxs-lookup"><span data-stu-id="15aca-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="15aca-113">\<code ></span><span class="sxs-lookup"><span data-stu-id="15aca-113">\<code></span></span>](./code.md)|<span data-ttu-id="15aca-114">[\<param >](./param.md) \*</span><span class="sxs-lookup"><span data-stu-id="15aca-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="15aca-115">[\<seealso >](./seealso.md) \*</span><span class="sxs-lookup"><span data-stu-id="15aca-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="15aca-116">\<example ></span><span class="sxs-lookup"><span data-stu-id="15aca-116">\<example></span></span>](./example.md)|[<span data-ttu-id="15aca-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="15aca-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="15aca-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="15aca-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="15aca-119">[\<exception >](./exception.md) \*</span><span class="sxs-lookup"><span data-stu-id="15aca-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="15aca-120">[\<permission >](./permission.md) \*</span><span class="sxs-lookup"><span data-stu-id="15aca-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="15aca-121">[\<typeparam >](./typeparam.md) \*</span><span class="sxs-lookup"><span data-stu-id="15aca-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="15aca-122">[\<include >](./include.md) \*</span><span class="sxs-lookup"><span data-stu-id="15aca-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="15aca-123">\<remarks ></span><span class="sxs-lookup"><span data-stu-id="15aca-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="15aca-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="15aca-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="15aca-125">\<list ></span><span class="sxs-lookup"><span data-stu-id="15aca-125">\<list></span></span>](./list.md)|[<span data-ttu-id="15aca-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="15aca-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="15aca-127">\<value></span><span class="sxs-lookup"><span data-stu-id="15aca-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="15aca-128">(\* derleyicinin söz dizimini doğruladığını gösterir.)</span><span class="sxs-lookup"><span data-stu-id="15aca-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="15aca-129">Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, `<` ve `>` HTML kodlamasını kullanın `&lt;` ve `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="15aca-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="15aca-130">Bu kodlama aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="15aca-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="15aca-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15aca-131">See also</span></span>

- [<span data-ttu-id="15aca-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="15aca-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="15aca-133">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="15aca-133">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="15aca-134">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="15aca-134">XML Documentation Comments</span></span>](./index.md)
