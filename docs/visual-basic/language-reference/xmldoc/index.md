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
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814956"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="74f45-102">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74f45-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="74f45-103">Visual Basic Derleyicisi, bir XML dosyasına kod belge açıklamaları işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="74f45-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="74f45-104">Belgeleme XML dosyasını işlemek için ek araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74f45-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="74f45-105">XML açıklamaları kod yapıları türleri gibi izin verilen ve tür üyelerini.</span><span class="sxs-lookup"><span data-stu-id="74f45-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="74f45-106">Üyeleri yorum hiçbir sınırlama olsa kısmi türleri için XML açıklamaları, türü yalnızca bir parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="74f45-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74f45-107">Belge açıklamaları ad alanları için uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="74f45-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="74f45-108">Nedeni, bir ad alanı, çeşitli derlemeler yayılabilir ve tüm derlemeleri, aynı anda yüklü olmak zorunda olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="74f45-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="74f45-109">Derleyici, geçerli bir XML değil herhangi bir etiket işler.</span><span class="sxs-lookup"><span data-stu-id="74f45-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="74f45-110">Aşağıdaki kullanıcı belgeleri, yaygın olarak kullanılan işlevler sunar.</span><span class="sxs-lookup"><span data-stu-id="74f45-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="74f45-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="74f45-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="74f45-112">\<kod ></span><span class="sxs-lookup"><span data-stu-id="74f45-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="74f45-113">\<Örnek ></span><span class="sxs-lookup"><span data-stu-id="74f45-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="74f45-114">[\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="74f45-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="74f45-115">[\<Ekle >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="74f45-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="74f45-116">\<listesi ></span><span class="sxs-lookup"><span data-stu-id="74f45-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="74f45-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="74f45-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="74f45-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="74f45-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="74f45-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="74f45-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="74f45-120">[\<izni >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="74f45-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="74f45-121">\<REMARKS ></span><span class="sxs-lookup"><span data-stu-id="74f45-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="74f45-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="74f45-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="74f45-123">[\<bkz: >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="74f45-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="74f45-124">[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="74f45-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="74f45-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="74f45-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="74f45-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="74f45-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="74f45-127">\<value></span><span class="sxs-lookup"><span data-stu-id="74f45-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="74f45-128">(<sup>1</sup> derleyici sözdizimini doğrular.)</span><span class="sxs-lookup"><span data-stu-id="74f45-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74f45-129">Açılı belgeleri açıklama metninde görünmesini istiyorsanız kullanın `&lt;` ve `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="74f45-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="74f45-130">Örneğin, dize `"&lt;text in angle brackets&gt;"` olarak görünür `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="74f45-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f45-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74f45-131">See also</span></span>

- [<span data-ttu-id="74f45-132">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="74f45-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="74f45-133">/doc</span><span class="sxs-lookup"><span data-stu-id="74f45-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="74f45-134">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74f45-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
