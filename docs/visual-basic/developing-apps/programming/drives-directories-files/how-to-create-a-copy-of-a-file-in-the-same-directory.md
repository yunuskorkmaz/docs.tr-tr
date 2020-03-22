---
title: 'Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 33a4f5424ac50de7b5dc988034ca15127dc1ed02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348816"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="07483-102">Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07483-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="07483-103">Dosyaları `My.Computer.FileSystem.CopyFile` kopyalamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="07483-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="07483-104">Parametreler, varolan dosyaların üzerine yazmanızı, dosyayı yeniden adlandırmanızı, işlemin ilerlemesini göstermenizi ve kullanıcının işlemi iptal etmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="07483-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="07483-105">Aynı klasördeki bir dosyanın kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="07483-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="07483-106">Hedef `CopyFile` dosyayı ve konumu sağlayarak yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="07483-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="07483-107">Aşağıdaki `test.txt` örnek, .. `test2.txt`</span><span class="sxs-lookup"><span data-stu-id="07483-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="07483-108">Aynı klasördeki bir dosyanın kopyasını oluşturmak için varolan dosyaların üzerine yazma</span><span class="sxs-lookup"><span data-stu-id="07483-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="07483-109">Yöntemi kullanarak, hedef dosyayı ve konumu sağlama `True`ve '' a ayarlama `overwrite` `CopyFile`</span><span class="sxs-lookup"><span data-stu-id="07483-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="07483-110">Aşağıdaki örnek, `test.txt` çağrılan `test2.txt` bir kopyasını oluşturur ve bu ada göre varolan dosyaların üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="07483-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="07483-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="07483-111">Robust Programming</span></span>  

 <span data-ttu-id="07483-112">Aşağıdaki koşullar bir özel durum atılmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="07483-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="07483-113">Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="07483-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="07483-114">Sistem mutlak yolu alamadım<xref:System.ArgumentException>( ).</span><span class="sxs-lookup"><span data-stu-id="07483-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="07483-115">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="07483-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="07483-116">Kaynak dosya geçerli değil veya yok<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="07483-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="07483-117">Birleştirilmiş yol varolan bir<xref:System.IO.IOException>dizine işaret eder ( ).</span><span class="sxs-lookup"><span data-stu-id="07483-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="07483-118">Hedef dosya var `overwrite` ve `False` ayarlanır<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="07483-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="07483-119">Kullanıcının dosyaya erişmek için yeterli izinleri yoktur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="07483-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="07483-120">Hedef klasörde aynı ada sahip bir<xref:System.IO.IOException>dosya kullanılıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="07483-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="07483-121">Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="07483-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="07483-122">`ShowUI`ayarlanır `True` `onUserCancel` , olarak ayarlanır `ThrowException`ve kullanıcı işlemi iptal etti<xref:System.OperationCanceledException>( ).</span><span class="sxs-lookup"><span data-stu-id="07483-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="07483-123">`ShowUI`ayarlanır `True` `onUserCancel` ve belirtilmemiş bir G/Ç hatası oluşur (<xref:System.OperationCanceledException>). `ThrowException`</span><span class="sxs-lookup"><span data-stu-id="07483-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="07483-124">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="07483-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="07483-125">Kullanıcının gerekli izni yoktur<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="07483-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="07483-126">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="07483-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07483-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07483-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="07483-128">Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="07483-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="07483-129">Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07483-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="07483-130">Nasıl Yapılır: Bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="07483-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="07483-131">Nasıl Yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="07483-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
