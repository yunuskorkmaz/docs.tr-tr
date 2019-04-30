---
title: -> İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: be74f02a85aa05cdab32768ed38222fc4d9289b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660020"
---
# <a name="--operator-c-reference"></a>-> İşleci (C# Başvurusu)

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
