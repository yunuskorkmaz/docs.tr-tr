---
title: Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 7830db136e9b900458496b36df5bc37f76661129
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523972"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="04672-102">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04672-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="04672-103">Visual Basic Derleyicisi, kodunuzdaki belge açıklamalarını bir XML dosyasına işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="04672-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="04672-104">XML dosyasını belgelere işlemek için ek araçlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04672-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="04672-105">Türler ve tür üyeleri gibi kod yapılarında XML yorumlarına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="04672-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="04672-106">Kısmi türler için, türünün yalnızca bir kısmı XML yorumlarına sahip olabilir, ancak üyelerini açıklama eklemek için herhangi bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="04672-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04672-107">Belge açıklamaları ad alanlarına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="04672-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="04672-108">Bunun nedeni, bir ad alanının birçok derlemeyi yaymasına ve tüm derlemelerin aynı anda yüklenebilmesidir.</span><span class="sxs-lookup"><span data-stu-id="04672-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="04672-109">Derleyici geçerli XML olan herhangi bir etiketi işler.</span><span class="sxs-lookup"><span data-stu-id="04672-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="04672-110">Aşağıdaki Etiketler kullanıcı belgelerinde yaygın olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="04672-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="04672-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="04672-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="04672-112">\<code ></span><span class="sxs-lookup"><span data-stu-id="04672-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="04672-113">\<example ></span><span class="sxs-lookup"><span data-stu-id="04672-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="04672-114">[\<exception >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04672-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="04672-115">[\<include >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04672-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="04672-116">\<list ></span><span class="sxs-lookup"><span data-stu-id="04672-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="04672-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="04672-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="04672-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04672-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="04672-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="04672-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="04672-120">[\<permission >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04672-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="04672-121">\<remarks ></span><span class="sxs-lookup"><span data-stu-id="04672-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="04672-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="04672-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="04672-123">[\<see >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04672-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="04672-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04672-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="04672-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="04672-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="04672-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04672-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="04672-127">\<value></span><span class="sxs-lookup"><span data-stu-id="04672-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="04672-128">(<sup>1</sup> derleyici söz dizimini doğrular.)</span><span class="sxs-lookup"><span data-stu-id="04672-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04672-129">Bir belge açıklamasının metninde açılı ayraç görüntülenmesini istiyorsanız `&lt;` ve `&gt;` kullanın.</span><span class="sxs-lookup"><span data-stu-id="04672-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="04672-130">Örneğin `"&lt;text in angle brackets&gt;"` dize, `<text in angle brackets>` olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="04672-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04672-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04672-131">See also</span></span>

- [<span data-ttu-id="04672-132">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="04672-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="04672-133">-doc</span><span class="sxs-lookup"><span data-stu-id="04672-133">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="04672-134">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="04672-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
