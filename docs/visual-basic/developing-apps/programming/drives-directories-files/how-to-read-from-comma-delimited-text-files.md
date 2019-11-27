---
title: 'Nasıl yapılır: virgülle ayrılmış metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9b93893e2221b156b65ce8e945089269ea28c989
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335071"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="6a401-102">Nasıl yapılır: Visual Basic içinde virgülle ayrılmış metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="6a401-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="6a401-103">`TextFieldParser` nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a401-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="6a401-104">`TextFieldType` özelliği, ayrılmış bir dosya mı yoksa sabit genişlikte metin alanları mı olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a401-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="6a401-105">Virgülle ayrılmış bir metin dosyasını ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6a401-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="6a401-106">Yeni bir `TextFieldParser`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6a401-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="6a401-107">Aşağıdaki kod, `MyReader` adlı `TextFieldParser` oluşturur ve dosyayı `test.txt`açar.</span><span class="sxs-lookup"><span data-stu-id="6a401-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="6a401-108">`TextField` türünü ve sınırlandırıcıyı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6a401-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="6a401-109">Aşağıdaki kod, `Delimited` olarak `TextFieldType` özelliğini ve sınırlandırıcıyı "," olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a401-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="6a401-110">Dosyadaki alanlar arasında döngü gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="6a401-110">Loop through the fields in the file.</span></span> <span data-ttu-id="6a401-111">Herhangi bir satır bozuksa bir hata bildirin ve ayrıştırmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="6a401-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="6a401-112">Aşağıdaki kod, dosyasında her bir alanı görüntüleyerek ve yanlış biçimlendirilmiş tüm alanları bildiren bir dosya üzerinden döngü başlatır.</span><span class="sxs-lookup"><span data-stu-id="6a401-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="6a401-113">`End While` ve `End Using``While` ve `Using` blokları kapatın.</span><span class="sxs-lookup"><span data-stu-id="6a401-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="6a401-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a401-114">Example</span></span>  

 <span data-ttu-id="6a401-115">Bu örnek `test.txt`dosyadan okur.</span><span class="sxs-lookup"><span data-stu-id="6a401-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6a401-116">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="6a401-116">Robust programming</span></span>  

 <span data-ttu-id="6a401-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="6a401-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6a401-118">Satır belirtilen biçim (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>) kullanılarak ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="6a401-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="6a401-119">Özel durum iletisi, özel duruma neden olan satırı belirtir, <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliğine satırda içerilen metin atanır.</span><span class="sxs-lookup"><span data-stu-id="6a401-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="6a401-120">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="6a401-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="6a401-121">Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu.</span><span class="sxs-lookup"><span data-stu-id="6a401-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="6a401-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="6a401-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="6a401-123">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="6a401-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="6a401-124">Kullanıcı, dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="6a401-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a401-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a401-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="6a401-126">Nasıl Yapılır: Sabit Genişlikli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="6a401-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="6a401-127">Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="6a401-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="6a401-128">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="6a401-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="6a401-129">İzlenecek yol: Visual Basic dosya ve dizinleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6a401-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="6a401-130">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="6a401-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
