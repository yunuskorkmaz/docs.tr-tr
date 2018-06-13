---
title: '&gt;&gt; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 061a69250ef5524fa6b5f7bb4b9527057dd86e05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285895"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; İşleci (C# Başvurusu)
Sağa kaydırma işleci (`>>`) ilk işlenen kendi ikinci işlenen tarafından belirtilen BITS sayısına göre sağa kaydırır.  
  
## <a name="remarks"></a>Açıklamalar  
 İlk işlenen ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey beş BITS ikinci işleneninin verilmiştir (ikinci işleneni & 0x1f).  
  
 İlk işlenen ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey altı BITS ikinci işleneninin verilmiştir (ikinci işleneni & 0x3f).  
  
 İlk işlenen ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uzun](../../../csharp/language-reference/keywords/long.md), aritmetik kaydırma sağa kaydırma olduğu (yüksek düzey boş BITS oturum bit ayarlanır). İlk işlenen türü ise [uint](../../../csharp/language-reference/keywords/uint.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md), sağa kaydırma olduğundan mantıksal shift (yüksek düzey BITS sıfır doldurulmuş).  
  
 Kullanıcı tanımlı türler aşırı yükleme `>>` işleci; ilk işlenen türü kullanıcı tanımlı tür olmalıdır ve ikinci işlenen türünde olmalıdır [int](../../../csharp/language-reference/keywords/int.md). Daha fazla bilgi için bkz: [işleci](../../../csharp/language-reference/keywords/operator.md). İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
