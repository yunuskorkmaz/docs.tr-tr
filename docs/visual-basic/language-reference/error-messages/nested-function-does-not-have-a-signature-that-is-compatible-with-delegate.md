---
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 04eae6d2c6d64e8a0f46ae3c2801a7eb6d893dca
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822304"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="c4f73-102">İç içe geçmiş işlev temsilcisiyle uyumlu bir imzası yok '\<delegateName'in >'</span><span class="sxs-lookup"><span data-stu-id="c4f73-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>
<span data-ttu-id="c4f73-103">Bir lambda ifadesi, uyumlu bir imzası olan bir temsilci atanmış durumda.</span><span class="sxs-lookup"><span data-stu-id="c4f73-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="c4f73-104">Örneğin, aşağıdaki kodda, temsilci `Del` iki tamsayı parametre yok.</span><span class="sxs-lookup"><span data-stu-id="c4f73-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="c4f73-105">Bir bağımsız değişkenli lambda ifadesi türü olarak bildirilirse hataya neden `Del`:</span><span class="sxs-lookup"><span data-stu-id="c4f73-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="c4f73-106">**Hata Kimliği:** BC36532</span><span class="sxs-lookup"><span data-stu-id="c4f73-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4f73-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c4f73-107">To correct this error</span></span>  
  
-   <span data-ttu-id="c4f73-108">Temsilci tanımı veya atanmış bir lambda ifadesi, imzaları uyumlu olacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c4f73-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f73-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4f73-109">See also</span></span>

- [<span data-ttu-id="c4f73-110">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c4f73-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="c4f73-111">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c4f73-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
