---
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 28d07f01c0fd467cb68d73749988273eee95edf4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409432"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>İç içe yerleştirilmiş işlevin imzası '\<delegatename>' temsilcisiyle uyumlu değil

Uyumsuz imzaya sahip bir temsilciye bir lambda ifadesi atandı. Örneğin, aşağıdaki kodda, temsilcinin `Del` iki tamsayı parametresi vardır.

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

Bir bağımsız değişkeni olan bir lambda ifadesi tür olarak bildirilirse hata oluşur `Del` :

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**Hata kimliği:** BC36532

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

İmzaların uyumlu olması için temsilci tanımı ya da atanan lambda ifadesini ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Gevşek Temsilci Dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
