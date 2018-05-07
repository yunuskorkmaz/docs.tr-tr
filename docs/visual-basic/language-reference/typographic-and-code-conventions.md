---
title: Tipografi ve Kod Kuralları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: eb7a33ef21bf6beda730dffa8eb7ff9cabe599fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Tipografi ve Kod Kuralları (Visual Basic)
Visual Basic belgelerine aşağıdaki tipografi ve kod kuralları kullanır.  
  
## <a name="typographic-conventions"></a>Tipografi kuralları  
  
|Örnek|Açıklama|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Dile özgü anahtar sözcükleri ve çalışma zamanı üyeleri ilk büyük harfler varsa ve bu örnekte gösterildiği gibi biçimlendirilir.|  
|**SmallProject**, **ButtonCollection**|Bu örnekte gösterildiği gibi sözcükler ve yazabileceğiniz başlatmamanız tümcecikleri biçimlendirilir.|  
|[Module Deyimi](../../visual-basic/language-reference/statements/module-statement.md)|Bu örnekte gösterildiği gibi başka bir yardım sayfasına gitmek için tıklatabileceği bağlantı biçimlendirilir.|  
|*Nesne*, *variableName*, `argumentList`|Bu örnekte gösterildiği gibi sağladığınız bilgileri yer tutucular biçimlendirilir.|  
|[Gölge], [ *izleyen* ]|Söz dizimi, isteğe bağlı öğeleri parantez içine alınmıştır.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Söz dizimi, iki veya daha fazla öğe arasında bir seçim yapmanız gerekir, öğeler ayraçlar içinde ve dikey çubuk tarafından ayrılmış.<br /><br /> Bir ve yalnızca, öğelerden birini seçmeniz gerekir.|  
|[ `Protected` &#124; `Friend` ]|Söz dizimi, iki veya daha fazla öğe arasında seçme seçeneğine sahip olduğunuzda öğeler köşeli ayraç ve dikey çubuk tarafından ayrılmış.<br /><br /> Öğeleri herhangi bir bileşimini veya öğe seçebilirsiniz.|  
|[{ `ByVal` &#124; `ByRef` }]|Sözdiziminde, birden fazla öğe seçebilirsiniz, ancak öğeleri tamamen atlayabilirsiniz öğeleri köşeli ayraç içinde çevrelenmiş ve dikey çubuk tarafından ayrılmış parantez içine alınır.|  
|*memberName*1, *memberName*2, *memberName*3|Birden çok örneğini aynı yer tutucu, örnekte gösterildiği gibi indisleri tarafından ayrılır.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|Sözdizimi, bir üç nokta (...) içinde üç nokta hemen önünde tür öğeler belirsiz sayıda göstermek için kullanılır.<br /><br /> Kod içinde üç nokta kodu daha anlaşılır olması amacıyla atlanmış türünü belirtir.|  
|ESC, GİRİN|Anahtar adları ve klavyedeki anahtar sıraları tüm büyük harflerle görünür.|  
|ALT + F1|Artı işareti (+) anahtar adları arasında görüntülendiğinde, diğer basarak bir tuşunu basılı tutun gerekir. Örneğin, ALT + F1 F1 tuşuna basarak ALT tuşunu basılı tutun anlamına gelir.|  
  
## <a name="code-conventions"></a>Kod kuralları  
  
|Örnek|Açıklama|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Kod örnekleri sabit aralık yazı tipiyle görünür ve bu örnekte gösterildiği gibi biçimlendirilir.|  
|Önceki ifadenin değerini ayarlar `sampleString` için "Hello, world!"|Bu örnekte gösterildiği gibi açıklayıcı metin kod öğeleri sabit aralık yazı tipiyle görünür.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Kod açıklamaları, kesme işareti (') ya da REM anahtar sözcük tarafından sunulur.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Satırın sonuna bir alt çizgi (_) ve ardından bir boşluk deyimi aşağıdaki satırda devam ettiğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic Dil Başvurusu](../../visual-basic/language-reference/index.md)  
 [Anahtar Sözcükler](../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic Çalışma Süresi Kitaplık Üyeleri](../../visual-basic/language-reference/runtime-library-members.md)  
 [Visual Basic adlandırma kuralları](../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Code’daki Açıklamalar](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
