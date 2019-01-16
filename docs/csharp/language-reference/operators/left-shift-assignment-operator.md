---
title: '&lt;&lt;= işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333258"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= işleci (C# Başvurusu)

Sola kaydırma atama işleci.

## <a name="remarks"></a>Açıklamalar

Bir ifade formu

```csharp
x <<= y
```

olarak değerlendirilir

```csharp
x = x << y
```

dışında `x` yalnızca bir kez değerlendirilir. [<< İşleci](left-shift-operator.md) kaydırır `x` tarafından belirtilen bit sayısı kadar sola `y`.

`<<=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [<< işleci](left-shift-operator.md) (bkz [işleci](../keywords/operator.md)).

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
