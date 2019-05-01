---
title: Null koşullu işleçleri (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: b83435b8448b53eca63aac0519e9eed2f7dfa9f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028697"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. ve? () null koşullu işleçleri (Visual Basic)

Sol işlenen null değerini test eder (`Nothing`) üye erişimi gerçekleştirmeden önce (`?.`) ya da dizin (`?()`) döndürür; işlem `Nothing` sol işlenen değerlendirilirse `Nothing`. Normalde değer türleri döndüren ifadeler null koşullu işleci döndürmediğine dikkat edin bir <xref:System.Nullable%601>.

Bu işleçler null denetimleri, özellikle veri yapılarda azalan zaman işlemek için daha az kod yazmanıza yardımcı olur. Örneğin:

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

Karşılaştırma için ilk kez bir null koşullu işleci olmadan bu ifadelerin alternatif koddur:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Null koşullu işleçleri short-circuiting.  Koşullu üye erişimi ve dizin işlemlerini zincirinin tek bir işlemde döndürürse `Nothing`, kalan zincirinin yürütmeyi durdurur.  Aşağıdaki örnekte, `C(E)` değilse değerlendirilmez `A`, `B`, veya `C` değerlendiren `Nothing`.

```vb
A?.B?.C?(E);
```

Başka bir null koşullu üye erişimi için temsilciler çok daha az kod ile iş parçacığı güvenli bir şekilde çağırmak için kullanılır.  Aşağıdaki örnek, iki tür tanımlar. bir `NewsBroadcaster` ve `NewsReceiver`. Haber öğelerinin bir alıcı tarafından gönderilen `NewsBroadcaster.SendNews` temsilci.

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

Hiçbir öğe olarak varsa `SendNews` çağrı listesine `SendNews` temsilci oluşturur bir <xref:System.NullReferenceException>. Null koşullu işleçleri önce aşağıdaki temsilci çağırma listesi olmadığını sağlamış gibi kod `Nothing`:

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

Yeni yolu çok daha kolaydır:  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı açısından güvenli yeni yoludur `SendNews` sonucu geçici bir değişkende tutma yalnızca bir kez. Açıkça çağırmak ihtiyacınız `Invoke` yöntemi hiçbir null koşullu temsilci çağırma söz dizimi olduğundan `SendNews?(String)`.  

## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler (Visual Basic)](index.md)
- [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
- [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)
