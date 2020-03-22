---
title: UInteger Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400787"
---
# <a name="uinteger-data-type"></a>UInteger veri türü

0 ile 4.294.967.295 arasında değişen imzasız 32 bit (4 bayt) tümsedoları tutar.

## <a name="remarks"></a>Açıklamalar

Veri `UInteger` türü, en verimli veri genişliğindeki en büyük imzasız değeri sağlar.

Varsayılan değeri `UInteger` 0'dır.

## <a name="literal-assignments"></a>Gerçek atamalar

Bir `UInteger` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz. Tamsayı literal aralığının `UInteger` dışında ysa (yani, daha az <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya daha <xref:System.UInt32.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, heksadesibel ve ikili edebi değerler olarak temsil edilen 3.000.000.000'e `UInteger` eşit tamsayılar değerlere atanır.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal literals, aşağıdaki `UI` örnekte `ui` görüldüğü `UInteger` gibi, veri türünü ifade etmek için veya [türü karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Programlama ipuçları

Daha `UInteger` `Integer` küçük tamsayı türleri (,`UShort`, `Short` `Byte`, ve `SByte`), daha az bit kullansalar bile, yüklemek, depolamak ve getirmek daha fazla zaman alsalar da, 32 bitlik bir işlemcide en iyi performansı sağlar.

- **Negatif Sayılar.** İmzalanmamış bir tür `UInteger` olduğundan, negatif bir sayıyı temsil edemez. Unary eksi (`-`) işleci, yazmayı `UInteger`değerlendiren bir ifadeüzerinde kullanırsanız, `Long` Visual Basic ifadeyi önce dönüştürür.

- **CLS Uyumluluğu.** Veri `UInteger` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.

- **Interop Hususlar.** .NET Framework için yazılmayan bileşenlerle (örneğin Otomasyon veya COM nesneleri) bir araya `uint` geliyorsanız, diğer ortamlarda farklı veri genişliğine (16 bit) sahip olabilecek türler olduğunu unutmayın. Böyle bir bileşene 16 bitlik bir bağımsız değişken `UShort` geçiyorsanız, bunu yönetilen Visual Basic kodunuz yerine `UInteger` olarak bildirin.

- **Genişletme.** Veri `UInteger` `Long`türü , , `ULong` `Decimal`, `Single`, `Double`ve . Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `UInteger` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.

- **Karakterleri yazın.** Gerçek türdeki `UI` karakterleri `UInteger` bir edebi aygıta ekler, onu veri türüne zorlar. `UInteger`tanımlayıcı türü karakteri yoktur.

- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.UInt32?displayProperty=nameWithType> tür yapıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt32>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
