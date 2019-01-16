---
title: ^ = işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333557"
---
# <a name="-operator-c-reference"></a>^ = işleci (C# Başvurusu)

Düzeyinde dışlamalı OR ataması işleci.

## <a name="remarks"></a>Açıklamalar

Bir ifade formu

```csharp
x ^= y
```

olarak değerlendirilir

```csharp
x = x ^ y
```

dışında `x` yalnızca bir kez değerlendirilir. [^ İşleci](xor-operator.md) bir bit düzeyinde dışlamalı OR işlemi integral işlenenlerde ve mantıksal hariç veya üzerinde gerçekleştirir [bool](../keywords/bool.md) işlenen.

^ = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [^ işleci](xor-operator.md) (bkz [işleci](../keywords/operator.md)).

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)