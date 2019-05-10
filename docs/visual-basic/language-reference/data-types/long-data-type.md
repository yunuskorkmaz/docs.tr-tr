---
title: Long Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 7b4226c83f25807e013823031820d58790bb6db2
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912783"
---
# <a name="long-data-type-visual-basic"></a>Long veri türü (Visual Basic)

İmzalı-9,223,372,036,854,775,808 değerden 9.223.372.036.854.775.807 arasında değişen 64-bit (8-bayt) tamsayıları tutar (9.2... E + 18).  
  
## <a name="remarks"></a>Açıklamalar

 Kullanım `Long` sığacak kadar büyük tamsayı sayılar içeren veri türü `Integer` veri türü.  
  
 Varsayılan değer olan `Long` 0'dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları 

Bildirmek ve başlatmak bir `Long` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren). Tamsayı sabit değeri aralığının dışında ise `Long` (diğer bir deyişle, bu ise kısa <xref:System.Int64.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int64.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 4,294,967,296 eşit ve ikili sabit değerler atanır `Long` değerleri.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `L` [türü karakteri](../../programming-guide/language-features/data-types/type-characters.md) belirtmek için `Long` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Birlikte çalışabilirlik değerlendirmeleri.** Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim olmadığını unutmayın `Long` diğer ortamlarda farklı veri genişliği (32 bit) sahiptir. Bir 32-bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `Integer` yerine `Long` yeni Visual Basic kod.  
  
- **Genişletme.** `Long` Widens veri türü için `Decimal`, `Single`, veya `Double`. Yani dönüştürebilirsiniz `Long` karşılaşmadan bu türlerden herhangi birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
- **Tür karakterleri.** Değişmez değer türü karakterinin `L` sabit değerine zorlar `Long` veri türü. Tanımlayıcı türü karakteri ekleme `&` herhangi bir tanımlayıcı zorlar `Long`.  
  
- **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Int64?displayProperty=nameWithType> yapısı.  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int64>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
