---
title: '>> Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 703d4ee50bb9f49c66df029de9c5a280449d11fa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255321"
---
# <a name="-operator-c-reference"></a>>> işleci (C# Başvurusu)

Sağa kaydırma işleci (`>>`) ilk işlenenin, ikinci işlenen tarafından belirtilen bit sayısının sağa kaydırır.

## <a name="remarks"></a>Açıklamalar

Birinci işlenenin ise bir [int](../keywords/int.md) veya [uint](../keywords/uint.md) (32-bit miktarı), kaydırma sayısı tarafından düşük sıra beş bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x1f).

Birinci işlenenin ise bir [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md) (64-bit miktarı), kaydırma sayısı tarafından düşük sıra altı bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x3f).

Birinci işlenenin ise bir [int](../keywords/int.md) veya [uzun](../keywords/long.md), sağa kaydırma aritmetik bir kaydırmadır (imza biti için yüksek düzeyli boş bit ayarlanır). Birinci işlenenin türü ise [uint](../keywords/uint.md) veya [ulong](../keywords/ulong.md), sağa kaydırma mantıksal bir kaydırmadır (yüksek düzeyli bitler sıfır dolgulu).

Kullanıcı tanımlı türler aşırı yükleme `>>` işleci; birinci işlenenin türü kullanıcı tanımlı bir tür olmalı ve ikinci işlenenin türünde olmalıdır [int](../keywords/int.md). Daha fazla bilgi için [işleci](../keywords/operator.md). İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)