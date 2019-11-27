---
title: Bildirilen Öğe Özellikleri
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
ms.openlocfilehash: 4e03cd28fed5e0ae109337739251c11a0ff3424a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331622"
---
# <a name="declared-element-characteristics-visual-basic"></a>Bildirilen Öğe Özellikleri (Visual Basic)
Tanımlı bir öğenin *özelliği* , kodun onunla etkileşime geçmesini etkileyen bu öğenin bir yönüdür. Her beyan edilen öğe, onunla ilişkili aşağıdaki özelliklerden birini veya daha fazlasını içerir:  
  
- *Veri türü* — öğenin tutacağı ve bu değerleri nasıl sakladığı değerleri. Daha fazla bilgi için bkz. [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
- *Yaşam süresi* — öğenin kullanıma hazır olduğu yürütme süresi dönemi. Daha fazla bilgi için [Visual Basic ömrü](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)' ne bakın.  
  
- *Kapsam* — öğenin adını nitelemeden başvurabilen tüm kod kümesi. Daha fazla bilgi için bkz. [nasıl yapılır: bir değişkenin kapsamını denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
- *Erişim düzeyi* — öğenin kullanımını sağlamak için kod izni. Daha fazla bilgi için bkz. [nasıl yapılır: bir değişkenin kullanılabilirliğini denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Öğelerin özellikleri  
 Aşağıdaki tabloda, tanımlanmış öğeler ve her biri için uygulanan özellikler gösterilmektedir.  
  
|Öğe|Veri Türü|Ömür|Kapsam <sup>1</sup>|Erişim düzeyi|  
|-------------|---------------|--------------|------------------------|------------------|  
|Değişken|Evet|Evet|Evet|Evet|  
|Sabit|Evet|Hayır|Evet|Evet|  
|Numaralandırma|Evet|Hayır|Evet|Evet|  
|Yapı|Hayır|Hayır|Evet|Evet|  
|Özellik|Evet|Evet|Evet|Evet|  
|Yöntem|Hayır|Evet|Evet|Evet|  
|Yordam (`Sub` veya `Function`)|Hayır|Evet|Evet|Evet|  
|Yordam parametresi|Evet|Evet|Evet|Hayır|  
|İşlev dönüşü|Evet|Evet|Evet|Hayır|  
|İşleç|Evet|Hayır|Evet|Evet|  
|Arabirim|Hayır|Hayır|Evet|Evet|  
|Sınıf|Hayır|Hayır|Evet|Evet|  
|Olay|Hayır|Hayır|Evet|Evet|  
|Temsilci|Hayır|Hayır|Evet|Evet|  
  
 <sup>1</sup> kapsam bazen *görünürlük*olarak adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğeler](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic ömrü](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
