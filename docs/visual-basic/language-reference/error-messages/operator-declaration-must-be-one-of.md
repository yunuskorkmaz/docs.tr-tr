---
title: "İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-, -, ^, &amp;, Like, Mod ve, Or, Xor, değil, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt; , &gt;=, CType, IsTrue, IsFalse"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords: BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="18599-102">İşleç bildirimi şunlardan biri olmalıdır: +,-, *,\,/, ^, &amp;, Like, Mod ve, Or, Xor, değil, &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="18599-102">Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="18599-103">Aşırı yükleme için uygun olan bir işleç bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18599-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="18599-104">Aşağıdaki tabloda bildirebilirsiniz işleçleri listeler.</span><span class="sxs-lookup"><span data-stu-id="18599-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="18599-105">Tür</span><span class="sxs-lookup"><span data-stu-id="18599-105">Type</span></span>|<span data-ttu-id="18599-106">İşleçler</span><span class="sxs-lookup"><span data-stu-id="18599-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="18599-107">Birli</span><span class="sxs-lookup"><span data-stu-id="18599-107">Unary</span></span>|<span data-ttu-id="18599-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="18599-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="18599-109">İkili</span><span class="sxs-lookup"><span data-stu-id="18599-109">Binary</span></span>|<span data-ttu-id="18599-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="18599-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="18599-111">Dönüştürme (tekli)</span><span class="sxs-lookup"><span data-stu-id="18599-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="18599-112">Unutmayın `=` işlecidir ikili listesinde atama işleci karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="18599-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="18599-113">**Hata Kimliği:** BC33000</span><span class="sxs-lookup"><span data-stu-id="18599-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18599-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="18599-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="18599-115">Fazla yüklenebilir işleçler kümesinden bir işleç seçin.</span><span class="sxs-lookup"><span data-stu-id="18599-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="18599-116">Doğrudan tekrar yükleyemez bir işleç aşırı yüklemesi işlevselliğini ihtiyacınız varsa oluşturma bir `Function` uygun parametreleri alır ve uygun değer döndüren bir yordam.</span><span class="sxs-lookup"><span data-stu-id="18599-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18599-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18599-117">See Also</span></span>  
 [<span data-ttu-id="18599-118">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="18599-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="18599-119">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="18599-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="18599-120">Nasıl yapılır: bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="18599-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="18599-121">Nasıl yapılır: bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="18599-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="18599-122">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="18599-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
