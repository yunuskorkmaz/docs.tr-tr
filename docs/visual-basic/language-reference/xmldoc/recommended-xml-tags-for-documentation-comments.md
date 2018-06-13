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
ms.openlocfilehash: 8f27a892117980e89fa7143b7e49551b9e8703f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604431"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="87db3-102">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87db3-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="87db3-103">Visual Basic derleyici kodunuzda bir XML dosyasına belge açıklamaları işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="87db3-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="87db3-104">XML dosyası belgeleri işlemek için ek araçlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87db3-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="87db3-105">XML açıklamaları kod yapıları türleri gibi izin verilen ve üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="87db3-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="87db3-106">Üyeleri yorum üzerinde herhangi bir kısıtlama olsa kısmi türler için XML açıklamaları türü yalnızca bir parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="87db3-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87db3-107">Belge açıklamaları için ad alanları uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="87db3-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="87db3-108">Nedeni, bir ad alanı birkaç derlemeler yayılabilir ve aynı anda yüklenmesi tüm derlemeleri sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="87db3-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="87db3-109">Derleyici, geçerli XML herhangi bir etiket işler.</span><span class="sxs-lookup"><span data-stu-id="87db3-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="87db3-110">Aşağıdaki kullanıcı belgelerinde yaygın olarak kullanılan işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="87db3-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="87db3-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="87db3-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="87db3-112">\<kodu ></span><span class="sxs-lookup"><span data-stu-id="87db3-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="87db3-113">\<Örnek ></span><span class="sxs-lookup"><span data-stu-id="87db3-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="87db3-114">[\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="87db3-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="87db3-115">[\<dahil >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="87db3-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="87db3-116">\<Liste ></span><span class="sxs-lookup"><span data-stu-id="87db3-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="87db3-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="87db3-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="87db3-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="87db3-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="87db3-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="87db3-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="87db3-120">[\<izni >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="87db3-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="87db3-121">\<Açıklamalar ></span><span class="sxs-lookup"><span data-stu-id="87db3-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="87db3-122">\<döndürür ></span><span class="sxs-lookup"><span data-stu-id="87db3-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="87db3-123">[\<bkz: >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="87db3-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="87db3-124">[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="87db3-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="87db3-125">\<Özet ></span><span class="sxs-lookup"><span data-stu-id="87db3-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="87db3-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="87db3-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="87db3-127">\<Değer ></span><span class="sxs-lookup"><span data-stu-id="87db3-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="87db3-128">(<sup>1</sup> sözdizimi derleyici doğrular.)</span><span class="sxs-lookup"><span data-stu-id="87db3-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87db3-129">Köşeli belgelerine açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`.</span><span class="sxs-lookup"><span data-stu-id="87db3-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="87db3-130">Örneğin, dize `"<text in angle brackets>"` olarak görünür `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="87db3-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87db3-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87db3-131">See Also</span></span>  
 [<span data-ttu-id="87db3-132">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="87db3-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="87db3-133">/doc</span><span class="sxs-lookup"><span data-stu-id="87db3-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="87db3-134">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="87db3-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
