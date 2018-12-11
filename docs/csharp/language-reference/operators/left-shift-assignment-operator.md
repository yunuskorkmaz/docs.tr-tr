---
title: '&lt;&lt;= İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: f49c6360d6fee3f6d612aee51446545f25cd7d18
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239179"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="20d3d-102">&lt;&lt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="20d3d-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="20d3d-103">Sola kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="20d3d-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20d3d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20d3d-104">Remarks</span></span>  
 <span data-ttu-id="20d3d-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="20d3d-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="20d3d-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="20d3d-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="20d3d-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="20d3d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="20d3d-108">[<< İşleci](../../../csharp/language-reference/operators/left-shift-operator.md) kaydırır `x` tarafından belirtilen bit sayısı kadar sola `y`.</span><span class="sxs-lookup"><span data-stu-id="20d3d-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="20d3d-109">`<<=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [<< işleci](../../../csharp/language-reference/operators/left-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="20d3d-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20d3d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="20d3d-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="20d3d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20d3d-111">See Also</span></span>

- [<span data-ttu-id="20d3d-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="20d3d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="20d3d-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="20d3d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="20d3d-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="20d3d-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
