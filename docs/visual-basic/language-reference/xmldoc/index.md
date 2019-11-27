---
title: Belge açıklamaları için önerilen XML etiketleri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 093c967557b899c8661fdec348d421996e948b94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352328"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)
Visual Basic Derleyicisi, kodunuzdaki belge açıklamalarını bir XML dosyasına işleyebilir. XML dosyasını belgelere işlemek için ek araçlar kullanabilirsiniz.  
  
 Türler ve tür üyeleri gibi kod yapılarında XML yorumlarına izin verilir. Kısmi türler için, türünün yalnızca bir kısmı XML yorumlarına sahip olabilir, ancak üyelerini açıklama eklemek için herhangi bir kısıtlama yoktur.  
  
> [!NOTE]
> Belge açıklamaları ad alanlarına uygulanamaz. Bunun nedeni, bir ad alanının birçok derlemeyi yaymasına ve tüm derlemelerin aynı anda yüklenebilmesidir.  
  
 Derleyici geçerli XML olan herhangi bir etiketi işler. Aşağıdaki Etiketler kullanıcı belgelerinde yaygın olarak kullanılan işlevleri sağlar.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<kodu >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<örnek >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<özel durum >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<içerme >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<listesi >](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<paragraf >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<izin >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<açıklamalar >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<bkz. >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seede >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> derleyici söz dizimini doğrular.)  
  
> [!NOTE]
> Bir belge açıklamasının metninde açılı ayraç görüntülenmesini istiyorsanız `&lt;` ve `&gt;`kullanın. Örneğin `"&lt;text in angle brackets&gt;"` dize, `<text in angle brackets>`olarak görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
