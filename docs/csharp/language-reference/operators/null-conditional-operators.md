---
title: "Null-conditional İşleçleri (C# ve Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="7c990-102">Null-conditional İşleçleri (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c990-102">Null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="7c990-103">Null üye erişimi gerçekleştirmeden önce test etmek için kullanılan (`?.`) veya dizin (`?[`) işlemi.</span><span class="sxs-lookup"><span data-stu-id="7c990-103">Used to test for null before performing a member access (`?.`) or index (`?[`) operation.</span></span>  <span data-ttu-id="7c990-104">Bu işleçleri özellikle veri yapılara azalan düzen için null işlemek için daha az kod denetler yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7c990-104">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="7c990-105">Null koşul işleçleri short-circuiting son örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7c990-105">The last example demonstrates that the null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="7c990-106">Koşullu üye erişimi ve dizin işlemi zinciri tek bir işlemde null değeri döndürülürse, rest zincirinin yürütme durdurur.</span><span class="sxs-lookup"><span data-stu-id="7c990-106">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="7c990-107">İfadedeki daha düşük önceliğe sahip diğer işlemleri devam edin.</span><span class="sxs-lookup"><span data-stu-id="7c990-107">Other operations with lower precedence in the expression continue.</span></span>  <span data-ttu-id="7c990-108">Örneğin, `E` ikinci satırında aşağıdaki yürütür ve `??` ve `==` işlemlerini yürütmek.</span><span class="sxs-lookup"><span data-stu-id="7c990-108">For example, `E` in the following executes in the second line, and the `??` and `==` operations execute.</span></span>  <span data-ttu-id="7c990-109">İlk satırdaki `??` kısa devreler ve `E` null olmayan için sol tarafındaki değerlendirirken, yürütmez.</span><span class="sxs-lookup"><span data-stu-id="7c990-109">In the first line, the `??` short circuits and `E` does not execute when the left side evaluates to non-null.</span></span>
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 <span data-ttu-id="7c990-110">Null koşul üyesi erişim için başka bir kullanım temsilciler çok daha az kod ile iş parçacığı açısından güvenli şekilde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7c990-110">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="7c990-111">Eski şekilde aşağıdaki gibi bir kod gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7c990-111">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="7c990-112">Yeni yol çok daha kolaydır:</span><span class="sxs-lookup"><span data-stu-id="7c990-112">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="7c990-113">Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı yeni yoludur `PropertyChanged` sonucu geçici bir değişkende tutma yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="7c990-113">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="7c990-114">Açıkça çağırmanız gerekir `Invoke` yöntemi hiçbir null-conditional temsilci çağırma sözdizimi olduğundan `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="7c990-114">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  <span data-ttu-id="7c990-115">İzin vermek için çok fazla belirsiz ayrıştırma durumlarda vardı.</span><span class="sxs-lookup"><span data-stu-id="7c990-115">There were too many ambiguous parsing situations to allow it.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="7c990-116">Dil belirtimleri</span><span class="sxs-lookup"><span data-stu-id="7c990-116">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="7c990-117">Daha fazla bilgi için bkz: [Visual Basic dil başvurusu](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c990-117">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c990-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c990-118">See Also</span></span>  
 [<span data-ttu-id="7c990-119">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="7c990-119">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="7c990-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7c990-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7c990-121">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7c990-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7c990-122">Visual Basic Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7c990-122">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="7c990-123">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7c990-123">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
