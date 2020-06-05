---
title: "'<variablename>' değişkeninin türü sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak"
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 98aeb5699fdd5e5e538a205acd37436019c3fc03
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363052"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>'\<variablename>' değişkeninin türü sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak

' ' Değişkeninin türü, \<variablename> kapsayan kapsamdaki bir alana bağlandığı için çıkarsmayacak. ' ' Adını değiştirin ya da \<variablename> tam adı kullanın (örneğin, ' me. variablename ' veya ' MyBase. variablename ').

Kodunuzda bir döngü denetim değişkeni, sınıfın veya diğer kapsayan kapsamdaki bir alanla aynı ada sahiptir. Denetim değişkeni bir yan tümce olmadan kullanıldığı için `As` , kapsayan kapsamdaki alana bağlanır ve derleyici bunun için yeni bir değişken oluşturmaz veya türünü çıkarmaz.

Aşağıdaki örnekte, `Index` deyimindeki denetim değişkeni, `For` `Index` sınıfındaki alana bağlanır `Customer` . Derleyici, denetim değişkeni için yeni bir değişken oluşturmaz `Index` veya türünü çıkarmaz.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

Bu ileti, varsayılan olarak bir uyarıdır. Uyarıların nasıl gizleneceği veya uyarıların hata olarak nasıl değerlendirildiğinin hakkında bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

**Hata kimliği:** BC42110

### <a name="to-address-this-warning"></a>Bu uyarıyı çözmek için

- Adını, aynı zamanda sınıfının bir alanının adı olmayan bir tanımlayıcı olarak değiştirerek döngü denetim değişkenini yerel yapın.

  ```vb
  For I = 1 To 10
  ```

- Döngü denetimi değişkeninin, değişken adına önek olarak sınıf alanına bağlamadığını açıklığa kavuşturun `Me.` .

  ```vb
  For Me.Index = 1 To 10
  ```

- Yerel tür çıkarımı güvenmek yerine, `As` döngü denetim değişkeni için bir tür belirtmek için bir yan tümce kullanın.

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a>Örnek
 Aşağıdaki kod, önceki örnekte yer aldığı ilk düzeltmeyi göstermektedir.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a>Ayrıca bkz.

- [Option Infer Deyimi](../statements/option-infer-statement.md)
- [For Each...Next Deyimi](../statements/for-each-next-statement.md)
- [For...Next Deyimi](../statements/for-next-statement.md)
- [Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase ve MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
