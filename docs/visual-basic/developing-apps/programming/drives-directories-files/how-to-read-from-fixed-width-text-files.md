---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic sabit genişlikli metin dosyalarından okuma'
title: 'Nasıl yapılır: sabit genişlikli metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 4f5868fa68009851cc65eeaf5ff6431ac22840d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797464"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="6aaa8-103">Nasıl yapılır: Visual Basic içindeki sabit genişlikli metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="6aaa8-103">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="6aaa8-104">`TextFieldParser`Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-104">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="6aaa8-105">`TextFieldType`Özelliği, ayrıştırılmış dosyanın ayrılmış bir dosya mı yoksa sabit genişlikte metin alanları olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-105">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="6aaa8-106">Sabit genişlikli bir metin dosyasında, sonundaki alanın bir değişken genişliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-106">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="6aaa8-107">Uçtaki alanın bir değişken genişliğine sahip olduğunu belirtmek için, bu değeri sıfıra eşit veya daha küçük bir genişliğe sahip olacak şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-107">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="6aaa8-108">Sabit genişlikli bir metin dosyasını ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6aaa8-108">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="6aaa8-109">Yeni bir oluştur `TextFieldParser` .</span><span class="sxs-lookup"><span data-stu-id="6aaa8-109">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="6aaa8-110">Aşağıdaki kod, `TextFieldParser` adlı adı oluşturur `Reader` ve dosyasını açar `test.log` .</span><span class="sxs-lookup"><span data-stu-id="6aaa8-110">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="6aaa8-111">Özelliği, `TextFieldType` `FixedWidth` genişliği ve biçimi tanımlayarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-111">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="6aaa8-112">Aşağıdaki kod, metnin sütunlarını tanımlar; Birincisi 5 karakter genişliğinde, ikinci 10, üçüncü 11 ve dördüncü değişken genişliktedir.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-112">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="6aaa8-113">Dosyadaki alanlar arasında döngü gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-113">Loop through the fields in the file.</span></span> <span data-ttu-id="6aaa8-114">Herhangi bir satır bozuksa, bir hata bildirin ve ayrıştırmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-114">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="6aaa8-115">Ve `While` `Using` bloklarıyla birlikte kapatın `End While` `End Using` .</span><span class="sxs-lookup"><span data-stu-id="6aaa8-115">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="6aaa8-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6aaa8-116">Example</span></span>  

 <span data-ttu-id="6aaa8-117">Bu örnek dosyadan okur `test.log` .</span><span class="sxs-lookup"><span data-stu-id="6aaa8-117">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6aaa8-118">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="6aaa8-118">Robust programming</span></span>  

 <span data-ttu-id="6aaa8-119">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="6aaa8-119">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6aaa8-120">Satır belirtilen biçim () kullanılarak ayrıştırılamıyor <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> .</span><span class="sxs-lookup"><span data-stu-id="6aaa8-120">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="6aaa8-121">Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özellik satırda bulunan metne atanır.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-121">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="6aaa8-122">Belirtilen dosya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="6aaa8-122">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="6aaa8-123">Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-123">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="6aaa8-124">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="6aaa8-124">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="6aaa8-125">Yol çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="6aaa8-125">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="6aaa8-126">Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="6aaa8-126">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aaa8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aaa8-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="6aaa8-128">Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="6aaa8-128">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="6aaa8-129">Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="6aaa8-129">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="6aaa8-130">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="6aaa8-130">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="6aaa8-131">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="6aaa8-131">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="6aaa8-132">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="6aaa8-132">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
