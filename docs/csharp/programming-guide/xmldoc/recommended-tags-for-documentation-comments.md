---
title: Belge açıklamaları için - önerilen etiketler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 7b2988273e7598b8653b3481c0ea713c5bb0f632
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415240"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="afa69-102">Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="afa69-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="afa69-103">C# Derleyici, kodunuzda belge açıklamaları işler ve bunları adı belirttiğiniz bir dosyasında XML olarak biçimlendirir **/doc** komut satırı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="afa69-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="afa69-104">Son belgeleri derleyici tarafından üretilen dosyaya dayalı oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="afa69-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="afa69-105">Etiketler, kod yapıları türleri gibi işlenir ve tür üyelerini.</span><span class="sxs-lookup"><span data-stu-id="afa69-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afa69-106">Belge açıklamaları için bir ad alanı uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="afa69-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="afa69-107">Derleyici, geçerli bir XML değil herhangi bir etiket işleyecektir.</span><span class="sxs-lookup"><span data-stu-id="afa69-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="afa69-108">Aşağıdaki kullanıcı belgeleri, genel olarak kullanılan işlevler sunar.</span><span class="sxs-lookup"><span data-stu-id="afa69-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="afa69-109">Etiketler</span><span class="sxs-lookup"><span data-stu-id="afa69-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="afa69-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="afa69-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="afa69-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="afa69-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="afa69-112">[\<bkz: >](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="afa69-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="afa69-113">\<kod ></span><span class="sxs-lookup"><span data-stu-id="afa69-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="afa69-114">[\<param >](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="afa69-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="afa69-115">[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="afa69-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="afa69-116">\<Örnek ></span><span class="sxs-lookup"><span data-stu-id="afa69-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="afa69-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="afa69-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="afa69-118">\<Summary ></span><span class="sxs-lookup"><span data-stu-id="afa69-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="afa69-119">[\<Özel Durum >](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="afa69-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="afa69-120">[\<izni >](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="afa69-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="afa69-121">[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="afa69-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="afa69-122">[\<Ekle >](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="afa69-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="afa69-123">\<REMARKS ></span><span class="sxs-lookup"><span data-stu-id="afa69-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="afa69-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="afa69-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="afa69-125">\<listesi ></span><span class="sxs-lookup"><span data-stu-id="afa69-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="afa69-126">\<döndürür ></span><span class="sxs-lookup"><span data-stu-id="afa69-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="afa69-127">\<Değer ></span><span class="sxs-lookup"><span data-stu-id="afa69-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="afa69-128">(\* derleyici sözdizimini doğrular gösterir.)</span><span class="sxs-lookup"><span data-stu-id="afa69-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="afa69-129">Açılı belgeleri açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="afa69-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="afa69-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afa69-130">See Also</span></span>

- [<span data-ttu-id="afa69-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="afa69-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="afa69-132">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="afa69-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [<span data-ttu-id="afa69-133">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="afa69-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
