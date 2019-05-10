---
title: "Nasıl yapılır: Visual Basic'te ikili dosyalara yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 79d104d7e4750bdd9f2a80bd2e2ef16ca6d9d7e1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665764"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="9072c-102">Nasıl yapılır: Visual Basic'te ikili dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="9072c-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="9072c-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Yöntemi veri bir ikili dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="9072c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="9072c-104">Varsa `append` parametresi `True`, dosyaya veri ekler; Aksi takdirde dosyasındaki verilerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="9072c-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="9072c-105">Dosya adı hariç belirtilen yol geçerli değilse bir <xref:System.IO.DirectoryNotFoundException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9072c-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="9072c-106">Yolun geçerli olduğundan, ancak dosya yok, dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9072c-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="9072c-107">Bir ikili dosyaya yazmak için</span><span class="sxs-lookup"><span data-stu-id="9072c-107">To write to a binary file</span></span>  
  
- <span data-ttu-id="9072c-108">Kullanım `WriteAllBytes` dosya yolu ve adı ile yazılacak baytları sağlama yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9072c-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="9072c-109">Bu örnek veri dizisi ekler `CustomerData` adlı dosyaya `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="9072c-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9072c-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9072c-110">Robust Programming</span></span>  
 <span data-ttu-id="9072c-111">Aşağıdaki koşullar özel bir durum oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="9072c-111">The following conditions may create an exception:</span></span>  
  
- <span data-ttu-id="9072c-112">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize; olan Bu, yalnızca boşluk içermektedir; veya geçersiz karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="9072c-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="9072c-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="9072c-113">(<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="9072c-114">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9072c-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="9072c-115">`File` mevcut olmayan bir yola işaret (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="9072c-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="9072c-116">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9072c-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="9072c-117">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="9072c-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="9072c-118">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="9072c-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="9072c-119">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9072c-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9072c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9072c-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="9072c-121">Nasıl yapılır: Dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="9072c-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
