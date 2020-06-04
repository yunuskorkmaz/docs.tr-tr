---
title: Null koşullu İşleçler
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: bffbba859968e0a050397cd9e685c142f801798a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401478"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. '? () null-koşullu işleçler (Visual Basic)

`Nothing`Bir üye erişimi () veya dizin () işlemi gerçekleştirmeden önce, sol taraftaki işlenenin değerini null () için sınar `?.` `?()` ; `Nothing` sol taraftaki işlenen olarak değerlendirilirse döndürür `Nothing` . Normalde değer türlerini döndüren ifadelerde null koşullu işlecin bir döndürür <xref:System.Nullable%601> .

Bu işleçler, özellikle veri yapılarına göre azalan sırada null denetimleri işlemek için daha az kod yazmanıza yardımcı olur. Örnek:

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

Bazen, bu nesnedeki bir Boole üyesinin değerine bağlı olarak null olabilecek bir nesne üzerinde işlem yapmanız gerekir (aşağıdaki örnekteki Boolean özelliği gibi `IsAllowedFreeShipping` ):

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

Null koşullu işleçler kısa devre dışı.  Bir koşullu üye erişimi ve dizin işlemleri zincirindeki bir işlem döndürülürse `Nothing` , zincir yürütmenin geri kalanı duraklar.  Aşağıdaki örnekte,,, `C(E)` `A` `B` veya `C` olarak değerlendirilirse olarak değerlendirilmez `Nothing` .

```vb
A?.B?.C?(E)
```

Null koşullu üye erişimi için başka bir kullanım, temsilcileri çok daha az kodla iş parçacığı güvenli bir şekilde çağırmektir.  Aşağıdaki örnek, ve a olmak üzere iki tür tanımlar `NewsBroadcaster` `NewsReceiver` . Haber öğeleri, temsilci tarafından alıcıya gönderilir `NewsBroadcaster.SendNews` .

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

Çağırma listesinde hiç öğe yoksa `SendNews` , `SendNews` temsilci bir oluşturur <xref:System.NullReferenceException> . Null koşullu işleçlerden önce, aşağıdaki gibi bir kod temsilci çağırma listesi olmadığı için `Nothing` :

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

Derleyici yalnızca bir kez değerlendirmek üzere kod oluşturduğundan `SendNews` ve sonucu geçici bir değişkende tutarak, yeni yöntem iş parçacığı açısından güvenlidir. `Invoke`Null koşullu temsilci çağırma sözdizimi olmadığından yöntemi açık bir şekilde çağırmanız gerekir `SendNews?(String)` .

## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler (Visual Basic)](index.md)
- [Visual Basic Programlama Kılavuzu](../../programming-guide/index.md)
- [Visual Basic dil başvurusu](../index.md)
