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
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="bcf1b-102">?.</span><span class="sxs-lookup"><span data-stu-id="bcf1b-102">?.</span></span> <span data-ttu-id="bcf1b-103">'? () null-koşullu işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcf1b-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="bcf1b-104">`Nothing`Bir üye erişimi () veya dizin () işlemi gerçekleştirmeden önce, sol taraftaki işlenenin değerini null () için sınar `?.` `?()` ; `Nothing` sol taraftaki işlenen olarak değerlendirilirse döndürür `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="bcf1b-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="bcf1b-105">Normalde değer türlerini döndüren ifadelerde null koşullu işlecin bir döndürür <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="bcf1b-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="bcf1b-106">Bu işleçler, özellikle veri yapılarına göre azalan sırada null denetimleri işlemek için daha az kod yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bcf1b-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="bcf1b-107">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bcf1b-107">For example:</span></span>

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

<span data-ttu-id="bcf1b-108">Karşılaştırma için, bu ifadelerin ilki için alternatif kod, null-Conditional işleci olmadan:</span><span class="sxs-lookup"><span data-stu-id="bcf1b-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="bcf1b-109">Bazen, bu nesnedeki bir Boole üyesinin değerine bağlı olarak null olabilecek bir nesne üzerinde işlem yapmanız gerekir (aşağıdaki örnekteki Boolean özelliği gibi `IsAllowedFreeShipping` ):</span><span class="sxs-lookup"><span data-stu-id="bcf1b-109">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

<span data-ttu-id="bcf1b-110">Kodunuzu kısaltabilir ve null koşullu işleci kullanarak null için el ile kontrol edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bcf1b-110">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="bcf1b-111">Null koşullu işleçler kısa devre dışı.</span><span class="sxs-lookup"><span data-stu-id="bcf1b-111">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="bcf1b-112">Bir koşullu üye erişimi ve dizin işlemleri zincirindeki bir işlem döndürülürse `Nothing` , zincir yürütmenin geri kalanı duraklar.</span><span class="sxs-lookup"><span data-stu-id="bcf1b-112">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="bcf1b-113">Aşağıdaki örnekte,,, `C(E)` `A` `B` veya `C` olarak değerlendirilirse olarak değerlendirilmez `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="bcf1b-113">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E)
```

<span data-ttu-id="bcf1b-114">Null koşullu üye erişimi için başka bir kullanım, temsilcileri çok daha az kodla iş parçacığı güvenli bir şekilde çağırmektir.</span><span class="sxs-lookup"><span data-stu-id="bcf1b-114">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="bcf1b-115">Aşağıdaki örnek, ve a olmak üzere iki tür tanımlar `NewsBroadcaster` `NewsReceiver` .</span><span class="sxs-lookup"><span data-stu-id="bcf1b-115">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="bcf1b-116">Haber öğeleri, temsilci tarafından alıcıya gönderilir `NewsBroadcaster.SendNews` .</span><span class="sxs-lookup"><span data-stu-id="bcf1b-116">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

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

<span data-ttu-id="bcf1b-117">Çağırma listesinde hiç öğe yoksa `SendNews` , `SendNews` temsilci bir oluşturur <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="bcf1b-117">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="bcf1b-118">Null koşullu işleçlerden önce, aşağıdaki gibi bir kod temsilci çağırma listesi olmadığı için `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="bcf1b-118">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

<span data-ttu-id="bcf1b-119">Yeni yol çok daha basittir:</span><span class="sxs-lookup"><span data-stu-id="bcf1b-119">The new way is much simpler:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="bcf1b-120">Derleyici yalnızca bir kez değerlendirmek üzere kod oluşturduğundan `SendNews` ve sonucu geçici bir değişkende tutarak, yeni yöntem iş parçacığı açısından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="bcf1b-120">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="bcf1b-121">`Invoke`Null koşullu temsilci çağırma sözdizimi olmadığından yöntemi açık bir şekilde çağırmanız gerekir `SendNews?(String)` .</span><span class="sxs-lookup"><span data-stu-id="bcf1b-121">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcf1b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcf1b-122">See also</span></span>

- [<span data-ttu-id="bcf1b-123">İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcf1b-123">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="bcf1b-124">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bcf1b-124">Visual Basic Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bcf1b-125">Visual Basic dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="bcf1b-125">Visual Basic Language Reference</span></span>](../index.md)
