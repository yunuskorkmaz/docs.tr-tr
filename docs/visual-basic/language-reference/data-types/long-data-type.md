---
title: Long Veri Türü
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
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400815"
---
# <a name="long-data-type-visual-basic"></a>Uzun veri türü (Visual Basic)

-9.223.372.036.854.775.808 ile 9.223.036.854.775.807 (9.2...E+18) değerinde 64 bit (8 bayt) tümleç ler imzalı tutar.

## <a name="remarks"></a>Açıklamalar

`Integer` Veri türüne `Long` sığmayacak kadar büyük tamsayı numaraları içerecek şekilde veri türünü kullanın.

Varsayılan değeri `Long` 0'dır.

## <a name="literal-assignments"></a>Gerçek atamalar

Bir `Long` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz. Tamsayı literal aralığının `Long` dışında ysa (yani, daha az <xref:System.Int64.MinValue?displayProperty=nameWithType> veya daha <xref:System.Int64.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, heksadesibel ve ikili edebi değerlerolarak temsil edilen 4.294.967.296'ya `Long` eşit tamsayılar atamıştır.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal literals, aşağıdaki örnekte görüldüğü `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Long` gibi, veri türünü ifade etmek için tür karakterini de içerebilir.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Interop Hususlar.** .NET Framework için yazılmayan bileşenlerle (örneğin Otomasyon veya COM nesneleri) `Long` bir araya geldiyseniz, diğer ortamlarda farklı veri genişliğine (32 bit) sahip olduğunu unutmayın. Böyle bir bileşene 32 bitlik bir bağımsız değişken `Integer` geçiyorsanız, bunu yeni Visual Basic kodunuzda değil, `Long` olarak bildirin.

- **Genişletme.** Veri `Long` türü `Decimal`, veya `Single` `Double`. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Long` hatayla karşılaşmadan bu türlerden herhangi birine dönüştürebileceğiniz anlamına gelir.

- **Karakterleri yazın.** Gerçek tür karakterini `L` bir edebi karaktere ekler, `Long` onu veri türüne zorlar. Tanımlayıcı türü karakterini `&` herhangi bir tanımlayıcıya `Long`ekolarak .

- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.Int64?displayProperty=nameWithType> tür yapıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int64>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
