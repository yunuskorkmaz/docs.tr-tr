---
title: SByte Veri Türü (Visual Basic)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: b2ef4f083cd9b6f38dc91bf8bf0eac9cd21c2618
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148090"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte veri türü (Visual Basic)

Değeri -128 ile 127 arasında 8-bit (1-bayt) tamsayıları tutar imzalanmış.  
  
## <a name="remarks"></a>Açıklamalar

Kullanım `SByte` veri türü, tam veri genişliği gerektirmeyen tamsayı değerler içerecek şekilde `Integer` ve hatta yarım veri genişliği `Short`. Bazı durumlarda, ortak dil çalışma zamanı paketi mümkün olabilir, `SByte` değişkenleri yakından birlikte ve bellek tüketimi.

Varsayılan değer olan `SByte` 0'dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları
  
Bildirmek ve başlatmak bir `SByte` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren).

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen-102 eşit ve ikili sabit değerler atanır `SByte` değerleri. Bu örnek ile derleme gerektirir `/removeintchecks` derleyici anahtarı.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Tamsayı sabit değeri aralığının dışında ise `SByte` (diğer bir deyişle, bu ise kısa <xref:System.SByte.MinValue?displayProperty=nameWithType> veya ondan <xref:System.SByte.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur. Tamsayı sabit değeri, sonek varsa bir [tamsayı](integer-data-type.md) algılanır. Tamsayı sabit değeri aralığının dışında ise `Integer` türü, bir [uzun](long-data-type.md) algılanır. Bu, önceki örneklerde, sayısal değişmez değerleri anlamına `0x9A` ve `0b10011010` aşıyor 156, değerini 32-bit imzalı tamsayı olarak yorumlanır <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Başarıyla bir ondalık olmayan tamsayı olarak atar. Bu kodu derlemek için bir `SByte`, aşağıdakilerden birini yapabilirsiniz:

- Tamsayı sınırları denetimlerini ile derleme tarafından devre dışı `/removeintchecks` derleyici anahtarı.

- Kullanım bir [türü karakteri](../../programming-guide/language-features/data-types/type-characters.md) atamak istediğiniz değişmez değer açıkça tanımlamak için `SByte`. Aşağıdaki örnek, negatif bir sabit değer atar `Short` değerini bir `SByte`. Negatif sayılar için dikkat edin, yüksek sıralı bitten yüksek düzeyli Word sayısal sabit değerinin ayarlanması gerekir. Bizim örneğimizde söz konusu olduğunda bu bit sabit değerinin 15 `Short` değeri.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Programlama ipuçları
  
-   **CLS uyumluluğu.** `SByte` Veri türü değil parçası [ortak dil belirtimi](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), böylece onu kullanan bileşen CLS uyumlu kod kullanamıyor.

-   **Genişletme.** `SByte` Widens veri türü için `Short`, `Integer`, `Long`, `Decimal`, `Single`, ve `Double`. Yani dönüştürebilirsiniz `SByte` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.
  
-   **Tür karakterleri.** `SByte` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.SByte?displayProperty=nameWithType> yapısı.
  
## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.SByte?displayProperty=nameWithType>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
