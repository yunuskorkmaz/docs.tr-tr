---
title: '&lt;&lt; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 036acd6159bcf5ca1677ee6383c9db357625cd67
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276818"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt; İşleci (C# Başvurusu)
Sola kaydırma işleci (`<<`) ilk işlenenin sol tarafından ikinci işlenen tarafından belirtilen bit sayısı kadar kaydırır. İkinci işlenenin türünde olmalıdır bir [int](../../../csharp/language-reference/keywords/int.md) veya önceden tanımlanmış bir örtük sayısal dönüştürme için olan bir türü `int`.  
  
## <a name="remarks"></a>Açıklamalar  
 Birinci işlenenin ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit miktarı), kaydırma sayısı tarafından düşük sıra beş bitleri ikinci işlenenin verilir. Diğer bir deyişle, gerçek kaydırma sayısı 0-31 bittir.  
  
 Birinci işlenenin ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit miktarı), kaydırma sayısı tarafından düşük sıra altı bitleri ikinci işlenenin verilir. Diğer bir deyişle, gerçek kaydırma sayısı 0 ila 63 bittir.  
  
 Shift sonra birinci işlenenin türü aralık içinde değil olan herhangi bir yüksek sıra bitleri atılır ve düşük düzey boş bitler sıfır dolguludur. Kaydırma işleçlerini, hiçbir zaman taşıyor neden.  
  
 Kullanıcı tanımlı türler aşırı yükleme `<<` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)); birinci işlenenin türü kullanıcı tanımlı bir tür olmalı ve ikinci işlenenin türünde olmalıdır `int`. İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Unutmayın `i<<1` ve `i<<33` aynı düşük sıra beş bitleri 1 ve 33 olduğundan aynı sonucu verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
