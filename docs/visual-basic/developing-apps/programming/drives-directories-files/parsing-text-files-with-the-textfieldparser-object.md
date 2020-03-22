---
title: Metin dosyalarını TextFieldParser nesnesiyle ayrıştırma
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
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Metin dosyalarını TextFieldParser nesnesi ile ayrıştırma (Visual Basic)

Nesne, `TextFieldParser` günlük dosyaları veya eski veritabanı bilgileri gibi sınırlı genişlikte metin sütunları olarak yapılandırılan çok büyük dosyayı ayrıştırmanızı ve işlemenizi sağlar. Metin dosyasını ayrıştırmak `TextFieldParser` metin dosyası üzerinde yineleme yle benzerken, metin alanlarını ayıklamak için ayrıştırma yöntemi, sınırlandırılmış dizeleri belirtebilmek için kullanılan dize işleme yöntemlerine benzer.  
  
## <a name="parsing-different-types-of-text-files"></a>Farklı metin dosyalarını ayrıştma  

 Metin dosyaları, virgül veya sekme alanı gibi bir karakterle sınırlandırılmış çeşitli genişlikteki alanlara sahip olabilir. Aşağıdaki `TextFieldType` örnekte olduğu gibi, sekme sınırlandırılmış `SetDelimiters` bir metin dosyasını tanımlamak için yöntemi kullanan sınırlayıcıyı tanımlayın:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Diğer metin dosyaları sabit alan genişlikleri olabilir. Bu gibi durumlarda, aşağıdaki `TextFieldType` örnekte olduğu gibi, her alanın genişlikleri olarak `FixedWidth` tanımlamak ve tanımlamak gerekir. Bu örnek, `SetFieldWidths` metin sütunlarını tanımlamak için yöntemi kullanır: ilk sütun 5 karakter genişliğinde, ikinci 10, üçüncü 11 ve dördüncü değişken genişliği.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Biçim tanımlandıktan sonra, her satırı sırayla `ReadFields` işlemek için yöntemi kullanarak dosya yı kullanabilirsiniz.  
  
 Bir alan belirtilen biçimle eşleşmiyorsa, bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durum atılır. Bu tür özel durumlar `ErrorLine` atıldığında, özel durum ve bu metnin satır numarasıneden metin ve `ErrorLineNumber` özellikleri tutun.  
  
## <a name="parsing-files-with-multiple-formats"></a>Dosyaları birden çok biçimle ayrışdırma  

 `TextFieldParser` Nesnenin `PeekChars` yöntemi, okumadan önce her alanı denetlemek için kullanılabilir, böylece alanlar için birden çok biçim tanımlamak ve buna göre tepki vermek. Daha fazla bilgi [için bkz: Birden Çok Biçimli Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
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
