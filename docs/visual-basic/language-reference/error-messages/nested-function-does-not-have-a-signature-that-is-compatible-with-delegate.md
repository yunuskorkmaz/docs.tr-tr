---
description: "Şu konuda daha fazla bilgi edinin: BC36532: Iç Içe yerleştirilmiş işlev, ' ' temsilcisiyle uyumlu bir imzaya sahip değil <delegatename>"
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: ff6abda015187d0d7d0690f2f1fd00772e63c61b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483553"
---
# <a name="bc36532-nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>BC36532: Iç Içe yerleştirilmiş işlevin imzası ' ' temsilcisiyle uyumlu değil \<delegatename>

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
