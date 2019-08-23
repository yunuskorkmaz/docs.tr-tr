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
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913498"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="7dbe6-102">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="7dbe6-103">Visual Basic Derleyicisi, kodunuzdaki belge açıklamalarını bir XML dosyasına işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="7dbe6-104">XML dosyasını belgelere işlemek için ek araçlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="7dbe6-105">Türler ve tür üyeleri gibi kod yapılarında XML yorumlarına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="7dbe6-106">Kısmi türler için, türünün yalnızca bir kısmı XML yorumlarına sahip olabilir, ancak üyelerini açıklama eklemek için herhangi bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dbe6-107">Belge açıklamaları ad alanlarına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="7dbe6-108">Bunun nedeni, bir ad alanının birçok derlemeyi yaymasına ve tüm derlemelerin aynı anda yüklenebilmesidir.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="7dbe6-109">Derleyici geçerli XML olan herhangi bir etiketi işler.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="7dbe6-110">Aşağıdaki Etiketler kullanıcı belgelerinde yaygın olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="7dbe6-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="7dbe6-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="7dbe6-112">\<kod ></span><span class="sxs-lookup"><span data-stu-id="7dbe6-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="7dbe6-113">\<örnek ></span><span class="sxs-lookup"><span data-stu-id="7dbe6-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="7dbe6-114">özel durum > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/exception.md)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="7dbe6-115">dahil > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/include.md)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="7dbe6-116">\<Liste ></span><span class="sxs-lookup"><span data-stu-id="7dbe6-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="7dbe6-117">\<Para ></span><span class="sxs-lookup"><span data-stu-id="7dbe6-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="7dbe6-118">param > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/param.md)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="7dbe6-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="7dbe6-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="7dbe6-120">izin > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/permission.md)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="7dbe6-121">\<açıklamalar ></span><span class="sxs-lookup"><span data-stu-id="7dbe6-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="7dbe6-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="7dbe6-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="7dbe6-123">bkz. > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/see.md)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="7dbe6-124">seede > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/seealso.md)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="7dbe6-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="7dbe6-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="7dbe6-126">typeparam > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/typeparam.md)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="7dbe6-127">\<value></span><span class="sxs-lookup"><span data-stu-id="7dbe6-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="7dbe6-128">(<sup>1</sup> derleyici söz dizimini doğrular.)</span><span class="sxs-lookup"><span data-stu-id="7dbe6-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dbe6-129">Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, ve `&lt;` `&gt;`kullanın.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="7dbe6-130">Örneğin, dize `"&lt;text in angle brackets&gt;"` olarak `<text in angle brackets>`görünür.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dbe6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dbe6-131">See also</span></span>

- [<span data-ttu-id="7dbe6-132">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="7dbe6-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="7dbe6-133">/doc</span><span class="sxs-lookup"><span data-stu-id="7dbe6-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="7dbe6-134">Nasıl yapılır: XML belgeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="7dbe6-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
