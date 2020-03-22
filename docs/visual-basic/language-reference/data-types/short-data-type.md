---
title: Short Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400731"
---
# <a name="short-data-type-visual-basic"></a>Kısa veri türü (Visual Basic)

-32.768 ile 32.767 arasında değişen imzalı 16 bit (2 bayt) tümsedoları tutar.  
  
## <a name="remarks"></a>Açıklamalar  

 Tam `Short` veri genişliği gerektirmeyen tamsayı değerlerini içerecek şekilde veri türünü kullanın. `Integer` Bazı durumlarda, ortak dil çalışma süresi `Short` değişkenlerinizi birbirine yakın bir şekilde paketleyebilir ve bellek tüketiminden tasarruf edebilir.  
  
 Varsayılan değeri `Short` 0'dır.  
  
## <a name="literal-assignments"></a>Gerçek atamalar

Bir `Short` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz. Tamsayı literal aralığının `Short` dışında ysa (yani, daha az <xref:System.Int16.MinValue?displayProperty=nameWithType> veya daha <xref:System.Int16.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, heksadesimal ve ikili literalolarak temsil edilen 1.034'e eşit tamsayılar dolaylı olarak `Short` [Tamsayı'dan](integer-data-type.md) değerlere dönüştürülür.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal literals, aşağıdaki örnekte görüldüğü `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Short` gibi, veri türünü ifade etmek için tür karakterini de içerebilir.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Genişletme.** Veri `Short` `Integer`türü , , `Long` `Decimal` `Single`, , `Double`veya . Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Short` hatayla karşılaşmadan bu türlerden herhangi birine dönüştürebileceğiniz anlamına gelir.  
  
- **Karakterleri yazın.** Gerçek tür karakterini `S` bir edebi karaktere ekler, `Short` onu veri türüne zorlar. `Short`tanımlayıcı türü karakteri yoktur.  
  
- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.Int16?displayProperty=nameWithType> tür yapıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int16?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
