---
title: "Dize Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.String
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90f126a5cca36969617446e81a8d13434e39df75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="string-data-type-visual-basic"></a>Dize Veri Türü (Visual Basic)
İmzasız 16-bit (2-bayt) kod noktaları dizilerini bu aralık 0 ile 65535 arasında bir değer olarak tutar. Her *kod noktası*, veya karakter kodu, tek bir Unicode karakteri temsil eder. Bir dize 0'dan yaklaşık iki milyardan içerebilir (2 ^ 31) Unicode karakterler.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `String` birden çok karakter dizisi yönetim yükü olmadan tutmak için veri türü `Char()`, bir dizi `Char` öğeleri.  
  
 Varsayılan değer olan `String` olan `Nothing` (bir null başvuru). Bu boş dize olarak aynı değildir (değer `""`).  
  
## <a name="unicode-characters"></a>Unicode karakterler  
 Unicode ilk 128 kod noktası (0 – 127) harf ve sembol Standart ABD klavyedeki karşılık gelir. Bu ilk 128 kod noktaları ASCII karakter kümesi tanımlar aynıdır. İkinci 128 kod noktaları (128-255) Latin tabanlı alfabedeki harfleri, vurgular, para birimi simgeleri ve kesirler gibi özel karakterleri temsil eder. Unicode çok çeşitli sembolleri için kalan kod noktaları (256-65535) kullanır. Bu, dünya çapında metinsel karakter, Vurgu ve matematiksel ve teknik simgeleri içerir.  
  
 Yöntemleri gibi kullanabilir <xref:System.Char.IsDigit%2A> ve <xref:System.Char.IsPunctuation%2A> tek tek bir karakter üzerinde bir `String` kendi Unicode sınıflandırmasını belirlemek için değişkeni.  
  
## <a name="format-requirements"></a>Biçim gereksinimleri  
 İçine almalısınız bir `String` değişmez değer tırnak işaretleri içindeki (`" "`). Bir dizedeki karakter olarak bir tırnak işareti içermelidir, iki bitişik tırnak işareti kullanın (`""`). Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Tırnak işareti dizeyi temsil eden bitişik tırnak işaretleri başlayıp bitmelidir tırnak işaretleri bağımsız olduğuna dikkat edin `String` değişmez.  
  
## <a name="string-manipulations"></a>Dize işlemeleri  
 Bir dizeyi atadıktan sonra bir `String` değişkeni, bu bir dizedir *değişmez*, anlamına gelir, uzunluk veya içeriği değiştiremezsiniz. Herhangi bir şekilde bir dize değiştirdiğinizde, Visual Basic yeni bir dize oluşturur ve önceki bir kenara bırakır. `String` Değişkeni sonra yeni dizeye işaret eder.  
  
 İçeriğini işleyebileceğiniz bir `String` dize işlevleri, çeşitli kullanarak değişken. Aşağıdaki örnek gösterilmektedir <xref:Microsoft.VisualBasic.Strings.Left%2A> işlevi  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Başka bir bileşen tarafından oluşturulan bir dize başında veya sonunda boşluk ile doldurulan. Bu tür bir dize almaya devam ederseniz, kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, ve <xref:Microsoft.VisualBasic.Strings.RTrim%2A> işlevleri bu boşlukları Kaldır.  
  
 Dize işlemeleri hakkında daha fazla bilgi için bkz: [dizeleri](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Negatif sayılar.** Karakterleri tarafından tutulan unutmayın `String` imzasız ve negatif değerler temsil edilemez. Her iki durumda da kullanılamaz `String` sayısal değerleri tutmak için.  
  
-   **Birlikte çalışma hakkında dikkat edilecek noktalar** .NET Framework için yazılmaz bileşenleriyle arabirim örnek otomasyon veya COM nesneleri için karakter dize farklı veri genişliği (8 bit) sahip diğer ortamlarda unutmayın. Bu tür bir bileşen için 8 bit karakter dizesi bağımsız değişkeni geçirilirse olarak bildirme `Byte()`, bir dizi `Byte` öğeleri yerine `String` yeni Visual Basic kodunuzda.  
  
-   **Karakterleri yazın.** Tanımlayıcı türü karakteri ekleme `$` herhangi bir tanımlayıcı zorlar `String` veri türü. `String`değişmez değer türü karakteri var. Ancak, tırnak işaretleri içine değişmez değerleri derleyici değerlendirir (`" "`) olarak `String`.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.String?displayProperty=nameWithType> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String?displayProperty=nameWithType>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Char veri türü](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Nasıl yapılır: imzalanmamış türler isteyen bir Windows işlevi çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
