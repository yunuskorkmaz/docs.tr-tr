---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic birden çok biçimdeki fext dosyalarından okuma'
title: 'Nasıl yapılır: birden çok biçimdeki metin dosyalarından okuma'
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
ms.openlocfilehash: 90d981ad051fb395d57604434cf9ba6b74603e7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797451"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="657fe-103">Nasıl yapılır: Visual Basic birden çok biçimdeki fext dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="657fe-103">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="657fe-104"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="657fe-104">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="657fe-105">`PeekChars`Dosya aracılığıyla ayrıştırdığınızda her satırın biçimini belirleyebilmek için yöntemini kullanarak birden çok biçimdeki bir dosyayı işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="657fe-105">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="657fe-106">Birden çok biçimdeki bir metin dosyasını ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="657fe-106">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="657fe-107">Projenize *testfile.txt* adlı bir metin dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="657fe-107">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="657fe-108">Aşağıdaki içeriği metin dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="657fe-108">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="657fe-109">Beklenen biçimi ve bir hata bildirildiğinde kullanılan biçimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="657fe-109">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="657fe-110">Her dizideki son giriş-1 ' dir, bu nedenle son alan, değişken genişliği olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="657fe-110">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="657fe-111">Bu, dizideki son giriş 0 ' dan küçük veya buna eşit olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="657fe-111">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="657fe-112"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Genişliği ve biçimi tanımlayarak yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="657fe-112">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="657fe-113">Okumadan önce biçim için test eden satırlarda döngü yapın.</span><span class="sxs-lookup"><span data-stu-id="657fe-113">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="657fe-114">Konsola hataları yazın.</span><span class="sxs-lookup"><span data-stu-id="657fe-114">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="657fe-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="657fe-115">Example</span></span>

<span data-ttu-id="657fe-116">Aşağıda, dosyadan okuyan tüm örnek verilmiştir `testfile.txt` :</span><span class="sxs-lookup"><span data-stu-id="657fe-116">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="657fe-117">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="657fe-117">Robust programming</span></span>

<span data-ttu-id="657fe-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="657fe-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="657fe-119">Satır belirtilen biçim () kullanılarak ayrıştırılamıyor <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> .</span><span class="sxs-lookup"><span data-stu-id="657fe-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="657fe-120">Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özellik satırda bulunan metne atanır.</span><span class="sxs-lookup"><span data-stu-id="657fe-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="657fe-121">Belirtilen dosya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="657fe-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="657fe-122">Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu.</span><span class="sxs-lookup"><span data-stu-id="657fe-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="657fe-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="657fe-123">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="657fe-124">Yol çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="657fe-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="657fe-125">Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="657fe-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="657fe-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="657fe-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="657fe-127">Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="657fe-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="657fe-128">Nasıl yapılır: Sabit Genişlikli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="657fe-128">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="657fe-129">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="657fe-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
