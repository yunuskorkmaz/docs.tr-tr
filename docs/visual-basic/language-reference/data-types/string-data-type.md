---
title: Dize Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 3e87dc6527b4351467b1155439ee8266157c16ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842297"
---
# <a name="string-data-type-visual-basic"></a>Dize Veri Türü (Visual Basic)
İmzasız 16-bit (2 baytlık) kod noktaları dizisi bu aralık 0 ile 65535 arasında bir değer tutar. Her *kod noktası*, ya da karakter kodunu tek bir Unicode karakterini temsil eder. Bir dize yaklaşık iki milyardan fazla 0'dan içerebilir (2 ^ 31) Unicode karakter.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `String` birden çok karakter dizisi yönetim yükü olmadan tutmak için veri türü `Char()`, bir dizi `Char` öğeleri.  
  
 Varsayılan değer olan `String` olduğu `Nothing` (null bir başvuru). Bu boş bir dize ile aynı olduğunu unutmayın (değer `""`).  
  
## <a name="unicode-characters"></a>Unicode karakterler  
 Unicode ilk 128 kod noktası (0-127) harf ve sembol Standart ABD klavyedeki karşılık gelir. Bu ilk 128 kod noktaları ASCII karakter kümesi tanımlar aynıdır. İkinci 128 kod noktası (128-255) Latin tabanlı alfabedeki harfleri, vurgular, para birimi simgeleri ve kesirli gibi özel karakterleri temsil eder. Unicode çok çeşitli semboller için kalan kod noktası (256-65535) kullanır. Bu, dünya çapında metinsel karakterler, aksanlar ve matematik ve teknik semboller içerir.  
  
 Gibi yöntemler kullanmanız <xref:System.Char.IsDigit%2A> ve <xref:System.Char.IsPunctuation%2A> tekil karakter, üzerinde bir `String` kendi Unicode sınıflandırmasını belirlemek için değişkeni.  
  
## <a name="format-requirements"></a>Biçim gereksinimlerini  
 İçine almalısınız bir `String` tırnak işaretleri içindeki sabit değeri (`" "`). Bir dizedeki karakter olarak bir tırnak işareti içermelidir, iki bitişik tırnak işareti kullanın (`""`). Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Bitişik dize bir tırnak işareti temsil eden tırnak başlayıp bitiş tırnak işareti bağımsız olduğunu unutmayın `String` değişmez.  
  
## <a name="string-manipulations"></a>Dize işlemeleri  
 Bir dizeye atadıktan sonra bir `String` değişken olduğundan, o dizeyi *değişmez*, anlamına gelir, uzunluk veya içeriği değiştiremezsiniz. Bir dizedeki herhangi bir şekilde değiştirdiğinizde, Visual Basic yeni bir dize oluşturur ve önceki bırakır. `String` Değişkeni sonra yeni dizeye işaret eder.  
  
 İçeriğini işleyebileceğiniz bir `String` değişken dize işlevleri çeşitli kullanarak. Aşağıdaki örnekte gösterilmiştir <xref:Microsoft.VisualBasic.Strings.Left%2A> işlevi  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Başka bir bileşen tarafından oluşturulan bir dize, baştaki veya sondaki boşlukları ile sıfır. Bu tür bir dize alırsanız, kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, ve <xref:Microsoft.VisualBasic.Strings.RTrim%2A> işlevleri bu boşlukları Kaldır.  
  
 Dize işlemeleri hakkında daha fazla bilgi için bkz: [dizeleri](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Negatif sayılar.** Karakter tarafından tutulan unutmayın `String` işaretsizdir ve negatif değerleri temsil edemez. Her iki durumda da kullanmamalısınız `String` sayısal değerleri tutmak için.  
  
-   **Birlikte çalışabilirlik değerlendirmeleri.** .NET Framework yazılmaz bileşenleriyle arabirim örnek otomasyon ve COM nesneleri için dize karakterlerine farklı veri genişliği (8 bit) sahip diğer ortamlarda unutmayın. 8 bitlik karakterleri bir dize bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `Byte()`, bir dizi `Byte` öğeleri yerine `String` yeni Visual Basic kod.  
  
-   **Tür karakterleri.** Tanımlayıcı türü karakteri ekleme `$` herhangi bir tanımlayıcı zorlar `String` veri türü. `String` hiçbir değişmez değer türü karakteri var. Ancak, derleyici değişmez değerleri tırnak içine işler (`" "`) olarak `String`.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.String?displayProperty=nameWithType> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
