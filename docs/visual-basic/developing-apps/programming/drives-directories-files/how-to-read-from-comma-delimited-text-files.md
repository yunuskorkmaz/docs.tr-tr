---
description: 'Hakkında daha fazla bilgi için: nasıl yapılır: Visual Basic virgülle sınırlandırılmış metin dosyalarından okuma'
title: 'Nasıl yapılır: virgülle ayrılmış metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: dc4d4d5a7639ab7b5aa342aa8646b02985e40797
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797490"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="5dfe5-103">Nasıl yapılır: Visual Basic içinde virgülle ayrılmış metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="5dfe5-103">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="5dfe5-104">`TextFieldParser`Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-104">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="5dfe5-105">`TextFieldType`Özelliği, bunun ayrılmış bir dosya mı yoksa sabit genişlikte metin alanları mı olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-105">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="5dfe5-106">Virgülle ayrılmış bir metin dosyasını ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5dfe5-106">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="5dfe5-107">Yeni bir oluştur `TextFieldParser` .</span><span class="sxs-lookup"><span data-stu-id="5dfe5-107">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="5dfe5-108">Aşağıdaki kod, `TextFieldParser` adlı adı oluşturur `MyReader` ve dosyasını açar `test.txt` .</span><span class="sxs-lookup"><span data-stu-id="5dfe5-108">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="5dfe5-109">`TextField`Türü ve sınırlandırıcıyı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-109">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="5dfe5-110">Aşağıdaki kod, `TextFieldType` `Delimited` "," olarak özelliği ve sınırlandırıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-110">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="5dfe5-111">Dosyadaki alanlar arasında döngü gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-111">Loop through the fields in the file.</span></span> <span data-ttu-id="5dfe5-112">Herhangi bir satır bozuksa bir hata bildirin ve ayrıştırmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-112">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="5dfe5-113">Aşağıdaki kod, dosyasında her bir alanı görüntüleyerek ve yanlış biçimlendirilmiş tüm alanları bildiren bir dosya üzerinden döngü başlatır.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-113">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="5dfe5-114">Ve `While` `Using` bloklarıyla birlikte kapatın `End While` `End Using` .</span><span class="sxs-lookup"><span data-stu-id="5dfe5-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="5dfe5-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dfe5-115">Example</span></span>  

 <span data-ttu-id="5dfe5-116">Bu örnek dosyadan okur `test.txt` .</span><span class="sxs-lookup"><span data-stu-id="5dfe5-116">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5dfe5-117">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="5dfe5-117">Robust programming</span></span>  

 <span data-ttu-id="5dfe5-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="5dfe5-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5dfe5-119">Satır belirtilen biçim () kullanılarak ayrıştırılamıyor <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> .</span><span class="sxs-lookup"><span data-stu-id="5dfe5-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="5dfe5-120">Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliğe satırda içerilen metin atanır.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="5dfe5-121">Belirtilen dosya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="5dfe5-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="5dfe5-122">Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="5dfe5-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5dfe5-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="5dfe5-124">Yol çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="5dfe5-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5dfe5-125">Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="5dfe5-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dfe5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dfe5-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="5dfe5-127">Nasıl yapılır: Sabit Genişlikli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="5dfe5-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="5dfe5-128">Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="5dfe5-128">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="5dfe5-129">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="5dfe5-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="5dfe5-130">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="5dfe5-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="5dfe5-131">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="5dfe5-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
