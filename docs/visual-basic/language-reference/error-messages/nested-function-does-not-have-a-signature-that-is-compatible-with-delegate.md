---
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 912962e2ab39c4811294ccc225814b230100e12a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592006"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="f2862-102">İç içe geçmiş işlev temsilcisiyle uyumlu bir imzası yok '\<delegateName'in >'</span><span class="sxs-lookup"><span data-stu-id="f2862-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>
<span data-ttu-id="f2862-103">Bir lambda ifadesi, uyumlu bir imzası olan bir temsilci atanmış durumda.</span><span class="sxs-lookup"><span data-stu-id="f2862-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="f2862-104">Örneğin, aşağıdaki kodda, temsilci `Del` iki tamsayı parametre yok.</span><span class="sxs-lookup"><span data-stu-id="f2862-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="f2862-105">Bir bağımsız değişkenli lambda ifadesi türü olarak bildirilirse hataya neden `Del`:</span><span class="sxs-lookup"><span data-stu-id="f2862-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="f2862-106">**Hata Kimliği:** BC36532</span><span class="sxs-lookup"><span data-stu-id="f2862-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f2862-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f2862-107">To correct this error</span></span>  
  
- <span data-ttu-id="f2862-108">Temsilci tanımı veya atanmış bir lambda ifadesi, imzaları uyumlu olacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2862-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2862-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2862-109">See also</span></span>

- [<span data-ttu-id="f2862-110">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f2862-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="f2862-111">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f2862-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
