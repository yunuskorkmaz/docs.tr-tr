---
title: '>> Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219730"
---
# <a name="-operator-c-reference"></a>>> işleci (C# Başvurusu)

Sağa kaydırma işleci `>>` ilk işlenenin ikinci işleneni tarafından tanımlanan bit sayısına göre sağa kaydırır. Tüm tamsayı türlerini destekleyen `>>` işleci. Ancak, ikinci işlenenin türünde olmalıdır [int](../keywords/int.md) veya olan bir türü bir [örtülü sayısal dönüştürme önceden tanımlanmış](../keywords/implicit-numeric-conversions-table.md) için `int`.

Sağa kaydırma işlemi alt sıra bitleri atar. Yüksek düzeyli boş bit konumları birinci işlenenin türünde şu şekilde göre ayarlanır:

- Birinci işlenenin türü ise [int](../keywords/int.md) veya [uzun](../keywords/long.md), sağa kaydırma işleci gerçekleştiren bir **aritmetik** shift: ilk en önemli bite (imza biti) değeri işlenen, yüksek sıralı boş bit konumlarına yayılır. Diğer bir deyişle, ilk işlenen negatif ise yüksek düzeyli boş bit konumları sıfır olarak ayarlanır ve negatif ise birine ayarlayın.

- Birinci işlenenin türü ise [uint](../keywords/uint.md) veya [ulong](../keywords/ulong.md), sağa kaydırma işleci gerçekleştiren bir **mantıksal** shift: yüksek düzeyli boş bit konumları her zaman sıfır olarak ayarlayın.

Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a>Kaydırma sayısı

İfade için `x >> count`, gerçek kaydırma sayısı türüne bağlıdır `x` gibi:

- Varsa türünü `x` olduğu [int](../keywords/int.md) veya [uint](../keywords/uint.md), kaydırma sayısı düşük düzey tarafından verilen *beş* ikinci işlenenin bit. Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x1F` (veya `count & 0b_1_1111`).

- Varsa türünü `x` olduğu [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md), kaydırma sayısı düşük düzey tarafından verilen *altı* ikinci işlenenin bit. Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x3F` (veya `count & 0b_11_1111`).

Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a>Açıklamalar

Kaydırma işleçlerini hiçbir zaman taşıyor neden ve aynı sonuçlar [checked ve unchecked](../keywords/checked-and-unchecked.md) bağlamı.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `>>` işleci. Kullanıcı tanımlı bir tür ederse `T` aşırı `>>` işleci, birinci işlenenin türü olmalıdır `T` ve ikinci işlenenin türünde olmalıdır `int`. Zaman `>>` işleci aşırı yüklenmiş, [sağa kaydırma atama işleci](right-shift-assignment-operator.md) `>>=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)
- [<< işleci](left-shift-operator.md)