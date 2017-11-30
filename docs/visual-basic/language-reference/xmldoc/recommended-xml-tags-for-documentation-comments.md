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
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici kodunuzda bir XML dosyasına belge açıklamaları işleyebilir. XML dosyası belgeleri işlemek için ek araçlar kullanabilirsiniz.  
  
 XML açıklamaları kod yapıları türleri gibi izin verilen ve üyeleri yazın. Üyeleri yorum üzerinde herhangi bir kısıtlama olsa kısmi türler için XML açıklamaları türü yalnızca bir parçası olabilir.  
  
> [!NOTE]
>  Belge açıklamaları için ad alanları uygulanamaz. Nedeni, bir ad alanı birkaç derlemeler yayılabilir ve aynı anda yüklenmesi tüm derlemeleri sahip olmasıdır.  
  
 Derleyici, geçerli XML herhangi bir etiket işler. Aşağıdaki kullanıcı belgelerinde yaygın olarak kullanılan işlevler sağlar.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<kodu >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<Örnek >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<dahil >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<Liste >](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<izni >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<Açıklamalar >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<döndürür >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<bkz: >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<Değer >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> sözdizimi derleyici doğrular.)  
  
> [!NOTE]
>  Köşeli belgelerine açıklama metninde görünmesini istiyorsanız kullanın `<` ve `>`. Örneğin, dize `"<text in angle brackets>"` olarak görünür `<text in angle``brackets>`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ile kodunuzu belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/ doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Nasıl yapılır: XML belgesi oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
