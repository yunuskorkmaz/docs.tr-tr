---
title: /= İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: c31ff374e6af4c08c329a971fdd8af169e239395
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a6972-102">/= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6972-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="a6972-103">Bölme atama işleci.</span><span class="sxs-lookup"><span data-stu-id="a6972-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6972-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6972-104">Remarks</span></span>  
 <span data-ttu-id="a6972-105">Bir ifade kullanılarak `/=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="a6972-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="a6972-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="a6972-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="a6972-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a6972-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a6972-108">[/ İşleci](../../../csharp/language-reference/operators/division-operator.md) bölme gerçekleştirmek sayısal türler için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="a6972-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="a6972-109">`/=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [/ işleci](../../../csharp/language-reference/operators/division-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a6972-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a6972-110">Tüm bileşik atama işleçleri üzerinde örtük olarak ikili İşleç aşırı yüklemesi eşdeğer bileşik atama overloads.</span><span class="sxs-lookup"><span data-stu-id="a6972-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6972-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6972-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a6972-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6972-112">See Also</span></span>  
 [<span data-ttu-id="a6972-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a6972-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a6972-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a6972-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a6972-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="a6972-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
