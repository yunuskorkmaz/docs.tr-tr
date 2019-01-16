---
title: '* = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333440"
---
# <a name="-operator-c-reference"></a>\*= İşleci (C# Başvurusu)

İkili çarpma atama işleci.

## <a name="remarks"></a>Açıklamalar

Bir ifade kullanarak `*=` atama işleci gibi

```csharp
x *= y
```

eşdeğerdir

```csharp
x = x * y
```

dışında `x` yalnızca bir kez değerlendirilir. [ \* İşleci](multiplication-operator.md) çarpma işlemi gerçekleştirmek sayısal türleri için önceden tanımlanmış.

`*=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [ \* işleci](multiplication-operator.md) (bkz [işleci](../keywords/operator.md)).

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
