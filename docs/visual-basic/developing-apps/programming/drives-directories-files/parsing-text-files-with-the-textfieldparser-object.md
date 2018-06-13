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
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="68517-102">(Visual Basic) TextFieldParser nesnesiyle metin dosyalarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="68517-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>
<span data-ttu-id="68517-103">`TextFieldParser` Ayrıştırmak için ve ayrılmış genişliği sütunları günlük dosyaları veya eski veritabanı bilgileri gibi bir metin olarak yapılandırılmış çok büyük bir dosya işlem nesnesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="68517-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="68517-104">Bir metin dosyası ile ayrıştırma `TextFieldParser` metin alanlarını ayıklamak için parse yöntemi sınırlandırılmış dizeleri simgeleştirilecek kullanılan dize işleme yöntemlerini benzer olsa da bir metin dosyası yineleme için benzer.</span><span class="sxs-lookup"><span data-stu-id="68517-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="68517-105">Farklı türde metin dosyalarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="68517-105">Parsing different types of text files</span></span>  
 <span data-ttu-id="68517-106">Metin dosyaları, virgül veya sekme alanı gibi bir karakterle sınırlı çeşitli genişliğinin alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="68517-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="68517-107">Tanımlamak `TextFieldType` ve sınırlayıcı kullanan aşağıdaki örnekteki gibi `SetDelimiters` yöntemi bir sekmeyle ayrılmış metin dosyası tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="68517-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 <span data-ttu-id="68517-108">Diğer metin dosyaları giderilen genişlikleriyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="68517-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="68517-109">Böyle durumlarda, tanımlamanız gerekir. `TextFieldType` olarak `FixedWidth` ve aşağıdaki örnekteki gibi her bir alan genişlikleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="68517-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="68517-110">Bu örnekte `SetFieldWidths` metin sütunları tanımlamak için yöntemi: 5 karakter geniş ilk sütun olması, 10 saniyedir, üçüncü 11 olması ve değişken genişliğini dördüncü olduğu.</span><span class="sxs-lookup"><span data-stu-id="68517-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 <span data-ttu-id="68517-111">Biçimi tanımlandıktan sonra dosyayı aracılığıyla döngü kullanarak `ReadFields` her satırın sırayla işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="68517-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="68517-112">Bir alan belirtilen biçim eşleşmiyorsa bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="68517-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="68517-113">Bu tür özel durumlar, `ErrorLine` ve `ErrorLineNumber` özellikleri tutmak özel durumu ve bu metnin satır numarası neden olan metin.</span><span class="sxs-lookup"><span data-stu-id="68517-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="68517-114">Birden çok biçimli dosyalarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="68517-114">Parsing files with multiple formats</span></span>  
 <span data-ttu-id="68517-115">`PeekChars` Yöntemi `TextFieldParser` nesnesi, her bir alan, alanlar için birden çok biçim tanımlamak ve uygun şekilde tepki olanak tanıyan okumadan önce denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68517-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="68517-116">Daha fazla bilgi için bkz: [nasıl yapılır: birden çok biçimleri ile metin dosyaları okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="68517-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68517-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68517-117">See also</span></span>  
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
