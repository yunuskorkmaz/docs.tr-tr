---
title: 'Nasıl Yapılır: Dosya Taşıma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 29c64a7a81028d47bf489212e6d8faec5e8dda75
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335367"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="00366-102">Nasıl Yapılır: Visual Basic'te Dosya Taşıma</span><span class="sxs-lookup"><span data-stu-id="00366-102">How to: Move a File in Visual Basic</span></span>

<span data-ttu-id="00366-103">`My.Computer.FileSystem.MoveFile` yöntemi, bir dosyayı başka bir klasöre taşımak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00366-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="00366-104">Hedef yapı yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00366-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="00366-105">Bir dosyayı taşımak için</span><span class="sxs-lookup"><span data-stu-id="00366-105">To move a file</span></span>  
  
- <span data-ttu-id="00366-106">Kaynak dosya ve hedef dosya için dosya adını ve konumunu belirterek dosyayı taşımak için `MoveFile` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="00366-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="00366-107">Bu örnek `test.txt` adlı dosyayı `TestDir1` `TestDir2`olarak taşır.</span><span class="sxs-lookup"><span data-stu-id="00366-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="00366-108">Hedef dosya adının, kaynak dosya adıyla aynı olmasına rağmen belirtildiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="00366-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="00366-109">Bir dosyayı taşımak ve yeniden adlandırmak için</span><span class="sxs-lookup"><span data-stu-id="00366-109">To move a file and rename it</span></span>  
  
- <span data-ttu-id="00366-110">Kaynak dosya adını ve konumunu, hedef konumu ve hedef konumdaki yeni adı belirterek dosyayı taşımak için `MoveFile` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="00366-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="00366-111">Bu örnek, `TestDir1` `test.txt` adlı dosyayı `TestDir2` 'e taşır ve `nexttest.txt`yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="00366-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="00366-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="00366-112">Robust Programming</span></span>  

 <span data-ttu-id="00366-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="00366-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="00366-114">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.</span><span class="sxs-lookup"><span data-stu-id="00366-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="00366-115">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="00366-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="00366-116">`destinationFileName` `Nothing` veya boş bir dizedir (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="00366-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="00366-117">Kaynak dosya geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="00366-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="00366-118">Birleşik yol, var olan bir dizine işaret eder, hedef dosya bulunur ve `overwrite` `False`, hedef dizindeki aynı ada sahip bir dosya kullanımda veya kullanıcı dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="00366-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="00366-119">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="00366-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="00366-120">`showUI` `True`olarak ayarlanır `onUserCancel` `ThrowException`olarak ayarlanır ve Kullanıcı işlemi iptal etti ya da belirtilmeyen g/ç hatası oluşur (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="00366-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="00366-121">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="00366-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="00366-122">Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="00366-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="00366-123">Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="00366-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00366-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00366-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="00366-125">Nasıl Yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="00366-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [<span data-ttu-id="00366-126">Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="00366-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="00366-127">Nasıl Yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="00366-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
