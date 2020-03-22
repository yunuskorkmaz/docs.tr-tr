---
title: 'Nasıl Yapılır: Metin Dosyalarından Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 8af088ad269cc77bc5c83aedb86bde9af2e37a15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334587"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="76cfd-102">Nasıl Yapılır: Visual Basic'te Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="76cfd-102">How to: Read From Text Files in Visual Basic</span></span>

<span data-ttu-id="76cfd-103">`My.Computer.FileSystem` Nesnenin <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> yöntemi bir metin dosyasından okumanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="76cfd-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="76cfd-104">Dosyanın içeriği ASCII veya UTF-8 gibi bir kodlama kullanıyorsa dosya kodlaması belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="76cfd-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>

<span data-ttu-id="76cfd-105">Genişletilmiş karakterler içeren bir dosyadan okuma yapıyorsanız, dosya kodlamasını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="76cfd-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>

> [!NOTE]
> <span data-ttu-id="76cfd-106">Bir dosyayı bir defada tek bir metin <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> satırı `My.Computer.FileSystem` okumak için nesnenin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="76cfd-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="76cfd-107">`OpenTextFileReader` metodu bir <xref:System.IO.StreamReader> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="76cfd-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="76cfd-108">Bir dosyayı <xref:System.IO.StreamReader.ReadLine%2A> bir `StreamReader` defada bir satır okumak için nesnenin yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cfd-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="76cfd-109">`StreamReader` Nesnenin <xref:System.IO.StreamReader.EndOfStream%2A> yöntemini kullanarak dosyanın sonu için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cfd-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>

## <a name="to-read-from-a-text-file"></a><span data-ttu-id="76cfd-110">Bir metin dosyasından okumak için</span><span class="sxs-lookup"><span data-stu-id="76cfd-110">To read from a text file</span></span>

<span data-ttu-id="76cfd-111">Bir `ReadAllText` metin dosyasının içeriğini bir dize halinde okumak ve yolu sağlamak için `My.Computer.FileSystem` nesnenin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="76cfd-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="76cfd-112">Aşağıdaki örnek, test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="76cfd-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="76cfd-113">Kodlanmış bir metin dosyasından okumak için</span><span class="sxs-lookup"><span data-stu-id="76cfd-113">To read from a text file that is encoded</span></span>

<span data-ttu-id="76cfd-114">Yol `ReadAllText` ve dosya `My.Computer.FileSystem` kodlama türünü sağlayarak bir metin dosyasının içeriğini bir dize halinde okumak için nesnenin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="76cfd-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="76cfd-115">Aşağıdaki örnek, UTF32 biçimindeki test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="76cfd-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a><span data-ttu-id="76cfd-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="76cfd-116">Robust Programming</span></span>

<span data-ttu-id="76cfd-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="76cfd-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="76cfd-118">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunlukta bir dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, ya da bir aygıt yolu ( ).<xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="76cfd-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="76cfd-119">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="76cfd-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="76cfd-120">Dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="76cfd-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>

- <span data-ttu-id="76cfd-121">Dosya başka bir işlem tarafından kullanılıyor veya G/Ç<xref:System.IO.IOException>hatası oluşur ( ).</span><span class="sxs-lookup"><span data-stu-id="76cfd-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="76cfd-122">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="76cfd-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="76cfd-123">Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="76cfd-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="76cfd-124">Arabellek için dize yazmak için yeterli<xref:System.OutOfMemoryException>bellek yoktur ( ).</span><span class="sxs-lookup"><span data-stu-id="76cfd-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>

- <span data-ttu-id="76cfd-125">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="76cfd-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

<span data-ttu-id="76cfd-126">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="76cfd-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="76cfd-127">Örneğin, Form1.vb dosyası Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="76cfd-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>

<span data-ttu-id="76cfd-128">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="76cfd-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="76cfd-129">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="76cfd-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="76cfd-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76cfd-130">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="76cfd-131">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="76cfd-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="76cfd-132">Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="76cfd-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="76cfd-133">Nasıl Yapılır: Sabit Genişlikli Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="76cfd-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="76cfd-134">Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="76cfd-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="76cfd-135">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="76cfd-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="76cfd-136">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="76cfd-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="76cfd-137">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="76cfd-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
