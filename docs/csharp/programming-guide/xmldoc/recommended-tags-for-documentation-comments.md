---
title: Belge açıklamaları için önerilen Etiketler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 4506402c85096ae0ae11b28ad03646c7fa215e5a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587819"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="04669-102">Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="04669-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="04669-103">C# Derleyici kodunuzda belge açıklamalarını işler ve adı **/doc** komut satırı SEÇENEĞINDE belirttiğiniz bir dosyada xml olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="04669-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="04669-104">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04669-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="04669-105">Etiketler, türler ve tür üyeleri gibi kod yapıları üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="04669-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04669-106">Belge açıklamaları bir ad alanına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="04669-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="04669-107">Derleyici geçerli XML olan herhangi bir etiketi işleyecek.</span><span class="sxs-lookup"><span data-stu-id="04669-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="04669-108">Aşağıdaki Etiketler kullanıcı belgelerinde genel olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="04669-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="04669-109">Etiketler</span><span class="sxs-lookup"><span data-stu-id="04669-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="04669-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="04669-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="04669-111">\<Para ></span><span class="sxs-lookup"><span data-stu-id="04669-111">\<para></span></span>](./para.md)|<span data-ttu-id="04669-112">[\<bkz. >](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="04669-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="04669-113">\<kod ></span><span class="sxs-lookup"><span data-stu-id="04669-113">\<code></span></span>](./code.md)|<span data-ttu-id="04669-114">[\<param >](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="04669-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="04669-115">[\<SeeAlso >](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="04669-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="04669-116">\<örnek ></span><span class="sxs-lookup"><span data-stu-id="04669-116">\<example></span></span>](./example.md)|[<span data-ttu-id="04669-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="04669-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="04669-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="04669-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="04669-119">[\<özel durum >](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="04669-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="04669-120">[\<izin >](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="04669-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="04669-121">[\<typeparam >](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="04669-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="04669-122">[\<> dahil et](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="04669-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="04669-123">\<açıklamalar ></span><span class="sxs-lookup"><span data-stu-id="04669-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="04669-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="04669-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="04669-125">\<Liste ></span><span class="sxs-lookup"><span data-stu-id="04669-125">\<list></span></span>](./list.md)|[<span data-ttu-id="04669-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="04669-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="04669-127">\<value></span><span class="sxs-lookup"><span data-stu-id="04669-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="04669-128">(\* derleyicinin söz dizimini doğruladığını gösterir.)</span><span class="sxs-lookup"><span data-stu-id="04669-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="04669-129">Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız `<` , ve `&gt;` sırasıyla ve `>` olan `&lt;` HTML kodlamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="04669-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="04669-130">Bu kodlama aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="04669-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="04669-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04669-131">See also</span></span>

- [<span data-ttu-id="04669-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="04669-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04669-133">/Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="04669-133">/doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="04669-134">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="04669-134">XML Documentation Comments</span></span>](./index.md)
