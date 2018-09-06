---
title: '&gt;&gt;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: f2bac6a4320980d80a9b6c2597dcf8dc6f08ac70
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748732"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="68e01-102">&gt;&gt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="68e01-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="68e01-103">Sağa kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="68e01-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68e01-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68e01-104">Remarks</span></span>  
 <span data-ttu-id="68e01-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="68e01-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="68e01-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="68e01-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="68e01-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="68e01-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="68e01-108">[>> İşleci](../../../csharp/language-reference/operators/right-shift-operator.md) kaydırır `x` sağ tarafından belirtilen bir miktara göre `y`.</span><span class="sxs-lookup"><span data-stu-id="68e01-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="68e01-109">>> = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [>> işleci](../../../csharp/language-reference/operators/right-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="68e01-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68e01-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="68e01-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="68e01-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68e01-111">See Also</span></span>

- [<span data-ttu-id="68e01-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="68e01-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="68e01-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="68e01-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="68e01-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="68e01-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
