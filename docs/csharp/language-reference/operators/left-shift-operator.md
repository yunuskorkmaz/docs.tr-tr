---
title: << işleci - C# başvurusu
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219443"
---
# <a name="-operator-c-reference"></a>\<\< İşleci (C# Başvurusu)

Sola kaydırma işleci `<<` ilk işleneni sol tarafından ikinci işleneni tarafından tanımlanan bit sayısı kadar kaydırır. Tüm tamsayı türlerini destekleyen `<<` işleci. Ancak, ikinci işlenenin türünde olmalıdır [int](../keywords/int.md) veya olan bir türü bir [örtülü sayısal dönüştürme önceden tanımlanmış](../keywords/implicit-numeric-conversions-table.md) için `int`.

Sonuç türü aralığının dışında olan yüksek sıra bitleri atılır ve düşük düzey boş bit konumları, aşağıdaki örnekte gösterildiği gibi sıfır olarak ayarlayın:

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a>Kaydırma sayısı

İfade için `x << count`, gerçek kaydırma sayısı türüne bağlıdır `x` gibi:

- Varsa türünü `x` olduğu [int](../keywords/int.md) veya [uint](../keywords/uint.md), kaydırma sayısı düşük düzey tarafından verilen *beş* ikinci işlenenin bit. Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x1F` (veya `count & 0b_1_1111`).

- Varsa türünü `x` olduğu [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md), kaydırma sayısı düşük düzey tarafından verilen *altı* ikinci işlenenin bit. Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x3F` (veya `count & 0b_11_1111`).

Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a>Açıklamalar

Kaydırma işleçlerini hiçbir zaman taşıyor neden ve aynı sonuçlar [checked ve unchecked](../keywords/checked-and-unchecked.md) bağlamı.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `<<` işleci. Kullanıcı tanımlı bir tür ederse `T` aşırı `<<` işleci, birinci işlenenin türü olmalıdır `T` ve ikinci işlenenin türünde olmalıdır `int`. Zaman `<<` işleci aşırı yüklenmiş, [sola kaydırma atama işleci](left-shift-assignment-operator.md) `<<=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [>> işleci](right-shift-operator.md)
