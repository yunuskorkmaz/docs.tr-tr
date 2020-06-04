---
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
ms.openlocfilehash: 741f0c80ba268369ebdd598460e9d5fa13d09571
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401686"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="cec10-102">Nasıl Yapılır: Visual Basic'te Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cec10-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="cec10-103">`My.Computer.FileSystem.CopyFile`Dosyaları kopyalamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cec10-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="cec10-104">Parametreler var olan dosyaların üzerine yazılmasına, dosyayı yeniden adlandırmanıza, işlemin ilerlemesini göstermeye ve kullanıcının işlemi iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cec10-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="cec10-105">Aynı klasörde bir dosyanın kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cec10-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="cec10-106">`CopyFile`Hedef dosyayı ve konumu sağlayarak yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cec10-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="cec10-107">Aşağıdaki örnek, çağrılan bir kopyasını oluşturur `test.txt` `test2.txt` .</span><span class="sxs-lookup"><span data-stu-id="cec10-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="cec10-108">Varolan dosyaların üzerine yazarak aynı klasörde bir dosyanın kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cec10-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="cec10-109">Yöntemini kullanarak `CopyFile` hedef dosya ve konumu ve olarak ayarını yapın `overwrite` `True` .</span><span class="sxs-lookup"><span data-stu-id="cec10-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="cec10-110">Aşağıdaki örnek, adlı bir kopyasını oluşturur `test.txt` `test2.txt` ve bu ada göre var olan dosyaların üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="cec10-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cec10-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="cec10-111">Robust Programming</span></span>  

 <span data-ttu-id="cec10-112">Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="cec10-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="cec10-113">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="cec10-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="cec10-114">Sistem mutlak yolu ( <xref:System.ArgumentException> ) alamadı.</span><span class="sxs-lookup"><span data-stu-id="cec10-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="cec10-115">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="cec10-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="cec10-116">Kaynak dosya geçerli değil veya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="cec10-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="cec10-117">Birleşik yol, var olan bir dizine () işaret eder <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="cec10-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cec10-118">Hedef dosya vardır ve `overwrite` () olarak ayarlanır `False` <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="cec10-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cec10-119">Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="cec10-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cec10-120">Hedef klasörde aynı ada sahip bir dosya kullanımda ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="cec10-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cec10-121">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="cec10-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="cec10-122">`ShowUI`olarak ayarlanır `True` , olarak `onUserCancel` ayarlanır `ThrowException` ve Kullanıcı işlemi () iptal etti <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="cec10-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="cec10-123">`ShowUI`, olarak ayarlanır, olarak `True` `onUserCancel` ayarlanır `ThrowException` ve belirtilmemiş g/ç hatası oluşur ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="cec10-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="cec10-124">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="cec10-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="cec10-125">Kullanıcı gerekli izne () sahip değil <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="cec10-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="cec10-126">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="cec10-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec10-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cec10-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="cec10-128">Nasıl yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="cec10-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="cec10-129">Nasıl yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cec10-129">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="cec10-130">Nasıl yapılır: Bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="cec10-130">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="cec10-131">Nasıl yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="cec10-131">How to: Rename a File</span></span>](how-to-rename-a-file.md)
