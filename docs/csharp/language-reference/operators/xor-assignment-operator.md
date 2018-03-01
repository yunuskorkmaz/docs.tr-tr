---
title: "^= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ec909-102">^= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ec909-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="ec909-103">Dışlayan OR atama işleci.</span><span class="sxs-lookup"><span data-stu-id="ec909-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec909-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec909-104">Remarks</span></span>  
 <span data-ttu-id="ec909-105">Formun bir ifade</span><span class="sxs-lookup"><span data-stu-id="ec909-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="ec909-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="ec909-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="ec909-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ec909-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ec909-108">[^ İşleci](../../../csharp/language-reference/operators/xor-operator.md) bir bit düzeyinde özel OR işlemi tam sayı işlenenler ve mantıksal hariç veya üzerinde gerçekleştirir [bool](../../../csharp/language-reference/keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="ec909-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="ec909-109">^ = İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [^ işleci](../../../csharp/language-reference/operators/xor-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="ec909-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec909-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec909-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ec909-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec909-111">See Also</span></span>  
 [<span data-ttu-id="ec909-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ec909-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ec909-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ec909-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ec909-114">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="ec909-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
