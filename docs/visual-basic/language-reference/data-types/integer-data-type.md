---
title: Tamsayı Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: b553471fad6411cd5aa2edf42d8424aa652e9589
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592108"
---
# <a name="integer-data-type-visual-basic"></a>Tamsayı veri türü (Visual Basic)
Değer olarak -2.147.483.648 ile 2.147.483.647 arasında değişen imzalı 32 bitlik (4 bayt) tamsayıları tutar.  
  
## <a name="remarks"></a>Açıklamalar
 `Integer` Veri türü 32-bit işlemci üzerinde en iyi performansı sağlar. Diğer tamsayı türlerinin bellekten yüklenmesi ve belleğe depolanması daha yavaştır.  
  
 Varsayılan değer olan `Integer` 0'dır.  

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirmek ve başlatmak bir `Integer` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren). Tamsayı sabit değeri aralığının dışında ise `Integer` (diğer bir deyişle, bu ise kısa <xref:System.Int32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int32.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 90,946 eşit ve ikili sabit değerler atanır `Integer` değerleri.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `I` [türü karakteri](../../programming-guide/language-features/data-types/type-characters.md) belirtmek için `Integer` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Birlikte çalışabilirlik değerlendirmeleri.** Otomasyon ve COM nesneleri gibi .NET Framework için yazılmaz bileşenleriyle arabirim olmadığını unutmayın `Integer` diğer ortamlarda farklı veri genişliği (16 bit) sahiptir. Bir 16 bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `Short` yerine `Integer` yeni Visual Basic kod.  
  
- **Genişletme.** `Integer` Widens veri türü için `Long`, `Decimal`, `Single`, veya `Double`. Yani dönüştürebilirsiniz `Integer` karşılaşmadan bu türlerden herhangi birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
- **Tür karakterleri.** Değişmez değer türü karakterinin `I` sabit değerine zorlar `Integer` veri türü. Tanımlayıcı türü karakteri ekleme `%` herhangi bir tanımlayıcı zorlar `Integer`.  
  
- **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Int32?displayProperty=nameWithType> yapısı.  
  
## <a name="range"></a>Aralık

Tamsayı türünde bir değişkeni, bu türe ilişkin aralık dışında bir sayıya ayarlamaya çalışırsanız hata meydana gelir. Bir kesir olarak ayarlamaya çalışırsanız, sayı en yakın tamsayı değerine yukarı veya aşağı yuvarlanır. Sayı iki tamsayı değerine de eşit yakınlıkta ise, değer en yakın çift tamsayıya yuvarlanır. Bu davranış, bir orta nokta değerini tek bir yönde sürekli olarak yuvarlamaktan kaynaklanan yuvarlama hatalarını en aza indirir. Aşağıdaki kod, yuvarlama örneklerini göstermektedir.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int32?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
