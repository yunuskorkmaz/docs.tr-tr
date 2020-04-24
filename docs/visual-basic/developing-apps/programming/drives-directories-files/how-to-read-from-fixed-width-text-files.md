---
title: 'Nasıl yapılır: sabit genişlikli metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334623"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="4362b-102">Nasıl yapılır: Visual Basic içindeki sabit genişlikli metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="4362b-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="4362b-103">`TextFieldParser` Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4362b-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="4362b-104">`TextFieldType` Özelliği, ayrıştırılmış dosyanın ayrılmış bir dosya mı yoksa sabit genişlikte metin alanları olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4362b-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="4362b-105">Sabit genişlikli bir metin dosyasında, sonundaki alanın bir değişken genişliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="4362b-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="4362b-106">Uçtaki alanın bir değişken genişliğine sahip olduğunu belirtmek için, bu değeri sıfıra eşit veya daha küçük bir genişliğe sahip olacak şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4362b-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="4362b-107">Sabit genişlikli bir metin dosyasını ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4362b-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="4362b-108">Yeni `TextFieldParser`bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="4362b-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="4362b-109">Aşağıdaki kod, `TextFieldParser` adlı adı `Reader` oluşturur ve dosyasını `test.log`açar.</span><span class="sxs-lookup"><span data-stu-id="4362b-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="4362b-110">`TextFieldType` Özelliği `FixedWidth`, genişliği ve biçimi tanımlayarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4362b-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="4362b-111">Aşağıdaki kod, metnin sütunlarını tanımlar; Birincisi 5 karakter genişliğinde, ikinci 10, üçüncü 11 ve dördüncü değişken genişliktedir.</span><span class="sxs-lookup"><span data-stu-id="4362b-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="4362b-112">Dosyadaki alanlar arasında döngü gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="4362b-112">Loop through the fields in the file.</span></span> <span data-ttu-id="4362b-113">Herhangi bir satır bozuksa, bir hata bildirin ve ayrıştırmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="4362b-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="4362b-114">`While` Ve `Using` bloklarıyla birlikte `End While` kapatın. `End Using`</span><span class="sxs-lookup"><span data-stu-id="4362b-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="4362b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="4362b-115">Example</span></span>  

 <span data-ttu-id="4362b-116">Bu örnek dosyadan okur `test.log`.</span><span class="sxs-lookup"><span data-stu-id="4362b-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4362b-117">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="4362b-117">Robust programming</span></span>  

 <span data-ttu-id="4362b-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="4362b-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4362b-119">Satır belirtilen biçim (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>) kullanılarak ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="4362b-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="4362b-120">Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> Özellik satırda bulunan metne atanır.</span><span class="sxs-lookup"><span data-stu-id="4362b-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="4362b-121">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="4362b-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="4362b-122">Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu.</span><span class="sxs-lookup"><span data-stu-id="4362b-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="4362b-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4362b-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="4362b-124">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="4362b-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="4362b-125">Kullanıcı, dosyaya (<xref:System.UnauthorizedAccessException>) erişmek için yeterli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="4362b-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4362b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4362b-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="4362b-127">Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="4362b-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="4362b-128">Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="4362b-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="4362b-129">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="4362b-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="4362b-130">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="4362b-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="4362b-131">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="4362b-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
