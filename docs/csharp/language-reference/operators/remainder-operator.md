---
title: '% İşleci (C# Başvurusu)'
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: cd6d49b69d40f3b45aae060d46b58632dc8448f8
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144212"
---
# <a name="-operator-c-reference"></a>% İşleci (C# Başvurusu)

Kalan işleci `%` ilk işlenenin ikinci işleneni tarafından bölme işleminden kalanı hesaplar.

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `%` işleci. Zaman `%` aşırı yüklendi [kalan atama işleci](remainder-assignment-operator.md) `%=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

Kalan işleci tüm sayısal türlerin destekler.

## <a name="integer-remainder"></a>Tamsayı kalan
  
Sonucu tamsayı işlenenleri için `a % b` değeri tarafından üretilen `a - (a / b) * b`. Sıfır olmayan kalanı oturum, ilk işlenen, aşağıdaki örnekte gösterildiği gibi aynıdır:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a>Kayan nokta kalanını

İçin [float](../keywords/float.md) ve [çift](../keywords/double.md) işlenenler, sonucunu `x % y` sınırlı için `x` ve `y` değer `z` gibi

- işaretini `z`, sıfır olmayan, işaretini aynı `x`;
- mutlak değerini `z` değeri tarafından üretilen `|x| - n * |y|` burada `n` küçük veya eşit en büyük olası tamsayı `|x| / |y|` ve `|x|` ve `|y|` mutlak değerleri `x` ve `y`sırasıyla.

Davranışı hakkında bilgi için `%` sonlu olmayan işlenenler işleç bkz [kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).

> [!NOTE]
> Kalanı hesaplama, bu yöntem, tamsayı işlenenler için kullanılan benzer, ancak IEEE 754 farklıdır. IEEE 754 ile uyumlu işlemini ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi.

Aşağıdaki örnek için kalan işleci davranışını gösterir `float` ve `double` işlenenler:

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

Kayan nokta türleri ile ilişkilendirilebilen yuvarlama hataları unutmayın.

İçin [ondalık](../keywords/decimal.md) işlenenler, kalan işleci `%` eşdeğerdir [kalan işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) , <xref:System.Decimal?displayProperty=nameWithType> türü.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
