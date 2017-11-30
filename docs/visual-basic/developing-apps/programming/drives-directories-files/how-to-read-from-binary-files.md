---
title: "Nasıl Yapılır: Visual Basic'te İkili Dosyaları Okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6056f7d33b1137abb19b24246ce6874ff4d008
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="6e3bc-102">Nasıl Yapılır: Visual Basic'te İkili Dosyaları Okuma</span><span class="sxs-lookup"><span data-stu-id="6e3bc-102">How to: Read From Binary Files in Visual Basic</span></span>
<span data-ttu-id="6e3bc-103">`My.Computer.FileSystem` Nesnesi sağlar `ReadAllBytes` ikili dosyaları okuma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="6e3bc-104">İkili dosyasından okunamıyor</span><span class="sxs-lookup"><span data-stu-id="6e3bc-104">To read from a binary file</span></span>  
  
-   <span data-ttu-id="6e3bc-105">Kullanım `ReadAllBytes` bir bayt dizisi olarak bir dosyanın içeriğini döndürür yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="6e3bc-106">Bu örnek dosyadan okur `C:/Documents and Settings/selfportrait.jpg`.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   <span data-ttu-id="6e3bc-107">İkili büyük dosyalar için kullandığınız <xref:System.IO.FileStream.Read%2A> yöntemi <xref:System.IO.FileStream> aynı anda yalnızca belirtilen tutarı dosyasını okumaya nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="6e3bc-108">Sonra dosyanın ne kadar her okuma işlemi için belleğe yüklenen sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="6e3bc-109">Aşağıdaki kod örneği, bir dosyayı kopyalar ve ne kadar dosya okuma işlemi başına belleğe okunur belirtmek arayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6e3bc-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6e3bc-110">Robust Programming</span></span>  
 <span data-ttu-id="6e3bc-111">Aşağıdaki koşullar, bir özel durum oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="6e3bc-111">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="6e3bc-112">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="6e3bc-113">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="6e3bc-114">Dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="6e3bc-115">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştuğunda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="6e3bc-116">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="6e3bc-117">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="6e3bc-118">Dize arabelleğe yazmak için yeterli bellek yok (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="6e3bc-119">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="6e3bc-120">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="6e3bc-121">Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="6e3bc-122">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="6e3bc-123">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3bc-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [<span data-ttu-id="6e3bc-125">Dosyaları okuma</span><span class="sxs-lookup"><span data-stu-id="6e3bc-125">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="6e3bc-126">Nasıl yapılır: birden çok biçimli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="6e3bc-126">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="6e3bc-127">Verileri Panoda depolama ve panodan okuma</span><span class="sxs-lookup"><span data-stu-id="6e3bc-127">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
