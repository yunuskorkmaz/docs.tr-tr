---
title: 'Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348838"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="1dad5-102">Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1dad5-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="1dad5-103">Yöntem, `My.Computer.FileSystem.CopyFile` dosyaları kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dad5-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="1dad5-104">Parametreleri, varolan dosyaların üzerine yazma, dosyayı yeniden adlandırma, işlemin ilerlemesini gösterme ve kullanıcının işlemi iptal etmesine izin verme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dad5-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="1dad5-105">Metin dosyasını başka bir klasöre kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="1dad5-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="1dad5-106">Kaynak `CopyFile` dosya ve hedef dizini belirterek bir dosyayı kopyalamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1dad5-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="1dad5-107">Parametre, `overwrite` varolan dosyaların üzerine yazıp yazılmayacağınızı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1dad5-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="1dad5-108">Aşağıdaki kod örnekleri nasıl `CopyFile`kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dad5-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1dad5-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1dad5-109">Robust Programming</span></span>  

 <span data-ttu-id="1dad5-110">Aşağıdaki koşullar bir özel durum atılmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="1dad5-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="1dad5-111">Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="1dad5-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="1dad5-112">Sistem mutlak yolu alamadım<xref:System.ArgumentException>( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="1dad5-113">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="1dad5-114">Kaynak dosya geçerli değil veya yok<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="1dad5-115">Birleştirilmiş yol varolan bir<xref:System.IO.IOException>dizine işaret eder ( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1dad5-116">Hedef dosya var `overwrite` ve `False` ayarlanır<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1dad5-117">Kullanıcının dosyaya erişmek için yeterli izinleri yoktur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="1dad5-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1dad5-118">Hedef klasörde aynı ada sahip bir<xref:System.IO.IOException>dosya kullanılıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1dad5-119">Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="1dad5-120">`ShowUI`ayarlanır `True` `onUserCancel` , olarak ayarlanır `ThrowException`ve kullanıcı işlemi iptal etti<xref:System.OperationCanceledException>( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="1dad5-121">`ShowUI`ayarlanır `True` `onUserCancel` ve belirtilmemiş bir G/Ç hatası oluşur (<xref:System.OperationCanceledException>). `ThrowException`</span><span class="sxs-lookup"><span data-stu-id="1dad5-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="1dad5-122">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="1dad5-123">Kullanıcının gerekli izni yoktur<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="1dad5-124">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="1dad5-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dad5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dad5-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="1dad5-126">Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="1dad5-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="1dad5-127">Nasıl Yapılır: Aynı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1dad5-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="1dad5-128">Nasıl Yapılır: Bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="1dad5-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="1dad5-129">Nasıl Yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="1dad5-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
