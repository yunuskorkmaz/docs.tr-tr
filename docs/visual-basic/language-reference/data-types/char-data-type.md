---
title: Char Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 3dbbf9f6a2c4079775e05f5d2dcd8704c1ec4259
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387484"
---
# <a name="char-data-type-visual-basic"></a>Char Veri Türü (Visual Basic)

0 ile 65535 arasında değer değişen işaretsiz 16 bit (2 baytlık) kod noktalarını tutar. Her *kod noktası*veya karakter kodu, tek bir Unicode karakteri temsil eder.

## <a name="remarks"></a>Açıklamalar

`Char`Yalnızca tek bir karakter tutmanız gerektiğinde ve ek yüküne ihtiyaç duymadığınızda veri türünü kullanın `String` . Bazı durumlarda, `Char()` `Char` birden çok karakteri tutmak için bir dizi öğe kullanabilirsiniz.

Varsayılan değeri, `Char` bir kod noktası 0 olan karakterdir.

## <a name="unicode-characters"></a>Unicode karakterler

Unicode 'un ilk 128 kod noktası (0 – 127), standart bir ABD klavyesinde bulunan harflere ve simgelere karşılık gelir. Bu ilk 128 kod noktası, ASCII karakter kümesi tarafından tanımlananlarla aynıdır. İkinci 128 kod noktaları (128 – 255) Latin tabanlı alfabe harfleri, vurgular, para birimi sembolleri ve kesirler gibi özel karakterleri temsil eder. Unicode, dünya çapındaki metin karakterleri, Aksanlar ve matematik ve teknik semboller dahil olmak üzere çok çeşitli semboller için kalan kod noktalarını (256-65535) kullanır.

<xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A> `Char` Unicode sınıflandırmasını belirleyebilmeniz için bir değişkende ve gibi yöntemleri kullanabilirsiniz.

## <a name="type-conversions"></a>Tür Dönüştürmeleri

Visual Basic, ve sayısal türler arasında doğrudan dönüştürmez `Char` . Ya da işlevini, <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> `Char` `Integer` kod noktasını temsil eden bir değere dönüştürmek için kullanabilirsiniz. <xref:Microsoft.VisualBasic.Strings.Chr%2A>Veya <xref:Microsoft.VisualBasic.Strings.ChrW%2A> işlevini, `Integer` `Char` Bu kod noktasına sahip bir değeri öğesine dönüştürmek için kullanabilirsiniz.

Tür denetimi anahtarı ( [katı Ifade seçeneği](../statements/option-strict-statement.md)) açık ise, veri türü olarak tanımlamak için, değişmez değer türü karakterini tek karakterli bir dize sabit değerine eklemeniz gerekir `Char` . Aşağıdaki örnek bunu göstermektedir. Değişkene ilk atama, açık olduğu için `charVar` derleyici hatası [BC30512](../../misc/bc30512.md) oluşturur `Option Strict` . `c`Sabit değer türü karakteri değeri bir değer olarak tanımladığı için ikinci derleme başarıyla derlenir `Char` .

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a>Programlama İpuçları

- **Negatif sayılar.** `Char`işaretsiz bir tür ve negatif bir değer temsil edemez. Herhangi bir durumda, `Char` sayısal değerleri tutmak için kullanmamalısınız.

- **Birlikte çalışma konuları.** Örneğin Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabiriminiz varsa, başka ortamlarda karakter türlerinin farklı bir veri genişliğine (8 bit) sahip olduğunu unutmayın. Böyle bir bileşene 8 bitlik bir bağımsız değişken geçirirseniz, bunu `Byte` `Char` Yeni Visual Basic kodunuzda değil olarak bildirin.

- **Kan.** `Char`Widens veri türü `String` . Bu, `Char` ' a dönüştürebileceğiniz `String` ve ile karşılaşmayacak anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .

- **Tür karakterleri.** Değişmez değer türü karakterini `C` tek karakterli bir dize değişmez değerine eklemek, `Char` veri türüne zorlar. `Char`tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Char?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Veri türleri](index.md)
- [Dize Veri Türü](string-data-type.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
