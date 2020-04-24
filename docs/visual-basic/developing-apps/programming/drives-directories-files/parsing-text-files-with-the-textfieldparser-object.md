---
title: TextFieldParser nesnesiyle metin dosyalarını ayrıştırma
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333853"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>TextFieldParser nesnesiyle metin dosyalarını ayrıştırma (Visual Basic)

`TextFieldParser` Nesnesi, günlük dosyaları veya eski veritabanı bilgileri gibi, metnin ayrılmış genişlik sütunları olarak yapılandırılmış çok büyük bir dosyayı ayrıştırmanıza ve işleetmenize olanak tanır. Bir metin dosyasının `TextFieldParser` ayrıştırılmasında metin dosyası üzerinde yineleme yapmak benzer, ancak metin alanlarını ayıklamak için ayrıştırma yöntemi, sınırlandırılmış dizeleri simgeleştirmek için kullanılan dize işleme yöntemlerine benzerdir.  
  
## <a name="parsing-different-types-of-text-files"></a>Farklı metin dosyası türlerini ayrıştırma  

 Metin dosyalarında, virgül veya sekme alanı gibi bir karakterle ayrılmış çeşitli genişlik alanları olabilir. Aşağıdaki `TextFieldType` örnekte olduğu gibi, sekmeyle ayrılmış bir metin dosyası tanımlamak için `SetDelimiters` yöntemini kullanan sınırlayıcısı tanımlayın:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Diğer metin dosyaları, sabit olan alan genişliklerine sahip olabilir. Bu gibi durumlarda, aşağıdaki örnekte olduğu gibi, `TextFieldType` her `FixedWidth` bir alanın genişliğini tanımlamanız ve tanımlamanız gerekir. Bu örnek, `SetFieldWidths` metin sütunlarını tanımlamak için yöntemini kullanır: ilk sütun 5 karakter genişliğinde, ikincisi 10, üçüncüsü 11 ve dördüncü değişken genişliktir.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Biçim tanımlandıktan sonra, her satırı sırayla işlemek için `ReadFields` yöntemini kullanarak dosyasında döngü yapabilirsiniz.  
  
 Bir alan belirtilen biçimle eşleşmezse, bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durum oluşturulur. Bu tür özel durumlar oluştuğunda `ErrorLine` ve `ErrorLineNumber` özellikleri, özel duruma ve bu metnin satır numarasına neden olan metni tutar.  
  
## <a name="parsing-files-with-multiple-formats"></a>Birden çok biçimdeki dosyaları ayrıştırma  

 `TextFieldParser` Nesne `PeekChars` yöntemi, okumadan önce her bir alanı denetlemek için kullanılabilir ve alanlar için birden çok biçim tanımlamanızı ve buna uygun şekilde tepki vermesini sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: birden çok biçimdeki metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
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
