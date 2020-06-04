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
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400104"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)
Visual Basic Derleyicisi, kodunuzdaki belge açıklamalarını bir XML dosyasına işleyebilir. XML dosyasını belgelere işlemek için ek araçlar kullanabilirsiniz.  
  
 Türler ve tür üyeleri gibi kod yapılarında XML yorumlarına izin verilir. Kısmi türler için, türünün yalnızca bir kısmı XML yorumlarına sahip olabilir, ancak üyelerini açıklama eklemek için herhangi bir kısıtlama yoktur.  
  
> [!NOTE]
> Belge açıklamaları ad alanlarına uygulanamaz. Bunun nedeni, bir ad alanının birçok derlemeyi yaymasına ve tüm derlemelerin aynı anda yüklenebilmesidir.  
  
 Derleyici geçerli XML olan herhangi bir etiketi işler. Aşağıdaki Etiketler kullanıcı belgelerinde yaygın olarak kullanılan işlevleri sağlar.  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|[\<exception>](exception.md)<sup>1</sup>|[\<include>](include.md)<sup>1</sup>|[\<list>](list.md)|  
|[\<para>](para.md)|[\<param>](param.md)<sup>1</sup>|[\<paramref>](paramref.md)|  
|[\<permission>](permission.md)<sup>1</sup>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|[\<see>](see.md)<sup>1</sup>|[\<seealso>](seealso.md)<sup>1</sup>|[\<summary>](summary.md)|  
|[\<typeparam>](typeparam.md)<sup>1</sup>|[\<value>](value.md)||  
  
 (<sup>1</sup> derleyici söz dizimini doğrular.)  
  
> [!NOTE]
> Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, `&lt;` ve kullanın `&gt;` . Örneğin, dize `"&lt;text in angle brackets&gt;"` olarak görünür `<text in angle brackets>` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../reference/command-line-compiler/doc.md)
- [Nasıl yapılır: XML Belgesi Oluşturma](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
