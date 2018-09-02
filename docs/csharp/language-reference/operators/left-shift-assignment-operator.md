---
title: '&lt;&lt;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: c689aeccdf3ad6cc6c672cc101a4f0aa92f19791
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406980"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="2d3c5-102">&lt;&lt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2d3c5-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="2d3c5-103">Sola kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="2d3c5-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d3c5-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d3c5-104">Remarks</span></span>  
 <span data-ttu-id="2d3c5-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="2d3c5-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="2d3c5-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="2d3c5-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="2d3c5-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2d3c5-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="2d3c5-108">[<< İşleci](../../../csharp/language-reference/operators/left-shift-operator.md) kaydırır `x` tarafından belirtilen bit sayısı kadar sola `y`.</span><span class="sxs-lookup"><span data-stu-id="2d3c5-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="2d3c5-109">`<<=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [<< işleci](../../../csharp/language-reference/operators/left-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2d3c5-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d3c5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d3c5-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2d3c5-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d3c5-111">See Also</span></span>

- [<span data-ttu-id="2d3c5-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2d3c5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2d3c5-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2d3c5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2d3c5-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2d3c5-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
