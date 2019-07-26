---
title: "'<variablename>' değişkeninin türü sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak"
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512720"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>'\<VariableName > ' değişkeninin türü, kapsayan kapsamdaki bir alana bağlandığı için çıkarsmayacak

'\<VariableName > ' değişkeninin türü, kapsayan kapsamdaki bir alana bağlandığı için çıkarsmayacak. '\<VariableName > ' adını değiştirin ya da tam adı kullanın (örneğin, ' me. variablename ' veya ' MyBase. variablename ').

Kodunuzda bir döngü denetim değişkeni, sınıfın veya diğer kapsayan kapsamdaki bir alanla aynı ada sahiptir. Denetim değişkeni bir `As` yan tümce olmadan kullanıldığı için, kapsayan kapsamdaki alana bağlanır ve derleyici bunun için yeni bir değişken oluşturmaz veya türünü çıkarmaz.

Aşağıdaki örnekte `Index`, `For` deyimindeki denetim değişkeni, `Customer` sınıfındaki `Index` alana bağlanır. Derleyici, denetim değişkeni `Index` için yeni bir değişken oluşturmaz veya türünü çıkarmaz.

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

**Hata KIMLIĞI:** BC42110

### <a name="to-address-this-warning"></a>Bu uyarıyı çözmek için

- Adını, aynı zamanda sınıfının bir alanının adı olmayan bir tanımlayıcı olarak değiştirerek döngü denetim değişkenini yerel yapın.

  ```vb
  For I = 1 To 10
  ```

- Döngü denetimi değişkeninin, değişken adına önek `Me.` olarak sınıf alanına bağlamadığını açıklığa kavuşturun.

  ```vb
  For Me.Index = 1 To 10
  ```

- Yerel tür çıkarımı güvenmek yerine, döngü denetim değişkeni `As` için bir tür belirtmek için bir yan tümce kullanın.

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

- [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Nasıl yapılır: Nesnenin geçerli örneğine başvurma](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
