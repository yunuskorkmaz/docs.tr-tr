---
title: 'Nasıl Yapılır: Dosyayı Yeniden Adlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: e69dad9ad7f59002ad62b7a06299ff012488e534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334548"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="d504f-102">Nasıl Yapılır: Visual Basic'te Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="d504f-102">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="d504f-103">Geçerli `RenameFile` konumu, `My.Computer.FileSystem` dosya adını ve yeni dosya adını sağlayarak dosyayı yeniden adlandırmak için nesnenin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d504f-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="d504f-104">Bu yöntem bir dosyayı taşımak için kullanılamaz; dosyayı `MoveFile` taşımak ve yeniden adlandırmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d504f-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="d504f-105">Dosyayı yeniden adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="d504f-105">To rename a file</span></span>  
  
- <span data-ttu-id="d504f-106">Dosyayı `My.Computer.FileSystem.RenameFile` yeniden adlandırmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d504f-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="d504f-107">Bu örnek, `Test.txt` `SecondTest.txt`'' adlı dosyayı yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="d504f-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="d504f-108">Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d504f-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="d504f-109">Kod snippet toplayıcı, snippet Dosya sisteminde yer alır **- İşleme Sürücüler, Klasörler ve Dosyalar**.</span><span class="sxs-lookup"><span data-stu-id="d504f-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="d504f-110">Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.</span><span class="sxs-lookup"><span data-stu-id="d504f-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d504f-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d504f-111">Robust Programming</span></span>  

 <span data-ttu-id="d504f-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d504f-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d504f-113">Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d504f-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d504f-114">`newName`yol bilgilerini<xref:System.ArgumentException>içerir ( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d504f-115">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d504f-116">`newName`veya `Nothing` boş bir<xref:System.ArgumentNullException>dize ( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d504f-117">Kaynak dosya geçerli değil veya yok<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="d504f-118">() adlarında `newName` belirtilen varolan bir dosya<xref:System.IO.IOException>veya dizin vardır.</span><span class="sxs-lookup"><span data-stu-id="d504f-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d504f-119">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d504f-120">Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="d504f-121">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d504f-122">Kullanıcı nın gerekli izni yoktur<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="d504f-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d504f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d504f-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="d504f-124">Nasıl Yapılır: Dosya Taşıma</span><span class="sxs-lookup"><span data-stu-id="d504f-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [<span data-ttu-id="d504f-125">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="d504f-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="d504f-126">Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d504f-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="d504f-127">Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d504f-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
