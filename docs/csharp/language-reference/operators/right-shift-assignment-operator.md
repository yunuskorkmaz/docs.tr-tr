---
title: '>>= işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278986"
---
# <a name="-operator-c-reference"></a>>> = işleci (C# Başvurusu)

Sağa kaydırma atama işleci.

## <a name="remarks"></a>Açıklamalar

Bir ifade formu

```csharp
x >>= y
```

olarak değerlendirilir

```csharp
x = x >> y
```

dışında `x` yalnızca bir kez değerlendirilir. [>> İşleci](right-shift-operator.md) kaydırır `x` sağ tarafından belirtilen bir miktara göre `y`.

>> = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [>> işleci](right-shift-operator.md) (bkz [işleci](../keywords/operator.md)).

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)