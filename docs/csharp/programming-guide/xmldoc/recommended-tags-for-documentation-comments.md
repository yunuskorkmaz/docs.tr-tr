---
title: "Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d558bbe58d1f4a1c290b4f36718293d5ba1c734
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="74d93-102">Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="74d93-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="74d93-103">C# Derleyici, kodundaki belge açıklamaları işler ve bunları adı belirttiğiniz bir dosyada XML olarak biçimlendirir **/doc** komut satırı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="74d93-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="74d93-104">Derleyicinin ürettiği dosyasını temel alarak son belgeleri oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="74d93-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="74d93-105">Etiketleri kod yapıları türleri gibi işlenir ve üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="74d93-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74d93-106">Belge açıklamaları için bir ad alanı uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="74d93-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="74d93-107">Derleyici geçerli XML herhangi bir etiket işler.</span><span class="sxs-lookup"><span data-stu-id="74d93-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="74d93-108">Aşağıdaki kullanıcı belgelerinde genellikle kullanılan işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="74d93-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="74d93-109">Etiketler</span><span class="sxs-lookup"><span data-stu-id="74d93-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="74d93-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="74d93-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="74d93-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="74d93-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="74d93-112">[\<bkz: >](../../../csharp/programming-guide/xmldoc/see.md)*</span><span class="sxs-lookup"><span data-stu-id="74d93-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)*</span></span>|  
|[<span data-ttu-id="74d93-113">\<kodu ></span><span class="sxs-lookup"><span data-stu-id="74d93-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="74d93-114">[\<param >](../../../csharp/programming-guide/xmldoc/param.md)*</span><span class="sxs-lookup"><span data-stu-id="74d93-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)*</span></span>|<span data-ttu-id="74d93-115">[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)*</span><span class="sxs-lookup"><span data-stu-id="74d93-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)*</span></span>|  
|[<span data-ttu-id="74d93-116">\<Örnek ></span><span class="sxs-lookup"><span data-stu-id="74d93-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="74d93-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="74d93-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="74d93-118">\<Özet ></span><span class="sxs-lookup"><span data-stu-id="74d93-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="74d93-119">[\<Özel Durum >](../../../csharp/programming-guide/xmldoc/exception.md)*</span><span class="sxs-lookup"><span data-stu-id="74d93-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)*</span></span>|<span data-ttu-id="74d93-120">[\<izni >](../../../csharp/programming-guide/xmldoc/permission.md)*</span><span class="sxs-lookup"><span data-stu-id="74d93-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)*</span></span>|<span data-ttu-id="74d93-121">[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*</span><span class="sxs-lookup"><span data-stu-id="74d93-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)*</span></span>|  
|<span data-ttu-id="74d93-122">[\<dahil >](../../../csharp/programming-guide/xmldoc/include.md)*</span><span class="sxs-lookup"><span data-stu-id="74d93-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)*</span></span>|[<span data-ttu-id="74d93-123">\<Açıklamalar ></span><span class="sxs-lookup"><span data-stu-id="74d93-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="74d93-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="74d93-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="74d93-125">\<Liste ></span><span class="sxs-lookup"><span data-stu-id="74d93-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="74d93-126">\<döndürür ></span><span class="sxs-lookup"><span data-stu-id="74d93-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="74d93-127">\<Değer ></span><span class="sxs-lookup"><span data-stu-id="74d93-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="74d93-128">(* derleyici sözdizimi doğrular gösterir.)</span><span class="sxs-lookup"><span data-stu-id="74d93-128">(* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="74d93-129">Köşeli belgelerine açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="74d93-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74d93-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74d93-130">See Also</span></span>  
 [<span data-ttu-id="74d93-131">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="74d93-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="74d93-132">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="74d93-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="74d93-133">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="74d93-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
