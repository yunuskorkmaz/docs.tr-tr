---
title: "Char Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16ff547fccbf4481d31ca79537962cc7090fc9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="char-data-type-visual-basic"></a>Char Veri Türü (Visual Basic)
Değer 0 ile 65535 arasında değişen ayrı tutma imzasız 16-bit (2-bayt) kod noktaları. Her *kod noktası*, veya karakter kodu, tek bir Unicode karakteri temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Char` veri türü yalnızca tek bir tutmak gerektiğinde karakter ve yükü gerekmez `String`. Bazı durumlarda kullandığınız `Char()`, bir dizi `Char` birden çok karakter tutmak için öğeleri.  
  
 Varsayılan değer olan `Char` kod noktası 0 ile karakterdir.  
  
## <a name="unicode-characters"></a>Unicode karakterler  
 Unicode ilk 128 kod noktası (0 – 127) harf ve sembol Standart ABD klavyedeki karşılık gelir. Bu ilk 128 kod noktaları ASCII karakter kümesi tanımlar aynıdır. İkinci 128 kod noktaları (128-255) Latin tabanlı alfabedeki harfleri, vurgular, para birimi simgeleri ve kesirler gibi özel karakterleri temsil eder. Unicode için simgeler, dünya çapında metinsel karakter, Vurgu ve matematiksel ve teknik simgeleri de dahil olmak üzere çok çeşitli kalan kod noktaları (256-65535) kullanır.  
  
 Yöntemleri gibi kullanabilirsiniz <xref:System.Char.IsDigit%2A> ve <xref:System.Char.IsPunctuation%2A> üzerinde bir `Char` kendi Unicode sınıflandırmasını belirlemek için değişkeni.  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  
 Visual Basic değil Dönüştür doğrudan arasında `Char` ve sayısal türler. Kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Asc%2A> veya <xref:Microsoft.VisualBasic.Strings.AscW%2A> dönüştürmek için işlevi bir `Char` değeri bir `Integer` kod noktası temsil eden. Kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Chr%2A> veya <xref:Microsoft.VisualBasic.Strings.ChrW%2A> dönüştürmek için işlevi bir `Integer` değeri bir `Char` Bu kod noktası vardır.  
  
 Tür denetleme geçiş yaparsanız ([Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)) olduğundan, gerekir eklediğiniz değişmez değer türü karakteri olarak tanımlamak için değişmez değer tek karakterli bir dize için `Char` veri türü. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
-   **Negatif sayılar.** `Char`İmzasız bir tür olduğundan ve negatif bir değer temsil edilemez. Her iki durumda da kullanılamaz `Char` sayısal değerleri tutmak için.  
  
-   **Birlikte çalışma hakkında dikkat edilecek noktalar** .NET Framework için yazılmaz bileşenleriyle arabirim örnek otomasyon veya COM nesneleri için karakter türleri (8 bit) farklı veri genişliği sahip diğer ortamlarda unutmayın. Bu tür bir bileşen için 8 bit bağımsız değişken geçirirseniz, olarak bildirme `Byte` yerine `Char` yeni Visual Basic kodunuzda.  
  
-   **Genişletme.** `Char` Veri türü widens için `String`. Bu dönüştürebilirsiniz anlamına gelir `Char` için `String` ve değil karşılaşır bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ekleme `C` tek karakterli bir dize sabit değeri için zorlar `Char` veri türü. `Char`hiçbir tanımlayıcı türü karakteri var.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Char?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Dize veri türü](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Nasıl yapılır: imzalanmamış türler isteyen bir Windows işlevi çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
