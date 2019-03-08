---
title: Temsilcilerde varyans (Visual Basic) kullanma
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 19eb3070c1b8359a4eb050e7cf2f16622f66ebe9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679802"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Temsilcilerde varyans (Visual Basic) kullanma

Bir temsilci için bir yöntem atadığınızda *Kovaryans* ve *kontravaryans* yöntem imzasını bir temsilci türüyle eşleştirmek için esneklik sağlar. Kovaryans Temsilcide tanımlanan daha fazla türetilmiş dönüş türüne sahip bir yöntem sağlar. Kontravaryans, temsilci türü olanlardan daha az türetilmiş parametre türleri olan bir yönteme izin verir.

## <a name="example-1-covariance"></a>Örnek 1: Kovaryans

### <a name="description"></a>Açıklama

Bu örnekte, temsilci imzasında dönüş türünden türetilmiş dönüş türlerine sahip yöntemler ile temsilciler'ın nasıl kullanılabileceğini gösterir. Tarafından döndürülen veri türünü `DogsHandler` türünde `Dogs`, öğesinden türetildiğini `Mammals` Temsilcide tanımlanan tür.

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

Bu örnek, bir türün temsilci imzası parametre türü temel tür parametreleri olan yöntemler ile temsilciler nasıl kullanılabileceğini gösterir. Kontravaryans ile ayrı işleyicileri yerine bir olay işleyicisi kullanabilirsiniz. Kabul eden bir olay işleyicisi oluşturma gibi bir `EventArgs` giriş parametresi ve kullanılmakta olan bir `Button.MouseClick` gönderen olay bir `MouseEventArgs` türü bir parametre olarak ve ile bir `TextBox.KeyDown` gönderen olay bir `KeyEventArgs` parametresi.

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
- [İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
