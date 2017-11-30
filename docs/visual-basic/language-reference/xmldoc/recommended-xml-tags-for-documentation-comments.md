---
title: "Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54712deb8bb2a5ed1e7b1f5fb8aa073dcdaf76d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="e53c6-102">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e53c6-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="e53c6-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici kodunuzda bir XML dosyasına belge açıklamaları işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e53c6-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="e53c6-104">XML dosyası belgeleri işlemek için ek araçlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e53c6-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="e53c6-105">XML açıklamaları kod yapıları türleri gibi izin verilen ve üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="e53c6-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="e53c6-106">Üyeleri yorum üzerinde herhangi bir kısıtlama olsa kısmi türler için XML açıklamaları türü yalnızca bir parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="e53c6-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e53c6-107">Belge açıklamaları için ad alanları uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="e53c6-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="e53c6-108">Nedeni, bir ad alanı birkaç derlemeler yayılabilir ve aynı anda yüklenmesi tüm derlemeleri sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e53c6-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="e53c6-109">Derleyici, geçerli XML herhangi bir etiket işler.</span><span class="sxs-lookup"><span data-stu-id="e53c6-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="e53c6-110">Aşağıdaki kullanıcı belgelerinde yaygın olarak kullanılan işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e53c6-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="e53c6-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="e53c6-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="e53c6-112">\<kodu ></span><span class="sxs-lookup"><span data-stu-id="e53c6-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="e53c6-113">\<Örnek ></span><span class="sxs-lookup"><span data-stu-id="e53c6-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="e53c6-114">[\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e53c6-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="e53c6-115">[\<dahil >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e53c6-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="e53c6-116">\<Liste ></span><span class="sxs-lookup"><span data-stu-id="e53c6-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="e53c6-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="e53c6-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="e53c6-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e53c6-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="e53c6-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="e53c6-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="e53c6-120">[\<izni >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e53c6-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="e53c6-121">\<Açıklamalar ></span><span class="sxs-lookup"><span data-stu-id="e53c6-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="e53c6-122">\<döndürür ></span><span class="sxs-lookup"><span data-stu-id="e53c6-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="e53c6-123">[\<bkz: >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e53c6-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="e53c6-124">[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e53c6-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="e53c6-125">\<Özet ></span><span class="sxs-lookup"><span data-stu-id="e53c6-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="e53c6-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e53c6-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="e53c6-127">\<Değer ></span><span class="sxs-lookup"><span data-stu-id="e53c6-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="e53c6-128">(<sup>1</sup> sözdizimi derleyici doğrular.)</span><span class="sxs-lookup"><span data-stu-id="e53c6-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e53c6-129">Köşeli belgelerine açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`.</span><span class="sxs-lookup"><span data-stu-id="e53c6-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="e53c6-130">Örneğin, dize `"<text in angle brackets>"` olarak görünür `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="e53c6-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53c6-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e53c6-131">See Also</span></span>  
 [<span data-ttu-id="e53c6-132">XML ile kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="e53c6-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="e53c6-133">/ doc</span><span class="sxs-lookup"><span data-stu-id="e53c6-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="e53c6-134">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e53c6-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
