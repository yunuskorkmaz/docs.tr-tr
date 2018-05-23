---
title: '&gt;&gt;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: ccc3f688d985b9e35404550f0c53a7acf8095dd5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="70219-102">&gt;&gt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="70219-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="70219-103">Sağa kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="70219-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70219-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70219-104">Remarks</span></span>  
 <span data-ttu-id="70219-105">Formun bir ifade</span><span class="sxs-lookup"><span data-stu-id="70219-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="70219-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="70219-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="70219-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="70219-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="70219-108">[>> İşleci](../../../csharp/language-reference/operators/right-shift-operator.md) kaydırır `x` sağ tarafından belirtilen bir miktar `y`.</span><span class="sxs-lookup"><span data-stu-id="70219-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="70219-109">>> = İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [>> işleci](../../../csharp/language-reference/operators/right-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="70219-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70219-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="70219-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="70219-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70219-111">See Also</span></span>  
 [<span data-ttu-id="70219-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="70219-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="70219-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="70219-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="70219-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="70219-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
