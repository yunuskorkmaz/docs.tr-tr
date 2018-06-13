---
title: 'İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-, -, ^, &amp;, Like, Mod ve, Or, Xor, değil, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt; , &gt;=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: eb1e7e8088ec8661be2469aff043c0f1a96e4d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595026"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="d86a7-102">İşleç bildirimi şunlardan biri olmalıdır: +,-, \*,\,/, ^, &amp;, Like, Mod ve, Or, Xor, değil, &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="d86a7-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="d86a7-103">Aşırı yükleme için uygun olan bir işleç bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d86a7-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="d86a7-104">Aşağıdaki tabloda bildirebilirsiniz işleçleri listeler.</span><span class="sxs-lookup"><span data-stu-id="d86a7-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="d86a7-105">Tür</span><span class="sxs-lookup"><span data-stu-id="d86a7-105">Type</span></span>|<span data-ttu-id="d86a7-106">İşleçler</span><span class="sxs-lookup"><span data-stu-id="d86a7-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="d86a7-107">Birli</span><span class="sxs-lookup"><span data-stu-id="d86a7-107">Unary</span></span>|<span data-ttu-id="d86a7-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="d86a7-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="d86a7-109">İkili</span><span class="sxs-lookup"><span data-stu-id="d86a7-109">Binary</span></span>|<span data-ttu-id="d86a7-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="d86a7-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="d86a7-111">Dönüştürme (tekli)</span><span class="sxs-lookup"><span data-stu-id="d86a7-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="d86a7-112">Unutmayın `=` işlecidir ikili listesinde atama işleci karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="d86a7-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="d86a7-113">**Hata Kimliği:** BC33000</span><span class="sxs-lookup"><span data-stu-id="d86a7-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d86a7-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d86a7-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="d86a7-115">Fazla yüklenebilir işleçler kümesinden bir işleç seçin.</span><span class="sxs-lookup"><span data-stu-id="d86a7-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="d86a7-116">Doğrudan tekrar yükleyemez bir işleç aşırı yüklemesi işlevselliğini ihtiyacınız varsa oluşturma bir `Function` uygun parametreleri alır ve uygun değer döndüren bir yordam.</span><span class="sxs-lookup"><span data-stu-id="d86a7-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86a7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d86a7-117">See Also</span></span>  
 [<span data-ttu-id="d86a7-118">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="d86a7-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="d86a7-119">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="d86a7-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="d86a7-120">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d86a7-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="d86a7-121">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d86a7-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="d86a7-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="d86a7-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
