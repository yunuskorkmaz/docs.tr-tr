---
title: "Nasıl yapılır: Visual Basic'te farklı dizinde dosya kopyası oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 25b9ff1e3a97acd69b6a885788dbc83ce19e71f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813425"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="42acc-102">Nasıl yapılır: Visual Basic'te farklı dizinde dosya kopyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="42acc-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>
<span data-ttu-id="42acc-103">`My.Computer.FileSystem.CopyFile` Yöntemi dosyaları kopyalamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="42acc-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="42acc-104">Parametrelerini varolan dosyaların üzerine yaz, dosyayı yeniden adlandırın, işlemin ilerlemesini Göster ve kullanıcı işlemi iptal etme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="42acc-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="42acc-105">Bir metin dosyası başka bir klasöre kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="42acc-105">To copy a text file to another folder</span></span>  
  
-   <span data-ttu-id="42acc-106">Kullanım `CopyFile` yöntemi bir kaynak dosyası ve hedef dizini belirten bir dosyasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42acc-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="42acc-107">`overwrite` Parametre, var olan dosyaların üzerine yazılıp yazılmayacağını belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="42acc-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="42acc-108">Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="42acc-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="42acc-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="42acc-109">Robust Programming</span></span>  
 <span data-ttu-id="42acc-110">Aşağıdaki koşullar, bir özel durum oluşturulmasına neden:</span><span class="sxs-lookup"><span data-stu-id="42acc-110">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="42acc-111">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="42acc-112">Sistem mutlak yolu alınamadı (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="42acc-113">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="42acc-114">Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="42acc-115">Birleşik yolun mevcut bir dizine işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="42acc-116">Hedef dosya var ve `overwrite` ayarlanır `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="42acc-117">Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="42acc-118">Hedef klasörde aynı adda bir dosya kullanımda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="42acc-119">Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="42acc-120">`ShowUI` ayarlanır `True`, `onUserCancel` ayarlanır `ThrowException`, ve kullanıcı işlemi iptal etti (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="42acc-121">`ShowUI` ayarlanır `True`, `onUserCancel` ayarlanır `ThrowException`, belirtilmeyen bir g/ç hatası oluşur (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="42acc-122">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="42acc-123">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="42acc-124">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="42acc-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42acc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42acc-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="42acc-126">Nasıl yapılır: Belirli bir düzendeki dosyaları dizine kopyalama</span><span class="sxs-lookup"><span data-stu-id="42acc-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="42acc-127">Nasıl yapılır: Aynı dizinde dosya kopyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="42acc-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="42acc-128">Nasıl yapılır: Bir dizini diğerine kopyalama</span><span class="sxs-lookup"><span data-stu-id="42acc-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="42acc-129">Nasıl yapılır: Dosyayı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="42acc-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
