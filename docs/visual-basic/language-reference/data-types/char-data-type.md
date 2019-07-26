---
title: Char Veri Türü (Visual Basic)
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
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512786"
---
# <a name="char-data-type-visual-basic"></a>Char Veri Türü (Visual Basic)

0 ile 65535 arasında değer değişen işaretsiz 16 bit (2 baytlık) kod noktalarını tutar. Her *kod noktası*veya karakter kodu, tek bir Unicode karakteri temsil eder.

## <a name="remarks"></a>Açıklamalar

Yalnızca tek bir karakter tutmanız gerektiğinde ve `String`ek yüküne ihtiyaç duymadığınızda veritürünükullanın.`Char` Bazı durumlarda, birden çok karakteri `Char()`tutmak için bir `Char` dizi öğe kullanabilirsiniz.

Varsayılan değeri `Char` , bir kod noktası 0 olan karakterdir.

## <a name="unicode-characters"></a>Unicode karakterler

Unicode 'un ilk 128 kod noktası (0 – 127), standart bir ABD klavyesinde bulunan harflere ve simgelere karşılık gelir. Bu ilk 128 kod noktası, ASCII karakter kümesi tarafından tanımlananlarla aynıdır. İkinci 128 kod noktaları (128 – 255) Latin tabanlı alfabe harfleri, vurgular, para birimi sembolleri ve kesirler gibi özel karakterleri temsil eder. Unicode, dünya çapındaki metin karakterleri, Aksanlar ve matematik ve teknik semboller dahil olmak üzere çok çeşitli semboller için kalan kod noktalarını (256-65535) kullanır.

Unicode sınıflandırmasını belirleyebilmeniz için <xref:System.Char.IsDigit%2A> bir <xref:System.Char.IsPunctuation%2A> `Char` değişkende ve gibi yöntemleri kullanabilirsiniz.

## <a name="type-conversions"></a>Tür Dönüştürmeleri

Visual Basic, ve sayısal türler arasında `Char` doğrudan dönüştürmez. Ya <xref:Microsoft.VisualBasic.Strings.Asc%2A> `Char` `Integer` da işlevini, kod noktasını temsil eden bir değere dönüştürmek için kullanabilirsiniz. <xref:Microsoft.VisualBasic.Strings.AscW%2A> Veya <xref:Microsoft.VisualBasic.Strings.Chr%2A> `Integer` `Char` işlevini, bu kod noktasına sahip bir değeri öğesine dönüştürmek için kullanabilirsiniz. <xref:Microsoft.VisualBasic.Strings.ChrW%2A>

Tür denetleme anahtarı ([Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md)) açık ise, `Char` veri türü olarak tanımlamak için, değişmez değer türü karakterini tek karakterli bir dize sabit değerine eklemeniz gerekir. Aşağıdaki örnek bunu göstermektedir.

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a>Programlama İpuçları

- **Negatif sayılar.** `Char`işaretsiz bir tür ve negatif bir değer temsil edemez. Herhangi bir durumda, sayısal değerleri tutmak için `Char` kullanmamalısınız.

- **Birlikte çalışma konuları.** Örneğin Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabiriminiz varsa, başka ortamlarda karakter türlerinin farklı bir veri genişliğine (8 bit) sahip olduğunu unutmayın. Böyle bir bileşene 8 bitlik bir bağımsız değişken geçirirseniz, bunu yeni Visual Basic kodunuzda `Byte` `Char` değil olarak bildirin.

- **Kan.** `Char` Widens`String`veri türü. Bu, `Char` `String` ' a dönüştürebileceğiniz ve bir <xref:System.OverflowException?displayProperty=nameWithType> hatayla karşılaşacağınız anlamına gelir.

- **Tür karakterleri.** Değişmez değer türü karakterini `C` tek karakterli bir dize değişmez değerine eklemek, `Char` veri türüne zorlar. `Char`tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Char?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
