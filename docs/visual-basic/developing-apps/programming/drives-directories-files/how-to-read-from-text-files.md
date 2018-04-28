---
title: "Nasıl Yapılır: Visual Basic'te Metin Dosyalarını Okuma"
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e39b08fcee382674fcf6af07f9da7439eb1bea69
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="a4fc7-102">Nasıl Yapılır: Visual Basic'te Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="a4fc7-102">How to: Read From Text Files in Visual Basic</span></span>
<span data-ttu-id="a4fc7-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Yöntemi `My.Computer.FileSystem` nesne bir metin dosyasından okuma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="a4fc7-104">Dosyanın içeriği ASCII veya UTF-8 gibi bir kodlama kullanıyorsa dosya kodlaması belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>  
  
 <span data-ttu-id="a4fc7-105">Genişletilmiş karakterler içeren bir dosyadan okuma yapıyorsanız, dosya kodlamasını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4fc7-106">Bir dosyayı aynı anda tek satırlık metin okumak için kullanmak <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> yöntemi `My.Computer.FileSystem` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="a4fc7-107">`OpenTextFileReader` Yöntemi döndürür bir <xref:System.IO.StreamReader> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="a4fc7-108">Kullanabileceğiniz <xref:System.IO.StreamReader.ReadLine%2A> yöntemi `StreamReader` aynı anda dosya tek bir çizgi okumak için nesne.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="a4fc7-109">Kullanarak dosya sonu sınayabilirsiniz <xref:System.IO.StreamReader.EndOfStream%2A> yöntemi `StreamReader` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>  
  
### <a name="to-read-from-a-text-file"></a><span data-ttu-id="a4fc7-110">Bir metin dosyasından okumak için</span><span class="sxs-lookup"><span data-stu-id="a4fc7-110">To read from a text file</span></span>  
  
-   <span data-ttu-id="a4fc7-111">Kullanım `ReadAllText` yöntemi `My.Computer.FileSystem` yol sağlayan bir dize olarak bir metin dosyasının içeriğini okumak için nesne.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="a4fc7-112">Aşağıdaki örnek, test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="a4fc7-113">Kodlanmış bir metin dosyasından okumak için</span><span class="sxs-lookup"><span data-stu-id="a4fc7-113">To read from a text file that is encoded</span></span>  
  
-   <span data-ttu-id="a4fc7-114">Kullanım `ReadAllText` yöntemi `My.Computer.FileSystem` yol sağlayan bir dize olarak bir metin dosyasının içeriğini okumak ve dosya kodlama türü için nesne.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="a4fc7-115">Aşağıdaki örnek, UTF32 biçimindeki test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a4fc7-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a4fc7-116">Robust Programming</span></span>  
 <span data-ttu-id="a4fc7-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="a4fc7-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a4fc7-118">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="a4fc7-119">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="a4fc7-120">Dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="a4fc7-121">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştuğunda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a4fc7-122">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="a4fc7-123">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="a4fc7-124">Dize arabelleğe yazmak için yeterli bellek yok (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="a4fc7-125">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a4fc7-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="a4fc7-126">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="a4fc7-127">Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="a4fc7-128">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="a4fc7-129">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fc7-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4fc7-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>  
 [<span data-ttu-id="a4fc7-131">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="a4fc7-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="a4fc7-132">Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="a4fc7-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="a4fc7-133">Nasıl Yapılır: Sabit Genişlikli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="a4fc7-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="a4fc7-134">Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="a4fc7-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="a4fc7-135">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="a4fc7-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [<span data-ttu-id="a4fc7-136">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="a4fc7-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="a4fc7-137">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="a4fc7-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
