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
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333518"
---
# <a name="-operator-c-reference"></a>| işleç (C# Başvurusu)

İkili `|` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`. İntegral türleri için `|` kendi işlenenden bit seviyesinde veya hesaplar. İçin `bool` işlenenini `|` işlenenleri; mantıksal OR hesaplar diğer bir deyişle, sonucudur `false` , her iki işlenen ve yalnızca, `false`.

## <a name="remarks"></a>Açıklamalar

İkili `|` işleci, birinci bağımsız olarak her iki işlenen değerlendirilir değerini, buna için [koşullu-OR işleci](conditional-or-operator.md) `||`.

Kullanıcı tanımlı türler aşırı yükleme `|` işleci (bkz [işleci](../keywords/operator.md)).

## <a name="example"></a>Örnek

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)