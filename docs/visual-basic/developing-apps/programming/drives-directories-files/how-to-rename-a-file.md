---
title: "Nasıl yapılır: Visual Basic'te dosyayı yeniden adlandırma"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 0fac312c4c20f57e93dc88d0d6bb6b13932f7682
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966989"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="14362-102">Nasıl yapılır: Visual Basic'te dosyayı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="14362-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="14362-103">Kullanım `RenameFile` yöntemi `My.Computer.FileSystem` geçerli konumu, dosya adı ve yeni dosya adı sağlayarak bir dosyayı yeniden adlandırmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="14362-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="14362-104">Bu yöntem, bir dosyayı taşımak için kullanılamaz; kullanma `MoveFile` yöntemi taşımak ve dosyayı yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="14362-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="14362-105">Bir dosyayı yeniden adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="14362-105">To rename a file</span></span>  
  
-   <span data-ttu-id="14362-106">Kullanım `My.Computer.FileSystem.RenameFile` bir dosyayı yeniden adlandırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="14362-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="14362-107">Bu örnek adlı dosyayı yeniden adlandırır `Test.txt` için `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="14362-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="14362-108">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14362-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="14362-109">Kod parçacığı Seçici'de, kod parçacığında bulunan **dosya sistemi - işleme sürücüler, klasörler ve dosyaları**.</span><span class="sxs-lookup"><span data-stu-id="14362-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="14362-110">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="14362-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="14362-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="14362-111">Robust Programming</span></span>  
 <span data-ttu-id="14362-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="14362-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="14362-113">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="14362-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="14362-114">`newName` yol bilgisi içerir (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="14362-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="14362-115">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="14362-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="14362-116">`newName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="14362-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="14362-117">Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="14362-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="14362-118">Varolan bir dosya veya dizin belirtilen ada sahip olduğundan `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="14362-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="14362-119">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="14362-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="14362-120">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="14362-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="14362-121">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="14362-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="14362-122">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="14362-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14362-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14362-123">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="14362-124">Nasıl yapılır: Dosya taşıma</span><span class="sxs-lookup"><span data-stu-id="14362-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [<span data-ttu-id="14362-125">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="14362-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="14362-126">Nasıl yapılır: Aynı dizinde dosya kopyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="14362-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="14362-127">Nasıl yapılır: Farklı dizinde dosya kopyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="14362-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
