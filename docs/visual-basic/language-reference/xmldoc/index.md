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
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)
Visual Basic Derleyicisi, kodunuzdaki belge açıklamalarını bir XML dosyasına işleyebilir. XML dosyasını belgelere işlemek için ek araçlar kullanabilirsiniz.  
  
 Türler ve tür üyeleri gibi kod yapılarında XML yorumlarına izin verilir. Kısmi türler için, türünün yalnızca bir kısmı XML yorumlarına sahip olabilir, ancak üyelerini açıklama eklemek için herhangi bir kısıtlama yoktur.  
  
> [!NOTE]
> Belge açıklamaları ad alanlarına uygulanamaz. Bunun nedeni, bir ad alanının birçok derlemeyi yaymasına ve tüm derlemelerin aynı anda yüklenebilmesidir.  
  
 Derleyici geçerli XML olan herhangi bir etiketi işler. Aşağıdaki Etiketler kullanıcı belgelerinde yaygın olarak kullanılan işlevleri sağlar.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<kod >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<örnek >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|özel durum > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/exception.md)|dahil > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/include.md)|[\<Liste >](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<Para >](../../../visual-basic/language-reference/xmldoc/para.md)|param > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/param.md)|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|izin > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/permission.md)|[\<açıklamalar >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|bkz. > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/see.md)|seede > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/seealso.md)|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|typeparam > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/typeparam.md)|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> derleyici söz dizimini doğrular.)  
  
> [!NOTE]
> Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, ve `&lt;` `&gt;`kullanın. Örneğin, dize `"&lt;text in angle brackets&gt;"` olarak `<text in angle brackets>`görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Nasıl yapılır: XML belgeleri oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
