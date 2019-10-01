---
title: "Nasıl Yapılır: Visual Basic'te Birden Çok Biçimli Metin Dosyalarını Okuma"
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
ms.openlocfilehash: eae60b2fc72ee8b8653d3a0517eeaaf8012e0372
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696746"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="5eac8-102">Nasıl Yapılır: Visual Basic'te Birden Çok Biçimli Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="5eac8-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="5eac8-103">@No__t-0 nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5eac8-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="5eac8-104">Dosya aracılığıyla ayrıştırdığınızda her satırın biçimini belirleyebilmek için `PeekChars` yöntemini kullanarak birden çok biçimdeki bir dosyayı işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eac8-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="5eac8-105">Birden çok biçimdeki bir metin dosyasını ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5eac8-105">To parse a text file with multiple formats</span></span>  
  
1. <span data-ttu-id="5eac8-106">Projenize Testfile. txt adlı bir metin dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5eac8-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="5eac8-107">Aşağıdaki içeriği metin dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5eac8-107">Add the following content to the text file.</span></span>  
  
    ```text  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2. <span data-ttu-id="5eac8-108">Beklenen biçimi ve bir hata bildirildiğinde kullanılan biçimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5eac8-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="5eac8-109">Her dizideki son giriş-1 ' dir, bu nedenle son alan, değişken genişliği olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5eac8-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="5eac8-110">Bu, dizideki son giriş 0 ' dan küçük veya buna eşit olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5eac8-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]  
  
3. <span data-ttu-id="5eac8-111">Genişliği ve biçimi tanımlayarak yeni bir <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5eac8-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]  
  
4. <span data-ttu-id="5eac8-112">Okumadan önce biçim için test eden satırlarda döngü yapın.</span><span class="sxs-lookup"><span data-stu-id="5eac8-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]  
  
5. <span data-ttu-id="5eac8-113">Konsola hataları yazın.</span><span class="sxs-lookup"><span data-stu-id="5eac8-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="5eac8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5eac8-114">Example</span></span>  
 <span data-ttu-id="5eac8-115">Aşağıda `testfile.txt` dosyasından okuyan tam örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5eac8-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5eac8-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="5eac8-116">Robust Programming</span></span>  
 <span data-ttu-id="5eac8-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="5eac8-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5eac8-118">Satır belirtilen biçim kullanılarak ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="5eac8-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="5eac8-119">Özel durum iletisi, özel duruma neden olan satırı belirtir, <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırdaki içerilen metne atanır.</span><span class="sxs-lookup"><span data-stu-id="5eac8-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="5eac8-120">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5eac8-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="5eac8-121">Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu.</span><span class="sxs-lookup"><span data-stu-id="5eac8-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="5eac8-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5eac8-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="5eac8-123">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5eac8-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5eac8-124">Kullanıcı, dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="5eac8-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eac8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eac8-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="5eac8-126">Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="5eac8-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="5eac8-127">Nasıl Yapılır: Sabit Genişlikli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="5eac8-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="5eac8-128">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="5eac8-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
