---
title: Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: e1530c1772808249546b453294fc848c31c1e581
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582931"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)
Bir sayısal, `Boolean` veya tarih/saat değerini bir `String` dönüştürebilirsiniz. Ayrıca, dizenin içeriği hedef veri türünün geçerli bir değeri olarak yorumlanabileceğinden, bir dize değerinden sayısal, `Boolean` veya `Date` ters yönde dönüştürebilirsiniz. Bu durumda, bir çalışma zamanı hatası oluşur.  
  
 Her iki yönde de tüm bu atamaların dönüştürmeleri daraltma dönüştürmelerinde. Tür dönüştürme anahtar sözcüklerini (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, 0, 1, 2 , 3 ve 4). @No__t_0 ve <xref:Microsoft.VisualBasic.Conversion.Val%2A> işlevleri, dizeler ve sayılar arasındaki dönüştürmeler üzerinde ek denetim sağlar.  
  
 Bir sınıf veya yapı tanımladıysanız, `String` dönüştürme işleçlerini ve sınıf veya yapınızın türünü tanımlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Sayıları dizelere dönüştürme  
 Bir sayıyı biçimlendirilmiş bir dizeye dönüştürmek için `Format` işlevini kullanabilirsiniz. Bu, yalnızca uygun basamakları değil, ayrıca para birimi işareti (örneğin `$`), binlik ayırıcıları veya *Basamak gruplama sembolleri* (örneğin, @no gibi) biçimlendirme simgeleri içerebilir __t_3) ve bir ondalık ayırıcı (örneğin `.`). `Format`, Windows **Denetim Masası**'Nda belirtilen **Bölgesel Seçenekler** ayarlarına göre otomatik olarak uygun sembolleri kullanır.  
  
 Aşağıdaki örnekte gösterildiği gibi, birleştirme (`&`) işlecinin bir sayıyı örtük olarak bir dizeye dönüştürebileceğini unutmayın.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Dizelerin sayılara dönüştürülmesi  
 Bir dizedeki rakamları bir sayıya açıkça dönüştürmek için `Val` işlevini kullanabilirsiniz. `Val` sayı, boşluk, sekme, satır besleme veya nokta dışında bir karakterle karşılaşana kadar dizeyi okur. "& O" ve "& H" dizileri, sayı sisteminin temelini değiştirir ve taramayı sonlandırır. Okumayı durdurmadan `Val`, tüm uygun karakterleri sayısal bir değere dönüştürür. Örneğin, aşağıdaki ifade `141.825` değerini döndürür.  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic bir dizeyi sayısal bir değere dönüştürdüğünde, binlik ayırıcısını, ondalık ayırıcıyı ve para birimi simgesini yorumlamak için Windows **Denetim Masası** 'Nda belirtilen **Bölgesel Seçenekler** ayarlarını kullanır. Bu, dönüştürmenin bir ayar altında başarılı olabileceği ancak başka bir şekilde başarısız olabileceği anlamına gelir. Örneğin, `"$14.20"` Ingilizce (Birleşik Devletler) yerel ayarında kabul edilebilir, ancak herhangi bir Fransızca yerel ayarında kabul edilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Nasıl yapılır: Visual Basic bir nesneyi başka bir türe dönüştürme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [.NET Framework Tabanlı Uluslararası Uygulamalara Giriş](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
