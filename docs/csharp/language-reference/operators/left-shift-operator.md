---
title: '&lt;&lt; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: bacb444c08b1f9d6e18278337015d8a427fdbe46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286181"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt; İşleci (C# Başvurusu)
Sola kaydırma işleci (`<<`) ilk işlenen sola bit sayısı kadar ikinci işlenen tarafından belirtilen kaydırır. İkinci işlenen türünde olmalıdır bir [int](../../../csharp/language-reference/keywords/int.md) veya önceden tanımlanmış bir örtük sayısal dönüştürme için olan bir türü `int`.  
  
## <a name="remarks"></a>Açıklamalar  
 İlk işlenen ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey beş BITS ikinci işleneninin verilir. Diğer bir deyişle, gerçek üst karakter sayısı 0-31 bittir.  
  
 İlk işlenen ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey altı BITS ikinci işleneninin verilir. Diğer bir deyişle, gerçek üst karakter sayısı 0-63 bittir.  
  
 Olan herhangi bir yüksek düzey BITS shift sonra ilk işlenen türü aralık içinde değil atılır ve düşük düzey boş BITS sıfırla doldurulur. Shift işlemleri hiçbir zaman taşan neden olur.  
  
 Kullanıcı tanımlı türler aşırı yükleme `<<` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)); ilk işlenen türü kullanıcı tanımlı tür olmalıdır ve ikinci işlenen türünde olmalıdır `int`. İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Unutmayın `i<<1` ve `i<<33` 1 ve 33 aynı düşük düzey beş BITS olduğu için aynı sonucu verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
