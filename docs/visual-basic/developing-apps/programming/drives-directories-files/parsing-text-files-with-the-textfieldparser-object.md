---
title: (Visual Basic) TextFieldParser nesnesiyle metin dosyalarını ayrıştırma
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 520121ba549532c5ce73810347025949eee5a077
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587312"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>(Visual Basic) TextFieldParser nesnesiyle metin dosyalarını ayrıştırma
`TextFieldParser` Ayrıştırmak için ve ayrılmış genişliği sütunları günlük dosyaları veya eski veritabanı bilgileri gibi bir metin olarak yapılandırılmış çok büyük bir dosya işlem nesnesi sağlar. Bir metin dosyası ile ayrıştırma `TextFieldParser` metin alanlarını ayıklamak için parse yöntemi sınırlandırılmış dizeleri simgeleştirilecek kullanılan dize işleme yöntemlerini benzer olsa da bir metin dosyası yineleme için benzer.  
  
## <a name="parsing-different-types-of-text-files"></a>Farklı türde metin dosyalarını ayrıştırma  
 Metin dosyaları, virgül veya sekme alanı gibi bir karakterle sınırlı çeşitli genişliğinin alanları olabilir. Tanımlamak `TextFieldType` ve sınırlayıcı kullanan aşağıdaki örnekteki gibi `SetDelimiters` yöntemi bir sekmeyle ayrılmış metin dosyası tanımlayın:  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 Diğer metin dosyaları giderilen genişlikleriyle olabilir. Böyle durumlarda, tanımlamanız gerekir. `TextFieldType` olarak `FixedWidth` ve aşağıdaki örnekteki gibi her bir alan genişlikleri tanımlayın. Bu örnekte `SetFieldWidths` metin sütunları tanımlamak için yöntemi: 5 karakter geniş ilk sütun olması, 10 saniyedir, üçüncü 11 olması ve değişken genişliğini dördüncü olduğu.  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 Biçimi tanımlandıktan sonra dosyayı aracılığıyla döngü kullanarak `ReadFields` her satırın sırayla işlemek için yöntem.  
  
 Bir alan belirtilen biçim eşleşmiyorsa bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durumu oluşur. Bu tür özel durumlar, `ErrorLine` ve `ErrorLineNumber` özellikleri tutmak özel durumu ve bu metnin satır numarası neden olan metin.  
  
## <a name="parsing-files-with-multiple-formats"></a>Birden çok biçimli dosyalarını ayrıştırma  
 `PeekChars` Yöntemi `TextFieldParser` nesnesi, her bir alan, alanlar için birden çok biçim tanımlamak ve uygun şekilde tepki olanak tanıyan okumadan önce denetlemek için kullanılabilir. Daha fazla bilgi için bkz: [nasıl yapılır: birden çok biçimleri ile metin dosyaları okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
