---
title: '&lt;&lt;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: e5f3886670baa34b0360501ee15280b93fac36bc
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171799"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="aeadb-102">&lt;&lt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aeadb-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="aeadb-103">Sola kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="aeadb-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeadb-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeadb-104">Remarks</span></span>  
 <span data-ttu-id="aeadb-105">Formun bir ifade</span><span class="sxs-lookup"><span data-stu-id="aeadb-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="aeadb-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="aeadb-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="aeadb-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aeadb-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="aeadb-108">[<< İşleci](../../../csharp/language-reference/operators/left-shift-operator.md) kaydırır `x` tarafından belirtilen bit sayısı tarafından sol `y`.</span><span class="sxs-lookup"><span data-stu-id="aeadb-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="aeadb-109">`<<=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [<< işleci](../../../csharp/language-reference/operators/left-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="aeadb-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeadb-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeadb-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aeadb-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aeadb-111">See Also</span></span>  
 [<span data-ttu-id="aeadb-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aeadb-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aeadb-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aeadb-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aeadb-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="aeadb-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
