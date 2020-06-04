---
title: 'Nasıl yapılır: Metin Dosyalarını Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 0d99209ed123686355e8d49c82ba23f94084f895
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411622"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="d94ab-102">Nasıl Yapılır: Visual Basic'te Metin Dosyalarını Okuma</span><span class="sxs-lookup"><span data-stu-id="d94ab-102">How to: Read From Text Files in Visual Basic</span></span>

<span data-ttu-id="d94ab-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> `My.Computer.FileSystem` Nesnesinin yöntemi bir metin dosyasından okumanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d94ab-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="d94ab-104">Dosyanın içeriği ASCII veya UTF-8 gibi bir kodlama kullanıyorsa dosya kodlaması belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d94ab-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>

<span data-ttu-id="d94ab-105">Genişletilmiş karakterler içeren bir dosyadan okuma yapıyorsanız, dosya kodlamasını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d94ab-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>

> [!NOTE]
> <span data-ttu-id="d94ab-106">Tek seferde tek satırlık bir dosyayı okumak için <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> nesnenin yöntemini kullanın `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="d94ab-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="d94ab-107">`OpenTextFileReader` metodu bir <xref:System.IO.StreamReader> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d94ab-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="d94ab-108">Tek seferde bir <xref:System.IO.StreamReader.ReadLine%2A> `StreamReader` dosyayı bir satırı okumak için nesnesinin yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d94ab-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="d94ab-109">Nesnesinin yöntemini kullanarak dosyanın sonuna kadar test edebilirsiniz <xref:System.IO.StreamReader.EndOfStream%2A> `StreamReader` .</span><span class="sxs-lookup"><span data-stu-id="d94ab-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>

## <a name="to-read-from-a-text-file"></a><span data-ttu-id="d94ab-110">Bir metin dosyasından okumak için</span><span class="sxs-lookup"><span data-stu-id="d94ab-110">To read from a text file</span></span>

<span data-ttu-id="d94ab-111">`ReadAllText` `My.Computer.FileSystem` Bir metin dosyasının içeriğini bir dizeye okumak ve yolu sağlamak için nesnesinin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d94ab-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="d94ab-112">Aşağıdaki örnek, test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d94ab-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="d94ab-113">Kodlanmış bir metin dosyasından okumak için</span><span class="sxs-lookup"><span data-stu-id="d94ab-113">To read from a text file that is encoded</span></span>

<span data-ttu-id="d94ab-114">`ReadAllText` `My.Computer.FileSystem` Bir metin dosyasının içeriğini bir dizeye okumak için nesnesinin yöntemini kullanın, yol ve dosya kodlama türünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="d94ab-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="d94ab-115">Aşağıdaki örnek, UTF32 biçimindeki test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d94ab-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a><span data-ttu-id="d94ab-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d94ab-116">Robust Programming</span></span>

<span data-ttu-id="d94ab-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d94ab-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="d94ab-118">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="d94ab-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="d94ab-119">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="d94ab-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="d94ab-120">Dosya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="d94ab-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>

- <span data-ttu-id="d94ab-121">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="d94ab-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="d94ab-122">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="d94ab-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="d94ab-123">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="d94ab-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="d94ab-124">Dizeyi arabelleğe () yazmak için yeterli bellek yok <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="d94ab-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>

- <span data-ttu-id="d94ab-125">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="d94ab-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

<span data-ttu-id="d94ab-126">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="d94ab-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="d94ab-127">Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d94ab-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>

<span data-ttu-id="d94ab-128">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d94ab-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="d94ab-129">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="d94ab-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="d94ab-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d94ab-130">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="d94ab-131">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="d94ab-131">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="d94ab-132">Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="d94ab-132">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="d94ab-133">Nasıl yapılır: Sabit Genişlikli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="d94ab-133">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="d94ab-134">Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="d94ab-134">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="d94ab-135">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="d94ab-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="d94ab-136">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d94ab-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="d94ab-137">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="d94ab-137">File Encodings</span></span>](file-encodings.md)
