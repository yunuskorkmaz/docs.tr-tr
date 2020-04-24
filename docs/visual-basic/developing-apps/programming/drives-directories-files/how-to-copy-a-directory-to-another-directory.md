---
title: 'Nasıl Yapılır: Bir Dizini Diğerine Kopyalama'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: a23079f093f53ab8e20eb71c684a594dcf7f894b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348858"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="5cef8-102">Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="5cef8-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>

<span data-ttu-id="5cef8-103">Bir dizini <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> başka bir dizine kopyalamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cef8-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="5cef8-104">Bu yöntem, dizinin içeriğini ve dizinin kendisini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="5cef8-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="5cef8-105">Hedef dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5cef8-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="5cef8-106">Hedef konumda aynı ada sahip bir dizin varsa ve `overwrite` olarak `False`ayarlanırsa, iki dizinin içeriği birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5cef8-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="5cef8-107">İşlem sırasında dizin için yeni bir ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cef8-107">You can specify a new name for the directory during the operation.</span></span>

<span data-ttu-id="5cef8-108">Dosyaları bir dizin içinde kopyalarken, özel bir dosya (örneğin, birleştirme `overwrite` sırasında var olan bir dosya gibi) nedeniyle özel durumlar oluşturulabilir. `False`</span><span class="sxs-lookup"><span data-stu-id="5cef8-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="5cef8-109">Bu tür özel durumlar oluştuğunda, `Data` özelliği dosya veya dizin yolunun anahtar olduğu ve belirli özel durum iletisinin karşılık gelen değerde bulunduğu girdileri tutan tek bir özel durum halinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5cef8-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>

## <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="5cef8-110">Bir dizini başka bir dizine kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="5cef8-110">To copy a directory to another directory</span></span>

- <span data-ttu-id="5cef8-111">Kaynak ve `CopyDirectory` hedef dizin adlarını belirterek yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cef8-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="5cef8-112">Aşağıdaki örnek, var olan dosyaların üzerine `TestDirectory1` yazarak `TestDirectory2`adlı dizini içine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="5cef8-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    <span data-ttu-id="5cef8-113">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cef8-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="5cef8-114">Kod parçacığı seçicide **dosya sistemi Işleme sürücülerinde, klasörlerinde ve dosyalarında**bulunur.</span><span class="sxs-lookup"><span data-stu-id="5cef8-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="5cef8-115">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="5cef8-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="robust-programming"></a><span data-ttu-id="5cef8-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="5cef8-116">Robust Programming</span></span>

<span data-ttu-id="5cef8-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="5cef8-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="5cef8-118">Dizin için belirtilen yeni ad iki nokta içerir (:) veya eğik çizgi (\ veya/)<xref:System.ArgumentException>().</span><span class="sxs-lookup"><span data-stu-id="5cef8-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="5cef8-119">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="5cef8-120">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5cef8-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="5cef8-121">`destinationDirectoryName``Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="5cef8-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>

- <span data-ttu-id="5cef8-122">Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="5cef8-123">Kaynak dizin bir kök dizin (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="5cef8-124">Birleşik yol, var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5cef8-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="5cef8-125">Kaynak yolu ve hedef yolu aynı (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="5cef8-126">`ShowUI`, olarak `UIOption.AllDialogs` ayarlanır ve Kullanıcı işlemi iptal eder veya dizindeki bir veya daha fazla Dosya kopyalanamıyor (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>

- <span data-ttu-id="5cef8-127">İşlem döngüsel (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>

- <span data-ttu-id="5cef8-128">Yol iki nokta içerir (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="5cef8-129">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="5cef8-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="5cef8-130">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="5cef8-131">Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5cef8-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="5cef8-132">Hedef dosya var, ancak erişilemez (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="5cef8-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="5cef8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cef8-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="5cef8-134">Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="5cef8-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="5cef8-135">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="5cef8-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
