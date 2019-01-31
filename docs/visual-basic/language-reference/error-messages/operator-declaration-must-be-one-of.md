---
title: 'İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-, -, ^, &amp;, Like, Mod ve, Or, Xor, Not, <<>>,, <> =, <, < =, >, > =, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 7acec56be60f88147bac1ba4179ad0234ea1c6e1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270062"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="fd4c3-102">İşleç bildirimi şunlardan biri olmalıdır: +,-, \*,\,/, ^, &amp;, Like, Mod ve, Or, Xor, Not, \< \<, >>...</span><span class="sxs-lookup"><span data-stu-id="fd4c3-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="fd4c3-103">Aşırı yükleme için uygun olan bir işleç bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="fd4c3-104">Aşağıdaki tabloda bildirebilirsiniz işleçleri listelenir.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="fd4c3-105">Tür</span><span class="sxs-lookup"><span data-stu-id="fd4c3-105">Type</span></span>|<span data-ttu-id="fd4c3-106">İşleçler</span><span class="sxs-lookup"><span data-stu-id="fd4c3-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="fd4c3-107">Birli</span><span class="sxs-lookup"><span data-stu-id="fd4c3-107">Unary</span></span>|<span data-ttu-id="fd4c3-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="fd4c3-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="fd4c3-109">İkili</span><span class="sxs-lookup"><span data-stu-id="fd4c3-109">Binary</span></span>|<span data-ttu-id="fd4c3-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="fd4c3-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="fd4c3-111">Dönüştürme (tekli)</span><span class="sxs-lookup"><span data-stu-id="fd4c3-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="fd4c3-112">Unutmayın `=` işlecidir ikili listesinde karşılaştırma işleci atama işleci.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="fd4c3-113">**Hata Kimliği:** BC33000</span><span class="sxs-lookup"><span data-stu-id="fd4c3-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd4c3-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fd4c3-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="fd4c3-115">Fazla yüklenebilir işleçler kümesinden bir işleç seçin.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="fd4c3-116">Doğrudan aşırı yüklenemez operatör aşırı yüklemesi işlevselliğini gerekiyorsa, oluşturun bir `Function` uygun parametreleri alır ve uygun bir değer döndüren yordam.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4c3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-117">See also</span></span>
- [<span data-ttu-id="fd4c3-118">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="fd4c3-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="fd4c3-119">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="fd4c3-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="fd4c3-120">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="fd4c3-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="fd4c3-121">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="fd4c3-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="fd4c3-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="fd4c3-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
