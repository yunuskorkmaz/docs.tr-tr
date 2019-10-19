---
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: d65c8eab661675c955ff6562098248c04036d6e7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580646"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="158be-102">İç içe yerleştirilmiş işlevin imzası ' \<delegatename > ' temsilcisiyle uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="158be-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>

<span data-ttu-id="158be-103">Uyumsuz imzaya sahip bir temsilciye bir lambda ifadesi atandı.</span><span class="sxs-lookup"><span data-stu-id="158be-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="158be-104">Örneğin, aşağıdaki kodda, temsilci `Del` iki tamsayı parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="158be-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

<span data-ttu-id="158be-105">Bir bağımsız değişkeni olan bir lambda ifadesi `Del` tür olarak bildirilirse hata oluşur:</span><span class="sxs-lookup"><span data-stu-id="158be-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

<span data-ttu-id="158be-106">**Hata kimliği:** BC36532</span><span class="sxs-lookup"><span data-stu-id="158be-106">**Error ID:** BC36532</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="158be-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="158be-107">To correct this error</span></span>

<span data-ttu-id="158be-108">İmzaların uyumlu olması için temsilci tanımı ya da atanan lambda ifadesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="158be-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>

## <a name="see-also"></a><span data-ttu-id="158be-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="158be-109">See also</span></span>

- [<span data-ttu-id="158be-110">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="158be-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="158be-111">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="158be-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
