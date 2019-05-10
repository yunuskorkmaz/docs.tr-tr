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
ms.openlocfilehash: 6600b3b2945120f2f24e14d4cc898cd814366045
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647072"
---
# <a name="char-data-type-visual-basic"></a>Char Veri Türü (Visual Basic)
Değer 0 ile 65535 arasında değişen ayrı tutma imzasız 16-bit (2 baytlık) kod işaret eder. Her *kod noktası*, ya da karakter kodunu tek bir Unicode karakterini temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Char` veri türü, yalnızca tek bir tutacak ihtiyacınız olduğunda ek yükü gerekmez ve karakter `String`. Bazı durumlarda kullanabilirsiniz `Char()`, bir dizi `Char` birden çok karakter tutacak öğeleri.  
  
 Varsayılan değer olan `Char` bir kod noktası 0 ile karakterdir.  
  
## <a name="unicode-characters"></a>Unicode karakterler  
 Unicode ilk 128 kod noktası (0-127) harf ve sembol Standart ABD klavyedeki karşılık gelir. Bu ilk 128 kod noktaları ASCII karakter kümesi tanımlar aynıdır. İkinci 128 kod noktası (128-255) Latin tabanlı alfabedeki harfleri, vurgular, para birimi simgeleri ve kesirli gibi özel karakterleri temsil eder. Unicode kalan kod noktası (256-65535) için semboller, dünya çapında metinsel karakterler, aksanlar ve matematik ve teknik semboller de dahil olmak üzere çok çeşitli kullanır.  
  
 Yöntemler gibi kullanabileceğiniz <xref:System.Char.IsDigit%2A> ve <xref:System.Char.IsPunctuation%2A> üzerinde bir `Char` kendi Unicode sınıflandırmasını belirlemek için değişkeni.  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  
 Visual Basic değil dönüştürme arasında doğrudan `Char` ve sayısal türler. Kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Asc%2A> veya <xref:Microsoft.VisualBasic.Strings.AscW%2A> dönüştürmek için işlevi bir `Char` değerini bir `Integer` , kendi kod noktasını temsil eder. Kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Chr%2A> veya <xref:Microsoft.VisualBasic.Strings.ChrW%2A> dönüştürmek için işlevi bir `Integer` değerini bir `Char` o kod noktasına sahip.  
  
 Tür denetleme geçerseniz ([Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)) açıktır, gerekir eklediğiniz değişmez değer türü karakteri olarak tanımlamak için değişmez değer tek karakterli dize `Char` veri türü. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
- **Negatif sayılar.** `Char` işaretsiz bir türü ve negatif bir değeri temsil edemeyen. Her iki durumda da kullanmamalısınız `Char` sayısal değerleri tutmak için.  
  
- **Birlikte çalışabilirlik değerlendirmeleri.** .NET Framework yazılmaz bileşenleriyle arabirim örnek otomasyon ve COM nesneleri için karakter türleri farklı veri genişliği (8 bit) sahip diğer ortamlarda unutmayın. Böyle bir bileşene 8-bit bağımsız değişken geçirirseniz, olarak bildirin `Byte` yerine `Char` yeni Visual Basic kod.  
  
- **Genişletme.** `Char` Widens veri türü için `String`. Yani dönüştürebilirsiniz `Char` için `String` ve değil karşınıza çıkacak bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
- **Tür karakterleri.** Değişmez değer türü karakterinin `C` değişmez değer için bir tek karakter dizesine zorlar `Char` veri türü. `Char` hiçbir tanımlayıcı türü karakteri var.  
  
- **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Char?displayProperty=nameWithType> yapısı.  
  
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
