---
title: "Nasıl Yapılır: Visual Basic'te Dosyayı Yeniden Adlandırma"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: ef024f90567d8d69bdd432499db96e4f67578ce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586418"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="06512-102">Nasıl Yapılır: Visual Basic'te Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="06512-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="06512-103">Kullanım `RenameFile` yöntemi `My.Computer.FileSystem` geçerli konumu, dosya adı ve yeni dosya adını belirterek bir dosyayı yeniden adlandırmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="06512-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="06512-104">Bu yöntem, bir dosyayı taşımak için kullanılamaz; kullanmak `MoveFile` yöntemi taşımak ve dosyayı yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="06512-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="06512-105">Bir dosyayı yeniden adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="06512-105">To rename a file</span></span>  
  
-   <span data-ttu-id="06512-106">Kullanım `My.Computer.FileSystem.RenameFile` yöntemi bir dosyayı yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="06512-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="06512-107">Bu örnek adlı dosyayı yeniden adlandırır `Test.txt` için `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="06512-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 <span data-ttu-id="06512-108">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06512-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="06512-109">Kod parçacığı Seçici kod parçacığında bulunan **dosya sistemi - işleme sürücüleri, klasörleri ve dosyaları**.</span><span class="sxs-lookup"><span data-stu-id="06512-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="06512-110">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="06512-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="06512-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="06512-111">Robust Programming</span></span>  
 <span data-ttu-id="06512-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="06512-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="06512-113">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="06512-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="06512-114">`newName` yol bilgisi içerir (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="06512-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="06512-115">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="06512-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="06512-116">`newName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="06512-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="06512-117">Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="06512-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="06512-118">Varolan bir dosya veya dizin, belirtilen ada sahip olduğundan `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="06512-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="06512-119">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="06512-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="06512-120">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="06512-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="06512-121">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="06512-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="06512-122">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="06512-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06512-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06512-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>  
 [<span data-ttu-id="06512-124">Nasıl Yapılır: Dosya Taşıma</span><span class="sxs-lookup"><span data-stu-id="06512-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)  
 [<span data-ttu-id="06512-125">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="06512-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 [<span data-ttu-id="06512-126">Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="06512-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [<span data-ttu-id="06512-127">Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="06512-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
