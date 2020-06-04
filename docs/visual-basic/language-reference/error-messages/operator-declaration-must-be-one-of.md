---
title: 'İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-,-, ^, &amp; , LIKE, mod, and, or, XOR, Not,  <<,  >>, =,  <>, <, <=, >, >=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 3fb2cf392611e5ca83818e3bf173513be031085d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409341"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="639a4-102">İşleç bildirimi şunlardan biri olmalıdır: +,-, \*, \, /, ^, &amp; , LIKE, mod, and, or, XOR, Not, \<\<, >>...</span><span class="sxs-lookup"><span data-stu-id="639a4-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="639a4-103">Yalnızca aşırı yükleme için uygun bir işleç bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="639a4-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="639a4-104">Aşağıdaki tabloda, bildirebilmeniz için kullanabileceğiniz işleçler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="639a4-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="639a4-105">Tür</span><span class="sxs-lookup"><span data-stu-id="639a4-105">Type</span></span>|<span data-ttu-id="639a4-106">İşleçler</span><span class="sxs-lookup"><span data-stu-id="639a4-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="639a4-107">Birli</span><span class="sxs-lookup"><span data-stu-id="639a4-107">Unary</span></span>|<span data-ttu-id="639a4-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="639a4-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="639a4-109">İkili</span><span class="sxs-lookup"><span data-stu-id="639a4-109">Binary</span></span>|<span data-ttu-id="639a4-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="639a4-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="639a4-111">Dönüştürme (birli)</span><span class="sxs-lookup"><span data-stu-id="639a4-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="639a4-112">`=`İkili listedeki işlecin atama işleci değil karşılaştırma operatörü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="639a4-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="639a4-113">**Hata kimliği:** BC33000</span><span class="sxs-lookup"><span data-stu-id="639a4-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="639a4-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="639a4-114">To correct this error</span></span>  
  
1. <span data-ttu-id="639a4-115">Fazla yüklenebilir işleçler kümesinden bir işleç seçin.</span><span class="sxs-lookup"><span data-stu-id="639a4-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="639a4-116">Doğrudan aşırı yükleyemez olmayan bir işleci aşırı yükleme işlevselliğine ihtiyacınız varsa, `Function` uygun parametreleri alan ve uygun değeri döndüren bir yordam oluşturun.</span><span class="sxs-lookup"><span data-stu-id="639a4-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639a4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="639a4-117">See also</span></span>

- [<span data-ttu-id="639a4-118">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="639a4-118">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="639a4-119">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="639a4-119">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="639a4-120">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="639a4-120">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="639a4-121">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="639a4-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="639a4-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="639a4-122">Function Statement</span></span>](../statements/function-statement.md)
