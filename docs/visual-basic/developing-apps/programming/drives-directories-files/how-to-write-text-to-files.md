---
title: "Nasıl yapılır: Visual Basic'te dosyalara metin yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: 7862e9b471808c2d01771acacefef15bdb31dda5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975075"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="0a350-102">Nasıl yapılır: Visual Basic'te dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="0a350-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="0a350-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Yöntemi, dosyalara metin yazma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a350-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="0a350-104">Belirtilen dosya yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0a350-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="0a350-105">Yordam</span><span class="sxs-lookup"><span data-stu-id="0a350-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="0a350-106">Bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="0a350-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="0a350-107">Kullanım `WriteAllText` metin dosyasını ve yazılacak metin belirten bir dosyaya yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0a350-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="0a350-108">Bu örnek, satır Yazar `"This is new text."` adlı dosyaya `test.txt`, var olan herhangi bir metin dosyasındaki metni ekleme.</span><span class="sxs-lookup"><span data-stu-id="0a350-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="0a350-109">Dizeleri bir dizi bir dosyaya yazmak için</span><span class="sxs-lookup"><span data-stu-id="0a350-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="0a350-110">Dize koleksiyonu döngü.</span><span class="sxs-lookup"><span data-stu-id="0a350-110">Loop through the string collection.</span></span> <span data-ttu-id="0a350-111">Kullanım `WriteAllText` eklenecek dize ve hedef dosya belirtme bir dosyaya metin yazma yöntemi ve ayarı `append` için `True`.</span><span class="sxs-lookup"><span data-stu-id="0a350-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="0a350-112">Bu örnek, dosyaların adlarını Yazar `Documents and Settings` dizininden `FileList.txt`, arasında daha iyi okunabilirlik için her bir satır başı ekleme döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a350-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0a350-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0a350-113">Robust Programming</span></span>  
 <span data-ttu-id="0a350-114">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0a350-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="0a350-115">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="0a350-116">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="0a350-117">`File` mevcut olmayan bir yola işaret (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="0a350-118">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="0a350-119">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="0a350-120">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="0a350-121">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="0a350-122">Tam ve çağrısı disktir `WriteAllText` başarısız (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0a350-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="0a350-123">Kısmi güven bağlamda çalıştırıyorsanız, kod bir özel durum yetersiz ayrıcalıklar nedeniyle fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="0a350-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="0a350-124">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="0a350-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a350-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a350-125">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="0a350-126">Nasıl yapılır: Metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="0a350-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
