---
title: Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7815d4c9fddc4e760c7495ef7a2509c55141e96e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="b636b-102">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b636b-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="b636b-103">Visual Basic derleyici kodunuzda bir XML dosyasına belge açıklamaları işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b636b-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="b636b-104">XML dosyası belgeleri işlemek için ek araçlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b636b-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="b636b-105">XML açıklamaları kod yapıları türleri gibi izin verilen ve üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="b636b-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="b636b-106">Üyeleri yorum üzerinde herhangi bir kısıtlama olsa kısmi türler için XML açıklamaları türü yalnızca bir parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="b636b-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b636b-107">Belge açıklamaları için ad alanları uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="b636b-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="b636b-108">Nedeni, bir ad alanı birkaç derlemeler yayılabilir ve aynı anda yüklenmesi tüm derlemeleri sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b636b-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="b636b-109">Derleyici, geçerli XML herhangi bir etiket işler.</span><span class="sxs-lookup"><span data-stu-id="b636b-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="b636b-110">Aşağıdaki kullanıcı belgelerinde yaygın olarak kullanılan işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b636b-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="b636b-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="b636b-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="b636b-112">\<kodu ></span><span class="sxs-lookup"><span data-stu-id="b636b-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="b636b-113">\<Örnek ></span><span class="sxs-lookup"><span data-stu-id="b636b-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="b636b-114">[\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b636b-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="b636b-115">[\<dahil >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b636b-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="b636b-116">\<Liste ></span><span class="sxs-lookup"><span data-stu-id="b636b-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="b636b-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="b636b-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="b636b-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b636b-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="b636b-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="b636b-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="b636b-120">[\<izni >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b636b-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="b636b-121">\<Açıklamalar ></span><span class="sxs-lookup"><span data-stu-id="b636b-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="b636b-122">\<döndürür ></span><span class="sxs-lookup"><span data-stu-id="b636b-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="b636b-123">[\<bkz: >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b636b-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="b636b-124">[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b636b-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="b636b-125">\<Özet ></span><span class="sxs-lookup"><span data-stu-id="b636b-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="b636b-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b636b-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="b636b-127">\<Değer ></span><span class="sxs-lookup"><span data-stu-id="b636b-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="b636b-128">(<sup>1</sup> sözdizimi derleyici doğrular.)</span><span class="sxs-lookup"><span data-stu-id="b636b-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b636b-129">Köşeli belgelerine açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`.</span><span class="sxs-lookup"><span data-stu-id="b636b-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="b636b-130">Örneğin, dize `"<text in angle brackets>"` olarak görünür `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="b636b-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b636b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b636b-131">See Also</span></span>  
 [<span data-ttu-id="b636b-132">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="b636b-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="b636b-133">/doc</span><span class="sxs-lookup"><span data-stu-id="b636b-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="b636b-134">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b636b-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
