---
title: Belge açıklamaları için - önerilen etiketler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: a6d07b6c288ebbe24c9cf5c531ef333946855f82
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204723"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="917a2-102">Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="917a2-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="917a2-103">C# Derleyici, kodunuzda belge açıklamaları işler ve bunları adı belirttiğiniz bir dosyasında XML olarak biçimlendirir **/doc** komut satırı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="917a2-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="917a2-104">Son belgeleri derleyici tarafından üretilen dosyaya dayalı oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="917a2-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="917a2-105">Etiketler, kod yapıları türleri gibi işlenir ve tür üyelerini.</span><span class="sxs-lookup"><span data-stu-id="917a2-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="917a2-106">Belge açıklamaları için bir ad alanı uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="917a2-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="917a2-107">Derleyici, geçerli bir XML değil herhangi bir etiket işleyecektir.</span><span class="sxs-lookup"><span data-stu-id="917a2-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="917a2-108">Aşağıdaki kullanıcı belgeleri, genel olarak kullanılan işlevler sunar.</span><span class="sxs-lookup"><span data-stu-id="917a2-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="917a2-109">Etiketler</span><span class="sxs-lookup"><span data-stu-id="917a2-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="917a2-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="917a2-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="917a2-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="917a2-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="917a2-112">[\<bkz: >](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="917a2-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="917a2-113">\<kod ></span><span class="sxs-lookup"><span data-stu-id="917a2-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="917a2-114">[\<param >](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="917a2-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="917a2-115">[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="917a2-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="917a2-116">\<Örnek ></span><span class="sxs-lookup"><span data-stu-id="917a2-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="917a2-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="917a2-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="917a2-118">\<Summary ></span><span class="sxs-lookup"><span data-stu-id="917a2-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="917a2-119">[\<Özel Durum >](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="917a2-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="917a2-120">[\<izni >](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="917a2-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="917a2-121">[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="917a2-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="917a2-122">[\<Ekle >](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="917a2-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="917a2-123">\<REMARKS ></span><span class="sxs-lookup"><span data-stu-id="917a2-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="917a2-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="917a2-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="917a2-125">\<listesi ></span><span class="sxs-lookup"><span data-stu-id="917a2-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="917a2-126">\<döndürür ></span><span class="sxs-lookup"><span data-stu-id="917a2-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="917a2-127">\<Değer ></span><span class="sxs-lookup"><span data-stu-id="917a2-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="917a2-128">(\* derleyici sözdizimini doğrular gösterir.)</span><span class="sxs-lookup"><span data-stu-id="917a2-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="917a2-129">Açılı belgeleri açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="917a2-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="917a2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="917a2-130">See also</span></span>

- [<span data-ttu-id="917a2-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="917a2-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="917a2-132">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="917a2-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="917a2-133">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="917a2-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
