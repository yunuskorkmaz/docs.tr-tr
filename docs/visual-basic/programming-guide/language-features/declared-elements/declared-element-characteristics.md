---
title: Bildirilen Öğe Özellikleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 27dad8b2fbfbc8d17090df201bf36eb080966f51
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076930"
---
# <a name="declared-element-characteristics-visual-basic"></a>Bildirilen Öğe Özellikleri (Visual Basic)
A *karakteristik* bildirilen bir öğe kod ile nasıl etkileşim kurabileceğine etkiler o öğenin bir parçasıdır. Bildirilen her öğe bir veya daha fazla ilişkili aşağıdaki özelliklere sahiptir:  
  
-   *Veri türü* — öğesi değerlerini tutabileceği ve bu değerleri nasıl depolar. Daha fazla bilgi için [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
-   *Yaşam süresi* — süre yürütme sırasında öğe olduğu için kullanılabilir. Daha fazla bilgi için [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Kapsam* — adıyla nitelemeden öğesine başvurabilir tüm kod kümesi. Daha fazla bilgi için [nasıl yapılır: bir değişkenin kapsamını denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Erişim düzeyi* — iznini sağlamak için kod öğesi kullanın. Daha fazla bilgi için [nasıl yapılır: bir değişkenin kullanılabilirliğini denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Öğelerin özellikleri  
 Aşağıdaki tabloda, bildirilen öğeler ve her birine Uygula özellikleri gösterilmektedir.  
  
|Öğe|Veri Türü|Ömür|Kapsam <sup>1</sup>|Erişim düzeyi|  
|-------------|---------------|--------------|------------------------|------------------|  
|Değişken|Evet|Evet|Evet|Evet|  
|Sabit|Evet|Hayır|Evet|Evet|  
|Sabit Listesi|Evet|Hayır|Evet|Evet|  
|Yapı|Hayır|Hayır|Evet|Evet|  
|Özellik|Evet|Evet|Evet|Evet|  
|Yöntem|Hayır|Evet|Evet|Evet|  
|Yordam (`Sub` veya `Function`)|Hayır|Evet|Evet|Evet|  
|Yordam parametresi|Evet|Evet|Evet|Hayır|  
|İşlev döndürme|Evet|Evet|Evet|Hayır|  
|İşleç|Evet|Hayır|Evet|Evet|  
|Arabirim|Hayır|Hayır|Evet|Evet|  
|örneği|Hayır|Hayır|Evet|Evet|  
|Olay|Hayır|Hayır|Evet|Evet|  
|Temsilci|Hayır|Hayır|Evet|Evet|  
  
 <sup>1</sup> kapsam bazen olarak adlandırılır *görünürlük*.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilen Öğeler](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
