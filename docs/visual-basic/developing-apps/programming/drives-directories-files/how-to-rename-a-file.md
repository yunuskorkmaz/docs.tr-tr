---
description: 'Daha fazla bilgi: nasıl yapılır: Visual Basic bir dosyayı yeniden adlandırma'
title: 'Nasıl yapılır: Dosyayı Yeniden Adlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: cf182fa94befdfdcb1568052a0193d483670cf49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797412"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="c08a5-103">Nasıl Yapılır: Visual Basic'te Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="c08a5-103">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="c08a5-104">`RenameFile` `My.Computer.FileSystem` Geçerli konumu, dosya adını ve yeni dosya adını sağlayarak bir dosyayı yeniden adlandırmak için nesnesinin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c08a5-104">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="c08a5-105">Bu yöntem bir dosyayı taşımak için kullanılamaz; `MoveFile` dosyayı taşımak ve yeniden adlandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c08a5-105">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="c08a5-106">Bir dosyayı yeniden adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="c08a5-106">To rename a file</span></span>  
  
- <span data-ttu-id="c08a5-107">`My.Computer.FileSystem.RenameFile`Bir dosyayı yeniden adlandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c08a5-107">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="c08a5-108">Bu örnek, olarak adlandırılan dosyayı yeniden adlandırır `Test.txt` `SecondTest.txt` .</span><span class="sxs-lookup"><span data-stu-id="c08a5-108">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="c08a5-109">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c08a5-109">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c08a5-110">Kod parçacığı seçicide kod parçacığı, **dosya sistemi Işleme sürücülerinde, klasörlerinde ve dosyalarında** bulunur.</span><span class="sxs-lookup"><span data-stu-id="c08a5-110">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="c08a5-111">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c08a5-111">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c08a5-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c08a5-112">Robust Programming</span></span>  

 <span data-ttu-id="c08a5-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c08a5-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c08a5-114">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c08a5-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="c08a5-115">`newName` yol bilgilerini ( <xref:System.ArgumentException> ) içerir.</span><span class="sxs-lookup"><span data-stu-id="c08a5-115">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="c08a5-116">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="c08a5-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="c08a5-117">`newName``Nothing`ya da boş bir dizedir ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="c08a5-117">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="c08a5-118">Kaynak dosya geçerli değil veya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="c08a5-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="c08a5-119">() İçinde belirtilen ada sahip bir dosya veya dizin var `newName` <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="c08a5-119">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="c08a5-120">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="c08a5-120">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="c08a5-121">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="c08a5-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="c08a5-122">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="c08a5-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="c08a5-123">Kullanıcı gerekli izne () sahip değil <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="c08a5-123">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c08a5-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c08a5-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="c08a5-125">Nasıl yapılır: Dosya Taşıma</span><span class="sxs-lookup"><span data-stu-id="c08a5-125">How to: Move a File</span></span>](how-to-move-a-file.md)
- [<span data-ttu-id="c08a5-126">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="c08a5-126">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="c08a5-127">Nasıl yapılır: Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c08a5-127">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="c08a5-128">Nasıl yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c08a5-128">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
