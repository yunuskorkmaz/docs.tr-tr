---
title: "Nasıl Yapılır: Visual Basic'te Birden Çok Biçimli Metin Dosyalarını Okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 12362f932561bf16412e5beb364f785778c58814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="d49d6-102">Nasıl Yapılır: Visual Basic'te Birden Çok Biçimli Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="d49d6-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="d49d6-103"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesne kolay ve verimli günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d49d6-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="d49d6-104">Kullanarak bir dosyayı birden çok biçimli işleyebilir `PeekChars` dosyası aracılığıyla ayrıştırma gibi her bir satır biçimi belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d49d6-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="d49d6-105">Birden çok biçimli metin dosyası ayrıştırılamadı</span><span class="sxs-lookup"><span data-stu-id="d49d6-105">To parse a text file with multiple formats</span></span>  
  
1.  <span data-ttu-id="d49d6-106">Projeniz testdosyası.txt adlı bir metin dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d49d6-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="d49d6-107">Aşağıdaki içeriği metin dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d49d6-107">Add the following content to the text file.</span></span>  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  <span data-ttu-id="d49d6-108">Beklenen biçimle ve bir hata bildirildiğinde kullanılan biçimini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d49d6-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="d49d6-109">Her dizi son girişi -1, bu nedenle son alan değişken genişliğini olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d49d6-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="d49d6-110">Bu durum, son giriş dizideki veya 0 değerine eşit küçük oluşur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  <span data-ttu-id="d49d6-111">Yeni bir <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> nesnesi, genişlik ve biçim tanımlama.</span><span class="sxs-lookup"><span data-stu-id="d49d6-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  <span data-ttu-id="d49d6-112">Okuma önce biçimi için test etme satırları, döngü.</span><span class="sxs-lookup"><span data-stu-id="d49d6-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  <span data-ttu-id="d49d6-113">Konsola yazma hatası.</span><span class="sxs-lookup"><span data-stu-id="d49d6-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="d49d6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d49d6-114">Example</span></span>  
 <span data-ttu-id="d49d6-115">Dosyadan okur tam bir örnek verilmiştir `testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="d49d6-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d49d6-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d49d6-116">Robust Programming</span></span>  
 <span data-ttu-id="d49d6-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d49d6-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d49d6-118">Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="d49d6-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="d49d6-119">Özel durum iletisi satırı belirtir özel duruma neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırında bulunan metin atanır.</span><span class="sxs-lookup"><span data-stu-id="d49d6-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="d49d6-120">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d49d6-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d49d6-121">Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="d49d6-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="d49d6-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d49d6-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d49d6-123">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d49d6-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d49d6-124">Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d49d6-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d49d6-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d49d6-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 [<span data-ttu-id="d49d6-126">Nasıl yapılır: virgülle ayrılmış metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="d49d6-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="d49d6-127">Nasıl yapılır: Sabit genişlikli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="d49d6-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="d49d6-128">TextFieldParser nesnesiyle metin dosyalarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="d49d6-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
