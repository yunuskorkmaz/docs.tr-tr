---
title: 'Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: f2e6a97e78bc42ebea9519eb0aa4411e9aec24cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)
Sahip bir değişken oluşturmak bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için  
  
1.  Değişken bildirme bir `Dim` deyimi.  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  Değişkenin özellikleri için belirtimleri gibi içeren [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md), veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Daha fazla bilgi için bkz: [bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     İhtiyacınız olmayan `Dim` bildiriminde diğer anahtar sözcükler kullanırsanız, anahtar sözcük.  
  
3.  Visual Basic kuralları ve kurallarına uymalıdır değişkenin adını belirtimlere izleyin. Daha fazla bilgi için bkz: [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Adlı izleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesini değişkenin veri türü belirtin.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Veri türünü belirtmezseniz varsayılan kullanır: `Object`.  
  
5.  İzleyin `As` yan tümcesi eşittir işareti (`=`) ve değişken ilk değerinin eşittir işaretiyle izleyin.  
  
     Visual Basic her çalıştığında bu belirtilen değere değişkenine atar `Dim` deyimi. Bir başlangıç değeri belirtmezseniz, ilk içeren kodu girdiğinde, Visual Basic değişkenin veri türü için varsayılan başlangıç değeri atar `Dim` deyimi.  
  
     Değişkeni bir başvuru türü ise dahil ederek kendi sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcük `As` yan tümcesi. Kullanmıyorsanız, `New`, ilk değer değişkenin [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Deyimler](../../../../visual-basic/language-reference/statements/index.md)  
 [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
