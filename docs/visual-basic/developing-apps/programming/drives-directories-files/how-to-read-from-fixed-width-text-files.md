---
title: "Nasıl yapılır: Visual Basic'te sabit genişlikli metin dosyalarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 4d6019bd9f39a6ae8db4b8c580db4c5ec9d4d4b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816219"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="af036-102">Nasıl yapılır: Visual Basic'te sabit genişlikli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="af036-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="af036-103">`TextFieldParser` Nesneyi kolayca ve verimli bir şekilde günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="af036-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="af036-104">`TextFieldType` Özelliği ayrıştırılmış dosya sınırlandırılmış bir dosyanın veya bir sabit genişlikli metin alanlarının sahip olup olmadığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af036-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="af036-105">Bir sabit genişlikli metin dosyasında, alanın sonunda bir değişken genişliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="af036-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="af036-106">Alanın sonunda bir değişken genişliği olduğunu belirtmek için bir genişlik daha az veya eşit sıfır olması tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="af036-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="af036-107">Sabit genişlikte metin dosyası ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="af036-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="af036-108">Yeni bir `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="af036-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="af036-109">Aşağıdaki kod oluşturur `TextFieldParser` adlı `Reader` ve dosyayı açar `test.log`.</span><span class="sxs-lookup"><span data-stu-id="af036-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2.  <span data-ttu-id="af036-110">Tanımlama `TextFieldType` özelliği olarak `FixedWidth`, genişliği tanımlama ve biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="af036-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="af036-111">Aşağıdaki kod, metin sütunlarını tanımlar; ilk 5 karakterini geniş, ikinci 10, üçüncü 11 ve dördüncü değişken genişliği.</span><span class="sxs-lookup"><span data-stu-id="af036-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3.  <span data-ttu-id="af036-112">Dosya alanları döngü.</span><span class="sxs-lookup"><span data-stu-id="af036-112">Loop through the fields in the file.</span></span> <span data-ttu-id="af036-113">Satırları bozuk, bir hata rapor ve ayrıştırma devam edin.</span><span class="sxs-lookup"><span data-stu-id="af036-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4.  <span data-ttu-id="af036-114">Kapat `While` ve `Using` ile engeller `End While` ve `End Using`.</span><span class="sxs-lookup"><span data-stu-id="af036-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="af036-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="af036-115">Example</span></span>  
 <span data-ttu-id="af036-116">Bu örnekte dosyadan okur `test.log`.</span><span class="sxs-lookup"><span data-stu-id="af036-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="af036-117">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="af036-117">Robust programming</span></span>  
 <span data-ttu-id="af036-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="af036-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="af036-119">Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="af036-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="af036-120">Özel durum iletisi satırı belirtir. özel durum neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırda bulunan metin atanır.</span><span class="sxs-lookup"><span data-stu-id="af036-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="af036-121">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="af036-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="af036-122">Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="af036-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="af036-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="af036-123">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="af036-124">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="af036-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="af036-125">Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="af036-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af036-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af036-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="af036-127">Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="af036-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="af036-128">Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="af036-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="af036-129">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="af036-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="af036-130">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="af036-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="af036-131">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="af036-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
