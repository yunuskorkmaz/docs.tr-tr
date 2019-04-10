---
title: '| operator - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312884"
---
# <a name="-operator-c-reference"></a>| işleç (C# Başvurusu)

İkili `|` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`. İntegral türleri için `|` kendi işlenenden bit seviyesinde veya hesaplar. İçin `bool` işlenenini `|` işlenenleri; mantıksal OR hesaplar diğer bir deyişle, sonucudur `false` , her iki işlenen ve yalnızca, `false`.

## <a name="remarks"></a>Açıklamalar

İkili `|` işleci, birinci bağımsız olarak her iki işlenen değerlendirilir değerini, buna için [koşullu-OR işleci](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.

Kullanıcı tanımlı türler aşırı yükleme `|` işleci (bkz [işleci](../keywords/operator.md)).

## <a name="example"></a>Örnek

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# işleçleri](index.md)