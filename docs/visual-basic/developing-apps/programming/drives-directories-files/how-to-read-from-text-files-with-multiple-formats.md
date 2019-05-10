---
title: "Nasıl yapılır: Visual Basic'te birden çok biçimli metin dosyalarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: 9fa484f0a74d900bd6f0365f2ce71fd32e1422db
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623186"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="654da-102">Nasıl yapılır: Visual Basic'te birden çok biçimli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="654da-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="654da-103"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesneyi kolayca ve verimli bir şekilde günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="654da-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="654da-104">Birden çok biçimli bir dosya kullanarak işleyebilir `PeekChars` dosyasını ayrıştırma gibi her satırın biçimini belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="654da-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="654da-105">Birden çok biçimli metin dosyası ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="654da-105">To parse a text file with multiple formats</span></span>  
  
1. <span data-ttu-id="654da-106">Projenize testfile.txt adında bir metin dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="654da-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="654da-107">Aşağıdaki içeriği metin dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="654da-107">Add the following content to the text file.</span></span>  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2. <span data-ttu-id="654da-108">Beklenen biçim ve bir hata bildirildiğinde kullanılan biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="654da-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="654da-109">Her dizi son girişi -1, bu nedenle son alan değişken genişliği olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="654da-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="654da-110">Dizideki son girişin 0'a eşit veya daha az olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="654da-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]  
  
3. <span data-ttu-id="654da-111">Yeni bir <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> genişlik ve biçimini tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="654da-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]  
  
4. <span data-ttu-id="654da-112">Satırları okuma önce biçimi için test etme, döngü.</span><span class="sxs-lookup"><span data-stu-id="654da-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]  
  
5. <span data-ttu-id="654da-113">Konsola yazma hatası.</span><span class="sxs-lookup"><span data-stu-id="654da-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="654da-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="654da-114">Example</span></span>  
 <span data-ttu-id="654da-115">Dosyadan okur tam bir örnek aşağıdadır `testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="654da-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="654da-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="654da-116">Robust Programming</span></span>  
 <span data-ttu-id="654da-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="654da-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="654da-118">Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="654da-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="654da-119">Özel durum iletisi satırı belirtir. özel durum neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırda bulunan metin atanır.</span><span class="sxs-lookup"><span data-stu-id="654da-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="654da-120">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="654da-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="654da-121">Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="654da-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="654da-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="654da-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="654da-123">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="654da-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="654da-124">Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="654da-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654da-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="654da-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="654da-126">Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="654da-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="654da-127">Nasıl yapılır: Sabit genişlikli metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="654da-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="654da-128">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="654da-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
