---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic ' de aynı dizinde bir dosyanın kopyasını oluşturma"
title: 'Nasıl yapılır: Aynı Dizinde Dosya Kopyası Oluşturma'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 27fecc22a9317dd45e663aa37884c6c1f1e36349
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797620"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="0d746-103">Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d746-103">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="0d746-104">`My.Computer.FileSystem.CopyFile`Dosyaları kopyalamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d746-104">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="0d746-105">Parametreler var olan dosyaların üzerine yazılmasına, dosyayı yeniden adlandırmanıza, işlemin ilerlemesini göstermeye ve kullanıcının işlemi iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d746-105">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="0d746-106">Aynı klasörde bir dosyanın kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0d746-106">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="0d746-107">`CopyFile`Hedef dosyayı ve konumu sağlayarak yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d746-107">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="0d746-108">Aşağıdaki örnek, çağrılan bir kopyasını oluşturur `test.txt` `test2.txt` .</span><span class="sxs-lookup"><span data-stu-id="0d746-108">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="0d746-109">Varolan dosyaların üzerine yazarak aynı klasörde bir dosyanın kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0d746-109">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="0d746-110">Yöntemini kullanarak `CopyFile` hedef dosya ve konumu ve olarak ayarını yapın `overwrite` `True` .</span><span class="sxs-lookup"><span data-stu-id="0d746-110">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="0d746-111">Aşağıdaki örnek, adlı bir kopyasını oluşturur `test.txt` `test2.txt` ve bu ada göre var olan dosyaların üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="0d746-111">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0d746-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0d746-112">Robust Programming</span></span>  

 <span data-ttu-id="0d746-113">Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0d746-113">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="0d746-114">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0d746-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0d746-115">Sistem mutlak yolu ( <xref:System.ArgumentException> ) alamadı.</span><span class="sxs-lookup"><span data-stu-id="0d746-115">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0d746-116">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="0d746-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0d746-117">Kaynak dosya geçerli değil veya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="0d746-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="0d746-118">Birleşik yol, var olan bir dizine () işaret eder <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="0d746-118">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0d746-119">Hedef dosya vardır ve `overwrite` () olarak ayarlanır `False` <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="0d746-119">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0d746-120">Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="0d746-120">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0d746-121">Hedef klasörde aynı ada sahip bir dosya kullanımda ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="0d746-121">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0d746-122">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="0d746-122">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0d746-123">`ShowUI` olarak ayarlanır `True` , olarak `onUserCancel` ayarlanır `ThrowException` ve Kullanıcı işlemi () iptal etti <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="0d746-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="0d746-124">`ShowUI` , olarak ayarlanır, olarak `True` `onUserCancel` ayarlanır `ThrowException` ve belirtilmemiş g/ç hatası oluşur ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="0d746-124">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="0d746-125">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="0d746-125">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="0d746-126">Kullanıcı gerekli izne () sahip değil <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="0d746-126">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="0d746-127">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="0d746-127">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d746-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d746-128">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="0d746-129">Nasıl yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="0d746-129">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="0d746-130">Nasıl yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d746-130">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="0d746-131">Nasıl yapılır: Bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="0d746-131">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="0d746-132">Nasıl yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="0d746-132">How to: Rename a File</span></span>](how-to-rename-a-file.md)
