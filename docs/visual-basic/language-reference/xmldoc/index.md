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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814956"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)
Visual Basic Derleyicisi, bir XML dosyasına kod belge açıklamaları işleyebilir. Belgeleme XML dosyasını işlemek için ek araçları kullanabilirsiniz.  
  
 XML açıklamaları kod yapıları türleri gibi izin verilen ve tür üyelerini. Üyeleri yorum hiçbir sınırlama olsa kısmi türleri için XML açıklamaları, türü yalnızca bir parçası olabilir.  
  
> [!NOTE]
>  Belge açıklamaları ad alanları için uygulanamaz. Nedeni, bir ad alanı, çeşitli derlemeler yayılabilir ve tüm derlemeleri, aynı anda yüklü olmak zorunda olmasıdır.  
  
 Derleyici, geçerli bir XML değil herhangi bir etiket işler. Aşağıdaki kullanıcı belgeleri, yaygın olarak kullanılan işlevler sunar.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<kod >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<Örnek >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<Ekle >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<listesi >](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<izni >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<REMARKS >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<bkz: >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> derleyici sözdizimini doğrular.)  
  
> [!NOTE]
>  Açılı belgeleri açıklama metninde görünmesini istiyorsanız kullanın `&lt;` ve `&gt;`. Örneğin, dize `"&lt;text in angle brackets&gt;"` olarak görünür `<text in angle brackets>`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Nasıl yapılır: XML belgesi oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
