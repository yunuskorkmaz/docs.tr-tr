---
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 0dde340164f1ba80d0e1d9fbb5d17ba6da0a5bc4
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160060"
---
# <a name="bc36532-nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="7721b-102">BC36532: Iç Içe yerleştirilmiş işlevin imzası ' ' temsilcisiyle uyumlu değil \<delegatename></span><span class="sxs-lookup"><span data-stu-id="7721b-102">BC36532: Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>

<span data-ttu-id="7721b-103">Uyumsuz imzaya sahip bir temsilciye bir lambda ifadesi atandı.</span><span class="sxs-lookup"><span data-stu-id="7721b-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="7721b-104">Örneğin, aşağıdaki kodda, temsilcinin `Del` iki tamsayı parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="7721b-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

<span data-ttu-id="7721b-105">Bir bağımsız değişkeni olan bir lambda ifadesi tür olarak bildirilirse hata oluşur `Del` :</span><span class="sxs-lookup"><span data-stu-id="7721b-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

<span data-ttu-id="7721b-106">**Hata kimliği:** BC36532</span><span class="sxs-lookup"><span data-stu-id="7721b-106">**Error ID:** BC36532</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7721b-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7721b-107">To correct this error</span></span>

<span data-ttu-id="7721b-108">İmzaların uyumlu olması için temsilci tanımı ya da atanan lambda ifadesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7721b-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>

## <a name="see-also"></a><span data-ttu-id="7721b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7721b-109">See also</span></span>

- [<span data-ttu-id="7721b-110">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7721b-110">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="7721b-111">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="7721b-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
