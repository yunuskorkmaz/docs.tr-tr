---
title: "Nasıl yapılır: Visual Basic'te ikili dosyaları okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: e9b30d119a404396e2bf37aa445a420f7823c57b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980392"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="e79ba-102">Nasıl yapılır: Visual Basic'te ikili dosyaları okuma</span><span class="sxs-lookup"><span data-stu-id="e79ba-102">How to: Read From Binary Files in Visual Basic</span></span>
<span data-ttu-id="e79ba-103">`My.Computer.FileSystem` Nesnesi sağlar `ReadAllBytes` ikili dosyaları okuma için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e79ba-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="e79ba-104">İkili dosyasından okunamıyor</span><span class="sxs-lookup"><span data-stu-id="e79ba-104">To read from a binary file</span></span>  
  
-   <span data-ttu-id="e79ba-105">Kullanım `ReadAllBytes` yöntemi bir bayt dizisi olarak bir dosyanın içeriğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e79ba-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="e79ba-106">Bu örnekte dosyadan okur `C:/Documents and Settings/selfportrait.jpg`.</span><span class="sxs-lookup"><span data-stu-id="e79ba-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
-   <span data-ttu-id="e79ba-107">Büyük ikili dosyalar için kullandığınız <xref:System.IO.FileStream.Read%2A> yöntemi <xref:System.IO.FileStream> dosyasından belirtilen bir miktarı bir kerede okumak için nesne.</span><span class="sxs-lookup"><span data-stu-id="e79ba-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="e79ba-108">Ardından, dosyanın ne kadar her okuma işlemi için belleğe yüklenen sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e79ba-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="e79ba-109">Aşağıdaki kod örneği, bir dosyayı kopyalar ve ne kadar dosya okuma işlemi başına belleğe okunur belirtmek çağıranın izin verir.</span><span class="sxs-lookup"><span data-stu-id="e79ba-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e79ba-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e79ba-110">Robust Programming</span></span>  
 <span data-ttu-id="e79ba-111">Aşağıdaki koşullar, bir özel durum oluşturulmasına neden:</span><span class="sxs-lookup"><span data-stu-id="e79ba-111">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="e79ba-112">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e79ba-113">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e79ba-114">Dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="e79ba-115">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e79ba-116">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="e79ba-117">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="e79ba-118">Dizeyi arabelleğe yazmak için yeterli bellek yok (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="e79ba-119">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e79ba-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="e79ba-120">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="e79ba-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e79ba-121">Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e79ba-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="e79ba-122">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e79ba-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="e79ba-123">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e79ba-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79ba-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e79ba-124">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="e79ba-125">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="e79ba-125">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="e79ba-126">Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="e79ba-126">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="e79ba-127">Verileri Panoda Depolama ve Panodan Okuma</span><span class="sxs-lookup"><span data-stu-id="e79ba-127">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
