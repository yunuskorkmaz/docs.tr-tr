---
title: '|= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45744097"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f4eb6-102">|= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f4eb6-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="f4eb6-103">OR atama işleci.</span><span class="sxs-lookup"><span data-stu-id="f4eb6-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4eb6-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4eb6-104">Remarks</span></span>  
 <span data-ttu-id="f4eb6-105">Bir ifade kullanarak `|=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="f4eb6-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```csharp  
x |= y  
```  
  
 <span data-ttu-id="f4eb6-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="f4eb6-106">is equivalent to</span></span>  
  
```csharp  
x = x | y  
```  
  
 <span data-ttu-id="f4eb6-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f4eb6-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f4eb6-108">[ &#124; İşleci](../../../csharp/language-reference/operators/or-operator.md) bool işlenenlerde integral işlenen üzerinde bit düzeyinde bir mantıksal OR işlem ve mantıksal OR gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f4eb6-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="f4eb6-109">`|=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [ &#124; işleci](../../../csharp/language-reference/operators/or-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f4eb6-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4eb6-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4eb6-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f4eb6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4eb6-111">See Also</span></span>

- [<span data-ttu-id="f4eb6-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f4eb6-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f4eb6-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f4eb6-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f4eb6-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f4eb6-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
