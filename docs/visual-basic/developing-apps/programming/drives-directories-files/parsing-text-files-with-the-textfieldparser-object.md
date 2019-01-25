---
title: (Visual Basic) TextFieldParser nesnesiyle metin dosyalarını ayrıştırma
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 09821e9b1985913b7433b070ae19c4818265926e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585408"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>(Visual Basic) TextFieldParser nesnesiyle metin dosyalarını ayrıştırma
`TextFieldParser` Ayrıştırmak için ve günlük dosyaları veya eski bir veritabanı bilgileri gibi bir metin ayrılmış genişlikte sütun olarak yapılandırılmış çok büyük bir dosya işlem nesnesi sağlar. Bir metin dosyası ayrıştırma `TextFieldParser` parse metodunu metin alanlarını ayıklamak için kullanılan ayrılmış dizeleri simgeleştirilecek dize işleme yöntemlerini benzer olmakla birlikte, bir metin dosyası içinde yineleme için benzer.  
  
## <a name="parsing-different-types-of-text-files"></a>Farklı türde metin dosyalarını ayrıştırma  
 Metin dosyaları, virgül veya bir sekme alanı gibi karakteriyle ayrılmış çeşitli genişliğinin alanları olabilir. Tanımlama `TextFieldType` ve kullanır aşağıdaki örnekte olduğu gibi bir sınırlayıcı `SetDelimiters` yöntemi, bir sekmeyle ayrılmış metin dosyası tanımlamak için:  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 Diğer metin dosyaları sabit alan genişlikleri olabilir. Böyle durumlarda tanımlamanız gerekir. `TextFieldType` olarak `FixedWidth` ve aşağıdaki örnekte olduğu gibi her bir alanın genişlikleri tanımlayın. Bu örnekte `SetFieldWidths` metin sütunları tanımlamak için yöntem: ilk sütun 5 karakter geniş değilse, 10 saniyedir, 11'in altında üçüncü ve dördüncü değişken genişliğidir.  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 Biçim tanımlandıktan sonra dosyası aracılığıyla döngü kullanarak `ReadFields` sırayla her satırı işlemek için yöntemi.  
  
 Bir alan belirtilen biçim eşleşmiyorsa bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durumu oluşturulur. Bu tür özel durumlar oluşturulduğunda `ErrorLine` ve `ErrorLineNumber` özellikleri tutmak özel durum ve satır numarası metnin neden olan metin.  
  
## <a name="parsing-files-with-multiple-formats"></a>Birden çok biçimli dosyalarını ayrıştırma  
 `PeekChars` Yöntemi `TextFieldParser` nesnesi, her bir alan, böylece alanları için birden çok biçimde tanımlamak ve uygun şekilde tepki okumadan önce denetlemek için kullanılabilir. Daha fazla bilgi için [nasıl yapılır: Birden çok biçimli metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
