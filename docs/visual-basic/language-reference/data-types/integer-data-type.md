---
title: Tamsayı Veri Türü
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
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343990"
---
# <a name="integer-data-type-visual-basic"></a>Tamsayı veri türü (Visual Basic)

Değer olarak -2.147.483.648 ile 2.147.483.647 arasında değişen imzalı 32 bitlik (4 bayt) tamsayıları tutar.  
  
## <a name="remarks"></a>Açıklamalar

 `Integer` veri türü, 32 bitlik bir işlemcide en iyi performansı sağlar. Diğer tamsayı türlerinin bellekten yüklenmesi ve belleğe depolanması daha yavaştır.  
  
 `Integer` varsayılan değeri 0 ' dır.  

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `Integer` değişkeni bir ondalık sabit değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz. Tamsayı sabit değeri `Integer` aralığının dışındaysa (yani, <xref:System.Int32.MinValue?displayProperty=nameWithType> veya <xref:System.Int32.MaxValue?displayProperty=nameWithType>değerinden daha küçükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 90.946 'e eşit tamsayılar `Integer` değerlere atanır.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `Integer` veri türünü belirtmek için `I` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimsiz değilseniz, `Integer` başka ortamlarda farklı bir veri genişliğine (16 bit) sahip olduğunu unutmayın. Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu yeni Visual Basic kodunuzda `Integer` yerine `Short` olarak bildirin.  
  
- **Kan.** `Integer` veri türü `Long`, `Decimal`, `Single`veya `Double`için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Integer` bu türlerden birine dönüştürebileceğiniz anlamına gelir.  
  
- **Tür karakterleri.** Değişmez değer türü karakter `I` bir sabit değere eklenmesi, `Integer` veri türüne zorlar. Tanımlayıcı türü karakter `%` herhangi bir tanımlayıcıya eklemek bunu `Integer`zorlar.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Int32?displayProperty=nameWithType> yapısıdır.  
  
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
