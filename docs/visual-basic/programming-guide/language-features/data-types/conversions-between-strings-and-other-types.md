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
ms.openlocfilehash: 1e42fca7800a76cab10fd60058e34d31ae8b8830
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821667"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)
Bir sayısal dönüştürebilirsiniz `Boolean`, veya tarih/saat değerine bir `String`. Ters yönde de dönüştürebilirsiniz: sayısal bir dize değerinden `Boolean`, veya `Date` — sağlanan dizenin içeriği hedef veri türünün geçerli bir değer olarak yorumlanabilir. Desteklemiyorlarsa, bir çalışma zamanı hatası oluşur.  
  
 Herhangi bir yönde tüm bu atamalar, dönüştürmeleri daraltma dönüştürmeleri. Tür Dönüşüm anahtar sözcükleri kullanmanız gerekir (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, ve `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A> Ve <xref:Microsoft.VisualBasic.Conversion.Val%2A> işlevlerini dizeler ve sayılar arasında dönüştürmeler üzerinde ek denetim verir.  
  
 Bir sınıf veya yapı tanımladıysanız, tür dönüştürme işleçleri arasında tanımlayabilirsiniz `String` ve sınıf veya yapı türü. Daha fazla bilgi için [nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Sayı dizeleri dönüştürme  
 Kullanabilirsiniz `Format` bir sayı değil yalnızca uygun rakamları içerebilir bir biçimlendirilmiş dize dönüştürme işlevini ancak aynı zamanda bir para birimi simgesi gibi simgeleri biçimlendirme (gibi `$`), binlik ayırıcıları veya *basamak gruplandırma semboller* (gibi `,`) ve ondalık ayırıcı (gibi `.`). `Format` şunlara göre uygun semboller otomatik olarak kullanan **Bölgesel Seçenekler** Windows içinde belirtilen ayarları **Denetim Masası**.  
  
 Unutmayın birleştirme (`&`) işleci dönüştürebilir bir sayıyı bir dizeye örtük olarak, aşağıdaki örnekte gösterildiği gibi.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Dizeleri sayılara dönüştürme  
 Kullanabileceğiniz `Val` açıkça bir dizesindeki basamak bir sayıya dönüştürmek için işlevi. `Val` Bu rakam, boşluk, sekme, satır besleme veya süresi dışında bir karakterle karşılaştığında kadar dize okur. Dizileri "&" ve "& H" sayı sistemini tabanı alter ve tarama sonlandırın. Okuma, durduruluncaya kadar `Val` uygun tüm karakterleri, sayısal bir değere dönüştürür. Örneğin, aşağıdaki ifade değerini verir `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic sayısal değer bir dize dönüştürür, kullandığı **Bölgesel Seçenekler** Windows içinde belirtilen ayarları **Denetim Masası** binlik yorumlamak için ayırıcısı, ondalık ayırıcı, ve para birimi simgesi. Başka bir deyişle, altında bir ayarı ancak başka bir dönüştürme başarısız olabilir. Örneğin, `"$14.20"` kabul edilebilir İngilizce (Amerika Birleşik Devletleri) yerel ayarında ancak Fransızca herhangi bir yerel ayar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Nasıl yapılır: Bir nesneyi Visual Basic'de başka bir türe dönüştürme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [.NET Framework Tabanlı Uluslararası Uygulamalara Giriş](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
