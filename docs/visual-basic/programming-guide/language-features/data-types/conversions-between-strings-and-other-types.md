---
title: "Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 71ece18d4ce33b7b637410110e825b389affcd67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)
Bir sayısal dönüştürebilirsiniz `Boolean`, veya tarih/saat değerine bir `String`. Ters yönde de dönüştürebilirsiniz — bir sayısal dize değerinden `Boolean`, veya `Date` — dize içeriği hedef veri türü geçerli bir değer yorumlanacak sağlanan. Desteklemiyorlarsa, bir çalışma zamanı hatası oluşur.  
  
 Tüm bu atamaları herhangi bir yönde dönüştürmelerde daraltma dönüşümleri. Tür Dönüşüm anahtar sözcükleri kullanması gereken (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, ve `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A> Ve <xref:Microsoft.VisualBasic.Conversion.Val%2A> işlevleri dizeler ve sayılar arasında dönüştürmeler üzerinde ek denetim sunar.  
  
 Bir sınıf veya yapı tanımladıysanız, tür dönüştürme işleçleri arasında tanımlayabilirsiniz `String` ve sınıf veya yapı türü. Daha fazla bilgi için bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Sayıların dizeleri dönüştürme  
 Kullanabileceğiniz `Format` yalnızca uygun rakam içerebilen biçimlendirilmiş bir dize için bir sayı dönüştürmek için çalışır ancak aynı zamanda bir para birimi oturum gibi semboller biçimlendirme (gibi `$`), binlik ayırıcı veya *basamak gruplandırma Simgeler* (gibi `,`) ve ondalık ayırıcı (gibi `.`). `Format`otomatik olarak göre uygun simgeleri kullanır **Bölgesel Seçenekler** Windows belirtilen ayarları **Denetim Masası**.  
  
 Unutmayın birleştirme (`&`) işleci dönüştürebilir sayıyı dizeye örtük olarak, aşağıdaki örnekte gösterildiği gibi.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Dizeleri sayılara dönüştürme  
 Kullanabileceğiniz `Val` açıkça bir dize sayıları sayıya dönüştürme işlevi. `Val`basamak, boşluk, sekme, satır besleme veya süresi dışında bir karakter bulduğu kadar dize okur. Dizileri "& O" ve "& H" sayı sistemini tabanı alter ve tarama sonlanır. Okuma, durduruluncaya kadar `Val` tüm uygun karakterleri sayısal bir değere dönüştürür. Örneğin, aşağıdaki ifade değerini verir `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Zaman [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sayısal bir değeri dizeye dönüştürür, kullandığı **Bölgesel Seçenekler** Windows belirtilen ayarları **Denetim Masası** binlerce yorumlamaya ayırıcı, ondalık ayırıcı, ve para birimi simgesi. Başka bir deyişle, bir dönüştürme altında bir ancak başka ayarlama başarılı olabilir. Örneğin, `"$14.20"` kabul edilebilir İngilizce (ABD) yerel ancak Fransızca tüm yerel ayarlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Genişletme ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Örtük ve açık dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [.NET Framework tabanlı Uluslararası uygulamalara giriş](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
