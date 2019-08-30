---
title: Temsilcilerde varyans kullanma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: ebba7e862e1b4677d9438aa301ef2b713fba3712
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169076"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Temsilcilerde varyans kullanma (Visual Basic)

Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar. Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar. Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.

## <a name="example-1-covariance"></a>Örnek 1: Ko

### <a name="description"></a>Açıklama

Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir. Tarafından `DogsHandler` döndürülen veri `Dogs` türü`Mammals` , temsilde tanımlanan türden türetilen türüdür.

### <a name="code"></a>Kod

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a>Örnek 2: Kontravaryans

### <a name="description"></a>Açıklama

Bu örnek, temsilci imza parametre türünün temel türleri olan parametrelere sahip Yöntemler ile temsilcilerin nasıl kullanılabileceğini gösterir. Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz. Aşağıdaki örnek iki temsilcinin kullanımını sağlar:

- <xref:System.Windows.Forms.KeyEventHandler> [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir temsilci. İmzası:

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <xref:System.Windows.Forms.MouseEventHandler> [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir temsilci. İmzası:

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

Örnek, <xref:System.EventArgs> parametresiyle bir olay işleyicisini tanımlar ve `Button.KeyDown` hem hem de `Button.MouseClick` olaylarını işlemek için onu kullanır. Bu <xref:System.EventArgs> <xref:System.Windows.Forms.KeyEventArgs> ,<xref:System.Windows.Forms.MouseEventArgs>hem hem de temel türü olduğundan bunu yapabilir.

### <a name="code"></a>Kod

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a>Ayrıca bkz.

- [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
