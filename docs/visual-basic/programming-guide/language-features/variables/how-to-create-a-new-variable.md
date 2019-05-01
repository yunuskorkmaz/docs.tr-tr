---
title: 'Nasıl yapılır: (Visual Basic) yeni değişken oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: ee1e93b4e9819992f17738eb024004a4d66210d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938248"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Nasıl yapılır: (Visual Basic) yeni değişken oluşturma
Bir değişken ile oluşturduğunuz bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için  
  
1. Değişken bildirimini bir `Dim` deyimi.  
  
    ```  
    Dim newCustomer  
    ```  
  
2. Değişkenin özelliklerini belirtimleri gibi dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Daha fazla bilgi için [bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Gereksinim duymadığınız `Dim` bildiriminde diğer anahtar sözcükler kullanırsanız anahtar sözcüğü.  
  
3. Visual Basic kuralları ve kuralları izlemelidir değişkenin adıyla belirtimleri izleyin. Daha fazla bilgi için [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4. Adıyla izleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan değişkenin veri türü belirtin.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Veri türü belirtmezseniz varsayılan kullanır: `Object`.  
  
5. İzleyin `As` yan tümcesiyle birlikte bir eşittir işareti (`=`) ve değişkenin başlangıç değeri eşittir işaretiyle izleyin.  
  
     Visual Basic her çalıştırıldığında bu belirtilen değeri bir değişkene atar `Dim` deyimi. Bir başlangıç değeri belirtmezseniz, ilk içerdiği kodu girdiğinde Visual Basic değişken veri türü için varsayılan başlangıç değeri atar `Dim` deyimi.  
  
     Değişken bir başvuru türü ise ekleyerek, sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü `As` yan tümcesi. Kullanmıyorsanız, `New`, ilk değişken değeri [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
