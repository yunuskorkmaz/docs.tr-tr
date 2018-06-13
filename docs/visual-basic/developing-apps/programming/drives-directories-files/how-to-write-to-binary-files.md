---
title: "Nasıl Yapılır: Visual Basic'te İkili Dosyalara Yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 59edf84c1addd287eb1d1615c46258f329b1c7e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587208"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="c228f-102">Nasıl Yapılır: Visual Basic'te İkili Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="c228f-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="c228f-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Yöntemi için ikili dosya verileri yazar.</span><span class="sxs-lookup"><span data-stu-id="c228f-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="c228f-104">Varsa `append` parametresi `True`, veri dosyasına eklenir; Aksi takdirde dosyasındaki verilerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="c228f-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="c228f-105">Dosya adı hariç belirtilen yol geçerli değilse bir <xref:System.IO.DirectoryNotFoundException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="c228f-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="c228f-106">Yolun geçerli olduğundan, ancak dosya mevcut değil, dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c228f-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="c228f-107">İkili bir dosyaya yazmak için</span><span class="sxs-lookup"><span data-stu-id="c228f-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="c228f-108">Kullanım `WriteAllBytes` yöntemi, dosya yolu ve adı ve yazılacak bayt sağlama.</span><span class="sxs-lookup"><span data-stu-id="c228f-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="c228f-109">Bu örnek veri dizisi ekler `CustomerData` adlı dosyaya `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="c228f-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c228f-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c228f-110">Robust Programming</span></span>  
 <span data-ttu-id="c228f-111">Aşağıdaki koşullar, bir özel durum oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c228f-111">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="c228f-112">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize; olduğu yalnızca boşluk içeriyor; veya geçersiz karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c228f-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="c228f-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c228f-113">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c228f-114">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c228f-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c228f-115">`File` var olmayan bir yola işaret eden (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c228f-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="c228f-116">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştuğunda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c228f-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="c228f-117">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c228f-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="c228f-118">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="c228f-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="c228f-119">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c228f-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c228f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c228f-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [<span data-ttu-id="c228f-121">Nasıl Yapılır: Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="c228f-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
