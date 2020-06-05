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
ms.openlocfilehash: 9d1e327c25689bed1405ea9a627da6232abb707b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392954"
---
# <a name="declared-element-characteristics-visual-basic"></a>Bildirilen Öğe Özellikleri (Visual Basic)
Tanımlı bir öğenin *özelliği* , kodun onunla etkileşime geçmesini etkileyen bu öğenin bir yönüdür. Her beyan edilen öğe, onunla ilişkili aşağıdaki özelliklerden birini veya daha fazlasını içerir:  
  
- *Veri türü* — öğenin tutacağı ve bu değerleri nasıl sakladığı değerleri. Daha fazla bilgi için bkz. [veri türleri](../../../language-reference/data-types/index.md).  
  
- *Yaşam süresi* — öğenin kullanıma hazır olduğu yürütme süresi dönemi. Daha fazla bilgi için [Visual Basic ömrü](lifetime.md)' ne bakın.  
  
- *Kapsam* — öğenin adını nitelemeden başvurabilen tüm kod kümesi. Daha fazla bilgi için bkz. [nasıl yapılır: bir değişkenin kapsamını denetleme](how-to-control-the-scope-of-a-variable.md).  
  
- *Erişim düzeyi* — öğenin kullanımını sağlamak için kod izni. Daha fazla bilgi için bkz. [nasıl yapılır: bir değişkenin kullanılabilirliğini denetleme](how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Öğelerin özellikleri  
 Aşağıdaki tabloda, tanımlanmış öğeler ve her biri için uygulanan özellikler gösterilmektedir.  
  
|Öğe|Veri Türü|Ömür|Kapsam <sup>1</sup>|Erişim düzeyi|  
|-------------|---------------|--------------|------------------------|------------------|  
|Değişken|Yes|Yes|Yes|Yes|  
|Sabit|Yes|No|Evet|Yes|  
|Sabit Listesi|Yes|No|Evet|Yes|  
|Yapı|Hayır|Hayır|Evet|Yes|  
|Özellik|Yes|Yes|Yes|Yes|  
|Yöntem|No|Evet|Yes|Yes|  
|Yordam ( `Sub` veya `Function` )|No|Evet|Yes|Yes|  
|Yordam parametresi|Yes|Yes|Yes|No|  
|İşlev dönüşü|Yes|Yes|Yes|No|  
|Operatör|Yes|No|Evet|Yes|  
|Arabirim|Hayır|Hayır|Evet|Yes|  
|Sınıf|Hayır|Hayır|Evet|Yes|  
|Olay|Hayır|Hayır|Evet|Yes|  
|Temsilci|Hayır|Hayır|Evet|Yes|  
  
 <sup>1</sup> kapsam bazen *görünürlük*olarak adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmeyen öğeler](index.md)
- [Bildirilen Öğe Adları](declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Visual Basic'de Ömür](lifetime.md)
- [Visual Basic'de Kapsam](scope.md)
- [Visual Basic erişim düzeyleri](access-levels.md)
- [Veri türleri](../data-types/index.md)
- [Değişken Bildirimi](../variables/variable-declaration.md)
