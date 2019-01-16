---
title: -= işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333336"
---
# <a name="--operator-c-reference"></a>-= işleci (C# Başvurusu)

Çıkarma atama işleci.

## <a name="remarks"></a>Açıklamalar

Bir ifade kullanarak `-=` atama işleci gibi

```csharp
x -= y
```

 eşdeğerdir

```csharp
x = x - y
```

dışında `x` yalnızca bir kez değerlendirilir. Anlamını [-işleci](subtraction-operator.md) türlerine bağlıdır `x` ve `y` (sayısal işlenenler için çıkarma temsilci temsilcinin işlenenleri için temizleme vb.).

`-=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [-işleci](subtraction-operator.md) (bkz [işleci](../keywords/operator.md)).

-= İşleci ayrıca C# dilinde bir olayın aboneliğini kaldırmak için kullanılır. Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)
