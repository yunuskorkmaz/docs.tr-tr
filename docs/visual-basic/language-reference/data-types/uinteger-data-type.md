---
title: Uınteger veri türü (Visual Basic)
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
ms.openlocfilehash: 12447e56f89914121dcc9eda2bee0700343baf12
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646992"
---
# <a name="uinteger-data-type"></a>UInteger veri türü

Değeri 0'dan 4.294.967.295'e arasında değişen ayrı tutma işaretsiz 32-bit (4-bayt) tam sayı.  
  
## <a name="remarks"></a>Açıklamalar

 `UInteger` Veri türünü işaretsiz en büyük değeri en verimli veri genişliği sağlar.  
  
 Varsayılan değer olan `UInteger` 0'dır.  
  
## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirmek ve başlatmak bir `UInteger` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren). Tamsayı sabit değeri aralığının dışında ise `UInteger` (diğer bir deyişle, bu ise kısa <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 3,000,000,000 eşit ve ikili sabit değerler atanır `UInteger` değerleri.
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `UI` veya `ui` [türü karakteri](../../programming-guide/language-features/data-types/type-characters.md) belirtmek için `UInteger` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Programlama ipuçları

 `UInteger` Ve `Integer` veri türleri olduğundan bu en iyi performansı bir 32-bit işlemci üzerinde sağlamak daha küçük tamsayı türleri (`UShort`, `Short`, `Byte`, ve `SByte`), daha az BITS kullandıkları olsa bile daha fazla sürebilir Yükleme, depolama ve getirme.  
  
- **Negatif sayılar.** Çünkü `UInteger` işaretsiz bir türü, negatif bir sayıyı temsil edemez. Tek işlenenli eksi işareti kullanırsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `UInteger`, Visual Basic ifade dönüştürür `Long` ilk.  
  
- **CLS uyumluluğu.** `UInteger` Veri türü değil parçası [ortak dil belirtimi](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), böylece onu kullanan bileşen CLS uyumlu kod kullanamıyor.
  
- **Birlikte çalışabilirlik değerlendirmeleri.** Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, gibi türleri akılda tutulması `uint` diğer ortamlarda farklı veri genişliği (16 bit) olabilir. Bir 16 bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `UShort` yerine `UInteger` Yönetilen Visual Basic kodunuzda.  
  
- **Genişletme.** `UInteger` Widens veri türü için `Long`, `ULong`, `Decimal`, `Single`, ve `Double`. Yani dönüştürebilirsiniz `UInteger` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
- **Tür karakterleri.** Değişmez değer türü karakterleri ekleme `UI` sabit değerine zorlar `UInteger` veri türü. `UInteger` hiçbir tanımlayıcı türü karakteri var.  
  
- **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.UInt32?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt32>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
