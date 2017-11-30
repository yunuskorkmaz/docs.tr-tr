---
title: "Nasıl yapılır: Visual Basic'te virgülle ayrılmış metin dosyalarını okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd88762179d9760bcce37b4c500a2bb118e09173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="82e8f-102">Nasıl yapılır: Visual Basic'te virgülle ayrılmış metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="82e8f-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="82e8f-103">`TextFieldParser` Nesne kolay ve verimli günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="82e8f-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="82e8f-104">`TextFieldType` Özelliği sınırlandırılmış bir dosyanın veya bir metin sabit genişlikli alanlarla olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82e8f-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="82e8f-105">Sınırlandırılmış metin dosyası virgül ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="82e8f-105">To parse a comma delimited text file</span></span>  
  
1.  <span data-ttu-id="82e8f-106">Yeni bir `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="82e8f-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="82e8f-107">Aşağıdaki kod oluşturur `TextFieldParser` adlı `MyReader` ve dosyayı açar `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="82e8f-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  <span data-ttu-id="82e8f-108">Tanımlamak `TextField` türü ve sınırlayıcı.</span><span class="sxs-lookup"><span data-stu-id="82e8f-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="82e8f-109">Aşağıdaki kod tanımlar `TextFieldType` özelliği olarak `Delimited` ve ayırıcı olarak ",".</span><span class="sxs-lookup"><span data-stu-id="82e8f-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  <span data-ttu-id="82e8f-110">Dosyadaki alanların döngü.</span><span class="sxs-lookup"><span data-stu-id="82e8f-110">Loop through the fields in the file.</span></span> <span data-ttu-id="82e8f-111">Tüm satırları bozuksa, bir hata raporu ve ayrıştırma devam edin.</span><span class="sxs-lookup"><span data-stu-id="82e8f-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="82e8f-112">Aşağıdaki kod, her bir alan sırayla görüntüleme ve hatalı biçimlendirilmiş herhangi bir alan raporlama dosyasıyla döngüsü.</span><span class="sxs-lookup"><span data-stu-id="82e8f-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  <span data-ttu-id="82e8f-113">Kapat `While` ve `Using` ile engeller `End While` ve `End Using`.</span><span class="sxs-lookup"><span data-stu-id="82e8f-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="82e8f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="82e8f-114">Example</span></span>  
 <span data-ttu-id="82e8f-115">Bu örnek dosyadan okur `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="82e8f-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="82e8f-116">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="82e8f-116">Robust programming</span></span>  
 <span data-ttu-id="82e8f-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="82e8f-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="82e8f-118">Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="82e8f-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="82e8f-119">Özel durum iletisi satırı belirtir özel duruma neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırında bulunan metin atanır.</span><span class="sxs-lookup"><span data-stu-id="82e8f-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="82e8f-120">Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="82e8f-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="82e8f-121">Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="82e8f-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="82e8f-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="82e8f-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="82e8f-123">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="82e8f-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="82e8f-124">Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="82e8f-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e8f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e8f-125">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [<span data-ttu-id="82e8f-126">Nasıl yapılır: Sabit genişlikli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="82e8f-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="82e8f-127">Nasıl yapılır: birden çok biçimli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="82e8f-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="82e8f-128">TextFieldParser nesnesiyle metin dosyalarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="82e8f-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [<span data-ttu-id="82e8f-129">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="82e8f-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="82e8f-130">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="82e8f-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
