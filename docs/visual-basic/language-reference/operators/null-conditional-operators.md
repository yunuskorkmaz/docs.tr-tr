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
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="4b2e5-102">?.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-102">?.</span></span> <span data-ttu-id="4b2e5-103">ve? () null koşullu işleçleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b2e5-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="4b2e5-104">Sol işlenen null değerini test eder (`Nothing`) üye erişimi gerçekleştirmeden önce (`?.`) ya da dizin (`?()`) döndürür; işlem `Nothing` sol işlenen değerlendirilirse `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="4b2e5-105">Normalde değer türleri döndüren ifadeler null koşullu işleci döndürmediğine dikkat edin bir <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="4b2e5-106">Bu işleçler null denetimleri, özellikle veri yapılarda azalan zaman işlemek için daha az kod yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="4b2e5-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4b2e5-107">For example:</span></span>

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

<span data-ttu-id="4b2e5-108">Karşılaştırma için ilk kez bir null koşullu işleci olmadan bu ifadelerin alternatif koddur:</span><span class="sxs-lookup"><span data-stu-id="4b2e5-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="4b2e5-109">Null koşullu işleçleri short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-109">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="4b2e5-110">Koşullu üye erişimi ve dizin işlemlerini zincirinin tek bir işlemde döndürürse `Nothing`, kalan zincirinin yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-110">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="4b2e5-111">Aşağıdaki örnekte, `C(E)` değilse değerlendirilmez `A`, `B`, veya `C` değerlendiren `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-111">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="4b2e5-112">Başka bir null koşullu üye erişimi için temsilciler çok daha az kod ile iş parçacığı güvenli bir şekilde çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-112">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="4b2e5-113">Aşağıdaki örnek, iki tür tanımlar. bir `NewsBroadcaster` ve `NewsReceiver`.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-113">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="4b2e5-114">Haber öğelerinin bir alıcı tarafından gönderilen `NewsBroadcaster.SendNews` temsilci.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-114">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

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

<span data-ttu-id="4b2e5-115">Hiçbir öğe olarak varsa `SendNews` çağrı listesine `SendNews` temsilci oluşturur bir <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-115">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="4b2e5-116">Null koşullu işleçleri önce aşağıdaki temsilci çağırma listesi olmadığını sağlamış gibi kod `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="4b2e5-116">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

<span data-ttu-id="4b2e5-117">Yeni yolu çok daha kolaydır:</span><span class="sxs-lookup"><span data-stu-id="4b2e5-117">The new way is much simpler:</span></span>  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="4b2e5-118">Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı açısından güvenli yeni yoludur `SendNews` sonucu geçici bir değişkende tutma yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-118">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="4b2e5-119">Açıkça çağırmak ihtiyacınız `Invoke` yöntemi hiçbir null koşullu temsilci çağırma söz dizimi olduğundan `SendNews?(String)`.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-119">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4b2e5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b2e5-120">See also</span></span>

- [<span data-ttu-id="4b2e5-121">İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b2e5-121">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="4b2e5-122">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4b2e5-122">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="4b2e5-123">Visual Basic Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4b2e5-123">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
