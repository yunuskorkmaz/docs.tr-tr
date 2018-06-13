---
title: "Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 1584e2a768562670662d3a9636d23f0ffe38547e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589479"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="89f2b-102">Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="89f2b-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>
<span data-ttu-id="89f2b-103">`My.Computer.FileSystem.CopyFile` Yöntemi dosyaları kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="89f2b-104">Parametrelerinin varolan dosyaların üzerine yazıp, dosyayı yeniden adlandırın, işlemin ilerlemesini Göster ve kullanıcı işlemi iptal etme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="89f2b-105">Bir metin dosyası başka bir klasöre kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="89f2b-105">To copy a text file to another folder</span></span>  
  
-   <span data-ttu-id="89f2b-106">Kullanım `CopyFile` yöntemi bir kaynak dosya hem de hedef dizin belirten bir dosyasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89f2b-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="89f2b-107">`overwrite` Parametresi varolan dosyaların üzerine gerekip gerekmediğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="89f2b-108">Aşağıdaki kod örnekleri nasıl kullanılacağını gösteren `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="89f2b-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="89f2b-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="89f2b-109">Robust Programming</span></span>  
 <span data-ttu-id="89f2b-110">Aşağıdaki koşullar, bir özel durum oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="89f2b-110">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="89f2b-111">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="89f2b-112">Sistem mutlak yolu alınamadı (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="89f2b-113">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="89f2b-114">Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="89f2b-115">Birleşik yolu işaret ediyor. Varolan bir dizin (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="89f2b-116">Hedef dosyanın var olduğundan ve `overwrite` ayarlanır `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="89f2b-117">Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="89f2b-118">Hedef klasörde aynı ada sahip bir dosya kullanımda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="89f2b-119">Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="89f2b-120">`ShowUI` ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, ve kullanıcı işlemi iptal etti (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="89f2b-121">`ShowUI` ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, belirtilmeyen bir g/ç hatası nedeniyle oluşur (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="89f2b-122">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="89f2b-123">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="89f2b-124">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="89f2b-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f2b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89f2b-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="89f2b-126">Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="89f2b-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="89f2b-127">Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="89f2b-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [<span data-ttu-id="89f2b-128">Nasıl Yapılır: Bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="89f2b-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="89f2b-129">Nasıl Yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="89f2b-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
