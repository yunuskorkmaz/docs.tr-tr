---
title: UShort Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400696"
---
# <a name="ushort-data-type-visual-basic"></a>UShort veri türü (Visual Basic)

0 ile 65.535 arasında değişen imzasız 16 bit (2 bayt) tümsedoları tutar.  
  
## <a name="remarks"></a>Açıklamalar

 `UShort` Için çok büyük ikili veri içerecek `Byte`şekilde veri türünü kullanın.  
  
 Varsayılan değeri `UShort` 0'dır.  

## <a name="literal-assignments"></a>Gerçek atamalar

Bir `UShort` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz. Tamsayı literal aralığının `UShort` dışında ysa (yani, daha az <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya daha <xref:System.UInt16.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, heksadeondamal ve ikili literaller olarak temsil edilen 65.034'e eşit tamsayılar değerlere `UShort` atanır.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal literals, aşağıdaki `US` örnekte `us` görüldüğü `UShort` gibi, veri türünü ifade etmek için veya [türü karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Programlama ipuçları
  
- **Negatif Sayılar.** İmzalanmamış bir tür `UShort` olduğundan, negatif bir sayıyı temsil edemez. Unary eksi (`-`) işleci, yazmayı `UShort`değerlendiren bir ifadeüzerinde kullanırsanız, `Integer` Visual Basic ifadeyi önce dönüştürür.  
  
- **CLS Uyumluluğu.** Veri `UShort` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.
  
- **Genişletme.** Veri `UShort` `Integer`türü , , `UInteger` `Long` `ULong`, `Decimal`, `Single`, `Double`ve . Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `UShort` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.  
  
- **Karakterleri yazın.** Gerçek türdeki `US` karakterleri `UShort` bir edebi aygıta ekler, onu veri türüne zorlar. `UShort`tanımlayıcı türü karakteri yoktur.  
  
- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.UInt16?displayProperty=nameWithType> tür yapıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt16>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
