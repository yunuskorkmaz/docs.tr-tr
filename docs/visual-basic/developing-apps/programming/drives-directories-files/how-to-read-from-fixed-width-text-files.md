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
ms.openlocfilehash: b1581800c4e16e3bbbf43685508cee781efa6901
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634577"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="0671c-102">Nasıl yapılır: Visual Basic'te sabit genişlikli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="0671c-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="0671c-103">`TextFieldParser` Nesneyi kolayca ve verimli bir şekilde günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0671c-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="0671c-104">`TextFieldType` Özelliği ayrıştırılmış dosya sınırlandırılmış bir dosyanın veya bir sabit genişlikli metin alanlarının sahip olup olmadığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0671c-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="0671c-105">Bir sabit genişlikli metin dosyasında, alanın sonunda bir değişken genişliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="0671c-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="0671c-106">Alanın sonunda bir değişken genişliği olduğunu belirtmek için bir genişlik daha az veya eşit sıfır olması tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0671c-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="0671c-107">Sabit genişlikte metin dosyası ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="0671c-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="0671c-108">Yeni bir `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="0671c-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="0671c-109">Aşağıdaki kod oluşturur `TextFieldParser` adlı `Reader` ve dosyayı açar `test.log`.</span><span class="sxs-lookup"><span data-stu-id="0671c-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  <span data-ttu-id="0671c-110">Tanımlama `TextFieldType` özelliği olarak `FixedWidth`, genişliği tanımlama ve biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="0671c-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="0671c-111">Aşağıdaki kod, metin sütunlarını tanımlar; ilk 5 karakterini geniş, ikinci 10, üçüncü 11 ve dördüncü değişken genişliği.</span><span class="sxs-lookup"><span data-stu-id="0671c-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  <span data-ttu-id="0671c-112">Dosya alanları döngü.</span><span class="sxs-lookup"><span data-stu-id="0671c-112">Loop through the fields in the file.</span></span> <span data-ttu-id="0671c-113">Satırları bozuk, bir hata rapor ve ayrıştırma devam edin.</span><span class="sxs-lookup"><span data-stu-id="0671c-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  <span data-ttu-id="0671c-114">Kapat `While` ve `Using` ile engeller `End While` ve `End Using`.</span><span class="sxs-lookup"><span data-stu-id="0671c-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="0671c-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0671c-115">Example</span></span>  
 <span data-ttu-id="0671c-116">Bu örnekte dosyadan okur `test.log`.</span><span class="sxs-lookup"><span data-stu-id="0671c-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0671c-117">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="0671c-117">Robust programming</span></span>  
 <span data-ttu-id="0671c-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0671c-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="0671c-119">Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="0671c-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="0671c-120">Özel durum iletisi satırı belirtir. özel durum neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırda bulunan metin atanır.</span><span class="sxs-lookup"><span data-stu-id="0671c-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="0671c-121">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0671c-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="0671c-122">Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="0671c-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="0671c-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0671c-123">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="0671c-124">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0671c-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="0671c-125">Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0671c-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0671c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0671c-126">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="0671c-127">Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="0671c-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="0671c-128">Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="0671c-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="0671c-129">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="0671c-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="0671c-130">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="0671c-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="0671c-131">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="0671c-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)

