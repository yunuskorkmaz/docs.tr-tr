---
title: "Nasıl yapılır: Visual Basic'te virgülle ayrılmış metin dosyalarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: f241a8fcb971cfcd94cb32f0b3c0273552954349
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314210"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="f5cb1-102">Nasıl yapılır: Visual Basic'te virgülle ayrılmış metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="f5cb1-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="f5cb1-103">`TextFieldParser` Nesneyi kolayca ve verimli bir şekilde günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="f5cb1-104">`TextFieldType` Özelliği sınırlandırılmış bir dosyanın veya bir sabit genişlikli metin alanlarının olup olmadığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="f5cb1-105">Sınırlandırılmış bir metin dosyasını virgül ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="f5cb1-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="f5cb1-106">Yeni bir `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="f5cb1-107">Aşağıdaki kod oluşturur `TextFieldParser` adlı `MyReader` ve dosyayı açar `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="f5cb1-108">Tanımlama `TextField` türü ve ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="f5cb1-109">Aşağıdaki kod tanımlar `TextFieldType` özelliği olarak `Delimited` ve ayırıcı olarak ",".</span><span class="sxs-lookup"><span data-stu-id="f5cb1-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="f5cb1-110">Dosya alanları döngü.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-110">Loop through the fields in the file.</span></span> <span data-ttu-id="f5cb1-111">Tüm satırları bozuk, bir hata rapor ve ayrıştırma devam edin.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="f5cb1-112">Aşağıdaki kod, her bir alan sırayla görüntüleme ve hatalı biçimlendirilmiş herhangi bir alan raporlama dosya döngüde kalır.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="f5cb1-113">Kapat `While` ve `Using` ile engeller `End While` ve `End Using`.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="f5cb1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5cb1-114">Example</span></span>  
 <span data-ttu-id="f5cb1-115">Bu örnekte dosyadan okur `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f5cb1-116">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="f5cb1-116">Robust programming</span></span>  
 <span data-ttu-id="f5cb1-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f5cb1-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f5cb1-118">Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="f5cb1-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="f5cb1-119">Özel durum iletisi satırı belirtir. özel durum neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırda bulunan metin atanır.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="f5cb1-120">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f5cb1-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="f5cb1-121">Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="f5cb1-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="f5cb1-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="f5cb1-123">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f5cb1-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="f5cb1-124">Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="f5cb1-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cb1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5cb1-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="f5cb1-126">Nasıl yapılır: Sabit genişlikli metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="f5cb1-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="f5cb1-127">Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="f5cb1-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="f5cb1-128">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="f5cb1-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="f5cb1-129">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="f5cb1-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="f5cb1-130">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="f5cb1-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
