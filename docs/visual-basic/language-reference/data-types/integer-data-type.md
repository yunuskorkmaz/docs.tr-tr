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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400738"
---
# <a name="integer-data-type-visual-basic"></a>Sonda veri türü (Visual Basic)

Değer olarak -2.147.483.648 ile 2.147.483.647 arasında değişen imzalı 32 bitlik (4 bayt) tamsayıları tutar.  
  
## <a name="remarks"></a>Açıklamalar

 Veri `Integer` türü, 32 bit işlemcide en iyi performansı sağlar. Diğer tamsayı türlerinin bellekten yüklenmesi ve belleğe depolanması daha yavaştır.  
  
 Varsayılan değeri `Integer` 0'dır.  

## <a name="literal-assignments"></a>Gerçek atamalar

Bir `Integer` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz. Tamsayı literal aralığının `Integer` dışında ysa (yani, daha az <xref:System.Int32.MinValue?displayProperty=nameWithType> veya daha <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, heksadeondamal ve ikili literaller olarak temsil edilen 90.946'ya eşit tamsayılar değerlere `Integer` atanır.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal literals, aşağıdaki örnekte görüldüğü `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Integer` gibi, veri türünü ifade etmek için tür karakterini de içerebilir.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Interop Hususlar.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle bir `Integer` arada bulunuyorsanız, diğer ortamlarda farklı veri genişliğine (16 bit) sahip olduğunu unutmayın. Böyle bir bileşene 16 bitlik bir bağımsız değişken `Short` geçiyorsanız, bunu yeni Visual Basic kodunuzda değil, `Integer` olarak bildirin.  
  
- **Genişletme.** Veri `Integer` türü `Long`, , `Decimal`, `Single`veya `Double`. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Integer` hatayla karşılaşmadan bu türlerden herhangi birine dönüştürebileceğiniz anlamına gelir.  
  
- **Karakterleri yazın.** Gerçek tür karakterini `I` bir edebi karaktere ekler, `Integer` onu veri türüne zorlar. Tanımlayıcı türü karakterini `%` herhangi bir tanımlayıcıya `Integer`ekolarak .  
  
- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.Int32?displayProperty=nameWithType> tür yapıdır.  
  
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
