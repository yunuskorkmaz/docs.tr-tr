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
ms.openlocfilehash: 36c55475b4930dc6c3202d52ef742072d5cee3e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075284"
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
|Sabit|Yes|Hayır|Yes|Yes|  
|Sabit Listesi|Yes|Hayır|Yes|Yes|  
|Yapı|Hayır|Hayır|Yes|Yes|  
|Özellik|Yes|Yes|Yes|Yes|  
|Yöntem|Hayır|Yes|Yes|Yes|  
|Yordam ( `Sub` veya `Function` )|Hayır|Yes|Yes|Yes|  
|Yordam parametresi|Yes|Yes|Yes|Hayır|  
|İşlev dönüşü|Yes|Yes|Yes|Hayır|  
|Operatör|Yes|Hayır|Yes|Yes|  
|Arabirim|Hayır|Hayır|Yes|Yes|  
|Sınıf|Hayır|Hayır|Yes|Yes|  
|Olay|Hayır|Hayır|Yes|Yes|  
|Temsilci|Hayır|Hayır|Yes|Yes|  
  
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
