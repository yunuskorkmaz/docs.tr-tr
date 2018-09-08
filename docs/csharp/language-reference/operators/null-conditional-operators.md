---
title: Null-conditional İşleçleri (C# ve Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: f00d5e489931d9c1172a21ee5f0d3e3d0a6f4a4e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192820"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="b8282-102">?.</span><span class="sxs-lookup"><span data-stu-id="b8282-102">?.</span></span> <span data-ttu-id="b8282-103">ve? [] null koşullu işleçleri (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8282-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="b8282-104">Üye erişimi gerçekleştirmeden önce sol işleneni null değerini test eder (`?.`) ya da dizin (`?[]`) döndürür; işlem `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="b8282-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span> 

<span data-ttu-id="b8282-105">Bu işleçler null işlemek için daha az kod denetler, özellikle azalan düzende veri yapılarda yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b8282-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="b8282-106">Null koşullu işleçleri short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="b8282-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="b8282-107">Null koşullu üye erişimi ve dizin işlemi zincirinin tek bir işlemde döndürürse, rest zincirinin yürütme durur.</span><span class="sxs-lookup"><span data-stu-id="b8282-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="b8282-108">Aşağıdaki örnekte, `E` değilse yürütülmez `A`, `B`, veya `C` null olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b8282-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="b8282-109">Null koşullu üye erişimi için başka bir kullanım temsilciler çok daha az kod ile iş parçacığı güvenli bir şekilde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b8282-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="b8282-110">Kod aşağıdaki gibi eski yöntem gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b8282-110">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="b8282-111">Yeni yolu çok daha kolaydır:</span><span class="sxs-lookup"><span data-stu-id="b8282-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 <span data-ttu-id="b8282-112">Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı açısından güvenli yeni yoludur `PropertyChanged` sonucu geçici bir değişkende tutma yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="b8282-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="b8282-113">Açıkça çağırmak ihtiyacınız `Invoke` yöntemi hiçbir null koşullu temsilci çağırma söz dizimi olduğundan `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="b8282-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="b8282-114">Dil özellikleri</span><span class="sxs-lookup"><span data-stu-id="b8282-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="b8282-115">Daha fazla bilgi için [Visual Basic dil başvurusu](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8282-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8282-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8282-116">See Also</span></span>

- [<span data-ttu-id="b8282-117">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="b8282-117">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)  
- [<span data-ttu-id="b8282-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b8282-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b8282-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b8282-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b8282-120">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b8282-120">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
