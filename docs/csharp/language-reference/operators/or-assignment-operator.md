---
title: "|= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aac4fd6016b65daa15da4bd3a414f385edce7c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2bbd8-102">|= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2bbd8-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="2bbd8-103">OR atama işleci.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bbd8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2bbd8-104">Remarks</span></span>  
 <span data-ttu-id="2bbd8-105">Bir ifade kullanılarak `|=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="2bbd8-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```  
x |= y  
```  
  
 <span data-ttu-id="2bbd8-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="2bbd8-106">is equivalent to</span></span>  
  
```  
x = x | y  
```  
  
 <span data-ttu-id="2bbd8-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="2bbd8-108">[&#124; işleci](../../../csharp/language-reference/operators/or-operator.md) tam sayı işlenen üzerinde bit tabanlı mantıksal OR işlemi ve mantıksal OR bool işlenen üzerinde gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="2bbd8-109">`|=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [&#124; işleci](../../../csharp/language-reference/operators/or-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2bbd8-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bbd8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2bbd8-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2bbd8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-111">See Also</span></span>  
 [<span data-ttu-id="2bbd8-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2bbd8-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2bbd8-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2bbd8-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2bbd8-114">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="2bbd8-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
