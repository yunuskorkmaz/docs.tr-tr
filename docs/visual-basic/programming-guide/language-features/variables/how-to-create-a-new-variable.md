---
title: 'Nasıl yapılır: Yeni değişken Oluştur (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630906"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Nasıl yapılır: Yeni değişken Oluştur (Visual Basic)

[Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md)bir değişken oluşturun.

### <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için

1. Değişkeni bir `Dim` ifadede bildirin.

    ```vb
    Dim newCustomer
    ```

2. Değişkenin [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [Gölge](../../../../visual-basic/language-reference/modifiers/shadows.md)veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)gibi özelliklerine ilişkin belirtimleri ekleyin. Daha fazla bilgi için bkz. [bildirilmemiş öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Bildirimde diğer anahtar sözcükleri kullanıyorsanız `Dim` , anahtar kelime gerek yoktur.

3. Visual Basic kuralları ve kuralları izlemeniz gereken değişkenin adıyla ilgili belirtimleri izleyin. Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Değişkenin veri türünü belirtmek için [as](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesiyle birlikte adı izleyin.

    ```vb
    Public Static newCustomer As Customer
    ```

    Veri türünü belirtmezseniz, varsayılan: `Object`' ı kullanır.

5. Eşittir işareti (`=`) ile yantümceyiizleyinvedeğişkeninbaşlangıçdeğeriyleeşittirişaretineuyun.`As`

    Visual Basic, `Dim` ifadeyi her çalıştırdığında belirtilen değeri değişkenine atar. Bir başlangıç değeri belirtmezseniz, Visual Basic değişkenin veri türü için varsayılan başlangıç değerini, `Dim` ifadeyi içeren kodu ilk kez girdiğinde atar.

    Değişken bir başvuru türü ise, `As` yan tümcesine [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyerek sınıfının bir örneğini oluşturabilirsiniz. Kullanmıyorsanız `New`, değişkenin ilk değeri [Nothing](../../../../visual-basic/language-reference/nothing.md)olur.

    ```vb
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
