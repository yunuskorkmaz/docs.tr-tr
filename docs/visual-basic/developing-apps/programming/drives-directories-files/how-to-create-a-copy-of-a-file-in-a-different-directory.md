---
title: 'Nasıl yapılır: Farklı Dizinde Dosya Kopyası Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 3b4b41e105d6bb6a17fbb688aa4718b33c23b9d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401699"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="ed9cc-102">Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed9cc-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="ed9cc-103">`My.Computer.FileSystem.CopyFile`Yöntemi, dosyaları kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed9cc-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="ed9cc-104">Parametreleri var olan dosyaların üzerine yazma, dosyayı yeniden adlandırma, işlemin ilerlemesini gösterme ve kullanıcının işlemi iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed9cc-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="ed9cc-105">Bir metin dosyasını başka bir klasöre kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="ed9cc-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="ed9cc-106">`CopyFile`Kaynak dosya ve hedef dizin belirterek bir dosyayı kopyalamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed9cc-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="ed9cc-107">`overwrite`Parametresi, var olan dosyaların üzerine yazılıp yazılmayacağını belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="ed9cc-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="ed9cc-108">Aşağıdaki kod örnekleri, nasıl kullanılacağını göstermektedir `CopyFile` .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ed9cc-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ed9cc-109">Robust Programming</span></span>  

 <span data-ttu-id="ed9cc-110">Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ed9cc-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="ed9cc-111">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ed9cc-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="ed9cc-112">Sistem mutlak yolu ( <xref:System.ArgumentException> ) alamadı.</span><span class="sxs-lookup"><span data-stu-id="ed9cc-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="ed9cc-113">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="ed9cc-114">Kaynak dosya geçerli değil veya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="ed9cc-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="ed9cc-115">Birleşik yol, var olan bir dizine () işaret eder <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ed9cc-116">Hedef dosya vardır ve `overwrite` () olarak ayarlanır `False` <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ed9cc-117">Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ed9cc-118">Hedef klasörde aynı ada sahip bir dosya kullanımda ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="ed9cc-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ed9cc-119">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="ed9cc-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="ed9cc-120">`ShowUI`olarak ayarlanır `True` , olarak `onUserCancel` ayarlanır `ThrowException` ve Kullanıcı işlemi () iptal etti <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="ed9cc-121">`ShowUI`, olarak ayarlanır, olarak `True` `onUserCancel` ayarlanır `ThrowException` ve belirtilmemiş g/ç hatası oluşur ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="ed9cc-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="ed9cc-122">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="ed9cc-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="ed9cc-123">Kullanıcı gerekli izne () sahip değil <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="ed9cc-124">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="ed9cc-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed9cc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed9cc-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="ed9cc-126">Nasıl yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="ed9cc-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="ed9cc-127">Nasıl yapılır: Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed9cc-127">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="ed9cc-128">Nasıl yapılır: Bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="ed9cc-128">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="ed9cc-129">Nasıl yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="ed9cc-129">How to: Rename a File</span></span>](how-to-rename-a-file.md)
