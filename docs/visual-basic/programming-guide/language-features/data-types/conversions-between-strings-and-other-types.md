---
title: Dizeler ve Diğer Türler Arasında Dönüştürmeler
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 823931f7d6beb8218e8b99d4a8d45716b7214304
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077156"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)

Bir sayısal, `Boolean` veya tarih/saat değerini bir olarak dönüştürebilirsiniz `String` . Ters yönde, bir dize değerinden sayısal, `Boolean` , veya `Date` — dize içeriği belirtilen hedef veri türünün geçerli bir değeri olarak yorumlanabilecek şekilde de dönüştürebilirsiniz. Bu durumda, bir çalışma zamanı hatası oluşur.  
  
 Her iki yönde de tüm bu atamaların dönüştürmeleri daraltma dönüştürmelerinde. Tür dönüştürme anahtar sözcüklerini ( `CBool` , `CByte` ,,,, `CDate` , `CDbl` , `CDec` `CInt` `CLng` `CSByte` , `CShort` , `CSng` , `CStr` ,,,, `CUInt` `CULng` `CUShort` ve `CType` ) kullanmanız gerekir. <xref:Microsoft.VisualBasic.Strings.Format%2A>Ve <xref:Microsoft.VisualBasic.Conversion.Val%2A> işlevleri, dizeler ve sayılar arasındaki dönüştürmeler üzerinde ek denetim sağlar.  
  
 Bir sınıf veya yapı tanımladıysanız, sınıf veya yapınızın türü dönüştürme işleçlerini tanımlayabilirsiniz `String` . Daha fazla bilgi için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Sayıları dizelere dönüştürme  

 `Format`Bir sayıyı biçimlendirilmiş bir dizeye dönüştürmek için işlevini kullanabilirsiniz. Bu, yalnızca uygun basamakları değil, bir para birimi işareti (örneğin `$` ), binlik ayırıcıları veya *Basamak gruplama sembolleri* (gibi) `,` ve bir ondalık ayırıcısı (gibi) biçimlendirme gibi simgeleri de içerebilir `.` . `Format`, Windows **Denetim Masası**'Nda belirtilen **Bölgesel Seçenekler** ayarlarına göre otomatik olarak uygun sembolleri kullanır.  
  
 `&`Aşağıdaki örnekte gösterildiği gibi, birleştirme () işlecinin bir sayıyı örtük olarak bir dizeye dönüştürebileceğini unutmayın.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Dizelerin sayılara dönüştürülmesi  

 `Val`Bir dizedeki rakamları bir sayıya açıkça dönüştürmek için işlevini kullanabilirsiniz. `Val` bir rakam, boşluk, sekme, satır akışı veya nokta dışında bir karakterle karşılaşana kadar dizeyi okur. "&O" ve "&H" dizileri, sayı sisteminin temelini değiştirir ve taramayı sonlandırır. Okumayı durdurmadan, `Val` tüm uygun karakterleri sayısal bir değere dönüştürür. Örneğin, aşağıdaki ifade değeri döndürür `141.825` .  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic bir dizeyi sayısal bir değere dönüştürdüğünde, binlik ayırıcısını, ondalık ayırıcıyı ve para birimi simgesini yorumlamak için Windows **Denetim Masası** 'Nda belirtilen **Bölgesel Seçenekler** ayarlarını kullanır. Bu, dönüştürmenin bir ayar altında başarılı olabileceği ancak başka bir şekilde başarısız olabileceği anlamına gelir. Örneğin, `"$14.20"` İngilizce (Birleşik Devletler) yerel ayarında kabul edilebilir, ancak herhangi bir Fransızca yerel ayarda yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Genişletme ve Daraltma Dönüşümleri](widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](implicit-and-explicit-conversions.md)
- [Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme](how-to-convert-an-object-to-another-type.md)
- [Dizi Dönüştürmeler](array-conversions.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../language-reference/functions/type-conversion-functions.md)
- [Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirin](/visualstudio/ide/globalizing-and-localizing-applications)
