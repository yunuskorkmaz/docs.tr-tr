---
title: Tipografi ve Kod Kuralları
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
ms.openlocfilehash: 0e36d9d61b0dd2701210ce614d15fd38f08f5401
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401361"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Tipografi ve Kod Kuralları (Visual Basic)

Visual Basic belgeler aşağıdaki tipografik ve kod kurallarını kullanır.  
  
## <a name="typographic-conventions"></a>Tipografik kurallar  
  
|Örnek|Description|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Dile özgü anahtar sözcükler ve çalışma zamanı üyeleri ilk büyük harflerdir ve bu örnekte gösterildiği gibi biçimlendirilir.|  
|**Smallproject**, **buttoncollection**|Yazmak istediğiniz sözcükler ve ifadeler bu örnekte gösterildiği gibi biçimlendirilir.|  
|[Module Deyimi](statements/module-statement.md)|Başka bir yardım sayfasına gitmek için tıkladığı bağlantılar, bu örnekte gösterildiği gibi biçimlendirilir.|  
|*nesne*, *VariableName*,`argumentList`|Sağladığınız bilgilerin yer tutucuları, bu örnekte gösterildiği gibi biçimlendirilir.|  
|[Gölgeler], [ *expressionlist* ]|Sözdiziminde, isteğe bağlı öğeler köşeli ayraçlar içine alınır.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Sözdiziminde, iki veya daha fazla öğe arasında seçim yapmanız gerektiğinde, öğeler küme ayraçları içine alınır ve dikey çubuklar ile ayrılır.<br /><br /> Öğelerin birini ve yalnızca birini seçmeniz gerekir.|  
|[ `Protected` &#124; `Friend` ]|Sözdiziminde, iki veya daha fazla öğe arasında seçim yapma seçeneğine sahip olduğunuzda, öğeler köşeli parantezler içine alınır ve dikey çubuklar ile ayrılır.<br /><br /> Öğelerin herhangi bir birleşimini seçebilirsiniz veya hiç öğe yoktur.|  
|[{ `ByVal` &#124; `ByRef` }]|Sözdiziminde, birden fazla öğe seçemezsiniz ancak öğeleri tamamen atlayabilirsiniz, öğeler küme ayraçları ile çevrelenmiş ve dikey çubuklar ile ayrılmış köşeli ayraç içine alınır.|  
|*MemberName*1, *MemberName*2, *MemberName*3|Aynı yer tutucunun birden çok örneği, örnekte gösterildiği gibi, alt simgeler ile ayırt edilir.|  
|*memberName1*<br /><br /> ...<br /><br /> *Membernamence*|Söz dizimi içinde, üç nokta (...), üç noktanın hemen önünde bulunan türden belirsiz öğe sayısını göstermek için kullanılır.<br /><br /> Kodda, üç nokta, açıklık için Atlanan kodu işaret eder.|  
|ESC, ENTER|Klavyede anahtar adlar ve anahtar dizileri, tüm büyük harflerle görüntülenir.|  
|ALT + F1|Anahtar adları arasında artı işaretleri (+) görünüyorsa, bir tuşa basarak bir alt tuşunu basılı tutmanız gerekir. Örneğin, ALT + F1, F1 tuşuna basıldığında ALT tuşunu basılı tutmaktır.|  
  
## <a name="code-conventions"></a>Kod kuralları  
  
|Örnek|Description|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Kod örnekleri sabit aralıklı bir yazı tipinde görüntülenir ve bu örnekte gösterildiği gibi biçimlendirilir.|  
|Önceki ifade değerini `sampleString` "Hello, World!" olarak ayarlar|Açıklayıcı metindeki kod öğeleri, bu örnekte gösterildiği gibi sabit aralıklı bir yazı tipinde görüntülenir.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Kod açıklamaları bir kesme işareti (') veya REM anahtar sözcüğü ile tanıtılmıştır.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Satırın sonundaki bir alt çizgi (_) izleyen bir boşluk, deyimin aşağıdaki satırda devam ettiğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dil başvurusu](index.md)
- [Anahtar sözcükler](keywords/index.md)
- [Visual Basic Çalışma Süresi Kitaplık Üyeleri](runtime-library-members.md)
- [Visual Basic Adlandırma Kuralları](../programming-guide/program-structure/naming-conventions.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Kod Açıklamaları](../programming-guide/program-structure/comments-in-code.md)
