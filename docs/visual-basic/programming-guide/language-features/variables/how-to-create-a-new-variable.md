---
title: 'Nasıl yapılır: Yeni Değişken Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410535"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)

[Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bir değişken oluşturun.

### <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için

1. Değişkeni bir `Dim` ifadede bildirin.

    ```vb
    Dim newCustomer
    ```

2. Değişkenin [özel](../../../language-reference/modifiers/private.md), [statik](../../../language-reference/modifiers/static.md), [Gölge](../../../language-reference/modifiers/shadows.md)veya [WithEvents](../../../language-reference/modifiers/withevents.md)gibi özelliklerine ilişkin belirtimleri ekleyin. Daha fazla bilgi için bkz. [bildirilmemiş öğe özellikleri](../declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    `Dim`Bildirimde diğer anahtar sözcükleri kullanıyorsanız, anahtar kelime gerek yoktur.

3. Visual Basic kuralları ve kuralları izlemeniz gereken değişkenin adıyla ilgili belirtimleri izleyin. Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Değişkenin veri türünü belirtmek için [as](../../../language-reference/statements/as-clause.md) yan tümcesiyle birlikte adı izleyin.

    ```vb
    Public Static newCustomer As Customer
    ```

    Veri türünü belirtmezseniz, varsayılan: ' ı kullanır `Object` .

5. `As`Eşittir işareti () ile yan tümceyi izleyin `=` ve değişkenin başlangıç değeriyle eşittir işaretine uyun.

    Visual Basic, ifadeyi her çalıştırdığında belirtilen değeri değişkenine atar `Dim` . Bir başlangıç değeri belirtmezseniz, Visual Basic değişkenin veri türü için varsayılan başlangıç değerini, ifadeyi içeren kodu ilk kez girdiğinde atar `Dim` .

    Değişken bir başvuru türü ise, yan tümcesine [New Operator](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyerek sınıfının bir örneğini oluşturabilirsiniz `As` . Kullanmıyorsanız `New` , değişkenin ilk değeri [Nothing](../../../language-reference/nothing.md)olur.

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](index.md)
- [Değişken Bildirimi](variable-declaration.md)
- [Bildirilen Öğe Adları](../declared-elements/declared-element-names.md)
- [Bildirilen Öğe Özellikleri](../declared-elements/declared-element-characteristics.md)
- [Değer Türleri ve Başvuru Türleri](../data-types/value-types-and-reference-types.md)
- [Deyimler](../../../language-reference/statements/index.md)
- [Yerel Tür Arabirimi](local-type-inference.md)
- [Option Infer Deyimi](../../../language-reference/statements/option-infer-statement.md)
