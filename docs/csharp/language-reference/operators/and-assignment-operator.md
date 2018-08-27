---
title: '&amp;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933958"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="676f8-102">&amp;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="676f8-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="676f8-103">AND atama işleci.</span><span class="sxs-lookup"><span data-stu-id="676f8-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="676f8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="676f8-104">Remarks</span></span>  
 <span data-ttu-id="676f8-105">Bir ifade kullanarak `&=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="676f8-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```csharp  
x &= y  
```  
  
 <span data-ttu-id="676f8-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="676f8-106">is equivalent to</span></span>  
  
```csharp  
x = x & y  
```  
  
 <span data-ttu-id="676f8-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="676f8-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="676f8-108">[& İşleci](../../../csharp/language-reference/operators/and-operator.md) integral işlenen ve mantıksal AND bit düzeyinde bir mantıksal ve işlem gerçekleştiren `bool` işlenen.</span><span class="sxs-lookup"><span data-stu-id="676f8-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="676f8-109">`&=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler ikili aşırı yükleme [& işleci](../../../csharp/language-reference/operators/and-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="676f8-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="676f8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="676f8-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="676f8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="676f8-111">See Also</span></span>

- [<span data-ttu-id="676f8-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="676f8-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="676f8-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="676f8-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="676f8-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="676f8-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
