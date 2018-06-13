---
title: "Nasıl Yapılır: Visual Basic'te Dosya Taşıma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 95a7deeec7c5f5d997a99ba9aa4bae8d7f972b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587299"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="d78ab-102">Nasıl Yapılır: Visual Basic'te Dosya Taşıma</span><span class="sxs-lookup"><span data-stu-id="d78ab-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="d78ab-103">`My.Computer.FileSystem.MoveFile` Yöntemi, bir dosyayı başka bir klasöre taşımak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d78ab-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="d78ab-104">Hedef yapı mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d78ab-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="d78ab-105">Bir dosyayı taşımak için</span><span class="sxs-lookup"><span data-stu-id="d78ab-105">To move a file</span></span>  
  
-   <span data-ttu-id="d78ab-106">Kullanım `MoveFile` kaynak dosyasını ve hedef dosya konumu ve dosya adını belirterek bu dosyayı taşımak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d78ab-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="d78ab-107">Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="d78ab-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="d78ab-108">Kaynak dosya adı ile aynı olmasına rağmen hedef dosya adı belirtilen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d78ab-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="d78ab-109">Dosya taşıma ve yeniden adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="d78ab-109">To move a file and rename it</span></span>  
  
-   <span data-ttu-id="d78ab-110">Kullanım `MoveFile` kaynak dosya adı ve konumu, hedef konumu ve hedef konumda yeni adını belirterek bu dosyayı taşımak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d78ab-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="d78ab-111">Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2` ve adlandırsa `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="d78ab-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d78ab-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d78ab-112">Robust Programming</span></span>  
 <span data-ttu-id="d78ab-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d78ab-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d78ab-114">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d78ab-115">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d78ab-116">`destinationFileName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d78ab-117">Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d78ab-118">Birleşik yol noktalarını varolan bir dizin için hedef dosyanın var olduğundan ve `overwrite` ayarlanır `False`, aynı ada sahip hedef dizinde bir dosyanın kullanımda olduğunu veya kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="d78ab-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d78ab-119">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="d78ab-120">`showUI` ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`ve her iki kullanıcı işlemi iptal etti veya belirtilmemiş bir g/ç hatası oluştuğunda (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="d78ab-121">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d78ab-122">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d78ab-123">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d78ab-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78ab-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d78ab-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>  
 [<span data-ttu-id="d78ab-125">Nasıl Yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="d78ab-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [<span data-ttu-id="d78ab-126">Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d78ab-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="d78ab-127">Nasıl Yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="d78ab-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
