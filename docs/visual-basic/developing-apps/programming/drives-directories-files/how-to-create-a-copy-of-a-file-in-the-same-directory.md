---
title: "Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af592e16bb1f7f0bbb188b2ea39394ec1074d302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="01b62-102">Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01b62-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="01b62-103">Kullanım `My.Computer.FileSystem.CopyFile` dosyaları kopyalamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="01b62-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="01b62-104">Parametreler, var olan dosyaların üzerine yazıp, dosyayı yeniden adlandırın, işlemin ilerlemesini Göster ve kullanıcı işlemi iptal izin ver olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="01b62-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="01b62-105">Aynı klasörde bir dosyanın bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="01b62-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="01b62-106">Kullanım `CopyFile` yöntemi, hedef dosya ve konum belirtin.</span><span class="sxs-lookup"><span data-stu-id="01b62-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="01b62-107">Aşağıdaki örnek, bir kopyasını oluşturur `test.txt` adlı `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="01b62-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="01b62-108">Var olan dosyaların üzerine yazılması aynı klasörde bir dosyanın bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="01b62-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="01b62-109">Kullanım `CopyFile` için bir hedef dosya ve konum sağlayarak ve ayarlama yöntemi `overwrite` için `True`.</span><span class="sxs-lookup"><span data-stu-id="01b62-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="01b62-110">Aşağıdaki örnek, bir kopyasını oluşturur `test.txt` adlı `test2.txt` ve bu adı mevcut dosyaların üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="01b62-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="01b62-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="01b62-111">Robust Programming</span></span>  
 <span data-ttu-id="01b62-112">Aşağıdaki koşullar, bir özel durum oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="01b62-112">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="01b62-113">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="01b62-114">Sistem mutlak yolu alınamadı (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="01b62-115">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="01b62-116">Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="01b62-117">Birleşik yolu işaret ediyor. Varolan bir dizin (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="01b62-118">Hedef dosyanın var olduğundan ve `overwrite` ayarlanır `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="01b62-119">Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="01b62-120">Hedef klasörde aynı ada sahip bir dosya kullanımda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="01b62-121">Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="01b62-122">`ShowUI`ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, ve kullanıcı işlemi iptal etti (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="01b62-123">`ShowUI`ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, belirtilmeyen bir g/ç hatası nedeniyle oluşur (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="01b62-124">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="01b62-125">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="01b62-126">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="01b62-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b62-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01b62-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="01b62-128">Nasıl yapılır: belirli düzendeki dosyaları dizine kopyalama</span><span class="sxs-lookup"><span data-stu-id="01b62-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="01b62-129">Nasıl yapılır: farklı dizinde dosya kopyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="01b62-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="01b62-130">Nasıl yapılır: bir dizini diğerine kopyalama</span><span class="sxs-lookup"><span data-stu-id="01b62-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="01b62-131">Nasıl yapılır: bir dosyayı yeniden adlandırın</span><span class="sxs-lookup"><span data-stu-id="01b62-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
