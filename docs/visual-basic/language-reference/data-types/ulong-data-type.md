---
title: ULong Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400703"
---
# <a name="ulong-data-type-visual-basic"></a>ULong veri türü (Visual Basic)

0 ile 18.446.744.073.709.551.615 (1,84 çarpı 10 ^ 19) arasında değişen imzasız 64 bit (8 bayt) tümsedoları tutar.

## <a name="remarks"></a>Açıklamalar

`ULong` Veri türünü, olası en büyük `UInteger`imzasız tümsado değeri için çok büyük ikili veriler veya içerecek şekilde kullanın.

Varsayılan değeri `ULong` 0'dır.

## <a name="literal-assignments"></a>Gerçek atamalar

Bir `ULong` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz. Tamsayı literal aralığının `ULong` dışında ysa (yani, daha az <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya daha <xref:System.UInt64.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, heksadesibel ve ikili edebi değerler olarak temsil edilen 7.934.076.125'e `ULong` eşit tamsayılar değerlere atanır.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal literals, aşağıdaki `UL` örnekte `ul` görüldüğü `ULong` gibi, veri türünü ifade etmek için veya [türü karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Negatif Sayılar.** İmzalanmamış bir tür `ULong` olduğundan, negatif bir sayıyı temsil edemez. Unary eksi (`-`) işleci, yazmayı `ULong`değerlendiren bir ifadeüzerinde kullanırsanız, `Decimal` Visual Basic ifadeyi önce dönüştürür.

- **CLS Uyumluluğu.** Veri `ULong` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.

- **Interop Hususlar.** .NET Framework için yazılmayan bileşenlerle (örneğin Otomasyon veya COM nesneleri) bir araya `ulong` geliyorsanız, diğer ortamlarda farklı veri genişliğine (32 bit) sahip olabilecek türler olduğunu unutmayın. Böyle bir bileşene 32 bitlik bir bağımsız değişken `UInteger` geçiyorsanız, bunu yönetilen Visual Basic kodunuz yerine `ULong` olarak bildirin.

  Ayrıca, Otomasyon Windows 95, Windows 98, Windows ME veya Windows 2000'deki 64 bit'lik tümseleri desteklemez. Visual Basic `ULong` bağımsız değişkenini bu platformlardaki bir Otomasyon bileşenine geçiremezsiniz.

- **Genişletme.** Veri `ULong` türü `Decimal`, , `Single`ve `Double`. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `ULong` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.

- **Karakterleri yazın.** Gerçek türdeki `UL` karakterleri `ULong` bir edebi aygıta ekler, onu veri türüne zorlar. `ULong`tanımlayıcı türü karakteri yoktur.

- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.UInt64?displayProperty=nameWithType> tür yapıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt64>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
