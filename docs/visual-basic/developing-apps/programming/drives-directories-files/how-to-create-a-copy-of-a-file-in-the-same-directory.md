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
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="18236-102">Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="18236-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="18236-103">Dosyaları kopyalamak `My.Computer.FileSystem.CopyFile` için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="18236-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="18236-104">Parametreler var olan dosyaların üzerine yazılmasına, dosyayı yeniden adlandırmanıza, işlemin ilerlemesini göstermeye ve kullanıcının işlemi iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="18236-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="18236-105">Aynı klasörde bir dosyanın kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="18236-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="18236-106">Hedef dosyayı `CopyFile` ve konumu sağlayarak yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="18236-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="18236-107">Aşağıdaki örnek, `test.txt` çağrılan `test2.txt`bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18236-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="18236-108">Varolan dosyaların üzerine yazarak aynı klasörde bir dosyanın kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="18236-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="18236-109">`CopyFile` Yöntemini kullanarak hedef dosya ve konumu ve olarak `overwrite` `True`ayarını yapın.</span><span class="sxs-lookup"><span data-stu-id="18236-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="18236-110">Aşağıdaki örnek, `test.txt` adlı `test2.txt` bir kopyasını oluşturur ve bu ada göre var olan dosyaların üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="18236-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="18236-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="18236-111">Robust Programming</span></span>  

 <span data-ttu-id="18236-112">Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="18236-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="18236-113">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="18236-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="18236-114">Sistem mutlak yolu (<xref:System.ArgumentException>) alamadı.</span><span class="sxs-lookup"><span data-stu-id="18236-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="18236-115">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="18236-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="18236-116">Kaynak dosya geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="18236-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="18236-117">Birleşik yol, var olan bir dizine (<xref:System.IO.IOException>) işaret eder.</span><span class="sxs-lookup"><span data-stu-id="18236-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="18236-118">Hedef dosya vardır ve `overwrite` ( `False` <xref:System.IO.IOException>) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="18236-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="18236-119">Kullanıcı, dosyaya (<xref:System.IO.IOException>) erişmek için yeterli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="18236-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="18236-120">Hedef klasörde aynı ada sahip bir dosya kullanımda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="18236-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="18236-121">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="18236-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="18236-122">`ShowUI`olarak ayarlanır `True`, `onUserCancel` olarak ayarlanır `ThrowException`ve Kullanıcı işlemi (<xref:System.OperationCanceledException>) iptal etti.</span><span class="sxs-lookup"><span data-stu-id="18236-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="18236-123">`ShowUI``True`, `onUserCancel` olarak ayarlanır, olarak ayarlanır `ThrowException`ve belirtilmemiş g/ç hatası oluşur (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="18236-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="18236-124">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="18236-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="18236-125">Kullanıcı gerekli izne (<xref:System.UnauthorizedAccessException>) sahip değil.</span><span class="sxs-lookup"><span data-stu-id="18236-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="18236-126">Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="18236-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18236-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18236-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="18236-128">Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="18236-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="18236-129">Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="18236-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="18236-130">Nasıl Yapılır: Bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="18236-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="18236-131">Nasıl Yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="18236-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
