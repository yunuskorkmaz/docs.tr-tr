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
ms.openlocfilehash: 3255dff8268cd5500a1244716f37bf30f5b43cfb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698609"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Tipografi ve Kod Kuralları (Visual Basic)
Visual Basic belgeleri aşağıdaki tipografi ve kod kuralları kullanır.  
  
## <a name="typographic-conventions"></a>Tipografi kuralları  
  
|Örnek|Açıklama|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Dile özgü anahtar sözcükleri ve çalışma zamanı üyeleri ilk büyük harfler varsa ve bu örnekte gösterildiği gibi biçimlendirilir.|  
|**SmallProject**, **ButtonCollection**|Bu örnekte gösterildiği gibi sözcük ve tümcecikleri türüne başlatmamanız biçimlendirilir.|  
|[Module Deyimi](../../visual-basic/language-reference/statements/module-statement.md)|Başka bir yardım sayfasına gitmek için tıklayabileceği bağlantıları, bu örnekte gösterildiği gibi biçimlendirilir.|  
|*Nesne*, *variableName*, `argumentList`|Yer tutucuları, sağladığınız bilgileri, bu örnekte gösterildiği gibi biçimlendirilir.|  
|[Gölgeler], [ *izleyen* ]|Sözdiziminde, isteğe bağlı öğeleri köşeli ayraç içine alınır.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Sözdiziminde, iki veya daha fazla öğe arasında bir seçim yapmasını gerektiren durumlarda öğeler ayraçlar içinde ve dikey çubuklar tarafından ayrılmış.<br /><br /> Bir ve yalnızca, öğelerden birini seçmeniz gerekir.|  
|[ `Protected` &#124; `Friend` ]|Sözdiziminde, iki veya daha fazla öğe arasında seçme seçeneğiniz varsa, öğeler köşeli parantez içine alınmış ve dikey çubuklar tarafından ayrılmış.<br /><br /> Herhangi bir birleşimini öğeleri veya hiçbir öğe seçebilirsiniz.|  
|[{ `ByVal` &#124; `ByRef` }]|Sözdiziminde, birden fazla öğe seçebilir, ancak tamamen öğeleri atlayabilirsiniz öğeleri köşeli ayraçları içine alınmış ve dikey çubuklar ayrılmış parantez içine alınır.|  
|*memberName*1 *memberName*2 *memberName*3|Aynı yer tutucu birden çok örneğini, örnekte gösterildiği gibi alt simgeler tarafından ayrılır.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|Sözdiziminde, üç nokta (...) öğeleri tür hemen önündeki nokta sonsuz sayıda belirtmek için kullanılır.<br /><br /> Kod içinde üç nokta açıklık için atlanmış kod türünü belirtir.|  
|ESC, ENTER|Anahtar adları ve klavyede tuş sıraları tamamı büyük harflerle görünür.|  
|ALT+F1|Artı işaretini (+) anahtar adları arasında görüntülendiğinde, diğer basılı tutarak bir tuşunu basılı tutun gerekir. Örneğin, ALT + F1, F1 tuşuna basarak ALT tuşunu basılı tutun anlamına gelir.|  
  
## <a name="code-conventions"></a>Kod kuralları  
  
|Örnek|Açıklama|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Kod örnekleri, bir sabit aralık yazı tipinde görünür ve bu örnekte gösterildiği gibi biçimlendirilir.|  
|Önceki deyim değerini ayarlar `sampleString` için "Hello, world!"|Açıklayıcı metin'ndaki kod öğeleri, bu örnekte gösterildiği gibi bir sabit aralık yazı tipinde görünür.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Kod açıklamaları, kesme işareti (') veya REM anahtar sözcüğe göre sunulmuştur.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Bir satırın sonuna bir alt çizgi (_) bir boşluk, deyim satırında devam ettiğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Dili Başvurusu](../../visual-basic/language-reference/index.md)
- [Anahtar Sözcükler](../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic Çalışma Süresi Kitaplık Üyeleri](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic adlandırma kuralları](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Code’daki Açıklamalar](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
