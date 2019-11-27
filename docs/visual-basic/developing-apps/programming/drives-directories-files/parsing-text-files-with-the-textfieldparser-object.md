---
title: TextFieldParser nesnesiyle metin dosyalarını ayrıştırma
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333853"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="91ba3-102">TextFieldParser nesnesiyle metin dosyalarını ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91ba3-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="91ba3-103">`TextFieldParser` nesnesi, günlük dosyaları veya eski veritabanı bilgileri gibi, metnin ayrılmış genişlikli sütunları olarak yapılandırılmış çok büyük bir dosyayı ayrıştırmanıza ve işleetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="91ba3-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="91ba3-104">Metin dosyalarını `TextFieldParser` ile ayrıştırmak, metin dosyası üzerinde yineleme yaparken benzerdir, ancak metin alanlarını ayıklamak için ayrıştırma yöntemi, sınırlandırılmış dizeleri simgeleştirmek için kullanılan dize işleme yöntemlerine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="91ba3-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="91ba3-105">Farklı metin dosyası türlerini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="91ba3-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="91ba3-106">Metin dosyalarında, virgül veya sekme alanı gibi bir karakterle ayrılmış çeşitli genişlik alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="91ba3-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="91ba3-107">Aşağıdaki örnekte olduğu gibi, sekmeyle ayrılmış bir metin dosyası tanımlamak için `SetDelimiters` yöntemini kullanan `TextFieldType` ve sınırlandırıcıyı tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="91ba3-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="91ba3-108">Diğer metin dosyaları, sabit olan alan genişliklerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="91ba3-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="91ba3-109">Bu gibi durumlarda, aşağıdaki örnekte olduğu gibi `TextFieldType` `FixedWidth` olarak tanımlamanız ve her bir alanın genişliklerini tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91ba3-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="91ba3-110">Bu örnek, metin sütunlarını tanımlamak için `SetFieldWidths` yöntemini kullanır: ilk sütun 5 karakter genişliğinde, ikincisi 10, üçüncü ise 11 ve dördüncü değişken genişliktedir.</span><span class="sxs-lookup"><span data-stu-id="91ba3-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="91ba3-111">Biçim tanımlandıktan sonra, her satırı sırayla işlemek için `ReadFields` yöntemini kullanarak dosyasında döngü yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ba3-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="91ba3-112">Bir alan belirtilen biçimle eşleşmezse, bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="91ba3-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="91ba3-113">Bu tür özel durumlar oluştuğunda, `ErrorLine` ve `ErrorLineNumber` özellikleri, metnin özel duruma ve satır numarasına neden olan metni tutar.</span><span class="sxs-lookup"><span data-stu-id="91ba3-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="91ba3-114">Birden çok biçimdeki dosyaları ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="91ba3-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="91ba3-115">`TextFieldParser` nesnesinin `PeekChars` yöntemi, okumadan önce her alanı denetlemek için kullanılabilir. böylece alanlar için birden çok biçim tanımlayabilir ve bunlara göre tepki verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ba3-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="91ba3-116">Daha fazla bilgi için bkz. [nasıl yapılır: birden çok biçimdeki metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="91ba3-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ba3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91ba3-117">See also</span></span>

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
