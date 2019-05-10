---
title: "Nasıl yapılır: Visual Basic'te dosya taşıma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: e529e263353b08778eba338b20aef34762e66824
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628858"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="0faa1-102">Nasıl yapılır: Visual Basic'te dosya taşıma</span><span class="sxs-lookup"><span data-stu-id="0faa1-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="0faa1-103">`My.Computer.FileSystem.MoveFile` Yöntemi, bir dosyayı başka bir klasöre taşımak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0faa1-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="0faa1-104">Hedef yapı mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0faa1-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="0faa1-105">Bir dosyayı taşımak için</span><span class="sxs-lookup"><span data-stu-id="0faa1-105">To move a file</span></span>  
  
- <span data-ttu-id="0faa1-106">Kullanım `MoveFile` yöntemi hem kaynak dosya hem de hedef dosya için konum ve dosya adı belirterek bu dosyayı taşır.</span><span class="sxs-lookup"><span data-stu-id="0faa1-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="0faa1-107">Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="0faa1-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="0faa1-108">Kaynak dosya adı ile aynı olmasına rağmen hedef dosya adı belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0faa1-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="0faa1-109">Dosya taşıma ve yeniden adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="0faa1-109">To move a file and rename it</span></span>  
  
- <span data-ttu-id="0faa1-110">Kullanım `MoveFile` yöntemi kaynak dosya adı ve konumu, hedef konum ve hedef konumda yeni bir ad belirterek bu dosyayı taşır.</span><span class="sxs-lookup"><span data-stu-id="0faa1-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="0faa1-111">Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2` ve yeniden adlandırsa `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="0faa1-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0faa1-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0faa1-112">Robust Programming</span></span>  
 <span data-ttu-id="0faa1-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0faa1-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0faa1-114">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0faa1-115">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0faa1-116">`destinationFileName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0faa1-117">Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="0faa1-118">Varolan bir dizin için birleştirilmiş yolun noktaları, hedef dosya var ve `overwrite` ayarlanır `False`, hedef dizinde aynı ada sahip bir dosya veya kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="0faa1-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0faa1-119">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0faa1-120">`showUI` ayarlanır `True`, `onUserCancel` ayarlanır `ThrowException`ve her iki kullanıcı işlemi iptal etti veya belirtilmeyen bir g/ç hatası oluşuyor (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="0faa1-121">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="0faa1-122">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0faa1-123">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0faa1-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faa1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0faa1-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="0faa1-125">Nasıl yapılır: Dosyayı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="0faa1-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [<span data-ttu-id="0faa1-126">Nasıl yapılır: Farklı dizinde dosya kopyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="0faa1-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="0faa1-127">Nasıl yapılır: Dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="0faa1-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
