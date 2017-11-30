---
title: "&amp;= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="b259d-102">&amp;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b259d-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="b259d-103">AND atama işleci.</span><span class="sxs-lookup"><span data-stu-id="b259d-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b259d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b259d-104">Remarks</span></span>  
 <span data-ttu-id="b259d-105">Bir ifade kullanılarak `&=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="b259d-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="b259d-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="b259d-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="b259d-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b259d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b259d-108">[& İşleci](../../../csharp/language-reference/operators/and-operator.md) tam sayı işlenenler ve mantıksal ve bit düzeyinde mantıksal AND işlemini gerçekleştirir. `bool` işlenen.</span><span class="sxs-lookup"><span data-stu-id="b259d-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="b259d-109">`&=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler ikili aşırı yükleme [& işleci](../../../csharp/language-reference/operators/and-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b259d-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b259d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b259d-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b259d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b259d-111">See Also</span></span>  
 [<span data-ttu-id="b259d-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b259d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b259d-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b259d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b259d-114">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="b259d-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
