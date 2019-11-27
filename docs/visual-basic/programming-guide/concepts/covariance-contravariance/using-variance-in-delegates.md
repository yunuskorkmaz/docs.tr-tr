---
title: Temsilcilerde Varyans Kullanma
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 9c2aad0e4b9408939600938412fe5c3e73b5bf15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349025"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Temsilcilerde varyans kullanma (Visual Basic)

Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar. Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar. Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.

## <a name="example-1-covariance"></a>Örnek 1: Kovaryans

### <a name="description"></a>Açıklama

Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir. `DogsHandler` tarafından döndürülen veri türü, temsilde tanımlanan `Mammals` türünden türetilen `Dogs`türüdür.

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

## <a name="example-2-contravariance"></a>Örnek 2: değişken varyans

### <a name="description"></a>Açıklama

Bu örnek, temsilci imza parametre türünün temel türleri olan parametrelere sahip Yöntemler ile temsilcilerin nasıl kullanılabileceğini gösterir. Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz. Aşağıdaki örnek iki temsilcinin kullanımını sağlar:

- [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir <xref:System.Windows.Forms.KeyEventHandler> temsilcisi. İmzası:

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir <xref:System.Windows.Forms.MouseEventHandler> temsilcisi. İmzası:

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

Örnek, <xref:System.EventArgs> parametresine sahip bir olay işleyicisini tanımlar ve `Button.KeyDown` ve `Button.MouseClick` olaylarını işlemek için onu kullanır. <xref:System.EventArgs>, hem <xref:System.Windows.Forms.KeyEventArgs> hem de <xref:System.Windows.Forms.MouseEventArgs>temel türü olduğundan bunu yapabilir.

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
