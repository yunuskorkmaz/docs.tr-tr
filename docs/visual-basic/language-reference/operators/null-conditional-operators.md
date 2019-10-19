---
title: Null-koşullu Işleçler (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 40cb63705eda563b4c3cfd30fa9836a8f632dccf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581631"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. '? () null-koşullu işleçler (Visual Basic)

Bir üye erişimi (`?.`) veya dizin (`?()`) işlemini gerçekleştirmeden önce sol işlenenin değerini null (`Nothing`) olarak sınar. Sol işlenen `Nothing` olarak değerlendirilirse `Nothing` döndürür. Normalde değer türlerini döndüren ifadelerde, null koşullu işlecin bir <xref:System.Nullable%601> döndürdüğünü unutmayın.

Bu işleçler, özellikle veri yapılarına göre azalan sırada null denetimleri işlemek için daha az kod yazmanıza yardımcı olur. Örneğin:

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

Karşılaştırma için, bu ifadelerin ilki için alternatif kod, null-Conditional işleci olmadan:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Bazen, bu nesnedeki bir Boole üyesinin değerine bağlı olarak null olabilecek bir nesne üzerinde işlem yapmanız gerekir (aşağıdaki örnekte `IsAllowedFreeShipping` Boolean özelliği gibi):

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

Kodunuzu kısaltabilir ve null koşullu işleci kullanarak null için el ile kontrol edebilirsiniz:

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Null koşullu işleçler kısa devre dışı.  Koşullu üye erişimi ve dizin işlemleri zincirindeki bir işlem `Nothing` döndürürse, zincir yürütmenin geri kalanı duraklar.  Aşağıdaki örnekte, `A`, `B` veya `C` `Nothing` değerlendirilirse `C(E)` değerlendirilmez.

```vb
A?.B?.C?(E);
```

Null koşullu üye erişimi için başka bir kullanım, temsilcileri çok daha az kodla iş parçacığı güvenli bir şekilde çağırmektir.  Aşağıdaki örnek, `NewsBroadcaster` ve `NewsReceiver` iki türü tanımlar. Haber öğeleri `NewsBroadcaster.SendNews` temsilcisi tarafından alıcıya gönderilir.

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

@No__t_0 çağrısı listesinde hiç öğe yoksa, `SendNews` temsilcisi bir <xref:System.NullReferenceException> oluşturur. Null koşullu işleçlerden önce, aşağıdaki gibi kod temsilci çağırma listesi `Nothing` değildi:

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

Yeni yol çok daha basittir:

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

Derleyici, yalnızca bir kez `SendNews` değerlendirmek üzere kod oluşturduğundan ve sonucu geçici bir değişkende tutarak, yeni yöntem iş parçacığı açısından güvenlidir. Null koşullu temsilci çağırma sözdizimi `SendNews?(String)` olmadığından `Invoke` yöntemi açıkça çağırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler (Visual Basic)](index.md)
- [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
- [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)
