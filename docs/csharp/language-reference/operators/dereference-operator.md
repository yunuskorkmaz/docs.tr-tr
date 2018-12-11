---
title: -&gt; Operator - C# başvurusu
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: bb1ccd026f403e68565c5c7681943d8017578d01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234896"
---
# <a name="-gt-operator-c-reference"></a>-&gt; İşleci (C# Başvurusu)

İşaretçi üye erişimi işleci `->` işaretçi yöneltme ve üye erişimi birleştirir.

Varsa `x` bir işaretçi türü `T*` ve `y` erişilebilir bir üyesidir `T`, bir ifade formu

```csharp
x->y
```

eşdeğerdir

```csharp
(*x).y
```

`->` İşleci gerektirir [güvenli](../keywords/unsafe.md) bağlamı.

Daha fazla bilgi için [nasıl yapılır: işaretçiyle bir üyeye erişme](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).

## <a name="operator-overloadability"></a>İşleç overloadability

`->` İşleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [işaretçi üye erişimi](~/_csharplang/spec/unsafe-code.md#pointer-member-access) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
