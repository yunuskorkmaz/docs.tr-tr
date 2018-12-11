---
title: '&gt;&gt; Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: fc3d683f212c71620049ec6adee3d20bd5c1437c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240001"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; İşleci (C# Başvurusu)
Sağa kaydırma işleci (`>>`) ilk işlenenin, ikinci işlenen tarafından belirtilen bit sayısının sağa kaydırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Birinci işlenenin ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit miktarı), kaydırma sayısı tarafından düşük sıra beş bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x1f).  
  
 Birinci işlenenin ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit miktarı), kaydırma sayısı tarafından düşük sıra altı bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x3f).  
  
 Birinci işlenenin ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uzun](../../../csharp/language-reference/keywords/long.md), sağa kaydırma aritmetik bir kaydırmadır (imza biti için yüksek düzeyli boş bit ayarlanır). Birinci işlenenin türü ise [uint](../../../csharp/language-reference/keywords/uint.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md), sağa kaydırma mantıksal bir kaydırmadır (yüksek düzeyli bitler sıfır dolgulu).  
  
 Kullanıcı tanımlı türler aşırı yükleme `>>` işleci; birinci işlenenin türü kullanıcı tanımlı bir tür olmalı ve ikinci işlenenin türünde olmalıdır [int](../../../csharp/language-reference/keywords/int.md). Daha fazla bilgi için [işleci](../../../csharp/language-reference/keywords/operator.md). İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
